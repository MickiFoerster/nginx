start-reverse-proxy: start-backend-servers
	nginx -t -c $$PWD/nginx.conf -p $$PWD
	nginx -c $$PWD/nginx.conf -p $$PWD

reverse-proxy : main.go
	go build -o $@ $^

s1:
	echo "Hello from server $@" > $@
s2:
	echo "Hello from server $@" > $@
s3:
	echo "Hello from server $@" > $@

start-backend-servers: reverse-proxy s1 s2 s3
	./reverse-proxy s1 9991 &
	./reverse-proxy s2 9992 &
	./reverse-proxy s3 9993 &

.PHONY: start-reverse-proxy start-backend-servers