---
title: "連結器工具錯誤 LNK2020 | Microsoft Docs"
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
  - "LNK2020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2020"
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未解析的語彙基元 'token'  
  
 與未定義的外部錯誤類似，除了透過中繼資料來參考之外。  在中繼資料中，必須定義所有函式和資料。  
  
 若要解決這個問題，請執行下列動作：  
  
-   定義遺漏的函式或資料，或  
  
-   包含已定義好卻遺漏的函式或資料所在的目的檔或程式庫。  
  
## 範例  
 下列範例會產生 LNK2020。  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## 範例  
 如果您建立 Managed 樣板型別的變數時，也會發生 LNK2020，但不要將型別也具現化。  
  
 下列範例會產生 LNK2020。  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```