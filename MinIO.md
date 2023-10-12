```
docker pull minio/minio

docker run -p 9000:9000 --name minio -d --restart=always -e "MINIO_ACCESS_KEY=minio" -e "MINIO_SECRET_KEY=minio123" -v /home/data:/data -v /home/config:/root/.minio minio/minio server /data

http:ip:9000

noted:
bucket - 类比文件系统的目录
Object - 类比文件系统的文件
Keys   - 类比文件名
```
