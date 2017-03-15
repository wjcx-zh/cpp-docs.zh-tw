---
title: "編譯器警告 (層級 1) C4490 | Microsoft Docs"
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
  - "C4490"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4490"
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4490
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'override' : 覆寫規範使用不當，'function' 與基底 ref 類別方法不符  
  
 覆寫規範使用方式不正確。  例如，您不要覆寫介面函式，而應該要加以實作。  
  
 如需詳細資訊，請參閱[覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C4490。  
  
```  
// C4490.cpp  
// compile with: /clr /c /W1  
  
interface struct IFace {  
   void Test();  
};  
  
ref struct Class1 : public IFace {  
   virtual void Test() override {}   // C4490  
   // try the following line instead  
   // virtual void Test() {}  
};  
```