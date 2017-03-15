---
title: "編譯器錯誤 C2569 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2569"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2569"
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2569
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'EnumOrUnion' : 列舉\/等位不可以用來當做基底類別  
  
 如果您必須從指定的等位或列舉上衍生一個型別，請將等位或列舉變更為類別或結構。  
  
 下列範例會產生 C2569：  
  
```  
// C2569.cpp  
// compile with: /c  
union ubase {};  
class cHasPubUBase : public ubase {};   // C2569  
// OK  
struct sbase {};  
class cHasPubUBase : public sbase {};  
```