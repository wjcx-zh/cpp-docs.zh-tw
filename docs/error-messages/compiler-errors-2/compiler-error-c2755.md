---
title: "編譯器錯誤 C2755 | Microsoft Docs"
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
  - "C2755"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2755"
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2755
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'param' : 部分特製化的非型別參數必須是簡單的識別項  
  
 非型別參數必須是簡單的識別項，也就是編譯器在編譯階段可以解析成單一識別項或常數值的項目。  
  
 下列範例會產生 C2755：  
  
```  
// C2755.cpp  
template<int I, int J>  
struct A {};  
  
template<int I>   
struct A<I,I*5> {};   // C2755  
// try the following line instead  
// struct A<I,5> {};  
```