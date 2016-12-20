---
title: "編譯器警告 (層級 2) C4094 | Microsoft Docs"
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
  - "C4094"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4094"
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2) C4094
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未標記的 'token' 宣告沒有符號  
  
 編譯器偵測到使用未標記結構、等位或類別的空白宣告。  忽略此宣告。  
  
## 範例  
  
```  
// C4094.cpp  
// compile with: /W2  
struct  
{  
};   // C4094  
  
int main()  
{  
}  
```  
  
 在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 之下，此情形會產生錯誤。