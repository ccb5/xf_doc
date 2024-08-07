# 文档指南

文档是用于帮助其他人了解你的代码、功能或者构思等信息的载体。

本文说明编写 xfusion 文档需要遵守的格式、内容等规则。

---

**适用范围：**

- *外部库以外*的所有文档，目前 xfusion 文档以 markdown 格式为主。

**阅读对象：**

- 所有贡献者。

---

本文假定读者已经对 markdown 语法有充分的了解，如对参考 markdown 语法，请参考[参考文献](#参考文献)中的`[2-3]`。

# 文档格式

xfusion 文档目前只提供中文和英文两种语言，为了管理不同语言文档中的图片，**请将文档中使用到的图片统一放到`doc/public/image`路径下**。

编写文档时，请遵循以下**文档规则：**

1. **一个段落写在同一行内。**

   **错误**示例如下。这个示例中将一段或者一句话分成了很多行。

   ```markdown {.line-numbers}
   我是一段很长的段落。在这个段落中，我将反复强调一个观点，那就是我是一段很长很长的
   段落。这个段落的目的是为了达到一定的字数，通过不断地重复“我是一段很长的段落”来实
   现。这种写作方式可能单调，但它有效地传达了信息，即我是一段很长的段落。总之，这个
   段落的核心就是它的长度和重复性。

   尽管现在的长度已经缩减，但核心思想仍然不变。这种重复的写作手法，虽然可能显得有些
   单调，却能够清晰地传达出一个信息：我是一段很长的段落。这就是这个段落存在的意义，
   它通过简洁的语言和重复的结构，向读者展示了其核心内容。总结来说，这个段落的主旨依
   然是它的冗长和重复，这是其独特的表达方式。
   ```

   **正确**的示例如下。
   markdown 在查看时通常会打开自动换行，不需要手动换行。
   一段话一行有助于在翻译软件中快速翻译，而不需要手动删除换行。

   ```markdown {.line-numbers}
   我是一段很长的段落。在这个段落中，我将反复强调一个观点，那就是我是一段很长很长的段落。这个段落的目的是为了达到一定的字数，通过不断地重复“我是一段很长的段落”来实现。这种写作方式可能单调，但它有效地传达了信息，即我是一段很长的段落。总之，这个段落的核心就是它的长度和重复性。

   尽管现在的长度已经缩减，但核心思想仍然不变。这种重复的写作手法，虽然可能显得有些单调，却能够清晰地传达出一个信息：我是一段很长的段落。这就是这个段落存在的意义，它通过简洁的语言和重复的结构，向读者展示了其核心内容。总结来说，这个段落的主旨依然是它的冗长和重复，这是其独特的表达方式。
   ```

1. **对齐中英文文档的行号。**

   这样做能帮助译者节省翻译的时间，而且通过比较行数也能在一定情况下反应某个语言的文档的领先和落后情况。

1. **使用自动格式化**，并注意一些格式细节。

   推荐使用 vscode 插件`esbenp.prettier-vscode`来完成格式化与 markdown 预览等功能。通过该插件可以使用`alt + shift + f`快捷键来快速格式化 markdown 文档而不用鼠标右键格式化或者手动格式化。

   1. **在中英文、数字间适当插入空格。**

      尽管很多渲染器在预览时可以自动插入空格，但还是有很多不支持。插入空格的 markdown 文档在阅读源码时更加美观。
      例如：`你说的对，但是《STM32》是由意法半导体 (ST) 推出的一系列 32 位的单片机。`。

   1. **使用`*`而不是`_`。**

      例如需要加粗的部分使用`**粗体**`、而不是`__粗体__`。
      因为`_`可能无法被正确识别，而且在输入中文时输入`_`需要频繁切换中英文输入。

   1. 代码块中**标注正确的语言种类**，以提供语法高亮。
   1. 建议在说明复杂的逻辑时使用`mermaid`、`wavedrom`绘制图表、时序图辅助说明。
   1. 不建议在 markdown 文档内使用注释，如`<!--  -->`。

1. 文件格式：

   1. 使用 3 或者 4 个空格替代`TAB`，并且**不要**使用制表符缩进代码；
   1. 行尾**不要**尾随空格；
   1. 文件编码格式为 **UTF-8** 格式；
   1. 使用 Unix 风格的 **LF** 行结束符。
   1. markdown 源码也需要保证一定的美观。
      TODO: markdown 源码格式具体规定。

# 文档内容

本节介绍文档中应当有什么内容。
目前主要说明 example 的介绍文档以及组件的说明文档应当有哪些内容。

## example 的介绍文档

TODO: example 的介绍文档模板。

example 的介绍文档需要包含以下内容：

1. **支持情况。**

   该示例**支持的芯片或平台**的概况。如：`stm32103c8`, `esp32`。

1. **示例简述。**

   这个示例**是什么**？提供了什么**功能**或者有什么**作用**？

1. **如何使用。**

   1. **所需的软件和硬件。**

      1. 软件如平台支持包。示例需要的**必要组件，如无特殊情况，必须集成到示例中**，而不需要再次克隆子模块等。
      1. 硬件包含芯片平台、所需要的片外外设，外设和芯片需要如何连接。

   1. 示例提供了什么**配置**？用户需要修改什么示例配置才能正常运行？
   1. 构建和烧录有什么步骤与特殊要点？

1. **运行现象。**

   运行该示例有什么**输出和现象**？

   1. 描述运行现象。
   1. 放出运行日志。

1. **常见问题。**

   示例有什么常见问题？需要如何解决？

1. **示例平台差异。**

   该示例在不同平台上运行会有什么不同表现？
   如果没有差异，该部分可以省略。如果有差异，需要怎么做才能屏蔽区别？如果无法屏蔽，请强调差异。

1. **示例详解。**（可以省略）

   主要介绍示例中的重点难点代码。

1. **测试环境。**

   需要列出以下信息确保其他人能够复现示例。

   1. 芯片型号；
   1. 芯片开发环境的 SDK 版本号；
   1. 工具链名称及版本号；
   1. 平台支持包版本号（如实现`xf_hal`的下层硬件驱动）。

## 组件的介绍文档

::: tip Note

组件的介绍文档模板。
:::

# 参考文献

1. [编写文档 - ESP32 - — ESP-IDF 编程指南 latest 文档 (espressif.com)](https://docs.espressif.com/projects/esp-idf/zh_CN/latest/esp32/contribute/documenting-code.html)
1. [Markdown 教程 | 菜鸟教程 (runoob.com)](https://www.runoob.com/markdown/md-tutorial.html)
1. [Markdown 入门基础 | Markdown 官方教程](https://markdown.com.cn/intro.html)
