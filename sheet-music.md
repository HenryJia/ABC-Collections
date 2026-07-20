---
layout: page
title: Sheet Music Collection
---

# Sheet Music Collection

This page displays all the sheet music from my ABC collection, converted to PDF format.

## Available PDFs

{% for pdf_file in site.static_files %}
  {% if pdf_file.path contains '/ABC-Collections/assets/pdf/' %}
    {% assign filename = pdf_file.name %}
    <div class="card mb-4">
      <div class="card-header">
        <h3>{{ filename }}</h3>
      </div>
      <div class="card-body">
        <p class="card-text">
          <a href="{{ pdf_file.path }}" class="btn btn-primary" target="_blank">Download PDF</a>
        </p>
        <div class="pdf-container" style="height: 600px; border: 1px solid #ccc; overflow: auto;">
          <object data="{{ pdf_file.path }}" type="application/pdf" width="100%" height="100%">
            <p>Your browser does not support viewing PDFs. <a href="{{ pdf_file.path | relative_url }}" target="_blank">Download the PDF</a> instead.</p>
          </object>
        </div>
      </div>
    </div>
  {% endif %}
{% endfor %}
## About This Collection

This collection contains various musical pieces converted from ABC notation to PDF format. The conversion is done automatically through a GitHub Actions workflow that processes the ABC files in `assets/abc/` and generates corresponding PDFs in `assets/pdf/`.

The PDFs are generated using `abcm2ps` and `ghostscript` tools, ensuring high-quality sheet music output.

## How to Use

You can download and view these PDF files directly. They contain the complete sheet music for each composition in this collection.

<div class="alert alert-info">
  <strong>Note:</strong> Some browsers may not display PDFs inline. If you experience issues viewing the PDFs, try downloading them first.
</div>

## Available ABC Files

The following ABC files are available in the repository:

{% for abc_file in site.static_files %}
  {% if abc_file.path contains 'assets/abc/' %}
    <code>{{ abc_file.name }}</code>
  {% endif %}
{% endfor %}

<div class="alert alert-info">
  <strong>Tip:</strong> The PDF files are automatically generated from these ABC files using a GitHub Actions workflow.
</div>

## Conversion Status

The following ABC files have been converted to PDF format:

{% assign abc_files = site.static_files | where: 'path', 'assets/abc/' %}
{% if abc_files.size > 0 %}
  {% for abc_file in abc_files %}
    {% assign filename = abc_file.name | split: '.' | first %}
    {% assign pdf_filename = filename | append: '.pdf' %}
    {% assign has_pdf = false %}
    {% for pdf_file in site.static_files %}
      {% if pdf_file.path contains 'assets/pdf/' and pdf_file.name == pdf_filename %}
        {% assign has_pdf = true %}
      {% endif %}
    {% endfor %}
    <div class="row">
      <div class="col-md-6">
        <code>{{ abc_file.name }}</code>
      </div>
      <div class="col-md-6">
        {% if has_pdf %}
          <span class="badge badge-success">PDF Available</span>
        {% else %}
          <span class="badge badge-warning">PDF Pending</span>
        {% endif %}
      </div>
    </div>
  {% endfor %}
{% else %}
  <p>No ABC files found in the assets/abc/ directory.</p>
{% endif %}

<div class="alert alert-info">
  <strong>Current Status:</strong> 
  {% assign abc_files = site.static_files | where: 'path', 'assets/abc/' %}
  {% assign pdf_files = site.static_files | where: 'path', 'assets/pdf/' %}
  {{ pdf_files.size }} of {{ abc_files.size }} ABC files have been converted to PDF format.
</div>