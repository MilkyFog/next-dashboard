# next-dashboard

- 参考视频: https://www.bilibili.com/video/BV1my4hetEbL/?vd_source=bbb17d49654d454c95ef8157b625f1bb
- github: https://github.com/TomIsLoading/react-tailwind-dashboard
- youtube: https://www.youtube.com/watch?v=vdxnBKRD7kU

## git history
- git cz
  - ni -D cz-customizable cz-conventional-changelog-zh
  - package.json
    ```json
    "config": {
      "commitizen": {
        "path": "./node_modules/cz-conventional-changelog-zh"
      }
    }
    ```
  - 
- next修改网页的title
- next项目的初始化环境
  - global.css: 去除响应式和暗色模式
    - before
      ```css
      @tailwind base;
      @tailwind components;
      @tailwind utilities;

      :root {
        --background: #ffffff;
        --foreground: #171717;
      }

      @media (prefers-color-scheme: dark) {
        :root {
          --background: #0a0a0a;
          --foreground: #ededed;
        }
      }

      body {
        color: var(--foreground);
        background: var(--background);
        font-family: Arial, Helvetica, sans-serif;
      }

      @layer utilities {
        .text-balance {
          text-wrap: balance;
        }
      }

      ```
    - after
      ```css
      @tailwind base;
      @tailwind components;
      @tailwind utilities;
      ```
    - 
  - package.json: 安装需要的软件包cmdk framer-motion react-icons recharts tailwind-merge
    - before
      ```json
      {
        "name": "next-dashboard",
        "version": "0.1.0",
        "private": true,
        "scripts": {
          "dev": "next dev",
          "build": "next build",
          "start": "next start",
          "lint": "next lint"
        },
        "dependencies": {
          "next": "14.2.9",
          "react": "^18",
          "react-dom": "^18"
        },
        "devDependencies": {
          "@types/node": "^20",
          "@types/react": "^18",
          "@types/react-dom": "^18",
          "cz-conventional-changelog-zh": "^0.0.2",
          "cz-customizable": "^7.2.1",
          "eslint": "^8",
          "eslint-config-next": "14.2.9",
          "postcss": "^8",
          "tailwindcss": "^3.4.1",
          "typescript": "^5"
        },
        "config": {
          "commitizen": {
            "path": "./node_modules/cz-conventional-changelog-zh"
          }
        }
      }
      ```
    - after
      ```json
      {
        "name": "next-dashboard",
        "version": "0.1.0",
        "private": true,
        "scripts": {
          "dev": "next dev",
          "build": "next build",
          "start": "next start",
          "lint": "next lint"
        },
        "dependencies": {
          "cmdk": "^1.0.0",
          "framer-motion": "^11.5.4",
          "next": "14.2.9",
          "react": "^18",
          "react-dom": "^18",
          "react-icons": "^5.3.0",
          "recharts": "^2.12.7",
          "tailwind-merge": "^2.5.2"
        },
        "devDependencies": {
          "@types/node": "^20",
          "@types/react": "^18",
          "@types/react-dom": "^18",
          "cz-conventional-changelog-zh": "^0.0.2",
          "cz-customizable": "^7.2.1",
          "eslint": "^8",
          "eslint-config-next": "14.2.9",
          "postcss": "^8",
          "tailwindcss": "^3.4.1",
          "typescript": "^5"
        },
        "config": {
          "commitizen": {
            "path": "./node_modules/cz-conventional-changelog-zh"
          }
        }
      }
      ```
  - page.tsx: 清空原来的元素 设置侧边栏和仪表盘的空间分布
    - before
      ```tsx
      import Image from 'next/image'

      export default function Home() {
        return (
          <div className="grid grid-rows-[20px_1fr_20px] items-center justify-items-center min-h-screen p-8 pb-20 gap-16 sm:p-20 font-[family-name:var(--font-geist-sans)]">
            <main className="flex flex-col gap-8 row-start-2 items-center sm:items-start">
              <Image
                className="dark:invert"
                src="https://nextjs.org/icons/next.svg"
                alt="Next.js logo"
                width={180}
                height={38}
                priority
              />
              <ol className="list-inside list-decimal text-sm text-center sm:text-left font-[family-name:var(--font-geist-mono)]">
                <li className="mb-2">
                  Get started by editing{' '}
                  <code className="bg-black/[.05] dark:bg-white/[.06] px-1 py-0.5 rounded font-semibold">
                    src/app/page.tsx
                  </code>
                  .
                </li>
                <li>Save and see your changes instantly.</li>
              </ol>

              <div className="flex gap-4 items-center flex-col sm:flex-row">
                <a
                  className="rounded-full border border-solid border-transparent transition-colors flex items-center justify-center bg-foreground text-background gap-2 hover:bg-[#383838] dark:hover:bg-[#ccc] text-sm sm:text-base h-10 sm:h-12 px-4 sm:px-5"
                  href="https://vercel.com/new?utm_source=create-next-app&utm_medium=appdir-template-tw&utm_campaign=create-next-app"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                  <Image
                    className="dark:invert"
                    src="https://nextjs.org/icons/vercel.svg"
                    alt="Vercel logomark"
                    width={20}
                    height={20}
                  />
                  Deploy now
                </a>
                <a
                  className="rounded-full border border-solid border-black/[.08] dark:border-white/[.145] transition-colors flex items-center justify-center hover:bg-[#f2f2f2] dark:hover:bg-[#1a1a1a] hover:border-transparent text-sm sm:text-base h-10 sm:h-12 px-4 sm:px-5 sm:min-w-44"
                  href="https://nextjs.org/docs?utm_source=create-next-app&utm_medium=appdir-template-tw&utm_campaign=create-next-app"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                  Read our docs
                </a>
              </div>
            </main>
            <footer className="row-start-3 flex gap-6 flex-wrap items-center justify-center">
              <a
                className="flex items-center gap-2 hover:underline hover:underline-offset-4"
                href="https://nextjs.org/learn?utm_source=create-next-app&utm_medium=appdir-template-tw&utm_campaign=create-next-app"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Image
                  aria-hidden
                  src="https://nextjs.org/icons/file.svg"
                  alt="File icon"
                  width={16}
                  height={16}
                />
                Learn
              </a>
              <a
                className="flex items-center gap-2 hover:underline hover:underline-offset-4"
                href="https://vercel.com/templates?framework=next.js&utm_source=create-next-app&utm_medium=appdir-template-tw&utm_campaign=create-next-app"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Image
                  aria-hidden
                  src="https://nextjs.org/icons/window.svg"
                  alt="Window icon"
                  width={16}
                  height={16}
                />
                Examples
              </a>
              <a
                className="flex items-center gap-2 hover:underline hover:underline-offset-4"
                href="https://nextjs.org?utm_source=create-next-app&utm_medium=appdir-template-tw&utm_campaign=create-next-app"
                target="_blank"
                rel="noopener noreferrer"
              >
                <Image
                  aria-hidden
                  src="https://nextjs.org/icons/globe.svg"
                  alt="Globe icon"
                  width={16}
                  height={16}
                />
                Go to nextjs.org →
              </a>
            </footer>
          </div>
        )
      }

      ```
    - after
      ```tsx
      export default function Home() {
        return (
          <main className="grid gap-4 p-4 grid-cols-[220px,_1fr]">
            <div className="sidebar">SideBar</div>
            <div className="dashboard">Dashboard</div>
          </main> 
        )
      }
      ```
    - 
  - layout.tsx: 设置body字体样式 颜色 背景颜色
    - before
      ```tsx
      import type { Metadata } from 'next'
      import localFont from 'next/font/local'
      import './globals.css'

      const geistSans = localFont({
        src: './fonts/GeistVF.woff',
        variable: '--font-geist-sans',
        weight: '100 900',
      })
      const geistMono = localFont({
        src: './fonts/GeistMonoVF.woff',
        variable: '--font-geist-mono',
        weight: '100 900',
      })

      export const metadata: Metadata = {
        title: 'Next Dashboard',
        description: 'Generated by create next app',
      }

      export default function RootLayout({
        children,
      }: Readonly<{
        children: React.ReactNode;
      }>) {
        return (
          <html lang="en">
            <body
              className={`${geistSans.variable} ${geistMono.variable} antialiased`}
            >
              {children}
            </body>
          </html>
        )
      }
      ```
    - after 
      ```tsx
      import type { Metadata } from 'next'
      import { Inter } from 'next/font/google'
      import './globals.css'

      const inter = Inter({ subsets: ['latin'] })

      export const metadata: Metadata = {
        title: 'Create Next App',
        description: 'Generated by create next app',
      }

      export default function RootLayout({
        children,
      }: Readonly<{
        children: React.ReactNode;
      }>) {
        return (
          <html lang="en">
            <body className={`${inter.className} text-stone-950 bg-stone-100`}>
              {children}
            </body>
          </html>
        )
      }
      ```
  - 
  - 
