---
layout: post
section-type: post
has-comments: true
title: "Primitive Type"
category: java
---

- 6 Digital types：
    - `byte`、`short`、`int`、`long`
    - `float`、`double`
- `char`
- `boolean`

| Type | Bits | Bytes | Default | Range |
| --- | --- | --- | --- | --- |
| byte | 8 | 1 | 0 | -128 ~ 127 |
| short | 16 | 2 | 0 | -32768 ~ 32767 |
| int | 32 | 4 | 0 | -2147483648 ~ 2147483647 |
| long | 64 | 8 | 0L | -9223372036854775808 ~ 9223372036854775807 |
| char | 16 | 2 | 'u0000' | 0 ~ 65535 |
| float | 32 | 4 | 0f | 1.4E-45 ~ 3.4028235E38 |
| double | 64 | 8 | 0d | 4.9E-324 ~ 1.7976931348623157E308 |
| boolean | 1 |  | false | true、false |

## Primitive Type VS Packaging Type

- If the packaging variable is default `null`, and the primitive variable has a **default value** (not null).
- Packaging types can be used for `generic`, but primitive types cannot.
- Primitive types take up less **space**

## Packing **VS Unpacking**

- Packing: Pack the primitive types with their corresponding packaging types.
    
    `Integer A=Integer.valueOf(1)`
    
- Unpacking: Convert the packaging type to the primitive type.
    
    `int a = new Integer(1).intValue()`