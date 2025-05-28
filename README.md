# AI阿拉伯书法生成器

本项目是一款基于人工智能的在线工具，旨在为用户提供便捷、高效且富有创意的阿拉伯书法作品生成体验。项目基于 [ShipAny AI SaaS Boilerplate](https://shipany.ai)进行二次开发，充分利用其提供的健全的基础设施（包括用户认证、支付系统等），使我们能够更专注于核心业务逻辑——AI驱动的书法艺术创作。

![preview](preview.png)

## 项目特点

- **基于 ShipAny 模板：** 快速启动开发，集成了登录、支付等SaaS基础功能。
- **聚焦核心业务：** 主要开发精力投入在AI阿拉伯书法生成引擎、独特的风格模板以及优化的用户创作流程上。
- **先进的AI技术：** 利用AI模型和提示词工程，生成具有高度艺术美感和个性化风格的书法作品。
- **用户友好的体验：** 提供直观的界面和流畅的交互，让用户轻松创作。

## 技术栈 (Technical Stack)

本项目采用以下主要技术和库构建：

-   **核心框架 (Core Framework):** [Next.js](https://nextjs.org/) (使用 App Router)
-   **编程语言 (Programming Language):** [TypeScript](https://www.typescriptlang.org/)
-   **UI 渲染 (UI Rendering):** [React](https://reactjs.org/)
-   **样式方案 (Styling):** [Tailwind CSS](https://tailwindcss.com/)
-   **UI 组件库 (UI Components):** [Shadcn UI](https://ui.shadcn.com/)
-   **状态管理 (State Management):** React Context
-   **用户认证 (Authentication):** [NextAuth.js](https://next-auth.js.org/)
-   **国际化 (Internationalization):** [next-intl](https://next-intl-docs.vercel.app/)
-   **支付集成 (Payment Integration):** [Stripe](https://stripe.com/)
-   **消息通知 (Toast Notifications):** [Sonner](https://sonner.emilkowal.ski/)
-   **AI SDK 集成 (AI SDK Integration):** [Vercel AI SDK](https://sdk.vercel.ai/) (包括 `@ai-sdk/openai`, `@ai-sdk/replicate` 等)
-   **后端服务/数据库 (Backend/Database):** [Supabase](https://supabase.io/)
-   **包管理器 (Package Manager):** [pnpm](https://pnpm.io/)

## 项目文件结构 (Project File Structure)

项目的目录结构组织如下，遵循标准的 Next.js 和 SaaS 应用实践：

-   `app/`: Next.js App Router 核心目录，包含所有页面、布局和 API 路由。
    -   `[locale]/`: 动态路由，用于支持国际化，`locale` 参数表示当前语言环境 (例如 `en`, `ar`)。
        -   `(pages)/`: 包含各个页面的目录 (例如 `dashboard`, `generate`, `pricing`)。
        -   `layout.tsx`: 该语言环境的根布局。
        -   `global.css`: 全局样式 (如果 `theme.css` 不在此处)。
    -   `api/`: 后端 API 路由 (例如 `checkout`, `generate-artwork`, `user-profile`)。
    -   `theme.css`: 应用的全局主题和基础样式。
-   `components/`: 可重用的 React 组件。
    -   `blocks/`: 较大的页面构建块，通常用于特定页面如着陆页 (例如 `HeroSection`, `FeatureGrid`)。
    -   `ui/`: 通用的、原子级的 UI 组件，许多基于或定制自 Shadcn UI (例如 `Button`, `Card`, `Input`)。
-   `contexts/`: React Context API 实现，用于全局或特定功能的状态管理 (例如 `AppContext`, `AuthContext`)。
-   `i18n/`: 国际化相关文件。
    -   `messages/`: 包含不同语言的翻译消息文件 (例如 `en.json`, `ar.json`)。
    -   `navigation.ts` (或类似文件): 可能用于定义国际化的导航链接。
    -   `pages/landing/` (或按页面组织): 特定页面的翻译文本。
-   `lib/`: 存放辅助函数、工具函数、常量和自定义逻辑的库代码 (例如 `utils.ts`, `stripe.ts`, `constants.ts`)。
-   `models/`: 定义应用的数据模型、接口以及与数据库交互的逻辑 (例如 `User`, `Artwork`, `StyleTemplate`)。
-   `services/`: 包含应用的业务逻辑层，处理复杂操作和与外部服务（如 AI API、支付网关）的交互。
-   `public/`: 存放静态资源，如图片、字体、图标等，这些文件可以直接通过根 URL 访问。
-   `types/`: TypeScript 类型定义文件，用于增强代码的类型安全。
    -   `index.ts` (或按模块组织): 全局或模块化的类型定义。
    -   `blocks/`: 针对 `components/blocks` 的类型。
    -   `pages/`: 针对特定页面的数据或 props 类型。
-   `auth/`: (若存在) NextAuth.js 的特定配置文件、回调处理或自定义页面。
-   `.env.example`, `.env.local`: 环境变量配置文件。
-   `middleware.ts`: Next.js 中间件，常用于处理国际化路由、认证保护等。
-   `next.config.mjs`: Next.js 的主要配置文件。
-   `package.json`: 定义项目依赖、脚本等。
-   `tailwind.config.ts`: Tailwind CSS 配置文件。
-   `tsconfig.json`: TypeScript 编译器配置文件。

## 快速开始 (基于ShipAny)

1.  **克隆仓库**

    ```bash
    git clone [您的项目仓库URL]
    ```

2.  **安装依赖**

    ```bash
    pnpm install
    ```

3.  **配置环境变量**
    复制示例环境变量文件，并根据您的本地开发环境和第三方服务（如AI模型API、数据库、CDN、支付网关）进行配置：
    ```bash
    cp .env.example .env.local
    ```
    请确保填充 `.env.local` 文件中所有必要的变量。

4.  **运行开发服务器**

    ```bash
    pnpm dev
    ```

## 自定义与开发重点

由于本项目基于 ShipAny 模板，大部分基础设置（如主题、国际化文件结构）可参考 ShipAny 的文档。本项目的主要自定义和开发内容包括：

-   **核心AI书法生成逻辑：**
    -   AI模型接口的集成与调用。
    -   `StyleTemplate`（风格模板）的设计、实现与管理。
    -   `GeneratedArtwork`（生成作品）的数据模型与业务逻辑。
    -   文生图及图生图的核心算法与流程。
-   **用户界面与交互：**
    -   创作页面的定制化设计，以符合阿拉伯书法艺术的调性。
    -   风格选择、参数调整、作品展示等核心交互流程的优化。
-   **数据库模型扩展：**
    -   根据 `功能与数据设计文档.md` 扩展和调整数据库表，以支持书法生成、风格管理、积分系统等业务需求。
-   **内容管理：**
    -   `i18n/pages/landing`：着陆页特定内容。
    -   `i18n/messages`：全局国际化文本。
-   **主题定制：**
    -   `app/theme.css`：根据项目视觉风格调整主题。参考 [shadcn-ui-theme-generator](https://zippystarter.com/tools/shadcn-ui-theme-generator)。

## 部署

部署方式可以参考 ShipAny 模板提供的指南，并根据本项目的特定配置（如环境变量、数据库连接等）进行调整。

-   **Vercel 部署参考:**

    [![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fshipanyai%2Fshipany-template-one&project-name=my-shipany-project&repository-name=my-shipany-project&redirect-url=https%3A%2F%2Fshipany.ai&demo-title=ShipAny&demo-description=Ship%20Any%20AI%20Startup%20in%20hours%2C%20not%20days&demo-url=https%3A%2F%2Fshipany.ai&demo-image=https%3A%2F%2Fpbs.twimg.com%2Fmedia%2FGgGSW3La8AAGJgU%3Fformat%3Djpg%26name%3Dlarge)

-   **Cloudflare 部署参考:**

    1.  **自定义生产环境变量:**
        ```bash
        cp .env.example .env.production
        cp wrangler.toml.example wrangler.toml
        ```
        编辑 `.env.production` 中的环境变量，并确保 `wrangler.toml` 文件中 `[vars]` 部分也正确配置。
    2.  **部署命令:**
        ```bash
        npm run cf:deploy
        ```

## ShipAny 社区与资源 (模板基础)

-   [ShipAny官网](https://shipany.ai)
-   [ShipAny文档](https://docs.shipany.ai)
-   [ShipAny Discord](https://discord.gg/HQNnrzjZQS)

## 许可证

本项目基于 ShipAny 模板开发，其许可证信息请参考：
-   [ShipAny AI SaaS Boilerplate License Agreement](LICENSE)

请同时关注本项目自身的任何附加许可证条款（如果适用）。
