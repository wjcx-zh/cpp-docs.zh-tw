---
title: "編譯器錯誤 C3189 | Microsoft Docs"
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
  - "C3189"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3189"
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3189
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'typeid\<type abstract declarator\>': 已不再支援這種語法，請用 ::typeid 代替  
  
 使用了過時形式的 [typeid](../../windows/typeid-cpp-component-extensions.md)，請使用新形式。  
  
 下列範例會產生 C3189：  
  
```  
// C3189.cpp  
// compile with: /clr  
int main() {  
   System::Type^ t  = typeid<System::Object>;   // C3189  
   System::Type^ t2  = System::Object::typeid;   // OK  
}  
```