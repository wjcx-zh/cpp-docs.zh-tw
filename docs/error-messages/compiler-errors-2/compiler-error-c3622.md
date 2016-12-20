---
title: "編譯器錯誤 C3622 | Microsoft Docs"
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
  - "C3622"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3622"
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3622
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': 宣告為 'keyword' 的類別無法執行個體化  
  
 嘗試對標示為 [abstract](../../windows/abstract-cpp-component-extensions.md) \(或 [\_\_abstract](../../misc/abstract.md)\) 的類別進行具現化。  標記為抽象的類別可以是基底類別，但不可以被具現化。  
  
## 範例  
 下列範例會產生 C3622。  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  
  
## 範例  
 下列範例會產生 C3622。  
  
```  
// C3622_b.cpp  
// compile with: /clr:oldSyntax  
__abstract class a {  
};  
int main() {  
   a aa;   // C3622  
}  
```