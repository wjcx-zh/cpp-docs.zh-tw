---
title: 編譯器警告 （層級 4） C4295 |Microsoft 文件
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
ms.openlocfilehash: 815a669bc359121b13b1d636009cad81dc332304
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296298"
---
# <a name="compiler-warning-level-4-c4295"></a>編譯器警告 (層級 4) C4295
  
> '*陣列*': 陣列是太小無法包含結束的 null 字元  
  
初始化陣列，但陣列中的最後一個字元不是 null。存取陣列做為字串可能會產生非預期的結果。  
  
## <a name="example"></a>範例  
  
下列範例會產生 C4295。 若要修正此問題，您可以宣告陣列大小更大，以保存結束的 null 從初始設定式的字串，或您可以使用陣列初始設定式清單進行這是陣列的意圖清除`char`，不是以 null 結束的字串。  
  
```C  
// C4295.c
// compile with: /W4


int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
