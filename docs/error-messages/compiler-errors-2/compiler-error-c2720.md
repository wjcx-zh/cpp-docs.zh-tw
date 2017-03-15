---
title: "編譯器錯誤 C2720 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2720"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2720"
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2720
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 成員上的 'specifier' 儲存類別規範不合法  
  
 儲存類別不能在宣告之外的類別成員上使用。  若要修正這個錯誤，請從類別宣告之外的成員定義中移除不需要的[儲存類別規範](http://msdn.microsoft.com/zh-tw/10b3d22d-cb40-450b-994b-08cf9a211b6c)。  
  
 下列範例會產生 C2720，並示範如何修正此問題：  
  
```  
// C2720.cpp  
struct S {  
   static int i;  
};  
static S::i;   // C2720 - remove the unneeded 'static' to fix it  
  
```