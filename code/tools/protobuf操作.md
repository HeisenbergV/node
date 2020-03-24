
mac go

/Users/zuojxin/ddd/protoc/bin/protoc protoc --go_out=plugins=grpc:. zmq.proto


windows c#
..\packages\Grpc.Tools.2.23.0\tools\windows_x64\protoc.exe --csharp_out . .\zmq.proto --grpc_out . --plugin=protoc-gen-grpc=..\packages\Grpc.Tools.2.23.0\tools\windows_x64\grpc_csharp_plugin.exe
https://blog.csdn.net/liyazhen2011/article/details/84937455