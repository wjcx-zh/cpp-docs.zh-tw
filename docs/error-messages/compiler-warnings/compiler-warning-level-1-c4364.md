---
title: 編譯器警告 (層級 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 5423a5525f9bef4d949bfee2de058fe19d0ec181
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220037"
---
# <a name="compiler-warning-level-1-c4364"></a>編譯器警告 (層級 1) C4364

\#針對先前在位置（line_number）看不到 as_friend 屬性的元件 ' file ' 使用as_friend 不適用

`#using`指定的中繼資料檔案已重複指示詞，但 **`as_friend`** 第一次出現時未使用限定詞; 編譯器會忽略第二個 **`as_friend`** 。

如需詳細資訊，請參閱[Friend 元件（c + +）](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>範例

下列範例會建立元件。

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>範例

下列範例會產生 C4364。

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
