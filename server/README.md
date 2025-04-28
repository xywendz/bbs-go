## 介绍
该项目使用Golang进行构建，具体参见：https://mlog.club

## 交叉编译

### Windows交叉编译Linux
powershell 设置环境变量：
$env:GOOS=linux
$env:GOARCH=amd64
$env:CGO_ENABLED=0
go build -o bbsgo main.go

## 服务环境变量设置
BBSGO_DB_URL=root:123456@tcp(bbs-go-mysql:3306)/bbsgo_db?charset=utf8mb4&parseTime=True&multiStatements=true&loc=Local
