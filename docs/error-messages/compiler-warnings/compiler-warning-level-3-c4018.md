---
title: 編譯器警告 （層級 3） C4018 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4018
dev_langs:
- C++
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5eb784c8a368b5f5836deaff17d07542519ba980
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290331"
---
# <a name="compiler-warning-level-3-c4018"></a>編譯器警告 （層級 3） C4018
'expression': signed/unsigned 不相符  
  
 比較的帶正負號和不帶正負號的數字所需的編譯器將帶正負號的值轉換成不帶正負號。  
  
 如果您轉換成下列其中一種測試帶正負號和不帶正負號類型時，可能會修正這個警告。  
  
 下列範例會產生 C4018:  
  
```  
// C4018.cpp  
// compile with: /W3  
int main() {  
   unsigned int uc = 0;  
   int c = 0;  
   unsigned int c2 = 0;  
  
   if (uc < c) uc = 0;   // C4018  
  
   // OK  
   if (uc == c2) uc = 0;  
}  
```