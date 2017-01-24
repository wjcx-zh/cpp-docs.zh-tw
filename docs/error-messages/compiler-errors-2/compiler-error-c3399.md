---
title: "編譯器錯誤 C3399 | Microsoft Docs"
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
  - "C3399"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3399"
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3399
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 建立泛型參數的執行個體時無法提供引數  
  
 當您指定 `gcnew()` 條件約束時，即指定了無參數建構函式的條件約束類型。 因此，它是嘗試具現化該類型並傳遞參數的錯誤。  
  
 如需詳細資訊，請參閱 [Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C3399。  
  
```  
// C3399.cpp // compile with: /clr /c generic <class T> where T : gcnew() void f() { T t = gcnew T(1);   // C3399 T t2 = gcnew T();   // OK }  
```