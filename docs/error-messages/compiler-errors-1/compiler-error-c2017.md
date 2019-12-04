---
title: 編譯器錯誤 C2017
ms.date: 11/04/2016
f1_keywords:
- C2017
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
ms.openlocfilehash: 3911ef9af2eb0fab7d0f9296ddce8a0f9b32ae0d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751049"
---
# <a name="compiler-error-c2017"></a>編譯器錯誤 C2017

不合法的轉義順序

Escape 序列（例如 \t）會出現在字元或字串常數的外部。

下列範例會產生 C2017：

```cpp
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

當字串化運算子與包含逸出序列的字串搭配使用時，可能會發生 C2017。

下列範例會產生 C2017：

```cpp
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```
