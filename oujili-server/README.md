# 技术架构

开发语言： java<br>
开发框架： springboot Spring Cloud Alibaba<br>
单体和微服务： 单体和微服务版是一个项目，设计时按微服务设计开发，鉴于微服务的复杂性，为降低维护成本，改造了一个单体springboot版本(其实就是微服务一个服务单独启动，不往注册中心注册就行了)，功能完全一样，可根据自己需求选择合适的版本<br>
默认为单体，如果要修改为微服务版，则删除 msfast-modules-msfast-nostalgia-pom.xml-微服务配置依赖代码 
数据库：mysql redis <br>
文件存储: minio <br>
短信通知：阿里云短信 <br>

# 基础环境

请确保本地基础环境搭建完毕 <br>
jdk 1.8<br>
Mysql 8.0<br>
redis<br>
minio<br>

# 快速启动

1. 新建数据库 数据库名：msfast_nostalgia，注意设置数据库 字符集为utf8mb4 排序规则为utf8mb4_unicode_ci<br>
2. 执行此项目doc文件夹下msfast_nostalgia.sql脚本 （获取方式见文末）<br>
3. 修改application.yml文件中相关配置，启动端口，数据库信息，redis连接信息，minio 连接信息，微信小程序appid等<br>
4. 构建好项目后，加载maven相关依赖，如果出现com.wxmblog相关依赖包无法下载，请检查maven仓库是否配置正确，例如 配置了阿里云maven镜像仓库时配置了central或是 ，如果工程中的jar包都能在阿里镜像中找到，mirrorOf填central还是都是可以的。central表示覆盖maven中央仓库的默认url，*表示所有的仓库都到我配置的这个url取，所以会导致部分依赖阿里云镜像更新不及时而提示包不存在的错误，请以maven官方中央仓库为准，可以尝试修改为maven默认配置，就是下载maven后最原始的配置，不使用阿里云仓库<br>
5. 部署启动命令 nohup java -Dfile.encoding=utf-8  -jar reservation.jar & <br> 
6. 运行时部分图片和字体文件会报404的错误，是为了减少客户端内存,静态资源文件部署在服务端，将此项目doc文件夹中upload文件夹（获取方式见文末）放至服务端静态文件路径下即可（可通过yml文件中 wxmfast.config.file.static-path 修改，例如：/home/oujili/upload） <br>
