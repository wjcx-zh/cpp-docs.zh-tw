---
title: 嚴重錯誤 C1094 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1094
dev_langs:
- C++
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e227cbfaf46eb7616ae63eda02816e7d274ab85b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227513"
---
# <a name="fatal-error-c1094"></a>嚴重錯誤 C1094
'-Zmval1': 命令列選項不一致，用來建置先行編譯標頭的值 ('-Zmval2')  
  
 值，傳遞至[/Yc](../../build/reference/yc-create-precompiled-header-file.md)必須是相同的值傳遞至[/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm**值必須在所有編譯中使用或建立相同的先行編譯的相同標頭檔）。  
  
 下列範例會產生 C1094:  
  
```  
// C1094.h  
int func1();  
```  
  
 然後，  
  
```  
// C1094.cpp  
// compile with: /Yc"C1094.h" /Zm200  
int u;  
int main() {  
   int sd = 32;  
}  
#include "C1094.h"  
```  
  
 然後，  
  
```  
// C1094b.cpp  
// compile with: /Yu"C1094.h" /Zm300 /c  
#include "C1094.h"   // C1094 compile with /Zm200  
void Test() {}  
```