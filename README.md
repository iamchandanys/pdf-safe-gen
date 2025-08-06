# pdf-safe-gen

A utility to convert DOCX files to PDF, apply password protection to PDFs, and upload the protected PDFs to Azure Blob Storage.

## Features

- Convert DOCX files (from a remote URL) to PDF
- Password-protect generated PDFs
- Upload protected PDFs to Azure Blob Storage
- Temporary files are managed in the `temps/` directory

## Requirements

- Python 3.7+
- See [requirements.txt](requirements.txt) for dependencies

## Setup

1. Install dependencies:

   ```sh
   pip install -r requirements.txt
   ```

2. Create a `.env` file with the following variables:
   ```
   AZURE_BLOB_CONTAINER_NAME=your-container-name
   AZURE_BLOB_CONNECTION_STRING=your-connection-string
   ```

## Usage

The main workflow is implemented in [docx-pdf.ipynb](docx-pdf.ipynb). Example steps:

1. Set the remote DOCX URL, generate a unique file name, and choose a password.
2. Convert the DOCX to PDF:
   ```python
   convert_docx_to_pdf(remote_url, file_name)
   ```
3. Protect the PDF with a password:
   ```python
   protect_pdf(password, file_name)
   ```
4. Upload the protected PDF to Azure Blob Storage:
   ```python
   url = upload_pdf_to_blob(open(f"temps/{file_name}-protected.pdf", "rb").read())
   print(f"Protected PDF URL: {url}")
   ```

See the notebook for a complete example.

## Directory Structure

- `temps/` — Temporary files (DOCX, PDF, protected PDF)
- `docx-pdf.ipynb` — Main notebook with all logic
- `back_up.ipynb` — Example usage and backup code

## License

MIT License (add your license if
