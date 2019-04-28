---
title: 編譯器錯誤 C2117
ms.date: 11/04/2016
f1_keywords:
- C2117
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
ms.openlocfilehash: 2f6a1e26972f093e50c5e655935f750195ab7d3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338567"
---
# <a name="compiler-error-c2117"></a>編譯器錯誤 C2117

'identifier': 陣列界限溢位

陣列中有太多的初始設定式：

- 陣列項目和初始設定式不相符的大小和數量。

- 給以 null 終止字串中沒有空間。

下列範例會產生 C2117:

```
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```