<div align="center">
<a href="https://empress-eco/">Explore the Docs</a>
·
<a href="https://github.com/empress-eco/dfp_external_storage/issues">Report Bug</a>
·
<a href="https://github.com/empress-eco/dfp_external_storage/issues">Request Feature</a>
</div>

## About The Project

### 📖 Overview
DFP External Storage revolutionizes your cloud file management experience. This solution enables you to assign an S3 compatible external bucket per folder, optimizing the location of your files within the local filesystem or an external S3 bucket. Developed for the Empress / Empresssystem, it's designed to enhance file management in diverse use cases.

### 🌟 Key Features
- Assign S3 bucket per folder.
- Access files with custom URLs.
- Bulk file relocation (upload and download).
- Stream data in chunks to and from S3 without reading whole files into memory.
- Support for S3/Minio presigned URLs.

## Technical Stack and Setup Instructions

This project is built on Empress (version >= 14). Follow these steps to get started:

### Prerequisites
Ensure you have Empress version >= 14 installed. You can install it following the official guide for your OS: [Empress Installation Guide](https://Empressframework.com/docs/v14/user/en/installation).

### Installation
1. Open your terminal and navigate to your home directory:

   ```sh
   cd ~
   ```
   
2. Create your personal "Empress-bench" environment:

   ```sh
   bench init Empress-bench
   ```

3. Install the "dfp_external_storage" app:

   ```sh
   cd ~/Empress-bench
   bench get-app https://github.com/empress-eco/dfp_external_storage.git
   ```

4. Create a new site with "dfp_external_storage" app installed:

   ```sh
   bench new-site dfp_external_storage_site.localhost --install-app dfp_external_storage
   ```

5. Initialize the servers to get the site running:

   ```sh
   bench start
   ```

### Usage
Create one or more "DFP External Storage"s, assign a folder to each, and start uploading your files.

To upload content from a local file, use the following:

```sh
file_doc = Empress.get_doc({
    "doctype":"File",
    "is_private":True,
    "file_name": "file name here"
})
file_doc.dfp_external_storage_upload_file(filepath)
file_doc.save()
```

To read a remote file directly via a proxy object, use the following:

```sh
file_doc = Empress.get_doc("File",doc_name)

#read zip file's table of contents without downloading the whole zip file
with zipfile.ZipFile(file_doc.dfp_external_storage_file_proxy()) as z:
  for zipinfo in z.infolist():
     print(f"{zipinfo.filename}")
```

## Contribution Guidelines
We highly value and welcome contributions from the community. Here's how you can contribute:

1. Fork the Project on GitHub.
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the Branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

## License and Acknowledgements

### License
This project is licensed under the MIT License. All contributions are also licensed under the MIT License.

### Acknowledgements
Special thanks to the Empress Community for their innovative tools and continuous support, which have been instrumental in the development of this project. We appreciate their foundational contributions and ongoing dedication. 

## Attributions
- Cloud storage icon by Iconstock from [Noun Project](https://thenounproject.com/browse/icons/term/cloud-storage/).
