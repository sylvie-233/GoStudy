# minio-go


## 基础介绍


Minio客户端


## 核心内容
```yaml
github.com/minio/minio-go/v7:
    pkg:
        credentials:
            NewStaticV4():
    minio:
        Options:
            Creds:
            Secure:
        New():
    Client: # 客户端
        BucketExists():
        FGetObject():
        FPutObject():
        ListObjects():
        MakeBucket():
        PresignedGetObject():
        RemoveObject():
```