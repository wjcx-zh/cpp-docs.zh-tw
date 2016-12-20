---
title: "編譯器錯誤 C3247 | Microsoft Docs"
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
  - "C3247"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3247"
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3247
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class1' : Coclass 無法繼承自其他 Coclass 'class2'  
  
 標記為 [coclass](../../windows/coclass.md) 屬性的類別無法繼承自另一個標記為 `coclass` 屬性的類別。  
  
 下列範例會產生 C3247：  
  
```  
// C3247.cpp [module(name="MyLib")]; [coclass] class a { }; [coclass] class b : public a {   // C3247 }; int main() { }  
```