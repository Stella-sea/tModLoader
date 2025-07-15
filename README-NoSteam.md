# tModLoader 无Steam启动版本

这是一个修改版的 tModLoader，允许在没有 Steam 的环境下运行。

## 🎯 主要特性

- **无需Steam验证**：绕过Steam API初始化检查
- **强制GoG模式**：自动检测为GoG平台，避免Steam依赖
- **保持兼容性**：仍然支持通过 `-steam` 参数强制使用Steam模式
- **官方启动脚本**：使用与官方版本相同的启动流程

## 🚀 使用方法

### 快速启动

```bash
# Linux/Mac
./start-tModLoader.sh

# Windows
start-tModLoader.bat
```

### 专用无Steam启动脚本

```bash
# Linux/Mac
./start-tModLoader-NoSteam.sh

# Windows
start-tModLoader-NoSteam.bat
```

### 手动启动

```bash
dotnet tModLoader.dll -nosteam
```

## 📁 安装说明

1. **编译项目**：
   ```bash
   dotnet build src/tModLoader/Terraria/Terraria.csproj -c Release
   ```

2. **准备Terraria内容**：
   - 将编译后的tModLoader放在Terraria安装目录旁边，或
   - 将Terraria的Content文件夹复制到tModLoader运行目录

3. **运行**：
   ```bash
   ./start-tModLoader.sh
   ```

## 🔧 技术细节

### 修改的文件

1. **InstallVerifier.cs**
   - 强制GoG平台检测
   - 跳过GoG验证检查
   - 设置虚拟Terraria.exe路径

2. **SocialAPI.cs**
   - 增强 `-nosteam` 参数支持
   - 改进非Steam环境检测

3. **Main.TML.cs**
   - 改进Content文件夹查找逻辑
   - 添加多个fallback路径

### 启动参数

- `-nosteam`：强制非Steam模式（默认）
- `-steam`：强制Steam模式
- 其他参数与官方版本相同

## 🎮 兼容性

- ✅ 支持所有平台（Windows、Linux、macOS）
- ✅ 兼容官方模组
- ✅ 支持本地多人游戏
- ❌ 不支持Steam Workshop（使用GoG模式）
- ❌ 不支持Steam成就

## 📝 注意事项

1. **Content文件夹**：需要Terraria的Content文件夹才能正常运行
2. **模组安装**：模组需要手动安装，无法使用Steam Workshop
3. **存档兼容**：与官方版本的存档完全兼容

## 🔄 从官方版本迁移

1. 备份你的模组和存档
2. 下载并编译此版本
3. 将tModLoader放在Terraria目录旁边
4. 使用新的启动脚本运行

## 🐛 故障排除

### 常见问题

**Q: 提示找不到Content文件夹**
A: 确保Terraria的Content文件夹在正确位置，或将tModLoader放在Terraria安装目录中

**Q: 模组无法加载**
A: 检查模组是否兼容当前tModLoader版本，手动安装模组到ModLoader/Mods目录

**Q: 游戏崩溃**
A: 查看日志文件（tModLoader-Logs/client.log）获取详细错误信息

## 📄 许可证

本项目基于官方 tModLoader 项目，遵循相同的许可证条款。

## 🤝 贡献

欢迎提交Issue和Pull Request来改进这个项目。

---

**免责声明**：此版本仅用于学习和研究目的。请支持官方 tModLoader 项目。
