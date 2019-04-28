---
title: 編譯器警告 (層級 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 4c48ad9349361324c18ec790c51d1095cce104e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280434"
---
# <a name="compiler-warning-level-1-c4739"></a>編譯器警告 (層級 1) C4739

變數 'var' 的參考超過了它的儲存空間

已指派值給變數，但該值大於變數的大小。 記憶體將寫入到變數的記憶體位置以外，因此可能會遺失資料。

若要解決這個警告，請只將值指派給其大小可容納該值的變數。

下列範例會產生 C4739：

```
// C4739.cpp
// compile with: /RTCs /Zi /W1 /c
char *pc;
int main() {
   char c;
   *(int *)&c = 1;   // C4739

   // OK
   *(char *)&c = 1;
}
```