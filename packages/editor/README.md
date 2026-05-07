# @susie/editor

一个基于 Plate.js 的强大富文本编辑器，支持实时协同编辑。

## 特性

- 🎨 **丰富的编辑功能** - 支持标题、列表、表格、代码块、数学公式等
- 🤝 **实时协同** - 基于 Liveblocks 的多人实时编辑
- 📝 **Markdown 支持** - 原生 Markdown 解析和序列化
- 🎯 **模块化设计** - 按需引入功能模块
- 🎨 **Tailwind CSS** - 现代化的样式系统
- 🤖 **AI Copilot** - 内置 AI 写作助手

## 安装

```bash
npm install @susie/editor
# 或
pnpm add @susie/editor
```

## 基础使用

```tsx
import { PlateEditor } from '@susie/editor'

function MyEditor() {
  const [content, setContent] = useState('')

  return (
    <PlateEditor
      initialMarkdown={content}
      onChange={setContent}
      placeholder="开始写作..."
    />
  )
}
```

## 自定义插件组合

```tsx
import { PlateEditor } from '@susie/editor'
import {
  BasicBlocksKit,
  BasicMarksKit,
  TableKit,
  MarkdownKit,
} from '@susie/editor/kits'

// 只使用需要的功能
const MyEditorKit = [
  ...BasicBlocksKit,
  ...BasicMarksKit,
  ...TableKit,
  ...MarkdownKit,
]

function MyEditor() {
  return <PlateEditor plugins={MyEditorKit} />
}
```

## 协同编辑

```tsx
import { RoomProvider, ClientSideSuspense } from '@susie/editor/collaborative'
import { PlateEditor } from '@susie/editor'

function CollaborativeEditor({ roomId }: { roomId: string }) {
  return (
    <RoomProvider
      id={roomId}
      initialPresence={{ cursor: null, selection: null, name: '用户', color: '#f00' }}
      initialStorage={{ content: '' }}
    >
      <ClientSideSuspense fallback={<div>Loading...</div>}>
        {() => <PlateEditor />}
      </ClientSideSuspense>
    </RoomProvider>
  )
}
```

## 可用的 Kit 模块

### 元素 (Elements)
- `BasicBlocksKit` - 段落、标题、引用、分隔线
- `CodeBlockKit` - 代码块
- `TableKit` - 表格
- `ToggleKit` - 折叠块
- `TocKit` - 目录
- `MediaKit` - 图片、视频、音频、文件
- `CalloutKit` - 提示框
- `ColumnKit` - 多列布局
- `MathKit` - 数学公式
- `DateKit` - 日期选择器
- `LinkKit` - 链接
- `MentionKit` - @提及

### 文本样式 (Marks)
- `BasicMarksKit` - 粗体、斜体、下划线、删除线、代码
- `FontKit` - 字体大小、颜色

### 块样式 (Block Styles)
- `ListKit` - 有序/无序列表
- `AlignKit` - 文本对齐
- `LineHeightKit` - 行高
- `IndentKit` - 缩进

### 协作 (Collaboration)
- `DiscussionKit` - 讨论
- `CommentKit` - 评论
- `SuggestionKit` - 建议

### 编辑增强 (Editing)
- `SlashKit` - 斜杠命令
- `AutoformatKit` - 自动格式化
- `BlockMenuKit` - 块菜单
- `DndKit` - 拖拽排序
- `EmojiKit` - 表情

### 解析器 (Parsers)
- `DocxKit` - Word 文档导入
- `MarkdownKit` - Markdown 解析

### AI
- `CopilotKit` - AI 写作助手

## Tailwind 配置

确保在你的 `tailwind.config.ts` 中包含编辑器的样式：

```ts
export default {
  content: [
    // ... 其他路径
    './node_modules/@susie/editor/dist/**/*.js',
  ],
  // ...
}
```

## License

MIT




