---
title: 編譯器警告 (層級 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 7f1c71cb3cd6a99d4ed9960032813e7cebca7591
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685075"
---
# <a name="compiler-warning-level-1-c4364"></a>編譯器警告 (層級 1) C4364

\#在不使用 as_friend 屬性的情況下，于位置 (line_number) 中所見的元件 ' file '。未套用 as_friend

指定的中繼資料檔有重複的指示詞 `#using` ，但在 **`as_friend`** 第一次發生時不會使用限定詞; 編譯器會忽略第二個 **`as_friend`** 。

如需詳細資訊，請參閱 [ (c + +) 的 Friend 元件 ](../../dotnet/friend-assemblies-cpp.md)。

## <a name="examples"></a>範例

下列範例會建立元件。

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

下列範例會產生 C4364。

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
