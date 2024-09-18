# Document AI PDF Annotation Tool

This Python tool leverages the Google Cloud Document AI API to automatically annotate PDF documents by identifying and labeling form fields. Annotations are added directly to the PDF, and the resulting annotated PDF is saved as an output.

## Table of Contents

- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Command-Line Arguments](#command-line-arguments)
  - [Example](#example)
  - [How It Works](#how-it-works)
- [Google Cloud Setup](#google-cloud-setup)
- [License](#license)

## Features

- **PDF Annotation**: Annotates PDF form fields by detecting names and values through the Google Document AI API.
- **Automatic Processor Management**: Automatically creates a Document AI processor if none exists for the specified form processor type.
- **Secure PDF Saving**: Saves the output PDF with field annotations and disables annotation modification.
- **Region Selection**: Supports multi-regional locations for document processing.

## Requirements

- **Python**: Version 3.6 or later.
- **Google Cloud SDK**: Installed and authenticated for Google Cloud.
- **Libraries**:
  - `google-auth`
  - `google-cloud-documentai`
  - `pikepdf`

## Installation

1. Install Python dependencies:

    ```bash
    pip install google-auth google-cloud-documentai pikepdf
    ```

2. Set up Google Cloud authentication (see [Google Cloud Setup](#google-cloud-setup)).

## Usage

This tool is executed via the command line and requires several arguments to function. Below are the available command-line arguments and an example usage.

### Command-Line Arguments

- `-i, --input`: (Required) The file path of the input PDF that you want to annotate.
- `--output`: (Optional) Path to save the annotated PDF. If not provided, the annotated PDF will be saved in the same directory as the input file with `_annotated` appended to the filename.
- `--project-id`: (Optional) The Google Cloud Project ID used to call the Document AI API. If not provided, the default project from your Google Cloud authentication will be used.
- `--multi-region-location`: (Optional) Multi-regional location for document storage and processing. Defaults to `us`.
- `--form-processor-type`: (Optional) Type of form processor, such as `FORM_W9_PROCESSOR`. Default is `FORM_PARSER_PROCESSOR`.

### Example

To annotate a PDF using the default project and save the output:

```bash
python annotate_pdf.py -i /path/to/input.pdf --output /path/to/output.pdf --project-id my-gcp-project
