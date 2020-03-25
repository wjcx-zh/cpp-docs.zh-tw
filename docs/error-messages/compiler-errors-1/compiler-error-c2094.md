---
title: 編譯器錯誤 C2094
ms.date: 11/04/2016
f1_keywords:
- C2094
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
ms.openlocfilehash: 022fca01706fefca2a14ea952586ec91b0c5b240
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207673"
---
# <a name="compiler-error-c2094"></a>編譯器錯誤 C2094

標籤 'identifier' 未定義

函式中沒有 [goto](../../cpp/goto-statement-cpp.md) 陳述式所使用的標籤。

## <a name="example"></a>範例

下列範例會產生 C2094：

```cpp
// C2094.c
int main() {
   goto test;
}   // C2094
```

可能的解決方案：

```cpp
// C2094b.c
int main() {
   goto test;
   test:
   {
   }
}
```
