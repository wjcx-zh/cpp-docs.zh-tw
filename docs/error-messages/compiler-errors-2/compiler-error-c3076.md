---
title: "編譯器錯誤 C3076 | Microsoft Docs"
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
  - "C3076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3076"
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'instance' : 不可將參考型別的執行個體 'type' 嵌入原生型別中  
  
 原生型別不能包含 CLR 型別的執行個體。  
  
 如需詳細資訊，請參閱[參考類型的 C\+\+ 堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## 範例  
 下列範例會產生 C3076。  
  
```  
// C3076.cpp  
// compile with: /clr /c  
ref struct U {};  
  
struct V {  
   U y;   // C3076  
};  
  
ref struct W {  
   U y;   // OK  
};  
```