---
title: "deprecated (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "deprecated"
  - "deprecated_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], deprecated"
  - "deprecated __declspec 關鍵字"
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deprecated (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\(Microsoft 專有\) **deprecated** 宣告可提供與 [deprecated](../preprocessor/deprecated-c-cpp.md) pragma 相同的功能，但有下列例外狀況：  
  
-   **deprecated** 宣告可讓您將特殊形式的函式多載指定為取代，而 pragma 形式則適用於所有多載形式的函式名稱。  
  
-   **deprecated** 宣告可讓您指定要在編譯時期顯示的訊息。  訊息的文字可以來自巨集。  
  
-   巨集只能使用 **deprecated** pragma 標示為取代。  
  
 如果編譯器遇到取代識別項的用法，則會擲回 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 警告。  
  
## 範例  
 下列範例將示範使用 deprecated 函式時，如何將函式標示為取代以及如何指定要在編譯時期顯示的訊息。  
  
```  
// deprecated.cpp  
// compile with: /W3  
#define MY_TEXT "function is deprecated"  
void func1(void) {}  
__declspec(deprecated) void func1(int) {}  
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}  
__declspec(deprecated(MY_TEXT)) void func3(int) {}  
  
int main() {  
   func1();  
   func1(1);   // C4996  
   func2(1);   // C4996  
   func3(1);   // C4996  
}  
```  
  
## 範例  
 下列範例將示範使用 deprecated 類別時，如何將類別標示為取代以及如何指定要在編譯時期顯示的訊息。  
  
```  
// deprecate_class.cpp  
// compile with: /W3  
struct __declspec(deprecated) X {  
   void f(){}  
};  
  
struct __declspec(deprecated("** X2 is deprecated **")) X2 {  
   void f(){}  
};  
  
int main() {  
   X x;   // C4996  
   X2 x2;   // C4996  
}  
```  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)