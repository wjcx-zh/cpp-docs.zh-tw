---
title: "編譯器警告 (層級 1) C4142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4142"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4142"
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4142
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

良性的型別重複定義  
  
 某一個型別被以一種對已產生程式碼無影響的方式重新定義。  
  
 若要透過檢查下列可能原因，以進行修正：  
  
-   某衍生類別的成員函式的傳回型別 \(Return Type\) 不同於對應基底類別的成員函式的傳回型別。  
  
-   以 `typedef` 命令定義的型別使用了不同語法進行重新定義。  
  
 下列範例會產生 C4142：  
  
```  
// C4142.c  
// compile with: /W1  
float X2;  
X2 = 2.0 + 1.0;   // C4142  
  
int main() {  
   float X2;  
   X2 = 2.0 + 1.0;   // OK  
}  
```