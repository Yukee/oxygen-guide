---
name: generate-image
description: Use when the user asks to generate an illustration or image for the guide, or says /generate-image. Takes a description of the desired image and an output filename.
---

# Generate Image with Gemini 3 Pro

Generate illustrations for the guide using the `gemini-3-pro-image-preview` model via Google's Generative Language API.

## Input

The user provides:
1. A description of the image they want
2. An output filename (e.g., `illustration-dose-spectrum.jpg`)

If the user doesn't provide a filename, infer one from the description using the project convention: `illustration-<descriptive-name>.jpg`.

## Style Guidelines

All generated images should match the project's existing illustration style:
- **Clean, flat infographic style** — not photorealistic
- **Color palette**: Blue and teal on light cream/white backgrounds
- **Clear labels and text annotations** where appropriate
- **Medical/educational feel** — informational, not decorative
- **16:9 aspect ratio** for consistency with existing illustrations

When writing the prompt, always prepend this style prefix:

> Clean flat infographic illustration on a light cream background. Blue and teal color palette. Medical educational style, not photorealistic. Simple clean lines and shapes.

Then append the user's specific description.

## Generation Steps

### 1. Build the prompt

Combine the style prefix with the user's description. If the user's description is vague, flesh it out with specifics that would make a useful illustration for the guide's target audience (50-something with no drug experience).

### 2. Call the API

Use this Python script via Bash, substituting `PROMPT_TEXT` and `OUTPUT_FILENAME`:

```bash
python3 << 'PYEOF'
import os, json, urllib.request, base64

key = os.environ['GOOGLE_API_KEY']
url = f'https://generativelanguage.googleapis.com/v1beta/models/gemini-3-pro-image-preview:generateContent?key={key}'

prompt = """PROMPT_TEXT"""

data = json.dumps({
    "contents": [{"parts": [{"text": prompt}]}],
    "generationConfig": {"responseModalities": ["IMAGE", "TEXT"]}
}).encode()

req = urllib.request.Request(url, data=data, headers={'Content-Type': 'application/json'})
resp = urllib.request.urlopen(req)
result = json.loads(resp.read())

parts = result['candidates'][0]['content']['parts']
for part in parts:
    if 'inlineData' in part:
        img_data = base64.b64decode(part['inlineData']['data'])
        outpath = '/Users/mace/clusterheaches/oxygen-guide/images/OUTPUT_FILENAME'
        with open(outpath, 'wb') as f:
            f.write(img_data)
        print(f'Saved: {outpath} ({len(img_data)} bytes)')
        break
    elif 'text' in part:
        print(f'Model text: {part["text"]}')
else:
    print('ERROR: No image in response')
    print(json.dumps(result, indent=2)[:1000])
PYEOF
```

### 3. Review the image

After generation, use the Read tool to view the image and verify:
- It matches the flat/blue/teal style of existing illustrations
- Text labels are legible and accurate (AI-generated text can have typos)
- The content matches what was requested

### 4. Regenerate if needed

If the image doesn't meet quality standards, adjust the prompt and regenerate. Common fixes:
- **Text came out garbled**: Simplify the text in the prompt, use fewer words per label
- **Wrong style**: Reinforce "flat infographic, not photorealistic" in the prompt
- **Missing elements**: Be more explicit about layout and positioning

### 5. Report

Tell the user:
- What file was generated and where
- Whether the image looks good or has issues (e.g., text typos)
- Suggest next steps (add to markdown, regenerate, etc.)

## Notes

- Images are saved to `images/` in the project root
- The `$GOOGLE_API_KEY` environment variable must be set
- The model returns JPEG images
- For multiple images, run generation calls in parallel using background tasks
- If you need to generate images AND add them to a markdown file, generate first, review, then add references using the pattern:
  ```markdown
  ![Alt text](images/filename.jpg)
  *Caption text*
  ```
