请将中文 README（README_CN.md）更新为与提供的英文 README (README.md) 内容一致，并保留中文 README 中“在线版”章节和捐赠章节中“爱发电”的链接。

更新后的中文 README 内容如下：

```markdown
# 漫画图片翻译器

![Commit activity](https://img.shields.io/github/commit-activity/m/zyddnys/manga-image-translator)
![Lines of code](https://img.shields.io/tokei/lines/github/zyddnys/manga-image-translator?label=lines%20of%20code)
![License](https://img.shields.io/github/license/zyddnys/manga-image-translator)
![Contributors](https://img.shields.io/github/contributors/zyddnys/manga-image-translator)
[![Discord](https://img.shields.io/discord/739305951085199490?logo=discord&label=discord&logoColor=white)](https://discord.gg/Ak8APNy4vb)

> 翻译漫画/图片中的文字。\
> [English](README.md) | [Change Log](CHANGELOG.md) \
> 欢迎加入我们的 Discord <https://discord.gg/Ak8APNy4vb>

一些漫画/图片可能永远不会被翻译，因此本项目应运而生。

- [漫画图片翻译器](#漫画图片翻译器)
    - [样例](#样例)
    - [在线版](#在线版)
    - [免责声明](#免责声明)
    - [安装](#安装)
        - [本地安装](#本地安装)
            - [Pip/venv](#pipvenv)
            - [**Windows** 额外说明](#windows-额外说明)
        - [Docker](#docker)
            - [托管 Web 服务器](#托管-web-服务器)
            - [用作 CLI](#用作-cli)
            - [设置翻译密钥](#设置翻译密钥)
            - [配合 Nvidia GPU 使用](#配合-nvidia-gpu-使用)
            - [本地构建](#本地构建)
    - [使用方法](#使用方法)
        - [批量模式 (默认)](#批量模式-默认)
        - [Demo 模式](#demo-模式)
        - [Web 模式](#web-模式)
        - [Api 模式](#api-模式)
    - [相关项目](#相关项目)
    - [文档](#文档)
        - [推荐模块](#推荐模块)
            - [提高翻译质量的技巧](#提高翻译质量的技巧)
        - [选项](#选项)
        - [语言代码参考](#语言代码参考)
        - [翻译器参考](#翻译器参考)
        - [配置文件文档](#配置文件文档)
        - [GPT 配置参考](#gpt-配置参考)
        - [使用 Gimp 进行渲染](#使用-gimp-进行渲染)
        - [Api 文档](#api-文档)
            - [同步模式](#同步模式)
            - [异步模式](#异步模式)
            - [人工翻译](#人工翻译)
    - [下一步](#下一步)
    - [支持我们](#支持我们)
        - [感谢所有贡献者:](#感谢所有贡献者)

## 样例

请注意，样例可能并非总是更新，可能不代表当前主分支版本的效果。

<table>
  <thead>
    <tr>
      <th align="center" width="50%">原始图片</th>
      <th align="center" width="50%">翻译后图片</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center" width="50%">
        <a href="https://user-images.githubusercontent.com/31543482/232265329-6a560438-e887-4f7f-b6a1-a61b8648f781.png">
          <img alt="佐藤さんは知っていた - 猫麦" src="https://user-images.githubusercontent.com/31543482/232265329-6a560438-e887-4f7f-b6a1-a61b8648f781.png" />
        </a>
        <br />
        <a href="https://twitter.com/09ra_19ra/status/1647079591109103617/photo/1">(Source @09ra_19ra)</a>
      </td>
      <td align="center" width="50%">
        <a href="https://user-images.githubusercontent.com/31543482/232265339-514c843a-0541-4a24-b3bc-1efa6915f757.png">
          <img alt="Output" src="https://user-images.githubusercontent.com/31543482/232265339-514c843a-0541-4a24-b3bc-1efa6915f757.png" />
        </a>
        <br />
        <a href="https://user-images.githubusercontent.com/31543482/232265376-01a4557d-8120-4b6b-b062-f271df177770.png">(Mask)</a>
      </td>
    </tr>
    <tr>
      <td align="center" width="50%">
        <a href="https://user-images.githubusercontent.com/31543482/232265479-a15c43b5-0f00-489c-9b04-5dfbcd48c432.png">
          <img alt="Gris finds out she's of royal blood - VERTI" src="https://user-images.githubusercontent.com/31543482/232265479-a15c43b5-0f00-489c-9b04-5dfbcd48c432.png" />
        </a>
        <br />
        <a href="https://twitter.com/VERTIGRIS_ART/status/1644365184142647300/photo/1">(Source @VERTIGRIS_ART)</a>
      </td>
      <td align="center" width="50%">
        <a href="https://user-images.githubusercontent.com/31543482/232265480-f8ba7a28-846f-46e7-8041-3dcb1afe3f67.png">
          <img alt="Output" src="https://user-images.githubusercontent.com/31543482/232265480-f8ba7a28-846f-46e7-8041-3dcb1afe3f67.png" />
        </a>
        <br />
        <code>--detector ctd</code>
        <a href="https://user-images.githubusercontent.com/31543482/232265483-99ad20af-dca8-4b78-90f9-a6599eb0e70b.png">(Mask)</a>
      </td>
    </tr>
    <tr>
      <td align="center" width="50%">
        <a href="https://user-images.githubusercontent.com/31543482/232264684-5a7bcf8e-707b-4925-86b0-4212382f1680.png">
          <img alt="陰キャお嬢様の新学期🏫📔🌸 (#3) - ひづき夜宵🎀💜" src="https://user-images.githubusercontent.com/31543482/232264684-5a7bcf8e-707b-4925-86b0-4212382f1680.png" />
        </a>
        <br />
        <a href="https://twitter.com/hiduki_yayoi/status/1645186427712573440/photo/2">(Source @hiduki_yayoi)</a>
      </td>
      <td align="center" width="50%">
        <a href="https://user-images.githubusercontent.com/31543482/232264644-39db36c8-a8d9-4009-823d-bf85ca0609bf.png">
          <img alt="Output" src="https://user-images.githubusercontent.com/31543482/232264644-39db36c8-a8d9-4009-823d-bf85ca0609bf.png" />
        </a>
        <br />
        <code>--translator none</code>
        <a href="https://user-images.githubusercontent.com/31543482/232264671-bc8dd9d0-8675-4c6d-8f86-0d5b7a342233.png">(Mask)</a>
      </td>
    </tr>
    <tr>
      <td align="center" width="50%">
        <a href="https://user-images.githubusercontent.com/31543482/232265794-5ea8a0cb-42fe-4438-80b7-3bf7eaf0ff2c.png">
          <img alt="幼なじみの高校デビューの癖がすごい (#1) - 神吉李花☪️🐧" src="https://user-images.githubusercontent.com/31543482/232265794-5ea8a0cb-42fe-4438-80b7-3bf7eaf0ff2c.png" />
        </a>
        <br />
        <a href="https://twitter.com/rikak/status/1642727617886556160/photo/1">(Source @rikak)</a>
      </td>
      <td align="center" width="50%">
        <a href="https://user-images.githubusercontent.com/31543482/232265795-4bc47589-fd97-4073-8cf4-82ae216a88bc.png">
          <img alt="Output" src="https://user-images.githubusercontent.com/31543482/232265795-4bc47589-fd97-4073-8cf4-82ae216a88bc.png" />
        </a>
        <br />
        <a href="https://user-images.githubusercontent.com/31543482/232265800-6bdc7973-41fe-4d7e-a554-98ea7ca7a137.png">(Mask)</a>
      </td>
    </tr>
  </tbody>
</table>

## 在线版

官方演示站 (由 zyddnys 维护)： <https://touhou.ai/imgtrans/>\
浏览器 Userscript (由 QiroNT 维护): <https://greasyfork.org/scripts/437569>

- 注意，由于 Google GCP 经常重启我的实例，在线演示站点有时可能无法访问。
  在这种情况下，您可以等待我重启服务，这可能需要长达 24 小时。
- 注意，此在线演示站点使用的是当前的 main 分支版本。

## 免责声明

[MMDOCR-HighPerformance](https://github.com/PatchyVideo/MMDOCR-HighPerformance) 的继任者。\
**这是一个业余项目，欢迎您贡献代码！**\
目前这只是一个简单的演示，存在许多不完善之处，我们需要您的支持来使这个项目变得更好！\
主要为翻译日语文本而设计，但也支持中文、英语和韩语。\
支持图像修复、文本渲染和着色。

## 安装

### 本地安装

#### Pip/venv

```bash
# 首先，您需要在系统上安装 Python(>=3.8)
# 最新版本可能尚不兼容某些 pytorch 库
$ python --version
Python 3.10.6

