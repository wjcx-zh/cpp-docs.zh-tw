---
title: 編譯器警告 (層級 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: db2774b6a73a989b4e9250719f99122826b486fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207104"
---
# <a name="compiler-warning-level-1-c4364"></a>編譯器警告 (層級 1) C4364

\#使用組件 'file' 先前看過在 location(line_number) 沒有 as_friend 屬性，因此未套用 as_friend

A`#using`指示詞重複指定的中繼資料檔案，但`as_friend`中的第一個未使用限定詞; 編譯器會忽略第二個`as_friend`。

如需詳細資訊，請參閱 < [Friend 組件 (C++)](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>範例

下列範例會建立元件。

```
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>範例

下列範例會產生 C4364。

```
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```