---
title: "編譯器警告 (層級 1) C4288 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4288"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4288"
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4288
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充 : 'var' : 在 for\-loop 範圍外使用 for\-loop 中所宣告的迴圈控制變數; 與外部範圍中的宣告衝突  
  
 利用 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 和 **\/Zc:forscope\-** 編譯時，在 [for](../../cpp/for-statement-cpp.md)\-loop 範圍之後會使用於 **for**\-loop 中宣告的變數。  C\+\+ 語言的 Microsoft 擴充功能允許此變數維持在範圍內，而 C4288 提醒您未使用變數的第一個宣告。  
  
 如需關於如何在 **for** 迴圈中用 \/Ze Microsoft 擴充功能的資訊，請參閱 [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)。  
  
 下列範例會產生 C4288：  
  
```  
// C4288.cpp  
// compile with: /W1 /c /Zc:forScope-  
int main() {  
   int i = 0;    // not used in this program  
   for (int i = 0 ; ; ) ;  
   i++;   // C4288 using for-loop declaration of i  
}  
```