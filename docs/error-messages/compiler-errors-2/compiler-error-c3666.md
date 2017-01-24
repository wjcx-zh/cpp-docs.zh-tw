---
title: "編譯器錯誤 C3666 | Microsoft Docs"
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
  - "C3666"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3666"
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3666
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constructor' : 建構函式上不允許有覆寫規範 'keyword'  
  
 在建構函上使用了覆寫規範，這是不允許的。  如需詳細資訊，請參閱[覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C3666。  
  
```  
// C3666.cpp  
// compile with: /clr /c  
ref struct R {  
   R() new {}   // C3666  
   R(int i) {}   // OK  
};  
```