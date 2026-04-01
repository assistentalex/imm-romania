---
name: nextcloud
description: File management for Nextcloud via WebDAV. Use for uploading, downloading, listing, moving, copying files and folders on Nextcloud. Triggers on phrases like "upload to nextcloud", "download from nextcloud", "list files on nextcloud", "nextcloud file operations".
---

# Nextcloud Module

File management on Nextcloud server using WebDAV protocol.

## Requirements

- Nextcloud instance with WebDAV enabled
- App password (generate from Nextcloud security settings)

## Configuration

Set environment variables:

```bash
export NEXTCLOUD_URL="https://cloud.example.com"
export NEXTCLOUD_USERNAME="your-username"
export NEXTCLOUD_APP_PASSWORD="your-app-password"
```

## Commands

### shared
List folders shared with the current user.

```bash
python3 -m modules.nextcloud shared
```

Returns: Name, owner, permissions, and path for each shared folder.

### list
List files and folders in a directory.

```bash
python3 -m modules.nextcloud list /path/to/directory/
```

Returns: File name, type (file/folder), size, and last modified date.

### upload
Upload a local file to Nextcloud.

```bash
python3 -m modules.nextcloud upload /local/file.txt /remote/directory/
```

### download
Download a file from Nextcloud to local filesystem.

```bash
python3 -m modules.nextcloud download /remote/file.txt /local/directory/
```

### mkdir
Create a new directory on Nextcloud.

```bash
python3 -m modules.nextcloud mkdir /new/folder/path/
```

### delete
Delete a file or directory on Nextcloud.

```bash
python3 -m modules.nextcloud delete /path/to/delete
```

### move
Move or rename a file or directory.

```bash
python3 -m modules.nextcloud move /old/path /new/path
```

### copy
Copy a file or directory.

```bash
python3 -m modules.nextcloud copy /source/path /destination/path
```

### info
Get detailed information about a file or directory.

```bash
python3 -m modules.nextcloud info /path/to/item
```

## Error Handling

- Exit code 0: Success
- Exit code 1: Missing environment variables
- Exit code 2: Connection/authentication error
- Exit code 3: File operation error
- Exit code 4: File not found

## Notes

- Nextcloud WebDAV uses user ID (not username) in paths - the script resolves this automatically
- For large files, ensure sufficient timeout settings
- Self-signed certificates may require additional configuration