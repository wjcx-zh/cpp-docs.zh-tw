---
title: "編譯器錯誤 C2143 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2143"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2143"
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# 編譯器錯誤 C2143
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤: 遺漏 'token1' \(在 'token2' 之前\)  
  
 編譯器必須有特定的語彙基元 \(亦即，某個不是泛空白字元的語言項目\)，但是找到另一個語彙基元。  
  
 如需使用 function\-try 區塊時發生此錯誤的相關資訊，請參閱[知識庫文件 241706](http://support.microsoft.com/kb/241706)。  
  
 請查閱 [C\+\+ 語言參考](../../cpp/cpp-language-reference.md)來判斷程式碼語法不正確的地方。  因為編譯器可能會在遇到造成此問題的該行之後才報告此錯誤，所以請檢查錯誤所在處的前幾行程式碼。  
  
 C2143 可能會在不同情況下發生。  
  
 這也可能會發生在可以限定名稱的運算子 \(`::`、 `->`和 `.`\) 後面都必須接著關鍵字 `template`，如下列範例所示：  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143  
    {  
    };  
};  
  
```  
  
 根據預設， C\+\+ 假設`Ty::PutFuncType` 不是範本；因此下列 `<` 會解譯成小於的符號。您必須明確地呼叫編譯器 `PutFuncType` 為樣板，以便它可以正確地解析角括弧。  若要更正這個錯誤，請在相依型別名稱使用 `template` 關鍵字，如下所示：  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct  
    {  
    };  
};  
  
```  
  
 在使用 **\/clr** 而且 `using` 指示詞發生語法錯誤時，C2143就會發生：  
  
```cpp  
// C2143a.cpp  
// compile with: /clr /c  
using namespace System.Reflection;   // C2143  
using namespace System::Reflection;  
```  
  
 嘗試使用 CLR 語法編譯原始程式檔，而未使用 **\/clr** 時，這也會發生：  
  
```cpp  
// C2143b.cpp  
ref struct A {   // C2143 error compile with /clr  
   void Test() {}  
};  
  
int main() {  
   A a;  
   a.Test();  
}  
```  
  
 接在 `if` 陳述式後面的第一個非泛空白字元必須為左括號。  編譯器不能轉譯任何其他字元：  
  
```cpp  
// C2143c.cpp  
int main() {  
   int j = 0;  
  
   // OK  
   if (j < 25)  
      ;  
  
   if (j < 25)   // C2143  
}  
```  
  
 偵測到錯誤的那一行、或偵測到之前其中一行遺漏了右大括號、括號或分號時，C2143就會發生：  
  
```caml  
// C2143d.cpp  
// compile with: /c  
class X {  
   int member1;  
   int member2   // C2143  
} x;  
```  
  
 或是在類別宣告無效的標記：  
  
```cpp  
// C2143e.cpp  
class X {  
   int member;  
} x;  
  
class + {};   // C2143 + is an invalid tag name  
class ValidName {};   // OK  
```  
  
 或當標記未附加至陳述式。  如果您必須單獨地放置一個標記 \(例如，放在複合陳述式後面\)，請將它附加到 null 陳述式：  
  
```cpp  
// C2143f.cpp  
// compile with: /c  
void func1() {  
   // OK  
   end1:  
      ;  
  
   end2:   // C2143  
}  
```  
  
 當一個未限定的呼叫為某一型別在 Standard C\+\+ 程式庫中時，可能會發生錯誤：  
  
```cpp  
// C2143g.cpp  
// compile with: /EHsc /c  
#include <vector>  
static vector<char> bad;   // C2143  
static std::vector<char> good;   // OK  
```  
  
 或有遺漏 `typename` 關鍵字：  
  
```cpp  
// C2143h.cpp  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
template <typename T>  
X<T>::Y X<T>::memFunc() {   // C2143  
// try the following line instead  
// typename X<T>::Y X<T>::memFunc() {  
   return Y();  
}  
```  
  
 或者如果您嘗試定義明確具現化 \(Explicit Instantiation\)：  
  
```cpp  
// C2143i.cpp  
// compile with: /EHsc /c  
// template definition  
template <class T>  
void PrintType(T i, T j) {}  
  
template void PrintType(float i, float j){}   // C2143  
template void PrintType(float i, float j);   // OK  
```  
  
 在 C 程式中，必須在函式開頭宣告變數，不能在函式執行非宣告指令之後宣告。  
  
```c  
// C2143j.c  
int main()   
{  
    int i = 0;  
    i++;  
    int j = 0; // C2143  
}  
  
```