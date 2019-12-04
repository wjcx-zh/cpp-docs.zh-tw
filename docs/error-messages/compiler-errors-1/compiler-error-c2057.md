---
title: 編譯器錯誤 C2057
ms.date: 11/04/2016
f1_keywords:
- C2057
helpviewer_keywords:
- C2057
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
ms.openlocfilehash: 37dbc2f6ae0614215f0a3de20baa601b48db9450
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742440"
---
# <a name="compiler-error-c2057"></a>編譯器錯誤 C2057

必須是常數運算式

此內容需要常數運算式，在編譯階段已知此運算式的值。

編譯器必須知道編譯階段的類型大小，才能為該類型的執行個體配置空間。

## <a name="example"></a>範例

下列範例會產生 C2057，並顯示如何修正此問題：

```cpp
// C2057.cpp
int i;
int b[i];   // C2057 - value of i is unknown at compile time
int main() {
   const int i = 8;
   int b[i]; // OK - value of i is fixed and known to compiler
}
```

## <a name="example"></a>範例

C 有更嚴格的常數運算式規則。  下列範例會產生 C2057，並顯示如何修正此問題：

```
// C2057b.c
#define ArraySize1 10
int main() {
   const int ArraySize2 = 10;
   int h[ArraySize2];   // C2057 - C does not allow variables here
   int h[ArraySize1];   // OK - uses preprocessor constant
}
```
