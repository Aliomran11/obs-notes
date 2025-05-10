# Certificate File Handling

## Storage Architecture
- Uses Google Cloud Storage (GCS)
- Files stored in `certificates/` directory
- Unique filenames with timestamp prefix
- Direct streaming from memory (no temp files)

## Upload Flow
1. Client submits multipart form with file
2. Multer processes in memory
3. Stream directly to GCS bucket
4. Store public URL in database

## Security
- Bucket-level access control
- No public write permissions
- Unique filenames prevent overwrites

## Error Handling
- 400 if no file provided
- 500 on stream errors
- Automatic cleanup on DB failures