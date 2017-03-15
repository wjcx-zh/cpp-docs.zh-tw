---
title: "編譯器警告 (層級 1) C4269 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4269"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4269"
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4269
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 'const' 將以編譯器產生的預設建構函式自動地初始化資料，這會產生無法預期的結果  
  
 非 Trivial 類別的 **const** 自動執行個體已由編譯器產生的預設建構函式進行初始化。  
  
## 範例  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 由於類別的此執行個體是在堆疊上所產生，因此 `m_data` 的初始值可以是任意值，  而且，由於它是 **const** 執行個體，所以無法變更 `m_data` 的值。