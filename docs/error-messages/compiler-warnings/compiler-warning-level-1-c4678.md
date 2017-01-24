---
title: "編譯器警告 (層級 1) C4678 | Microsoft Docs"
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
  - "C4678"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4678"
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4678
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

基底類別 'base\_type' 比 'derived\_type' 更難以存取  
  
 公用類型衍生自私用類型。 如果在參考的組件中具現化公用類型，則無法存取私用基底類型成員。  
  
 僅可使用 **\/clr:oldSyntax** 連接 C4678。 如果使用 **\/clr** 以擁有較少存取其衍生類別的基底類別，則會發生錯誤。  
  
 下列範例會產生 C4678：  
  
```  
// C4678.cpp // compile with: /clr:oldSyntax /LD /W1 #using <mscorlib.dll> private __gc struct privateG { // try the following line instead // public __gc struct privateG { public: int i; }; public __gc struct V: public privateG {   // C4678 public: int j; };  
```