---
title: "編譯器錯誤 C2450 | Microsoft Docs"
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
  - "C2450"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2450"
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2450
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

型別 'type' 的 switch 運算式不合法  
  
 `switch` 運算式評估為無效型別。  它必須評估為一個整數 \(Integer\) 型別或一個能夠不模稜兩可地 \(Unambiguous\) 轉換成整數型別的類別型別。  若它評估為使用者定義的型別，您就必須提供轉換運算子。  
  
 下列範例會產生 C2450：  
  
```  
// C2450.cpp  
class X {  
public:  
   int i;  
} x;  
  
class Y {  
public:  
   int i;  
   operator int() { return i; }   // conversion operator  
} y;  
  
int main() {  
   int j = 1;  
   switch ( x ) {   // C2450, x is not type int  
   // try the following line instead  
   // switch ( y ) {  
      default:  ;  
   }  
}  
```