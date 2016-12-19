---
title: Faster than scp
summary: On occasion everyone needs to move large files between servers,
         this is the fastest way.
---

On occasion everyone needs to move large files between servers, like say a 50GB
log dump from your DB that you want to analyze, or a 10GB SQL backup.

The internet is fast now-adays and most cloud services have great bandwidth,
but a lot of data is a lot of data and transferring it can take some time.

`scp` is the easiest way to transfer files using an ssh connection, but it can
be a bit slow on occasion, and it's compression is usually worthless.

So, the solution is to pipe the results from tar-gzip over an ssh connection.
NetCat(nc) is a tad faster but requires one more step to setup.

The Syntax
----------

    ssh user@source.com tar -zc /path/to/dir | tar -zx -C output/dir

The Results
-----------
For a 250MB txt file

*scp* : 19.7 seconds
*tar-gzip over ssh* : 7.6 seconds