## next
- "use client": 标记该tsx文件的组件是客户端组件 一般涉及到click 与用户交互的组件就需要使用客户端组件
- 
- 

## components

- Sidebar
  - Sidebar.tsx: 侧边栏
    - overflow-y-scroll sticky h-[calc(100vh-36p-38px)]
  - AccountToggle.tsx: 侧边栏的头部的用户栏 昵称 邮箱
  - Search.tsx: 搜索栏
  - CommandMenu.tsx: cmdk按钮 + 列表
  - RouteSelect.tsx: 选项列表
    - <button></button>: 使用button元素作为侧边栏的列表项
    - <Route></Route>: 自定义的Route组件
      - props: selected Icon title
      - 
    - 
  - Plan.tsx: 侧边栏最下面的计划表
- DashBoard
  - DashBoard.tsx: 
  - TopBar.tsx: 右侧仪表盘的头部
    - <FiCalendar />: 选择日期的组件
  - Grid.tsx: 放置DashBoard内容
    - grid-cols-12
    - components: <StatCard /> <ActivityGraph /> <UsageRadar />
  - StatCard.tsx: 仪表盘中的静态卡片
    - Card: 涉及财务报表的卡片 p-4 col-span-4
      - props: title value pillText trend period
      - 
    - 
  - ActivityGraph.tsx: 显示仪表盘中的折线图 曲线图
    - css: col-span-8 overflow-hidden
    - data: name desktop mobile amt
    - <ResponsiveContainer />
    - <LineChart width={500} height={300} data={data}></LineChart>
    - <CartesianGrid strokeDasharray="3 3"/>: 3 * 3的虚线网格
    - <XAxis dataKey="name" padding={{}} />
    - <YAxis />
    - <Line type="monotone" dataKey="New" stroke="#181818"  />
  - UsageRadar.tsx: 雷达图
    - 
  - RecentTransaction.tsx: 最近的交易结果
    - <TableHead />
      - thead > tr > th
    - <TableRow /> 
      - props: cusId, sku, date, price, order
      - <tr className={order % 2 ? 'bg-stone-100 text-sm' : 'text-sm'}></tr>
      - <td></td>
    - 
  - 
  - 
- 

## Recharts
- 一个显示折线图的图标库
- data 
- 

## Fi: 一个组件库

- <FiCalendar />: 选择日期的组件
- <FiTrendingUp />: 展示趋势的组件 
- <FiUser />: 

## TailwindCSS
- h-[calc(100vh_-_100px_-_16px)]: 原子化CSS如何使用calc() 数字 -前面需要加上_
- transition-colors
- space-y-1: 给里面的每个元素添加上margin-y-1 适合列表
- transition-[box-shadow,_background-color,_color]: transition指定特定属性添加动画
- ${selected ? "bg-white" : "bg-transparent"}: 根据变量选择特定的类名
- className={``}: 使用模版字符串
- shink-0: 设置给头像 防止因为flex布局 头像变小
- color: stone(石头灰色)
- col-span-4: grid布局中的元素占据4格宽度
- font-medium text-xs: 
- 

## icon
  - <FiLogOut />: 退出图标
## npm
  - cmdk: cmd + k进行search
## vscode
    