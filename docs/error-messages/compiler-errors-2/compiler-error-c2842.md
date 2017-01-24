---
title: "編譯器錯誤 C2842 | Microsoft Docs"
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
  - "C2842"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2842"
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2842
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class'：Managed 或 WinRT 類型不可以定義其自身的 'operator new' 或 'operator delete'  
  
 您可以定義自己的 [operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md) 或 [operator delete](../Topic/operator%20delete%20\(%3Cnew%3E\).md) 以管理原生堆積上的記憶體配置。  不過，參考類別不能定義這些運算子，因為它們只會配置於 Managed 堆積上。  
  
 如需詳細資訊，請參閱[使用者定義的運算子](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C2842。  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  
  
## 範例  
 下列範例會產生 C2842。  
  
```  
// C2842_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```