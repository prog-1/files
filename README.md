# Files

## Important packages

* `os` - Package os provides a platform-independent interface to operating system functionality.
* `io` - Package io provides basic interfaces to I/O primitives.
* `bufio` - Package bufio implements buffered I/O.
* `fmt` - Package fmt implements formatted I/O.

## Open and read files

```go
file, err := os.Open("file.txt") // For read access.
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
f, err := os.Open("file.txt")
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

## Reading integers from a file

`Scan`, `Scanf` and `Scanln` read from `os.Stdin`; `Fscan`, `Fscanf` and `Fscanln` read from a specified `io.Reader`.

```go
f, err := os.Open("file.txt")
if err != nil {
  log.Fatal(err)
}
defer f.Close()

var x, y int
fmt.Fscan(f, &x, &y)
fmt.Printf("x = %d\ny = %d\n", x, y)
```
