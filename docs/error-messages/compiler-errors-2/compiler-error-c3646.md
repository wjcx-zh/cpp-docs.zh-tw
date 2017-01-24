---
title: "編譯器錯誤 C3646 | Microsoft Docs"
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
  - "C3646"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3646"
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3646
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'specifier' : 未知的覆寫規範  
  
 編譯器在預期找到覆寫規範的位置上發現語彙基元，但編譯器無法辨認該語彙基元。  
  
 如需詳細資訊，請參閱[覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
 下列範例會產生 C3646：  
  
```  
// C3646.cpp  
// compile with: /clr /c  
ref class C {  
   void f() unknown;   // C3646  
   // try the following line instead  
   // virtual void f() abstract;  
};  
```