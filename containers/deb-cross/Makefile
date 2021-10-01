TAG=deb-cross

build:
	docker build -t $(TAG) .

run:
	docker run -it -v$$PWD:/deb-cross:z $(TAG)
