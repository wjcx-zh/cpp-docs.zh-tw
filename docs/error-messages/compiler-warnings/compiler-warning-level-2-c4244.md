---
title: "編譯器警告 (層級 2) C4244 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4244"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4244"
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 2) C4244
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'argument' : 將 'type1' 轉換為 'type2'，資料可能遺失  
  
 浮點型別已轉換成整數型別。可能會發生資料遺失的情形。  
  
 如果接到 C4244，應該要變更程式或使用相容的型別，或是加入一些邏輯至您的程式碼，以確保可能值的範圍一定會與要使用的型別相容。  
  
 C4244 也可能會在層級 3 和 4 上引發；如需詳細資訊，請參閱[編譯器警告 \(層級s 3 and 4\) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md)。  
  
## 範例  
 下列範例會產生 C4244：  
  
```  
// C4244_level2.cpp  
// compile with: /W2  
  
int f(int x){ return 0; }  
int main() {  
   double x = 10.1;  
   int i = 10;  
   return (f(x));   // C4244  
   // try the following line instead  
   // return (f(i));  
}  
```