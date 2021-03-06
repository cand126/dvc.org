# Configure

Once you install DVC, you will be able to start using it (in its local setup)
immediately.

However, remote storage (see `dvc remote`) should be set up if you need to share
data or models outside of a local environment. It's similar to the way you would
use Github or any other Git server to store and share your code.

For simplicity, let's setup a local remote:

```dvc
    $ dvc remote add -d myremote /tmp/dvc-storage
    $ git commit .dvc/config -m "initialize DVC local remote"
```
A remote can be specified by the remote type prefix and a path. As of this
version, DVC supports seven types of remotes:

* `local` - Local directory
* `s3` - Amazon Simple Storage Service
* `gs` - Google Cloud Storage
* `azure` - Azure Blob Storage
* `ssh` - Secure Shell
* `hdfs` - The Hadoop Distributed File System
* `http` - Support for HTTP and HTTPS protocol

> Depending on the [remote storage](/doc/commands-reference/remote) type you
plan to use to keep and share your data you might need to specify one of the
optional dependencies: `s3`, `gs`, `azure`, `ssh`. Or `all_remotes` to include
them all. The command should look like this: `pip install dvc[s3]` - it will
install `boto3` library along with DVC to support AWS S3 storage. This is valid
for `pip install` option only. Other ways to install DVC already include support
for all remotes.

For example, to setup an S3 remote:

```dvc
    $ dvc remote add -d myremote s3://mybucket/myproject
```

You can see, that DVC does not require installing any databases, servers, or
warehouses. It can use bare S3 or SSH to store data, intermediate results, and
your models.

See `dvc config` to get information about more configuration options and
`dvc remote` to learn more about remotes and get more examples.
