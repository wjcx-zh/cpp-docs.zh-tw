---
title: alignof 運算子
ms.date: 12/17/2018
f1_keywords:
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: 6a2046774674858211ae89abb9b4cfc7b09c0a6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227630"
---
# <a name="alignof-operator"></a>alignof 運算子

**`alignof`** 運算子會以位元組作為類型的值，傳回指定之類型的對齊方式 **`size_t`** 。

## <a name="syntax"></a>語法

```cpp
alignof( type )
```

## <a name="remarks"></a>備註

例如：

| 運算是 | 值 |
|--|--|
| **`alignof( char )`** | 1 |
| **`alignof( short )`** | 2 |
| **`alignof( int )`** | 4 |
| **`alignof( long long )`** | 8 |
| **`alignof( float )`** | 4 |
| **`alignof( double )`** | 8 |

**`alignof`** 值與 **`sizeof`** 適用于基本類型的值相同。 不過，請考慮這個範例：

```cpp
typedef struct { int a; double b; } S;
// alignof(S) == 8
```

在此情況下，此 **`alignof`** 值是結構中最大元素的對齊需求。

同樣地，針對

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`alignof(S)` 等於 `32`。

一種用途 **`alignof`** 是做為您自己的記憶體配置常式之一的參數。 例如，假設有下列定義的結構 `S`，您可以呼叫名為 `aligned_malloc` 的記憶體配置常式，至特定對齊界限上配置記憶體。

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), alignof(S));
```

如需修改對齊的詳細資訊，請參閱：

- [pack](../preprocessor/pack.md)

- [對齊](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp （結構成員對齊）](../build/reference/zp-struct-member-alignment.md)

- [結構對齊範例](../build/x64-software-conventions.md#examples-of-structure-alignment)（x64 專用）

如需適用於 x86 和 x64 之程式碼中的對齊差異的詳細資訊，請參閱：

- [與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

### <a name="microsoft-specific"></a>Microsoft 專有

**`alignof`** 和 **`__alignof`** 是 Microsoft 編譯器中的同義字。 Microsoft 專屬的操作員在成為 c + + 11 標準的一部分之前， **`__alignof`** 提供了這項功能。 若要獲得最大的可攜性，您應該使用 **`alignof`** 運算子，而不是 Microsoft 特有的 **`__alignof`** 運算子。

為了與舊版相容， **`_alignof`** **`__alignof`** 除非指定了編譯器選項 [停用[ `/Za` \( 語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能]，否則會是同義字。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
