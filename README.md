# Files

## Important packages

`os` - Package os provides a platform-independent interface to operating system functionality. 
`io` - Package io provides basic interfaces to I/O primitives.
`bufio` - Package bufio implements buffered I/O.

## Open and read files

```go
file, err := os.Open("file.go") // For read access.
if err != nil {
	log.Fatal(err)
}
defer file.Close()
// Read the file here.
```

```go
data := make([]byte, 100)
count, err := file.Read(data)
if err != nil {
	log.Fatal(err)
}
fmt.Printf("read %d bytes: %q\n", count, data[:count])
```

## Scan lines from a file

```go
f, err := os.Open("file.go")
if err != nil {
  log.Fatal(err)
}
defer f.Close()

s := bufio.NewScanner(f)
for s.Scan() {
  fmt.Println(s.Text())
}
if err := s.Err(); err != nil {
  log.Fatal(err)
}
```

