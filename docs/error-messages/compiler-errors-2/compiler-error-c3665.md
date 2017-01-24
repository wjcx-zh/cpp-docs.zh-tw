---
title: "編譯器錯誤 C3665 | Microsoft Docs"
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
  - "C3665"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3665"
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3665
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'destructor' : 解構函式\/完成項上不允許有覆寫規範 'keyword'  
  
 使用了解構函式或完成項上不允許的關鍵字。  
  
 例如，不能在解構函式或完成項上要求新位置。如需詳細資訊，請參閱 [明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md) 和 [解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
 下列範例會產生 C3665：  
  
```  
// C3665.cpp  
// compile with: /clr  
public ref struct R {  
   virtual ~R() { }  
   virtual void a() { }  
};  
  
public ref struct S : R {  
   virtual ~S() new {}   // C3665  
   virtual void a() new {}   // OK  
};  
```