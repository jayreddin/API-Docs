# Document understanding

The Gemini API supports PDF input, including long documents (up to 3600 pages). Gemini models process PDFs with native vision, and are therefore able to understand both text and image contents inside documents. With native PDF vision support, Gemini models are able to:

- Analyze diagrams, charts, and tables inside documents
- Extract information into structured output formats
- Answer questions about visual and text contents in documents
- Summarize documents
- Transcribe document content (e.g. to HTML) preserving layouts and formatting, for use in downstream applications

## PDF input

For PDF payloads under 20MB, you can choose between uploading base64 encoded documents or directly uploading locally stored files.

### Technical details

Gemini 1.5 Pro and 1.5 Flash support a maximum of 3,600 document pages. Document pages must be in one of the following text data MIME types:

- PDF - `application/pdf`
- JavaScript - `application/x-javascript`, `text/javascript`
- Python - `application/x-python`, `text/x-python`
- TXT - `text/plain`
- HTML - `text/html`
- CSS - `text/css`
- Markdown - `text/md`
- CSV - `text/csv`
- XML - `text/xml`
- RTF - `text/rtf`

Each document page is equivalent to 258 tokens.

While there are no specific limits to the number of pixels in a document besides the model's context window, larger pages are scaled down to a maximum resolution of 3072x3072 while preserving their original aspect ratio, while smaller pages are scaled up to 768x768 pixels. There is no cost reduction for pages at lower sizes, other than bandwidth, or performance improvement for pages at higher resolution.

For best results:

- Rotate pages to the correct orientation before uploading.
- Avoid blurry pages.
- If using a single page, place the text prompt after the page.

### Large PDFs

You can use the File API to upload a document of any size. Always use the File API when the total request size (including the files, text prompt, system instructions, etc.) is larger than 20 MB.

Call [`media.upload`](https://ai.google.dev/api/rest/v1beta/media/upload) to upload a file using the File API. The following code uploads a document file and then uses the file in a call to [`models.generateContent`](https://ai.google.dev/api/generate-content#method:-models.generatecontent).

You can verify the API successfully stored the uploaded file and get its metadata by calling [`files.get`](https://ai.google.dev/api/rest/v1beta/files/get). Only the `name` (and by extension, the `uri`) are unique.

### Multiple PDFs

The Gemini API is capable of processing multiple PDF documents in a single request, as long as the combined size of the documents and the text prompt stays within the model's context window.