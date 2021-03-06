# XenForo backup script
Made because I hate doing this manually

## You will need
- SSH access
- `pigz` or `pbzip2` installed (if you want to use the faster, multi-core compression methods)
- An Amazon S3 account (and `s3put` installed) if you want to sync your SQL backups with AWS
- A little experience with the Linux shell environment

## How to use
1. Download `backup_script.sh` [from the repo](https://github.com/CalamityJames/xenforo_backup/blob/master/backup_script.sh)
2. Save the backup script somewhere you'll remember. For example `/home/backups`
3. Make it executable with `chmod +x backup_script.sh`
4. Fill out the config variables (see below)
5. Add a crontab entry to run every night at a time when your site is likely to be less busy. Something like this will do: `0       3       *       *       *       /home/backups/backup_script.sh` (this will run at 3am every night)

### Config variables
- `db_username` - The username for your SQL database
- `db_password` - The passsword for your SQL database
- `db_name` - The name of your database
- `compression_method` - The compression executable that will be run. Choose between `pigz`, `pbzip2` or `gzip`
- `backup_path` - The location you want your backup files saved
- `web_dir` - The location of your xenForo installation
- `bucket_name` *(optional)* - The Amazon S3 bucket name and directory in which to sync the SQL backups