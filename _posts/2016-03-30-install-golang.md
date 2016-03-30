---
layout: inner
position: right
title: 'install golang'
date: 2016-03-30 18:08:00
categories: development
tags: golang
featured_image: ''
project_link: ''
button_icon: 'github'
button_text: 'Visit Project'
lead_text: 'golang'
---

# install golang

---

## download
	
	https://golang.org/dl/

## install

	sudo tar -C /usr/local -xzf go-version.tar.gz

## path
	
	vi .zshrc
	 
	 export PATH=$PATH:/usr/local/go/bin

	source .zshrc

## test
	
	go env

	GOARCH="amd64"
	GOBIN=""
	GOEXE=""
	GOHOSTARCH="amd64"
	GOHOSTOS="darwin"
	GOOS="darwin"
	GOPATH=""
	GORACE=""
	GOROOT="/usr/local/go"
	GOTOOLDIR="/usr/local/go/pkg/tool/darwin_amd64"
	GO15VENDOREXPERIMENT="1"
	CC="clang"
	GOGCCFLAGS="-fPIC -m64 -pthread -fno-caret-diagnostics -Qunused-arguments -fmessage-length=0 -fno-common"
	CXX="clang++"
	CGO_ENABLED="1"
