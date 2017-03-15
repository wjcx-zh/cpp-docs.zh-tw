---
title: "嚴重錯誤 C1197 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1197"
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 嚴重錯誤 C1197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法參考 'mscorlib.dll\_1'，因為程式已經參考了 'mscorlib.dll\_2'  
  
 該編譯器符合某一個版本的 Common Language Runtime，但是卻嘗試從舊版參考此版本 Common Language Runtime 的檔案。  
  
 若要修正這項錯誤，只能夠參考您用來進行編譯之 Visual C\+\+ 版本所隨附的 Common Language Runtime 版本的檔案。  
  
## 範例  
 下列範例會產生 C1197：  
  
```  
// C1197.cpp  
// compile with: /clr /c  
// processor: x86  
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197  
// try the following line instead  
// #using "mscorlib.dll"  
```