---
title: "編譯器錯誤 C3896 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3896"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3896"
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3896
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : 不當的初始設定式: 這個常值資料成員只能用 'nullptr' 初始化  
  
 [literal](../../windows/literal-cpp-component-extensions.md) 資料成員未正確初始化。如需詳細資訊，請參閱[nullptr](../../windows/nullptr-cpp-component-extensions.md)。  
  
 下列範例會產生 C3896：  
  
```  
// C3896.cpp  
// compile with: /clr /c  
ref class R{};  
  
value class V {  
   literal R ^ r = "test";   // C3896  
   literal R ^ r2 = nullptr;   // OK  
};  
```