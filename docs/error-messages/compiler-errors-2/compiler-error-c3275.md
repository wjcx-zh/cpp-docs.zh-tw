---
title: "編譯器錯誤 C3275 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3275"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3275"
ms.assetid: 5752680f-7d3e-4c42-ba9c-845e09d32e7a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3275
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'enum member': 必須提供限定詞才能使用這個符號  
  
 使用 Managed 程式碼時，以及兩個或更多列舉包含具有相同名稱的識別碼時，您必須明確限定識別項參考。  
  
 僅可使用 **\/clr:oldSyntax** 連接 C3275。  
  
 下列範例示範兩種產生 C3275 的情況：  
  
```  
// C3275.cpp // compile with: /clr:oldSyntax #using <mscorlib.dll> __value enum Jewelry { necklace, brooch, pin, ring, earring }; __value enum Phone { busy, ring, disconnect }; int main() { Phone p = ring;   // C3275 // try the following line instead // Phone p = Phone::ring; Console::Out->Write(ring);   // C3275 // try the following line instead // Console::Out->Write(Phone::ring); }  
```