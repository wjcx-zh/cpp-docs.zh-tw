---
title: __alignof 運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
dev_langs:
- C++
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffea0fdf40f7ef794563849f97b0b68631b9734e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099776"
---
# <a name="alignof-operator"></a>__alignof 運算子

C++11 引進**alignof**運算子，傳回的對齊方式，以位元組為單位指定的型別。 若要獲得最高可攜性，您應該使用 alignof 運算子，而不是 Microsoft-specific __alignof 運算子。

**Microsoft 專屬**

傳回值的型別`size_t`也就是類型的對齊需求。

## <a name="syntax"></a>語法

```cpp
  __alignof( type )
```

## <a name="remarks"></a>備註

例如: 

|運算式|值|
|----------------|-----------|
|**__alignof( char )**|1|
|**__alignof （短）**|2|
|**__alignof (int)**|4|
|**__alignof( \__int64 )**|8|
|**__alignof （浮點數）**|4|
|**__alignof( double )**|8|
|**__alignof( char\* )**|4|

**__Alignof**的值相同`sizeof`適用於基本類型。 不過，請考慮這個範例：

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

在此情況下， **__alignof**值是最大的項目在結構中的對齊需求。

同樣地，針對

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` 等於 `32`。

用法之一 **__alignof**會做為其中一個您自己的記憶體配置常式的參數。 例如，假設有下列定義的結構 `S`，您可以呼叫名為 `aligned_malloc` 的記憶體配置常式，至特定對齊界限上配置記憶體。

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

如需修改對齊的詳細資訊，請參閱：

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (結構成員對齊)](../build/reference/zp-struct-member-alignment.md)

- [結構對齊範例](../build/examples-of-structure-alignment.md)(x64 專用)

如需適用於 x86 和 x64 之程式碼中的對齊差異的詳細資訊，請參閱：

- [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)