---
title: "編譯器錯誤 C2638 | Microsoft Docs"
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
  - "C2638"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2638"
ms.assetid: 9d4275e8-406d-455e-afee-3a37799230e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2638
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 成員指標上的 \_\_based 修飾詞不合法  
  
 `__based` 修飾詞 \(Modifier\) 不能用於成員指標。  
  
 下列範例會產生 C2638：  
  
```  
// C2638.cpp  
void *a;  
  
class C {  
public:  
   int i;  
   int j;  
   int func();  
};  
int __based (a) C::* cpi = &C::i;  // C2638  
int (__based (a) C::* cpf)() = &C::func; // c2638  
```