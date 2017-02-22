---
title: "運算錯誤 M6111 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6111"
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算錯誤 M6111
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆疊反向溢位  
  
 浮點作業造成 8087\/287\/387 副處理器或模擬器的堆疊反向溢位 \(Stack Underflow\)。  
  
 此錯誤通常是因為呼叫無法傳回值的 `long double` 函式所造成。  例如，編譯並執行下列程式碼會產生此錯誤：  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 程式以結束代碼 139 結束。