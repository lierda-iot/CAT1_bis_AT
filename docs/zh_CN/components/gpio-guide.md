# GPIO 开发指导

这是一个组件开发指导的示例文档，请替换为你的实际内容。

## 功能概述

GPIO（通用输入输出）接口用于控制外部设备。

## API 说明

### 初始化

```c
// 示例代码
int gpio_init(int pin, int mode);
```

### 读写操作

```c
int gpio_read(int pin);
void gpio_write(int pin, int value);
```

## 示例代码

请参考 examples 目录中的 GPIO 示例程序。
