csync (Cloud Sync) with support for Amazon S3 and Joyent Manta
==============================================================

Synchronizes a given directory to either S3-compatible service or Joyent Manta. Useful for backup data purposes.

Dependencies
------------
If using S3-compatible service:

 - [s3cmd](http://s3tools.org/s3cmd)
 - .s3cfg properly configured

If using Joyent Manta

 - [manta CLI](https://npmjs.org/package/manta)
 - correct env variables set for Manta

Synchronization Modes
---------------------

There are two synchronization modes: 'contribute' and 'echo'

contribute uploads files found locally but missing remotely, but files deleted locally will not be deleted remotely

echo does what contribute does except files removed locally will also be removed remotely

Both modes won't sync changes done remotely back down locally.

Example Usage
-------------
**Using S3**

[~] csync backup s3://bucket-name/dir1/dir2 ~/dir

[~] csync restore s3://bucket-name/dir1/dir2 ~/dir

**Using Manta**

[~] csync -s manta backup /$MANTA_USER/stor/dir1/dir2 ~/dir

[~] csync -s manta restore /$MANTA_USER/stor/dir1/dir2 ~/dir

For more details, run `csync -h`