---
title: 編譯器警告 (層級 4) C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: d960e5a5e2d7ad2d2b650095c42e9afea7bfe7fb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219868"
---
# <a name="compiler-warning-level-4-c4295"></a>編譯器警告 (層級 4) C4295

> '*array*'：陣列太小，無法包含終止的 null 字元

已初始化陣列，但陣列中的最後一個字元不是 null;以字串形式存取陣列可能會產生非預期的結果。

## <a name="example"></a>範例

下列範例會產生 C4295。 若要修正這個問題，您可以將陣列大小宣告為較大，以保存初始化運算式字串的終止 null，或者您可以使用陣列初始化運算式清單，讓意圖清楚指出這是的陣列 **`char`** ，而不是以 null 結束的字串。

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