# 克隆此仓库
$ git clone https://github.com/zyddnys/manga-image-translator.git

# 创建 venv
$ python -m venv venv

# 激活 venv
$ source venv/bin/activate

# 对于 --use-gpu 选项，请访问 https://pytorch.org/ 并按照
# pytorch 安装说明进行操作。添加 `--upgrade --force-reinstall`
# 到 pip 命令以覆盖当前安装的 pytorch 版本。

# 安装依赖
$ pip install -r requirements.txt
```

模型将在运行时下载到 `./models` 目录中。

#### **Windows** 额外说明

在开始 pip 安装之前，请先安装 Microsoft C++ Build Tools ([下载](https://visualstudio.microsoft.com/vs/),
[说明](https://stackoverflow.com/questions/40504552/how-to-install-visual-c-build-tools))，
因为某些 pip 依赖项在没有它的情况下将无法编译。
(参见 [#114](https://github.com/zyddnys/manga-image-translator/issues/114))。

要在 Windows 上使用 [cuda](https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64)，
请按照 <https://pytorch.org/> 上的说明安装正确的 pytorch 版本。

### Docker

要求：

- Docker (CUDA / GPU 加速需要 19.03+ 版本)
- Docker Compose (如果您想使用 `demo/doc` 文件夹中的文件，则为可选)
- Nvidia Container Runtime (如果您想使用 CUDA，则为可选)

本项目在 `zyddnys/manga-image-translator:main` 镜像下提供 Docker 支持。
此 Docker 镜像包含项目所需的所有依赖项/模型。
需要注意的是，此镜像相当大 (~ 15GB)。

#### 托管 Web 服务器

可以使用以下命令托管 Web 服务器（CPU）：

```bash
docker run -p 5003:5003 -v result:/app/result --ipc=host --rm zyddnys/manga-image-translator:main -l ENG --manga2eng -v --mode web --host=0.0.0.0 --port=5003
```

或者

```bash
docker-compose -f demo/doc/docker-compose-web-with-cpu.yml up
```

取决于您的偏好。Web 服务器应在端口 [5003](http://localhost:5003) 上启动，
图像应位于 `/result` 文件夹中。

#### 用作 CLI

要将 Docker 与 CLI 一起使用（即在批量模式下）：

```bash
docker run -v <目标文件夹>:/app/<目标文件夹> -v <目标文件夹>-translated:/app/<目标文件夹>-translated  --ipc=host --rm zyddnys/manga-image-translator:main --mode=batch -i=/app/<目标文件夹> <cli flags>
```

**注意：** 如果您需要引用主机上的文件，
则需要将相关文件作为卷挂载到容器内的 `/app` 文件夹中。
CLI 的路径需要是 Docker 内部路径 `/app/...`，而不是主机上的路径。

#### 设置翻译密钥

某些翻译服务需要 API 密钥才能运行，要设置这些密钥，请将它们作为 env 变量传递到 Docker 容器中。例如：

```bash
docker run --env="DEEPL_AUTH_KEY=xxx" --ipc=host --rm zyddnys/manga-image-translator:main <cli flags>
```

#### 配合 Nvidia GPU 使用

> 要配合受支持的 GPU 使用，请先阅读初始 `Docker` 部分。您将需要使用一些特殊的依赖项

要使用以下标志运行容器：

```bash
docker run ... --gpus=all ... zyddnys/manga-image-translator:main ... --use-gpu
```

或者（对于 Web 服务器 + GPU）：

```bash
docker-compose -f demo/doc/docker-compose-web-with-gpu.yml up
```

#### 本地构建

要在本地构建 Docker 镜像，您可以运行（您的机器需要安装 make）：

```bash
make build-image
```

然后要测试构建的镜像，请运行：

```bash
make run-web-server
```

## 使用方法

### 本地模式

```bash
# 将 <path> 替换为图像文件夹或文件的路径。
$ python -m manga_translator local -v -i <path>
# 结果可以在 `<path_to_image_folder>-translated` 中找到。
```

### Web 模式

```bash
# 使用 `--mode web` 启动 Web 服务器。
$ cd server && python main.py --use-gpu
# 演示站点将在 http://127.0.0.1:8000 上提供服务
```

## 相关项目

GUI 实现: [BallonsTranslator](https://github.com/dmMaze/BallonsTranslator)

## 文档

### 推荐模块

检测器:

- ENG: ??
- JPN: ??
- CHS: ??
- KOR: ??
- 使用 `{"detector":{"detector": "ctd"}}` 可以增加检测到的文本行数

OCR:

- ENG: ??
- JPN: 48px
- CHS: ??
- KOR: 48px

翻译器:

- JPN -> ENG: **Sugoi**
- CHS -> ENG: ??
- CHS -> JPN: ??
- JPN -> CHS: ??
- ENG -> JPN: ??
- ENG -> CHS: ??

图像修复器: lama_large

着色器: **mc2**

<!-- Auto generated start (See devscripts/make_readme.py) -->

#### 提高翻译质量的技巧

- 小分辨率有时会使检测器出错，因为它不太擅长识别不规则的文本大小。为了
  规避这个问题，您可以使用放大器，通过指定 `--upscale-ratio 2` 或任何其他值
- 如果渲染的文本太小而无法阅读，请指定 `--font-size-minimum 30`，例如，或者使用 `--manga2eng`
  渲染器，它将尝试适应检测到的文本气泡
- 使用 `--font-path fonts/anime_ace_3.ttf` 等指定字体
- 设置 `mask_dilation_offset` 为 20~40。
- 使用 `lama_large` 作为图像修复器。
- 增加 `box_threshold` 可以帮助在一定程度上过滤掉 OCR 错误检测产生的乱码。
- 使用词汇表文件。

### 基本选项

```text
-h, --help                     show this help message and exit
-v, --verbose                  Print debug info and save intermediate images in result folder
--attempts ATTEMPTS            Retry attempts on encountered error. -1 means infinite times.
--ignore-errors                Skip image on encountered error.
--model-dir MODEL_DIR          Model directory (by default ./models in project root)
--use-gpu                      Turn on/off gpu (auto switch between mps and cuda)
--use-gpu-limited              Turn on/off gpu (excluding offline translator)
--font-path FONT_PATH          Path to font file
--pre-dict PRE_DICT            Path to the pre-translation replacement dictionary file
--post-dict POST_DICT          Path to the post-translation replacement dictionary file
--kernel-size KERNEL_SIZE      Set the convolution kernel size of the text erasure area to
                               completely clean up text residues
