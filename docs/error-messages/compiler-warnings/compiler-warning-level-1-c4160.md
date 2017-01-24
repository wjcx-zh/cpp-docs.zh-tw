---
title: "編譯器警告 (層級 1) C4160 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4160"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4160"
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4160
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\#pragma**   
 ***pragma* \(pop,...\): 未發現之前推入的識別項 '**   
 ***識別項* '**  
  
 原始程式碼中的 pragma 陳述式嘗試快顯尚未推入的識別項。 若要避免這個警告，請確定已正確推入所快顯的識別項。  
  
 下列範例會產生 C4160：  
  
```  
// C4160.cpp // compile with: /W1 #pragma pack(push) #pragma pack(pop, id)   // C4160 // use identifier when pushing to resolve the warning // #pragma pack(push, id) int main() { }  
```