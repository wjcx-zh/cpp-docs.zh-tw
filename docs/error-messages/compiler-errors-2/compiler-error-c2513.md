---
title: "編譯器錯誤 C2513 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2513"
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 在 '\=' 之前沒有宣告變數  
  
 出現在宣告內的型別規範沒有變數識別項。  
  
 下列範例會產生 C2513：  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 對 Visual Studio .NET 2003 的編譯器完成符合標準處理後也會出現這個錯誤：已不再允許執行 typedef 的初始設定。  標準並不允許 typedef 的初始設定，因此現在會產生編譯器錯誤。  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 另外一個方法是刪除 `typedef`，用彙總初始設定式清單定義變數，但並不建議您採取這種做法，因為它會用與型別相同的名稱建立變數，並隱藏型別名稱。