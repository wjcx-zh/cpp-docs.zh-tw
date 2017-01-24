---
title: "編譯器錯誤 C3539 | Microsoft Docs"
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
  - "C3539"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3539"
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3539
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 樣板引數的型別不可以包含 'auto'  
  
 指定的樣板引數型別中不可以使用 `auto` 關鍵字。  
  
### 更正這個錯誤  
  
1.  不要指定含有 `auto` 關鍵字的樣板引數。  
  
## 範例  
 下列範例會產生 C3539 錯誤。  
  
```  
// C3539.cpp  
// Compile with /Zc:auto  
template<class T> class C{};  
int main()  
{  
   C<auto> c;   // C3539  
   return 0;  
}  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)