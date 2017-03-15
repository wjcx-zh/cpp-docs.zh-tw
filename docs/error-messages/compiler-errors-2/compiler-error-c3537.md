---
title: "編譯器錯誤 C3537 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3537"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3537"
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3537
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 無法轉型為包含 'auto' 的型別  
  
 您無法將變數轉型為指定的型別，因為這個型別包含 `auto` 關鍵字，而且預設的 [\/Zc:auto](../../build/reference/zc-auto-deduce-variable-type.md) 編譯器選項還在作用中。  
  
## 範例  
 下列程式碼會產生 C3537 錯誤，因為變數要轉型為包含 `auto` 關鍵字的型別。  
  
```  
// C3537.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int value = 123;  
   auto(value);                        // C3537  
   (auto)value;                        // C3537  
   auto x1 = auto(value);              // C3537  
   auto x2 = (auto)value;              // C3537  
   auto x3 = static_cast<auto>(value); // C3537  
   return 0;  
}  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)