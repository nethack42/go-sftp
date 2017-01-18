# go-sftp

A pure SFTP protocol implementation for Go!

This library provides an SFTP client and server (*not yet*) implementation and
low-level packet definitions for SFTP version 3. The `cmd/sftp` package contains
a SFTP commandline client with interactive shell and auto-completion. 

```go
// Create a new sftp client. 
cli, _ := sftp.NewClient(sshConn)

// List contents of a directory
list, _ := cli.List("/tmp")
for _, fileInfo := range list {
    fmt.Printf("%s    %dbytes\n", fileInfo.Name(), fileInfo.Size())
}

// Create an io.Reader for a given file and copy contents to stdout
reader, _ := cli.FileReader("/etc/passwd")
io.Copy(os.Stdout, reader)

// Remove a file
cli.Remove("/tmp/foobar")

// Rename/Move a file or directory
cli.Rename("/tmp/bar", "/tmp/foo")

// Create a new directory
cli.MkDir("/tmp/mydir")

// Remove a directory
cli.RmDir("/tmp/mydir")
```

`go-sftp` is not yet complete an some protocol features are still missing. In
addition, the server implementation is postponed until the client is fully 
functional is not yet complete an some protocol features are still missing. In
addition, the server implementation is postponed until the client is fully 
functional.
