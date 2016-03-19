# Curl

---

## Downloading Files

```sh
curl -O http://www.example.org/repos/tarballs/file.tar.bz2
```

Option -O (upper-case O) is important. Without this, curl will start dumping the downloaded file on the stdout. Using -O, it downloads the files in the same name as the remote server
