---
title: 編譯器警告 (層級 4) C4242
ms.date: 11/04/2016
f1_keywords:
- C4242
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
ms.openlocfilehash: ed145444d6eec583c448a3a49167ca1f82644f0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510004"
---
# <a name="compiler-warning-level-4-c4242"></a>編譯器警告 (層級 4) C4242

' identifier ': 從 ' type1 ' 轉換為 ' type2 ', 資料可能遺失

類型不同。 類型轉換可能會導致資料遺失。 編譯器會進行類型轉換。

此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。

如需 C4242 的詳細資訊, 請參閱[常見的編譯器錯誤](/windows/win32/WinProg64/common-compiler-errors)。

下列範例會產生 C4242:

```
// C4242.cpp
// compile with: /W4
#pragma warning(4:4242)
int func() {
   return 0;
}

int main() {
   char a;
   a = func();   // C4242, return type and variable type do not match
}
```