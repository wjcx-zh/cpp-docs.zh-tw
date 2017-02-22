---
title: "編譯器警告 (層級 1) C4042 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4042"
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4042
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 有錯誤的儲存類別  
  
 在此內容中，指定的儲存類別 \(Storage Class\) 無法與此識別項一起使用。  編譯器改用預設的儲存類別：  
  
-   `extern`─如果 *identifier* 是一個函式。  
  
-   **auto**─如果 *identifier* 是一個型式參數或區域變數。  
  
-   沒有儲存類別─如果 *identifier* 是一個全域變數。  
  
 這項警告可能會因為在參數宣告中指定 **register** 以外的儲存類別而產生。  
  
 下列範例會產生 C4042  
  
```  
// C4042.cpp  
// compile with: /W1 /LD  
int func2( __declspec( thread ) int tls_i )    // C4042  
// try the following line instead  
// int func2( int tls_i )  
{  
   return tls_i;  
}  
```