# Utility Workflows

This directory contains general-purpose utility workflows for common automation tasks.

## Available Workflows

### Scheduled Data Backup
**File:** `scheduled-data-backup.json`

**Description:** A cron-based workflow that automatically creates daily backups with timestamp-based naming.

**Features:**
- Daily scheduled execution (customizable)
- Automatic timestamp generation
- Backup naming convention
- Logging and status tracking

**Prerequisites:**
- Storage location configured (local, cloud, or API endpoint)
- Appropriate access permissions

**Use Cases:**
- Regular data backups
- Automated archiving
- Compliance data retention
- Disaster recovery preparation

**Setup:**
1. Import the workflow into N8N
2. Customize the cron schedule in the "Daily Schedule" node:
   - Default: `0 0 * * *` (daily at midnight)
   - Modify for your preferred schedule
3. Update the "Save to Storage" node with your storage endpoint
4. Configure any required credentials for your storage system
5. Activate the workflow

**Schedule Examples:**
- Every day at midnight: `0 0 * * *`
- Every 6 hours: `0 */6 * * *`
- Every weekday at 9 AM: `0 9 * * 1-5`
- Every week on Sunday: `0 0 * * 0`

**Nodes Used:**
- Cron node (scheduling)
- Function nodes (backup preparation and logging)
- HTTP Request node (storage)

**Customization:**
- Change the backup schedule
- Modify filename format
- Add data compression
- Implement backup rotation
- Add notification on success/failure
- Configure retention policies
