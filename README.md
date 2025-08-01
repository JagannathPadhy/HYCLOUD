HyCloud Vault is a secure, cost-efficient hybrid cloud storage system that uses chunk-based deduplication, encryption, and cross-region replication to reduce storage costs and ensure high data availability.

The application automatically splits uploaded files into chunks, calculates their SHA-256 hashes, and checks a DynamoDB deduplication index before uploading them to Amazon S3.

If a chunk already exists, the system simply updates a reference counter without re-uploading.

If the chunk is new, it is encrypted (SSE-KMS optional) and uploaded to the primary S3 bucket.

An AWS Cross-Region Replication rule ensures the chunk is also stored in a backup S3 bucket for disaster recovery.

A scheduled AWS Lambda recovery function periodically verifies chunk integrity and automatically restores missing/corrupted chunks from the backup region.

The result is a reliable, secure, and cost-optimized cloud storage solution that supports both CLI-based interaction and UI prototypes for demonstration purposes.

🔧 Core Features
Deduplication – Chunk-based storage with SHA-256 hashing.

Cross-Region Replication – Automatic disaster recovery between regions.

Versioning – File history protection.

Encryption – AWS KMS (SSE-KMS) for secure storage.

Recovery Support – Lambda restores missing chunks from backups.

Cost Optimization – Reduced storage costs via deduplication and S3 Intelligent-Tiering.

🛠 Tech Stack
Backend & Cloud
AWS S3 – Primary + backup buckets with versioning and CRR.

AWS DynamoDB – Deduplication index + file metadata.

AWS Lambda – Chunk processing (optional), integrity checks, recovery logic.

AWS KMS – Encryption key management.

AWS CloudWatch – Monitoring and event triggers.

Python (boto3) – Core CLI and automation scripts.

UI Prototyping & Frontend
If you want to build a UI for uploads/downloads instead of only CLI:

Framework: ReactJS (web) or Flutter (cross-platform).

UI Prototyping:

Figma – For wireframes and clickable UI mockups.

Adobe XD – For interactive prototypes with animations.

Component Libraries:

Material UI (React) – Prebuilt responsive UI elements.

Ant Design – For enterprise-style dashboards.

Integration with Backend:

AWS Amplify or API Gateway to call Python/Lambda functions.

Presigned S3 URLs for secure file upload/download.

🚀 Example UI Prototype Flow
Login Screen – Auth via AWS Cognito (optional for demo).

Dashboard – Shows file list, storage savings from deduplication.

Upload Modal – Drag & drop or select file → chunked upload.

File Details Page – Displays version history, chunk integrity, storage locations (primary/backup).

Recovery Logs Page – Shows recent repairs done by Lambda.
