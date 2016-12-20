---
title: "編譯器錯誤 C3530 | Microsoft Docs"
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
  - "C3530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3530"
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'auto' 無法與任何其他型別規範合併使用  
  
 有某個型別規範與 `auto` 關鍵字搭配使用。  
  
### 更正這個錯誤  
  
1.  不要在使用 `auto` 關鍵字的變數宣告中使用型別規範。  
  
## 範例  
 下列範例會產生 C3530 錯誤，因為使用了 `auto` 關鍵字及 `int` 型別來宣告變數 `x`，而且是使用 **\/Zc:auto** 來編譯。  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)