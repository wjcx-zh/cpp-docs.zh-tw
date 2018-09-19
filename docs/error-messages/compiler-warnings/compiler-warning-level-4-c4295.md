---
title: 編譯器警告 （層級 4） C4295 |Microsoft Docs
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4295
dev_langs:
- C++
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36c6ac4d8c3e2899b744d1c456ae3079ec031698
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053572"
---
# <a name="compiler-warning-level-4-c4295"></a>編譯器警告 (層級 4) C4295

> '*陣列*': 陣列太小而無法包含結束的 null 字元

初始化陣列，但在陣列中的最後一個字元不是 null;存取做為字串陣列，可能會產生非預期的結果。

## <a name="example"></a>範例

下列範例會產生 C4295。 若要修正此問題，您可以宣告陣列的大小變大，來保留終止 null 初始設定式的字串，或您可以使用陣列初始設定式清單進行意圖純文字，這是陣列`char`，不是 null 結束的字串。

```C
// C4295.c
// compile with: /W4


int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
