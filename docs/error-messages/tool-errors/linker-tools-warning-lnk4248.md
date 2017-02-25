---
title: "連結器工具警告 LNK4248 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4248"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4248"
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 連結器工具警告 LNK4248
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法解析的 typeref 語彙基元 \(token\) \(對 'type' 而言\)，映像可能無法執行  
  
 型別在 MSIL 中繼資料內沒有定義。  
  
 LNK4248 可能發生的原因是：當 MSIL 模組 \(以 **\/clr** 編譯\) 中只有型別的轉送宣告時，而型別是在 MSIL 模組中參考，而且 MSIL 模組是與有型別定義的原生模組連結。  
  
 在此情況下，連結器將提供 MSIL 中繼資料內的原生型別定義，這樣可能會提供正確行為。  
  
 但是如果轉送型別宣告是 CLR 型別，則連結器的原生型別定義可能不會正確。  
  
 如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### 更正這個錯誤  
  
1.  提供 MSIL 模組中的型別定義。  
  
## 範例  
 下列範例會產生 LNK4248。  定義結構 A，解決問題。  
  
```  
// LNK4248.cpp  
// compile with: /clr /W1  
// LNK4248 expected  
struct A;  
void Test(A*){}  
  
int main() {  
   Test(0);  
}  
```  
  
## 範例  
 下列範例有型別的轉送定義。  
  
```  
// LNK4248_2.cpp  
// compile with: /clr /c  
class A;   // provide a definition for A here to resolve  
A * newA();  
int valueA(A * a);  
  
int main() {  
   A * a = newA();  
   return valueA(a);  
}  
```  
  
## 範例  
 下列範例會產生 LNK4248。  
  
```  
// LNK4248_3.cpp  
// compile with: /c  
// post-build command: link LNK4248_2.obj LNK4248_3.obj  
class A {  
public:   
   int b;  
};  
  
A* newA() {  
   return new A;  
}  
  
int valueA(A * a) {  
   return (int)a;  
}  
```