```

### 附加选项:

## 批量模式选项

```text
local                         Run in batch translation mode
-i, --input INPUT [INPUT ...] Path to an image folder (required)
-o, --dest DEST               Path to the destination folder for translated images (default: '')
-f, --format FORMAT           Output format of the translation.  Choices: [list the OUTPUT_FORMATS here, png,webp,jpg,jpeg,xcf,psd,pdf]
--overwrite                   Overwrite already translated images
--skip-no-text                Skip image without text (Will not be saved).
--use-mtpe                    Turn on/off machine translation post editing (MTPE) on the command line (works only on linux right now)
--save-text                   Save extracted text and translations into a text file.
--load-text                   Load extracted text and translations from a text file.
--save-text-file SAVE_TEXT_FILE  Like --save-text but with a specified file path. (default: '')
--prep-manual                 Prepare for manual typesetting by outputting blank, inpainted images, plus copies of the original for reference
--save-quality SAVE_QUALITY   Quality of saved JPEG image, range from 0 to 100 with 100 being best (default: 100)
--config-file CONFIG_FILE     path to the config file (default: None)
```

## WebSocket 模式选项

```text
ws                  Run in WebSocket mode
--host HOST         Host for WebSocket service (default: 127.0.0.1)
--port PORT         Port for WebSocket service (default: 5003)
--nonce NONCE       Nonce for securing internal WebSocket communication
--ws-url WS_URL     Server URL for WebSocket mode (default: ws://localhost:5000)
--models-ttl MODELS_TTL  How long to keep models in memory in seconds after last use (0 means forever)
```

## API 模式选项

```text
shared              Run in API mode
--host HOST         Host for API service (default: 127.0.0.1)
--port PORT         Port for API service (default: 5003)
--nonce NONCE       Nonce for securing internal API server communication
--report REPORT     reports to server to register instance (default: None)
--models-ttl MODELS_TTL  models TTL in memory seconds (0 means forever)
```

## Web 模式选项 (缺少一些基本选项，需要重新添加)

```text
--host HOST           The host address (default: 127.0.0.1)
--port PORT           The port number (default: 8000)
--start-instance      If a translator should be launched automatically
--nonce NONCE         Nonce for securing internal web server communication
--models-ttl MODELS_TTL  models TTL in memory in seconds (0 means forever)
```

## config-help 模式

```bash
python -m manga_translator config-help
```

### 语言代码参考

由配置中的 `translator/language` 使用

```yaml
CHS: Chinese (Simplified) # 简体中文
CHT: Chinese (Traditional) # 繁体中文
CSY: Czech # 捷克语
NLD: Dutch # 荷兰语
ENG: English # 英语
FRA: French # 法语
DEU: German # 德语
HUN: Hungarian # 匈牙利语
ITA: Italian # 意大利语
JPN: Japanese # 日语
KOR: Korean # 韩语
PLK: Polish # 波兰语
PTB: Portuguese (Brazil) # 葡萄牙语 (巴西)
ROM: Romanian # 罗马尼亚语
RUS: Russian # 俄语
ESP: Spanish # 西班牙语
TRK: Turkish # 土耳其语
UKR: Ukrainian # 乌克兰语
VIN: Vietnames # 越南语
ARA: Arabic # 阿拉伯语
SRP: Serbian # 塞尔维亚语
HRV: Croatian # 克罗地亚语
THA: Thai # 泰语
IND: Indonesian # 印度尼西亚语
FIL: Filipino (Tagalog) # 菲律宾语 (塔加路语)
```

### 翻译器参考

| 名称          | API 密钥 | 离线 | 注意事项                                                         |
|---------------|---------|---------|--------------------------------------------------------------|
| <s>google</s> |         |         | 暂时禁用                                                         |
| youdao        | ✔️      |         | 需要 `YOUDAO_APP_KEY` 和 `YOUDAO_SECRET_KEY`                       |
| baidu         | ✔️      |         | 需要 `BAIDU_APP_ID` 和 `BAIDU_SECRET_KEY`                          |
| deepl         | ✔️      |         | 需要 `DEEPL_AUTH_KEY`                                        |
| caiyun        | ✔️      |         | 需要 `CAIYUN_TOKEN`                                            |
| openai        | ✔️      |         | 实现 Requires `OPENAI_API_KEY`                                 |
| papago        |         |         |                                                                |
| sakura        |         |         | 需要 `SAKURA_API_BASE`                                         |
| custom openai |         |         | 需要 `CUSTOM_OPENAI_API_BASE` `CUSTOM_OPENAI_MODEL`             |
| offline       |         | ✔️      | 为语言选择最合适的离线翻译器                                                    |
| sugoi         |         | ✔️      | Sugoi V4.0 模型                                                  |
| m2m100        |         | ✔️      | 支持所有语言                                                        |
| m2m100_big    |         | ✔️      |                                                                |
| none          |         | ✔️      | 翻译成空白文本                                                        |
| original      |         | ✔️      | 保留原始文本                                                        |

- API 密钥：翻译器是否需要 API 密钥作为环境变量设置。
  为此，您可以在项目根目录中创建一个 .env 文件，其中包含您的 API 密钥，如下所示：

```env
OPENAI_API_KEY=sk-xxxxxxx...
DEEPL_AUTH_KEY=xxxxxxxx...
```
### 词汇表
- mit_glossory: 向 AI 模型发送词汇表以指导其翻译可以有效提高翻译质量，例如，确保专有名称和人名的翻译一致。它会自动从词汇表中提取当前翻译的有效条目，因此无需担心词汇表中的大量条目会影响翻译质量。（仅对 openaitranslator 有效，兼容 sakura_dict 和 galtransl_dict。）

- sakura_dict: sakura 词汇表，仅对 sakuratranslator 有效。没有自动词汇表功能。

```env
OPENAI_GLOSSARY_PATH=PATH_TO_YOUR_FILE
SAKURA_DICT_PATH=PATH_TO_YOUR_FILE
```


- 离线：翻译器是否可以离线使用。

- Sugoi 由 mingshiba 创建，请在 https://www.patreon.com/mingshiba 上支持他

### 配置文件

运行 `python -m manga_translator config-help >> config-info.json`

示例可以在 example/config-example.json 中找到

```json
{
  "$defs": {
    "Alignment": {
      "enum": [
        "auto",
        "left",
        "center",
        "right"
      ],
      "title": "Alignment",
      "type": "string"
    },
    "Colorizer": {
      "enum": [
        "none",
        "mc2"
      ],
      "title": "Colorizer",
      "type": "string"
    },
    "ColorizerConfig": {
      "properties": {
        "colorization_size": {
          "default": 576,
          "title": "Colorization Size",
          "type": "integer"
        },
        "denoise_sigma": {
          "default": 30,
          "title": "Denoise Sigma",
          "type": "integer"
        },
        "colorizer": {
          "$ref": "#/$defs/Colorizer",
          "default": "none"
        }
      },
      "title": "ColorizerConfig",
      "type": "object"
    },
    "Detector": {
      "enum": [
        "default",
        "dbconvnext",
        "ctd",
        "craft",
        "none"
      ],
      "title": "Detector",
      "type": "string"
    },
    "DetectorConfig": {
      "properties": {
        "detector": {
          "$ref": "#/$defs/Detector",
          "default": "default"
        },
        "detection_size": {
          "default": 1536,
          "title": "Detection Size",
          "type": "integer"
        },
        "text_threshold": {
          "default": 0.5,
          "title": "Text Threshold",
          "type": "number"
        },
        "det_rotate": {
          "default": false,
          "title": "Det Rotate",
          "type": "boolean"
        },
        "det_auto_rotate": {
          "default": false,
          "title": "Det Auto Rotate",
          "type": "boolean"
        },
        "det_invert": {
          "default": false,
          "title": "Det Invert",
          "type": "boolean"
        },
        "det_gamma_correct": {
          "default": false,
          "title": "Det Gamma Correct",
          "type": "boolean"
        },
        "box_threshold": {
          "default": 0.7,
          "title": "Box Threshold",
          "type": "number"
        },
        "unclip_ratio": {
          "default": 2.3,
          "title": "Unclip Ratio",
          "type": "number"
        }
      },
      "title": "DetectorConfig",
      "type": "object"
    },
    "Direction": {
      "enum": [
        "auto",
        "horizontal",
        "vertical"
      ],
      "title": "Direction",
      "type": "string"
    },
    "InpaintPrecision": {
      "enum": [
        "fp32",
        "fp16",
        "bf16"
      ],
      "title": "InpaintPrecision",
      "type": "string"
    },
    "Inpainter": {
      "enum": [
        "default",
        "lama_large",
        "lama_mpe",
        "sd",
        "none",
        "original"
      ],
      "title": "Inpainter",
      "type": "string"
    },
    "InpainterConfig": {
      "properties": {
        "inpainter": {
          "$ref": "#/$defs/Inpainter",
          "default": "none"
        },
        "inpainting_size": {
          "default": 2048,
          "title": "Inpainting Size",
          "type": "integer"
        },
        "inpainting_precision": {
          "$ref": "#/$defs/InpaintPrecision",
          "default": "fp32"
        }
      },
      "title": "InpainterConfig",
      "type": "object"
    },
    "Ocr": {
      "enum": [
        "32px",
        "48px",
        "48px_ctc",
        "mocr"
      ],
      "title": "Ocr",
      "type": "string"
    },
    "OcrConfig": {
      "properties": {
        "use_mocr_merge": {
          "default": false,
          "title": "Use Mocr Merge",
          "type": "boolean"
        },
        "ocr": {
          "$ref": "#/$defs/Ocr",
          "default": "48px"
        },
        "min_text_length": {
          "default": 0,
          "title": "Min Text Length",
          "type": "integer"
        },
        "ignore_bubble": {
          "default": 0,
          "title": "Ignore Bubble",
          "type": "integer"
        }
      },
      "title": "OcrConfig",
      "type": "object"
    },
    "RenderConfig": {
      "properties": {
        "renderer": {
          "$ref": "#/$defs/Renderer",
          "default": "default"
        },
        "alignment": {
          "$ref": "#/$defs/Alignment",
          "default": "auto"
        },
        "disable_font_border": {
          "default": false,
          "title": "Disable Font Border",
          "type": "boolean"
        },
        "font_size_offset": {
          "default": 0,
          "title": "Font Size Offset",
          "type": "integer"
        },
        "font_size_minimum": {
          "default": -1,
          "title": "Font Size Minimum",
          "type": "integer"
        },
        "direction": {
          "$ref": "#/$defs/Direction",
          "default": "auto"
        },
        "uppercase": {
          "default": false,
          "title": "Uppercase",
          "type": "boolean"
        },
        "lowercase": {
          "default": false,
          "title": "Lowercase",
          "type": "boolean"
        },
        "gimp_font": {
          "default": "Sans-serif",
          "title": "Gimp Font",
          "type": "string"
        },
        "no_hyphenation": {
          "default": false,
          "title": "No Hyphenation",
          "type": "boolean"
        },
        "font_color": {
          "anyOf": [
            {
              "type": "string"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Font Color"
        },
        "line_spacing": {
          "anyOf": [
            {
              "type": "integer"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Line Spacing"
        },
        "font_size": {
          "anyOf": [
            {
              "type": "integer"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Font Size"
        }
      },
      "title": "RenderConfig",
      "type": "object"
    },
    "Renderer": {
      "enum": [
        "default",
        "manga2eng",
        "none"
      ],
      "title": "Renderer",
      "type": "string"
    },
    "Translator": {
      "enum": [
        "youdao",
        "baidu",
        "deepl",
        "papago",
        "caiyun",
        "gpt3",
        "gpt3.5",
        "gpt4",
        "none",
        "original",
        "sakura",
        "deepseek",
        "groq",
        "offline",
        "nllb",
        "nllb_big",
        "sugoi",
        "jparacrawl",
        "jparacrawl_big",
        "m2m100",
        "m2m100_big",
        "mbart50",
        "qwen2",
        "qwen2_big"
      ],
      "title": "Translator",
      "type": "string"
    },
    "TranslatorConfig": {
      "properties": {
        "translator": {
          "$ref": "#/$defs/Translator",
          "default": "sugoi"
        },
        "target_lang": {
          "default": "ENG",
          "title": "Target Lang",
          "type": "string"
        },
        "no_text_lang_skip": {
          "default": false,
          "title": "No Text Lang Skip",
          "type": "boolean"
        },
        "skip_lang": {
          "anyOf": [
            {
              "type": "string"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Skip Lang"
        },
        "gpt_config": {
          "anyOf": [
            {
              "type": "string"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Gpt Config"
        },
        "translator_chain": {
          "anyOf": [
            {
              "type": "string"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Translator Chain"
        },
        "selective_translation": {
          "anyOf": [
            {
              "type": "string"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Selective Translation"
        }
      },
      "title": "TranslatorConfig",
      "type": "object"
    },
    "UpscaleConfig": {
      "properties": {
        "upscaler": {
          "$ref": "#/$defs/Upscaler",
          "default": "esrgan"
        },
        "revert_upscaling": {
          "default": false,
          "title": "Revert Upscaling",
          "type": "boolean"
        },
        "upscale_ratio": {
          "anyOf": [
            {
              "type": "integer"
            },
            {
              "type": "null"
            }
          ],
          "default": null,
          "title": "Upscale Ratio"
        }
      },
      "title": "UpscaleConfig",
      "type": "object"
    },
    "Upscaler": {
      "enum": [
        "waifu2x",
        "esrgan",
        "4xultrasharp"
      ],
      "title": "Upscaler",
      "type": "string"
    }
  },
  "properties": {
    "filter_text": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "type": "null"
        }
      ],
      "default": null,
      "title": "Filter Text"
    },
    "render": {
      "$ref": "#/$defs/RenderConfig",
      "default": {
        "renderer": "default",
        "alignment": "auto",
        "disable_font_border": false,
        "font_size_offset": 0,
        "font_size_minimum": -1,
        "direction": "auto",
        "uppercase": false,
        "lowercase": false,
        "gimp_font": "Sans-serif",
        "no_hyphenation": false,
        "font_color": null,
        "line_spacing": null,
        "font_size": null
      }
    },
    "upscale": {
      "$ref": "#/$defs/UpscaleConfig",
      "default": {
        "upscaler": "esrgan",
        "revert_upscaling": false,
        "upscale_ratio": null
      }
    },
    "translator": {
      "$ref": "#/$defs/TranslatorConfig",
      "default": {
        "translator": "sugoi",
        "target_lang": "ENG",
        "no_text_lang_skip": false,
        "skip_lang": null,
        "gpt_config": null,
        "translator_chain": null,
        "selective_translation": null
      }
    },
    "detector": {
      "$ref": "#/$defs/DetectorConfig",
      "default": {
        "detector": "default",
        "detection_size": 1536,
        "text_threshold": 0.5,
        "det_rotate": false,
        "det_auto_rotate": false,
        "det_invert": false,
        "det_gamma_correct": false,
        "box_threshold": 0.7,
        "unclip_ratio": 2.3
      }
    },
    "colorizer": {
      "$ref": "#/$defs/ColorizerConfig",
      "default": {
        "colorization_size": 576,
        "denoise_sigma": 30,
        "colorizer": "none"
      }
    },
    "inpainter": {
      "$ref": "#/$defs/InpainterConfig",
      "default": {
        "inpainter": "none",
        "inpainting_size": 2048,
        "inpainting_precision": "fp32"
      }
    },
    "ocr": {
      "$ref": "#/$defs/OcrConfig",
      "default": {
        "use_mocr_merge": false,
        "ocr": "48px",
        "min_text_length": 0,
        "ignore_bubble": 0
      }
    },
    "kernel_size": {
      "default": 3,
      "title": "Kernel Size",
      "type": "integer"
    },
    "mask_dilation_offset": {
      "default": 0,
      "title": "Mask Dilation Offset",
      "type": "integer"
    }
  },
  "title": "Config",
  "type": "object"
}
```

### GPT 配置参考

由 `--gpt-config` 参数使用。

```yaml
#  在要翻译的文本之前馈送到 GPT 的提示。
# 使用 {to_lang} 指示目标语言名称应插入的位置。
# 注意：ChatGPT 模型不使用此提示。
prompt_template: >
  请帮我将以下漫画文本翻译成 {to_lang}
  (如果它已经是 {to_lang} 或看起来像乱码，你必须按原样输出):\n

# 要使用的采样温度，介于 0 和 2 之间。
# 较高的值（如 0.8）会使输出更随机，
# 而较低的值（如 0.2）会使其更集中和确定。
temperature: 0.5

# 一种替代使用温度采样的方案，称为 nucleus sampling，
# 模型在其中考虑具有 top_p 概率质量的 tokens 的结果。
# 因此，0.1 意味着只考虑包含前 10% 概率质量的 tokens。
top_p: 1

# 是否在命令行输出中隐藏 _CHAT_SYSTEM_TEMPLATE 和 _CHAT_SAMPLE
verbose_logging: False

# 在要翻译的文本之前馈送到 ChatGPT 的提示。
# 使用 {to_lang} 指示目标语言名称应插入的位置。
# 此示例中使用的 Tokens：57+
chat_system_template: >
  你是一个专业的翻译引擎，
  请将故事翻译成口语化、
  优雅流畅的内容，
  不要参考机器翻译。
  你必须只翻译故事，绝不解释它。
  如果文本有任何问题，请按原样输出。

  翻译成 {to_lang}。

# 馈送到 ChatGPT 的示例，以显示对话示例。
# 以 [prompt, response] 格式，按目标语言名称键控。
#
# 通常，示例应包括一些翻译偏好的示例，理想情况下
# 一些可能遇到的角色名称。
#
# 如果您想禁用此功能，只需将其设置为空列表即可。
chat_sample:
  Simplified Chinese: # 此示例中使用的 Tokens：88 + 84
    - <|1|>恥ずかしい… 目立ちたくない… 私が消えたい…
      <|2|>きみ… 大丈夫⁉
      <|3|>なんだこいつ 空気読めて ないのか…？
    - <|1|>好尴尬…我不想引人注目…我想消失…
      <|2|>你…没事吧⁉
      <|3|>这家伙怎么看不懂气氛的…？

# 覆盖特定模型的配置。
# 目前列表为：gpt3、gpt35、gpt4
gpt35:
  temperature: 0.3
```

### 使用 Gimp 进行渲染

当将输出格式设置为 {`xcf`, `psd`, `pdf`} 时，将使用 Gimp 生成文件。

在 Windows 上，这假定 Gimp 2.x 安装在 `C:\Users\<Username>\AppData\Local\Programs\Gimp 2`。

生成的 `.xcf` 文件包含作为最底层layer的原始图像，并且图像修复作为单独的layer。
翻译后的文本框有自己的layer，原始文本作为layer名称，方便访问。

限制：

- Gimp 在保存 `.psd` 文件时会将文本layer转换为常规图像。
- Gimp 对旋转文本的处理效果不佳。编辑旋转文本框时，它还会弹出一个窗口，提示它已被外部程序修改。
- 字体族由 `--gimp-font` 参数单独控制。

### Api 文档

阅读 openapi 文档: `127.0.0.1:5003/docs`

## 下一步

以下是下一步需要完成的任务列表，欢迎您贡献代码。

1. 使用基于扩散模型的图像修复模型来实现接近完美的效果，但这可能会慢得多。
2. ~~**重要！！！需要帮助！！！** 当前的文本渲染引擎几乎不可用，我们需要您的帮助来改进
   文本渲染！~~
3. 文本渲染区域由检测到的文本行而不是语音气泡决定。\
   这适用于没有语音气泡的图像，但使得无法决定将翻译后的英语
   文本放在哪里。我不知道如何解决这个问题。
4. [Ryota et al.](https://arxiv.org/abs/2012.14271) 提出使用多模态机器翻译，也许我们可以添加 ViT
   特征来构建自定义 NMT 模型。
5. 使本项目适用于视频（用 C++ 重写代码并使用 GPU/其他硬件 NN 加速器）。\
   用于检测视频中的硬字幕，生成 ass 文件并完全删除它们。
6. ~~基于非深度学习算法的 Mask 优化，我目前正在测试基于 CRF 的算法。~~
7. ~~目前不支持倾斜文本区域合并~~
8. 创建 pip 仓库

## 支持我们

GPU 服务器价格昂贵，请考虑捐赠以支持我们。

- Ko-fi: <https://ko-fi.com/voilelabs>
- Patreon: <https://www.patreon.com/voilelabs>
- 爱发电: <https://afdian.net/@voilelabs>

  ### 感谢所有贡献者:
  <a href="https://github.com/zyddnys/manga-image-translator/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=zyddnys/manga-image-translator" />

</a>
```
