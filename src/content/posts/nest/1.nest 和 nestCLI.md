---
title: nest 和 nest-cli
published: 2024-04-25
description: "nest 和 nest-cli"
tags: ["nest"]
category: nest
draft: false
---

### nest 初始化项目
```
# 第一种要时不时更新, 第二种不用更新
npm install -g @nestjs/cli
nest new 项目名
# 或者
npx @nestjs/cli new 项目名
```

### nest-cli 生成的目录结构
```
src
  - app.controller.spec.ts (控制器单元测试)
  - app.controller.ts (控制器)
  - app.module.ts (应用的根模块)
  - app.service.ts (具有单一方法的基本服务)
  - main.ts (使用核心函数 NestFactory 创建 Nest 应用实例的应用入口文件)
```

### controller(控制器)
- 控制器负责处理传入请求并向客户端返回响应
- 前端的理解就是一个接口地址, 前端访问这个接口会进入这个控制器
- 控制器里面的方法名可以随意取, 但是要加上装饰器

### DTO(Data Transfer Object)
- 数据传输对象, 用于定义数据传输的结构

### controller 接收参数
``` typescript
/* url param */
@Get(':id')
urlParam(@Param('id') id: string) {
    return `This is the user with the id: ${id}`;
}

/* query */
@Get('find')
query(@Query('name') name: string) {
    return `This is the user with the name: ${name}`;
}

/* form urlencoded 和 json, 两者取值方法一样, 会根据请求头 content-type 去区分 */
class UserDto {
  name: string;
  age: number;
}
@Post()
body(@Body() user: UserDto) {
    return `This is the user with the name: ${user.name} and age: ${user.age}`;
}
```

### 控制器属于模块, 所以要在模块里面引入控制器
``` typescript
@Module({
  controllers: [AppController],
  providers: [AppService],
})
```

### 可以用 cli 生成控制器
```
nest g controller user
```

-------------------------------------------

### service(服务)
- 为控制器处理请求提供服务

### 用 cli 创建 service
```
nest g service cats
```

### 服务注册
```typescript
import { Module } from '@nestjs/common';
import { CatsController } from './cats/cats.controller';
import { CatsService } from './cats/cats.service';

@Module({
  controllers: [CatsController],
  providers: [CatsService],
})
export class AppModule {}
```

------------------------------------------

### module(模块)
- 模块是一个具有 @Module() 装饰器的类
- 模块是一个模块化的单元, 用于组织应用程序中的一些功能

### cli 创建模块
```
nest g module cats
```