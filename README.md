原项目地址https://github.com/XPixelGroup/HYPIR?tab=readme-ov-file
原项目地址：https://github.com/XPixelGroup/HYPIR?tab=readme-ov-file

# HYPIR ComfyUI Plugin
# HYPIR ComfyUI 插件

This is a ComfyUI plugin for [HYPIR (Harnessing Diffusion-Yielded Score Priors for Image Restoration)](https://github.com/XPixelGroup/HYPIR), a state-of-the-art image restoration model based on Stable Diffusion 2.1.
这是一个用于 [HYPIR（利用扩散得分先验进行图像修复）](https://github.com/XPixelGroup/HYPIR) 的 ComfyUI 插件，HYPIR 是基于 Stable Diffusion 2.1 的先进图像修复模型。

## Features
## 功能特性

- **Image Restoration**: Restore and enhance low-quality images using diffusion priors
- **图像修复**：利用扩散先验修复和增强低质量图像
- **Batch Processing**: Process multiple images at once
- **批量处理**：一次处理多张图片
- **Advanced Controls**: Fine-tune model parameters for optimal results
- **高级控制**：可微调模型参数以获得最佳效果
- **Model Management**: Load and reuse HYPIR models efficiently
- **模型管理**：高效加载和复用 HYPIR 模型
- **Upscaling**: Built-in upscaling capabilities (1x to 8x)
- **放大功能**：内置放大功能（1x 到 8x）

## Installation
## 安装方法

### 1. Install the Plugin
### 1. 安装插件

Place this folder in your ComfyUI `custom_nodes` directory:
将本文件夹放入 ComfyUI 的 `custom_nodes` 目录下：
```
ComfyUI/custom_nodes/Comfyui-HYPIR/
```

### 2. Install HYPIR Dependencies
### 2. 安装 HYPIR 依赖

Navigate to the HYPIR folder and install the required dependencies:
进入 HYPIR 文件夹并安装所需依赖：

```bash
cd ComfyUI/custom_nodes/Comfyui-HYPIR/HYPIR
pip install -r requirements.txt
```

### 3. Model Download (Automatic)
### 3. 模型下载（自动）

The plugin will automatically download the required models on first use:
插件首次使用时会自动下载所需模型：

#### HYPIR Model
#### HYPIR 模型
The HYPIR restoration model will be downloaded to:
HYPIR 修复模型将下载到：
```
ComfyUI/models/HYPIR/HYPIR_sd2.pth
```

#### Base Model (Stable Diffusion 2.1)
#### 基础模型（Stable Diffusion 2.1）
The base Stable Diffusion 2.1 model will be automatically downloaded when needed to:
基础 Stable Diffusion 2.1 模型将在需要时自动下载到：
```
ComfyUI/models/HYPIR/stable-diffusion-2-1-base/
```

**Manual Download (Optional):**
**手动下载（可选）：**

**HYPIR Model:**
**HYPIR 模型：**
If you prefer to download manually, you can get the HYPIR model from:
如果你希望手动下载，可以从以下地址获取 HYPIR 模型：
- **HuggingFace**: [HYPIR_sd2.pth](https://huggingface.co/lxq007/HYPIR/tree/main)
- **HuggingFace**：[HYPIR_sd2.pth](https://huggingface.co/lxq007/HYPIR/tree/main)
- **OpenXLab**: [HYPIR_sd2.pth](https://openxlab.org.cn/models/detail/linxqi/HYPIR/tree/main)
- **OpenXLab**：[HYPIR_sd2.pth](https://openxlab.org.cn/models/detail/linxqi/HYPIR/tree/main)

Place the `HYPIR_sd2.pth` file in:
请将 `HYPIR_sd2.pth` 文件放在以下任一位置：
- Plugin directory: `ComfyUI/custom_nodes/Comfyui-HYPIR/`
- 插件目录：`ComfyUI/custom_nodes/Comfyui-HYPIR/`
- ComfyUI models directory: `ComfyUI/models/checkpoints/`
- ComfyUI 模型目录：`ComfyUI/models/checkpoints/`
- Or let the plugin automatically manage it in `ComfyUI/models/HYPIR/`
- 或让插件自动管理，放在 `ComfyUI/models/HYPIR/`

**Base Model:**
**基础模型：**
The base Stable Diffusion 2.1 model can be downloaded manually from:
基础 Stable Diffusion 2.1 模型可从以下地址手动下载：
- **HuggingFace**: [stable-diffusion-2-1-base](https://huggingface.co/stabilityai/stable-diffusion-2-1-base)
- **HuggingFace**：[stable-diffusion-2-1-base](https://huggingface.co/stabilityai/stable-diffusion-2-1-base)

Place the base model in:
请将基础模型放在：
```
ComfyUI/models/HYPIR/stable-diffusion-2-1-base/
```

**Note:** The plugin will automatically check for the base model in the HYPIR directory first. If not found, it will automatically download it from HuggingFace.
**注意：** 插件会优先在 HYPIR 目录下查找基础模型，如未找到会自动从 HuggingFace 下载。

## Usage
## 使用方法

### Basic Image Restoration
### 基础图像修复

1. Add the **HYPIR Image Restoration** node to your workflow
1. 在工作流中添加 **HYPIR Image Restoration** 节点
2. Connect an image to the `image` input
2. 将图片连接到 `image` 输入
3. Set your prompt (e.g., "high quality, detailed")
3. 设置提示词（如："high quality, detailed"）
4. Adjust the upscale factor if needed (1-8x)
4. 如有需要调整放大倍数（1-8x）
5. Set a seed for reproducible results (or use -1 for random)
5. 设置随机种子以获得可复现结果（或用 -1 表示随机）
6. Run the workflow
6. 运行工作流

### Advanced Image Restoration
### 高级图像修复

1. Add the **HYPIR Advanced Restoration** node
1. 添加 **HYPIR Advanced Restoration** 节点
2. This node provides additional control over:
2. 此节点提供更多参数控制：
   - `model_t`: Model timestep (default: 200)
   - `model_t`：模型步数（默认200）
   - `coeff_t`: Coefficient timestep (default: 200)
   - `coeff_t`：系数步数（默认200）
   - `lora_rank`: LoRA rank (default: 256)
   - `lora_rank`：LoRA 阶数（默认256）
   - `patch_size`: Processing patch size (default: 512)
   - `patch_size`：处理块大小（默认512）

### Model Management
### 模型管理

For better performance when processing multiple images:
处理多张图片时建议：

1. Use **HYPIR Model Loader** to load the model once
1. 使用 **HYPIR Model Loader** 节点一次性加载模型
2. Connect the loaded model to **HYPIR Restore with Model** nodes
2. 将加载好的模型连接到 **HYPIR Restore with Model** 节点
3. This avoids reloading the model for each image
3. 这样可以避免每张图片都重复加载模型

### Automatic Model Download
### 自动模型下载

The plugin automatically downloads required models on first use:
插件首次使用时会自动下载所需模型：

1. **HYPIR Model Manager** - Check model status and manually download models
1. **HYPIR Model Manager** - 检查模型状态并手动下载模型
2. **HYPIR Model Path Getter** - Get model paths with optional auto-download
2. **HYPIR Model Path Getter** - 获取模型路径并可选择自动下载
3. Models are stored in `ComfyUI/models/HYPIR/` for easy management
3. 所有模型都存放在 `ComfyUI/models/HYPIR/` 便于管理

### Base Model Selection
### 基础模型选择

The plugin now supports dropdown selection for base models:
插件现已支持下拉选择基础模型：
- **Available Models**: Currently supports `stable-diffusion-2-1-base`
- **可用模型**：目前支持 `stable-diffusion-2-1-base`
- **Smart Download**: Only downloads when not found locally
- **智能下载**：本地未找到时才会下载
- **Local Priority**: Uses local models when available
- **本地优先**：优先使用本地模型
- **Automatic Management**: Handles model paths automatically
- **自动管理**：自动处理模型路径

### Batch Processing
### 批量处理

1. Use **HYPIR Batch Restoration** to process multiple images
1. 使用 **HYPIR Batch Restoration** 节点批量处理图片
2. Connect a batch of images to the `images` input
2. 将多张图片连接到 `images` 输入
3. All images will be processed with the same prompt and settings
3. 所有图片将用相同的提示词和设置进行处理

## Node Reference
## 节点参考

### HYPIR Image Restoration
### HYPIR 图像修复
- **Inputs**: image, prompt, upscale_factor, seed, model_name, base_model_path
- **输入**：image, prompt, upscale_factor, seed, model_name, base_model_path
- **Outputs**: restored_image, status_message
- **输出**：restored_image, status_message
- **Description**: Basic image restoration with default parameters
- **描述**：使用默认参数的基础图像修复

### HYPIR Advanced Restoration
### HYPIR 高级修复
- **Inputs**: image, prompt, upscale_factor, seed, model_name, base_model_path, model_t, coeff_t, lora_rank, patch_size
- **输入**：image, prompt, upscale_factor, seed, model_name, base_model_path, model_t, coeff_t, lora_rank, patch_size
- **Outputs**: restored_image, status_message
- **输出**：restored_image, status_message
- **Description**: Advanced restoration with full parameter control
- **描述**：可完全控制参数的高级修复

### HYPIR Batch Restoration
### HYPIR 批量修复
- **Inputs**: images, prompt, upscale_factor, seed, model_name, base_model_path
- **输入**：images, prompt, upscale_factor, seed, model_name, base_model_path
- **Outputs**: restored_images, status_message
- **输出**：restored_images, status_message
- **Description**: Process multiple images at once
- **描述**：一次处理多张图片

### HYPIR Model Loader
### HYPIR 模型加载器
- **Inputs**: model_name, base_model_path, model_t, coeff_t, lora_rank
- **输入**：model_name, base_model_path, model_t, coeff_t, lora_rank
- **Outputs**: hypir_model, status_message
- **输出**：hypir_model, status_message
- **Description**: Load and cache HYPIR model for reuse
- **描述**：加载并缓存 HYPIR 模型以便复用

### HYPIR Restore with Model
### HYPIR 使用模型修复
- **Inputs**: hypir_model, image, prompt, upscale_factor, seed
- **输入**：hypir_model, image, prompt, upscale_factor, seed
- **Outputs**: restored_image, status_message
- **输出**：restored_image, status_message
- **Description**: Use pre-loaded model for restoration
- **描述**：使用预加载模型进行修复

### HYPIR Model Manager
### HYPIR 模型管理器
- **Inputs**: action, model_name
- **输入**：action, model_name
- **Outputs**: status_message, result_message
- **输出**：status_message, result_message
- **Description**: Manage HYPIR models (check status, download, list)
- **描述**：管理 HYPIR 模型（检查状态、下载、列出）

### HYPIR Model Path Getter
### HYPIR 模型路径获取器
- **Inputs**: model_name, auto_download
- **输入**：model_name, auto_download
- **Outputs**: model_path, status_message
- **输出**：model_path, status_message
- **Description**: Get model path with optional auto-download
- **描述**：获取模型路径并可选择自动下载

## Configuration
## 配置

You can modify the default settings in `hypir_config.py`:
你可以在 `hypir_config.py` 中修改默认设置：

```python
HYPIR_CONFIG = {
    "default_weight_path": "HYPIR_sd2.pth",
    "default_base_model_path": "stable-diffusion-2-1-base",
    "available_base_models": ["stable-diffusion-2-1-base"],
    "model_t": 200,
    "coeff_t": 200,
    "lora_rank": 256,
    # ... more settings
}
```

### Model Path Management
### 模型路径管理

The plugin includes intelligent model path management:
插件包含智能模型路径管理：
- **HYPIR Model**: Automatically downloaded to `ComfyUI/models/HYPIR/HYPIR_sd2.pth`
- **HYPIR 模型**：自动下载到 `ComfyUI/models/HYPIR/HYPIR_sd2.pth`
- **Base Model**: Automatically downloaded to `ComfyUI/models/HYPIR/stable-diffusion-2-1-base/` when needed
- **基础模型**：需要时自动下载到 `ComfyUI/models/HYPIR/stable-diffusion-2-1-base/`
- **Local Priority**: The plugin checks for local models first before downloading
- **本地优先**：插件会优先查找本地模型
- **Automatic Download**: Only downloads when models are not found locally
- **自动下载**：仅在本地未找到模型时才下载

## Tips for Best Results
## 最佳效果小贴士

1. **Prompts**: Use descriptive prompts that match the image content
1. **提示词**：使用与图片内容相符的描述性提示词
   - For portraits: "high quality portrait, detailed face, sharp features"
   - 人像："high quality portrait, detailed face, sharp features"
   - For landscapes: "high quality landscape, detailed scenery, sharp focus"
   - 风景："high quality landscape, detailed scenery, sharp focus"
   - For general images: "high quality, detailed, sharp, clear"
   - 通用："high quality, detailed, sharp, clear"

2. **Upscaling**: 
2. **放大**：
   - Use 1x for restoration without size change
   - 1x 表示仅修复不放大
   - Use 2x-4x for moderate upscaling
   - 2x-4x 适合中等放大
   - Use 8x for maximum upscaling (may be slower)
   - 8x 为最大放大（速度较慢）

3. **Parameters**:
3. **参数**：
   - Higher `model_t` values (200-500) for stronger restoration
   - `model_t` 越高（200-500）修复越强
   - Higher `coeff_t` values (200-500) for more aggressive enhancement
   - `coeff_t` 越高（200-500）增强越明显
   - Higher `lora_rank` (256-512) for better quality (uses more memory)
   - `lora_rank` 越高（256-512）质量越好（占用更多内存）

4. **Memory Management**:
4. **内存管理**：
   - Use smaller `patch_size` (256-512) if you encounter memory issues
   - 如遇内存不足可用较小的 `patch_size`（256-512）
   - Process images in smaller batches
   - 分批处理图片
   - Use the Model Loader node to avoid repeated model loading
   - 使用模型加载器节点避免重复加载模型

## Troubleshooting
## 故障排查

### Common Issues
### 常见问题

1. **Import Error**: Make sure HYPIR dependencies are installed
1. **导入错误**：请确保已安装 HYPIR 依赖
   ```bash
   cd HYPIR
   pip install -r requirements.txt
   ```

2. **Model Not Found**: The plugin will automatically download missing models
2. **模型未找到**：插件会自动下载缺失的模型
   - Check internet connection for automatic download
   - 检查网络连接以便自动下载
   - **HYPIR Model**: Place `HYPIR_sd2.pth` in plugin directory or ComfyUI models directory
   - **HYPIR 模型**：将 `HYPIR_sd2.pth` 放在插件目录或 ComfyUI 模型目录
   - **Base Model**: Place `stable-diffusion-2-1-base` folder in `ComfyUI/models/HYPIR/`
   - **基础模型**：将 `stable-diffusion-2-1-base` 文件夹放在 `ComfyUI/models/HYPIR/`
   - The plugin will automatically check and download missing models
   - 插件会自动检查并下载缺失模型

3. **CUDA Out of Memory**: 
3. **CUDA 内存溢出**：
   - Reduce `patch_size` to 256
   - 将 `patch_size` 降至 256
   - Process smaller images
   - 处理较小的图片
   - Use CPU mode if available
   - 如可用可切换到 CPU 模式

4. **Slow Processing**:
4. **处理缓慢**：
   - Use Model Loader to avoid repeated model loading
   - 使用模型加载器避免重复加载模型
   - Reduce upscale factor
   - 降低放大倍数
   - Use smaller images
   - 使用较小的图片

### Error Messages
### 错误信息

- **"Error importing HYPIR"**: Install HYPIR dependencies
- **“Error importing HYPIR”**：请安装 HYPIR 依赖
- **"Error loading model"**: Check model file path and permissions
- **“Error loading model”**：请检查模型文件路径和权限
- **"Error during restoration"**: Check image format and size
- **“Error during restoration”**：请检查图片格式和尺寸

## License
## 许可证

This plugin is provided under the same license as the original HYPIR project. Please refer to the [HYPIR repository](https://github.com/XPixelGroup/HYPIR) for license details.
本插件遵循原 HYPIR 项目的相同许可证。详情请参见 [HYPIR 仓库](https://github.com/XPixelGroup/HYPIR)。

## Acknowledgments
## 致谢

- Original HYPIR implementation by [XPixelGroup](https://github.com/XPixelGroup/HYPIR)
- HYPIR 原始实现：[XPixelGroup](https://github.com/XPixelGroup/HYPIR)
- ComfyUI community for the excellent framework
- ComfyUI 社区提供了优秀的框架

## Support
## 支持

For issues related to this ComfyUI plugin, please check:
如遇本插件相关问题，请参考：
1. This README for troubleshooting
1. 本 README 故障排查部分
2. The original [HYPIR repository](https://github.com/XPixelGroup/HYPIR) for model-specific issues
2. 原 [HYPIR 仓库](https://github.com/XPixelGroup/HYPIR) 以获取模型相关问题
3. ComfyUI documentation for general ComfyUI questions 
3. ComfyUI 文档以了解通用 ComfyUI 问题 
