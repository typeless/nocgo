main: main.go
	rm -f main64 main32
	$(MAKE) -C testlib
	go build -o main64 main.go
	GOARCH=386 go build -o main32 main.go
	go run ../relink/relink.go main32
	go run ../relink/relink.go main64
	LD_LIBRARY_PATH=testlib ./main32 a b c
	LD_LIBRARY_PATH=testlib ./main64 a b c

.PHONY: main