---
title: "編譯器錯誤 C2975 | Microsoft Docs"
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
  - "C2975"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2975"
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2975
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'arg' : 對 'type' 無效的樣板引數，必須是編譯時期常數運算式  
  
 樣板引數與樣板宣告不相符；常數運算式應該出現在角括弧內。  變數不可當做樣板的實質引數 \(Actual Argument\)。  請檢查樣板定義以找出正確的型別。  
  
 下列範例會產生 C2975：  
  
```  
// C2975.cpp  
template<int I>  
class X {};  
  
int main() {  
   int i = 4, j = 2;  
   X<i + j> x1;   // C2975  
   X<6> x2;   // OK  
}  
```  
  
 當您使用 \_\_LINE\_\_ 做為編譯時期常數並搭配 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 時，也可能會發生 C2975。  只要搭配 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 而非 **\/ZI** 進行編譯，便可解決此問題。  
  
```  
// C2975b.cpp  
// compile with: /ZI  
// processor: x86  
template<long line>   
void test(void) {}  
  
int main() {  
   test<__LINE__>();   // C2975  
}  
```