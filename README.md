# Aliyun OSS SDK for Unity

[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE)
[![GitHub version](https://badge.fury.io/gh/aliyun%2Faliyun-oss-csharp-sdk.svg)](https://badge.fury.io/gh/aliyun%2Faliyun-oss-csharp-sdk)
[![Build Status](https://travis-ci.org/aliyun/aliyun-oss-csharp-sdk.svg?branch=master)](https://travis-ci.org/aliyun/aliyun-oss-csharp-sdk)
## 关于Unity版本
 - 此Unity SDK基于[阿里云OSS C# SDK](https://github.com/aliyun/aliyun-oss-csharp-sdk)简单修改而来，changes看checkin历史记录。
 - 只是简单测试了Editor和Android端的几个简单API，比如获取bucket信息，未全部测试Unity各平台及其它方法，请谨慎使用。
 - 弄这个版本只是懒得在Unity里用REST API，这里只是简单解决了c# sdk在Unity上使用出现空指针的问题，期望阿里云OSS官方支持Unity平台。
 
## 关于
 - 此Unity SDK基于[阿里云对象存储服务](http://www.aliyun.com/product/oss/) API构建。
 - 阿里云对象存储（Object Storage Service，简称OSS），是阿里云对外提供的海量，安全，低成本，高可靠的云存储服务。
 - OSS适合存放任意文件类型，适合各种网站、开发企业及开发者使用。
 - 使用此SDK，用户可以方便地在任何应用、任何时间、任何地点上传，下载和管理数据。

## 版本
 - 当前版本：2.4.0

## 运行环境

### Unity
 - 5.4.0可用，其它版本未测试
 
## 安装方法
 - build工程，将..sdk\bin\Debug\Aliyun.OSS.dll引入Unity工程。
 - 或者直接用build好的[版本](https://github.com/Shirlman/aliyun-oss-unity-sdk/blob/master/build/Aliyun.OSS.dll)
 
## 快速使用
#### 获取存储空间列表（List Bucket）
```csharp
    OssClient client = new OssClient(endpoint, accessKeyId, accessKeySecret);    
	var buckets = client.ListBuckets();
	
    foreach (var bucket in buckets)
    {
    	Console.WriteLine(bucket.Name + ", " + bucket.Location + ", " + bucket.Owner);
    }
```
    
#### 创建存储空间（Create Bucket）
```csharp
	OssClient client = new OssClient(endpoint, accessKeyId, accessKeySecret);
	client.CreateBucket(bucketName);
```
	
#### 删除存储空间（Delete Bucket）
```csharp
	OssClient client = new OssClient(endpoint, accessKeyId, accessKeySecret); 
	client.DeleteBucket(bucketName);
```

#### 上传文件（Put Object）
```csharp
	OssClient client = new OssClient(endpoint, accessKeyId, accessKeySecret); 
	client.PutObject(bucketName, key, filePathToUpload);
```

#### 下载文件 (Get Object)
```csharp
	OssClient client = new OssClient(endpoint, accessKeyId, accessKeySecret); 
	var object = ossClient.GetObject(bucketName, key);	
```

#### 获取文件列表（List Objects）
```csharp
	OssClient client = new OssClient(endpoint, accessKeyId, accessKeySecret);
	var listResult = client.ListObjects(bucketName);
	foreach (var summary in listResult.ObjectSummaries)
	{   
		Console.WriteLine(summary.Key);
	}
```
	
#### 删除文件(Delete Object)
```csharp
	OssClient client = new OssClient(endpoint, accessKeyId, accessKeySecret);
	client.DeleteObject(bucketName, key)
```

#### 其他
    上面的例子中，如果没有抛出异常则说明执行成功，否则失败，更详细的例子可以在aliyun-oss-sample项目中查看并运行。
	
## 注意事项
 - 如果要运行sample，需要将aliyun-oss-sdk-sample项目设为`启动项目`，并添加您自己的AccessKeyId，AccessKeySecret，bucket，key等后即可运行。

