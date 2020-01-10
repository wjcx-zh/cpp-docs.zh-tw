---
title: 編譯器錯誤 C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: 87b5afe2133bb737a8f9c855b0652c2f50ca27ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740516"
---
# <a name="compiler-error-c2601"></a>編譯器錯誤 C2601

' function '：區域函式定義不合法

程式碼嘗試在函式內定義函式。

或者，在 C2601 錯誤的位置之前，您的原始程式碼中可能會有額外的大括弧。

下列範例會產生 C2601：

```cpp
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```
