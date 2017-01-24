---
title: "嚴重錯誤 C1094 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1094"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1094"
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1094
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\-Zmval1' : 命令列選項與用來建置先行編譯標頭 \('\-Zmval2'\) 的值不一致  
  
 傳遞給 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 的值必須與傳遞給 [\/Yu](../../build/reference/yu-use-precompiled-header-file.md) 值相同 \(**\/Zm** 值必須在使用或建立相同先行編譯標頭檔的所有編譯中都相同\)。  
  
 下列範例會產生 C1094：  
  
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