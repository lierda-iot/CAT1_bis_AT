# GPIO Development Guide

This is a sample component development guide. Replace with your actual content.

## Overview

GPIO (General Purpose Input/Output) interface is used to control external devices.

## API Reference

### Initialization

```c
// Example code
int gpio_init(int pin, int mode);
```

### Read/Write Operations

```c
int gpio_read(int pin);
void gpio_write(int pin, int value);
```

## Example Code

Refer to the GPIO example programs in the examples directory.
