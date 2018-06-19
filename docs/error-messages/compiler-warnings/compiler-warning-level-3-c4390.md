---
title: 編譯器警告 （層級 3） C4390 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4390
dev_langs:
- C++
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d052a1fa6124aa1518cddec00566e14668fe111d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290084"
---
# <a name="compiler-warning-level-3-c4390"></a>編譯器警告 (層級 3) C4390
';': 控制找到空白陳述式。這是對應方式？  
  
 找不到不包含任何指令控制陳述式後面的分號。  
  
 如果您收到 C4390 由於巨集時，您應該使用[警告](../../preprocessor/warning.md)pragma 來停用 C4390 包含巨集的模組。  
  
 下列範例會產生 C4390:  
  
```  
// C4390.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
   if (i);   // C4390  
      i++;  
}  
```