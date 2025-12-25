# n8n-nodes-tencent-cos

这是一个为 n8n 开发的腾讯云 COS（对象存储）社区节点，基于 `cos-nodejs-sdk-v5` 构建。

[![NPM Version](https://img.shields.io/npm/v/n8n-nodes-tencent-cos.svg)](https://www.npmjs.com/package/n8n-nodes-tencent-cos)
[![License](https://img.shields.io/npm/l/n8n-nodes-tencent-cos.svg)](https://github.com/difyz9/n8n-nodes-tencent-cos/blob/main/LICENSE)

[n8n](https://n8n.io/) 是一个可扩展的工作流自动化平台，允许你连接各种服务和应用。

## 功能特性

此节点支持以下腾讯云 COS 操作：

### 文件操作 (File)
- **上传 (Upload)**: 上传文件到 COS 存储桶
- **下载 (Download)**: 从 COS 下载文件
- **删除 (Delete)**: 删除 COS 中的文件
- **获取信息 (Get)**: 获取文件的元数据信息
- **列表 (List)**: 列出存储桶中的文件和文件夹（支持分页、前缀过滤、分隔符）

### 存储桶操作 (Bucket)
- **创建 (Create)**: 创建新的存储桶
- **删除 (Delete)**: 删除存储桶
- **列表 (List)**: 列出所有存储桶

## 安装

### 社区节点安装（推荐）

1. 在 n8n 中，转到 **设置 > 社区节点**
2. 选择 **安装**
3. 输入 `n8n-nodes-tencent-cos`
4. 点击 **安装**

### 手动安装

在你的 n8n 根目录中运行：

```bash
npm install n8n-nodes-tencent-cos
```

## 配置

### 凭证设置

使用此节点前，你需要配置腾讯云 API 凭证：

1. 在 n8n 中创建新的 **Tencent COS API** 凭证
2. 填入以下信息：
   - **Secret ID**: 你的腾讯云 Secret ID（必填）
   - **Secret Key**: 你的腾讯云 Secret Key（必填）
   - **Default Bucket**: 默认存储桶名称（可选，方便在节点中复用）
   - **Default Region**: 默认地域（可选，方便在节点中复用）

> 💡 **提示**: 设置默认存储桶和地域后，在节点中可以不填这两个参数，系统会自动使用凭证中的默认值。当然，你也可以在节点中覆盖这些默认值。

#### 如何获取腾讯云凭证

1. 登录 [腾讯云控制台](https://console.cloud.tencent.com/)
2. 访问 [API 密钥管理](https://console.cloud.tencent.com/cam/capi)
3. 创建或查看你的 Secret ID 和 Secret Key

## 使用示例

### 上传文件

1. 添加 **Tencent COS** 节点到你的工作流
2. 选择凭证
3. 设置参数：
   - **Resource**: File
   - **Operation**: Upload
   - **Bucket Name**: 存储桶名称（例如：`my-bucket-1250000000`）。留空则使用凭证中的默认值
   - **Region**: 存储桶所在地域（例如：`ap-guangzhou`）。留空则使用凭证中的默认值
   - **File Key**: 文件在存储桶中的路径（例如：`folder/file.txt`）
   - **Binary Property**: 包含文件数据的二进制属性名（默认：`data`）

### 下载文件

1. 添加 **Tencent COS** 节点
2. 选择凭证
3. 设置参数：
   - **Resource**: File
   - **Operation**: Download
   - **Bucket Name**: 存储桶名称（留空使用默认值）
   - **Region**: 地域（留空使用默认值）
   - **File Key**: 要下载的文件路径
   - **Put Binary Property**: 存储下载文件的属性名

### 列出文件

1. 添加 **Tencent COS** 节点
2. 选择凭证
3. 设置参数：
   - **Resource**: File
   - **Operation**: List
   - **Bucket Name**: 存储桶名称（留空使用默认值）
   - **Region**: 地域（留空使用默认值）
   - **Prefix**: （可选）文件路径前缀。使用 `/` 访问根目录，使用 `folder/` 访问指定文件夹
   - **Delimiter**: （可选）分隔符，通常使用 `/` 来实现文件夹层级结构
   - **Max Keys**: 单次请求最大返回数量（默认：1000）
   - **Return All**: 是否返回所有结果（自动分页）

## 支持的地域

常用地域代码：
- `ap-guangzhou` - 广州
- `ap-shanghai` - 上海
- `ap-beijing` - 北京
- `ap-chengdu` - 成都
- `ap-chongqing` - 重庆
- `ap-hongkong` - 香港
- `ap-singapore` - 新加坡

更多地域请参考 [腾讯云 COS 地域列表](https://cloud.tencent.com/document/product/436/6224)。

## 开发

### 构建

```bash
npm run build
```

### 监听模式

```bash
npm run build:watch
```

### 代码规范检查

```bash
npm run lint
npm run lint:fix
```

## 资源

- [n8n 社区节点文档](https://docs.n8n.io/integrations/community-nodes/)
- [腾讯云 COS 文档](https://cloud.tencent.com/document/product/436)
- [cos-nodejs-sdk-v5 文档](https://cloud.tencent.com/document/product/436/8629)

## 微信交流群

欢迎加入我们的微信群，扫描下面的二维码加入讨论：



<div align="center">
   <img src="img/20251225210024_5_98.jpg" alt="微信联系二维码" width="200"/>
   <img src="img/n8n_0156.jpg" alt="微信交流群" width="200"/>
   <br/>
   <em>📱 扫码添加微信 - 技术交流与支持</em>
</div>


## 许可证

MIT

## 问题反馈

如有问题或建议，请在 [GitHub Issues](https://github.com/difyz9/n8n-nodes-tencent-cos/issues) 中提出。

