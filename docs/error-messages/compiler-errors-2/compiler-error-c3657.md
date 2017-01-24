---
title: "編譯器錯誤 C3657 | Microsoft Docs"
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
  - "C3657"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3657"
ms.assetid: 89a28a18-4c17-43a1-bda6-deb52c32d203
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3657
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

解構函式不可明確覆寫或被明確覆寫  
  
 解構函式或完成項無法加以明確覆寫。  如需詳細資訊，請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3657。  
  
```  
// C3657.cpp  
// compile with: /clr  
public ref struct I {  
   virtual ~I() { }  
   virtual void a();  
};  
  
public ref struct D : I {  
   virtual ~D() = I::~I {}   // C3657  
   virtual void a() = I::a {}   // OK  
};  
```