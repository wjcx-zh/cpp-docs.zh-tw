---
title: 編譯器警告 (層級 1) C4566
ms.date: 11/04/2016
f1_keywords:
- C4566
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
ms.openlocfilehash: 87d610980ffe9d9e5087ddaec0ecb91d813a4d60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162254"
---
# <a name="compiler-warning-level-1-c4566"></a>編譯器警告 (層級 1) C4566

以通用字元名稱 ' char ' 表示的字元，無法在目前的字碼頁中表示（頁面）

並非每個 Unicode 字元都可以在您目前的 ANSI 字碼頁中表示。

窄字串（一個位元組字元）會轉換成多位元組字元，而寬字元串（雙位元組字元）則不會。

下列範例會產生 C4566：

```cpp
// C4566.cpp
// compile with: /W1
int main() {
   char c1 = '\u03a0';   // C4566
   char c2 = '\u0642';   // C4566

   wchar_t c3 = L'\u03a0';   // OK
   wchar_t c4 = L'\u0642';   // OK
}
```
