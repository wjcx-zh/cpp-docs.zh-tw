---
title: "編譯器錯誤 C3532 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3532"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3532"
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3532
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 'auto' 的使用方式不正確  
  
 指定的型別無法以 `auto` 關鍵字宣告。  例如，您無法使用 `auto` 關鍵字來宣告陣列或方法傳回型別。  
  
### 更正這個錯誤  
  
1.  確定初始化運算式產生有效的型別。  
  
2.  確定您不會宣告陣列或方法傳回型別。  
  
## 範例  
 下列範例會產生 C3532 錯誤，因為 `auto` 關鍵字無法宣告方法傳回型別。  
  
```  
// C3532a.cpp  
// Compile with /Zc:auto  
auto f(){}   // C3532  
```  
  
## 範例  
 下列範例會產生 C3532 錯誤，因為 `auto` 關鍵字無法宣告陣列。  
  
```  
// C3532b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int x[5];  
   auto a[5];            // C3532  
   auto b[1][2];         // C3532  
   auto y[5] = x;        // C3532  
   auto z[] = {1, 2, 3}; // C3532  
   auto w[] = x;         // C3532  
   return 0;  
}  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)