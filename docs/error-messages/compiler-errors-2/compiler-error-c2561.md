---
title: "編譯器錯誤 C2561 | Microsoft Docs"
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
  - "C2561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2561"
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 函式必須傳回值  
  
 函式宣告為傳回值，但函式定義未包含 `return` 陳述式。  
  
 這項錯誤可能是因不正確函式原型而造成：  
  
1.  如果函式不傳回值，請使用 [void](../../cpp/void-cpp.md) 傳回型別來宣告函式。  
  
2.  檢查函式的所有可能分支，其傳回宣告於原型中的型別的數值。  
  
3.  包含將傳回值儲存在 `AX` 登錄之內嵌組件 \(Inline Assembly\) 常式的 C\+\+ 函式，可能需要一個 return 陳述式。  將 `AX` 內的值複製至暫存變數上，並從函式中將該變數傳回。  
  
 下列範例會產生 C2561：  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```