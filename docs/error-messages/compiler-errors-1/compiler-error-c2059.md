---
title: "編譯器錯誤 C2059 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2059"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2059"
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# 編譯器錯誤 C2059
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤: 'token'  
  
 此語彙基元 \(Token\) 導致語法錯誤。  
  
 下列範例會針對宣告 `j` 的程式碼行產生錯誤訊息。  
  
```  
// C2059e.cpp  
// compile with: /c  
// C2143 expected  
// Error caused by the incorrect use of '*'.  
   int j*; // C2059   
```  
  
 若要判斷錯誤原因，您不只需要檢查錯誤訊息列出的那一行，還需要檢查之前的幾行。  如果檢查這幾行後仍找不到問題的線索，試著註解錯誤訊息中所列出的該行程式碼以及前幾行。  
  
 如果該錯誤訊息緊接地出現在跟在 `typedef` 變數之後的符號，請確認該變數是否定義於原始程式碼之中。  
  
 如果符號沒有評估，則可能會發生 C2059，就像使用 **\/D**`symbol`**\=** 進行編譯時，也可能會發生 C2059。  
  
```  
// C2059a.cpp  
// compile with: /DTEST=  
#include <stdio.h>  
  
int main() {  
   #ifdef TEST  
      printf_s("\nTEST defined %d", TEST);   // C2059  
   #else  
      printf_s("\nTEST not defined");  
   #endif  
}  
```  
  
 另一個發生 C2059 錯誤的情況是，在您編譯一個指定結構為某函式預設引數 \(Argument\) 的應用程式時。  引數的預設值必須為運算式。  而初始設定式清單 \(例如，用來初始化結構\) 並不是一個運算式。解決方式是定義一個建構函式 \(Constructor\) 來執行必要的初始化。  
  
 下列範例會產生 C2059：  
  
```  
// C2059b.cpp  
// compile with: /c  
struct ag_type {  
   int a;  
   float b;  
   // Uncomment the following line to resolve.  
   // ag_type(int aa, float bb) : a(aa), b(bb) {}   
};  
  
void func(ag_type arg = {5, 7.0});   // C2059  
void func(ag_type arg = ag_type(5, 7.0));   // OK  
```  
  
 您可能也會在類別外定義成員樣板類別 \(Template Class\) 或函式時收到 C2059。  如需詳細資訊，請參閱[知識庫文件 241949](http://support.microsoft.com/kb/241949)。  
  
 所有格式不正確的轉型也都可能會發生 C2059。  
  
 下列範例會產生 C2059：  
  
```  
// C2059c.cpp  
// compile with: /clr  
using namespace System;  
ref class From {};  
ref class To : public From {};  
  
int main() {  
   From^ refbase = gcnew To();  
   To^ refTo = safe_cast<To^>(From^);   // C2059  
   To^ refTo2 = safe_cast<To^>(refbase);   // OK  
}  
```  
  
 如果您嘗試建立包含句號的命名空間名稱，也可能會發生 C2059。  
  
 下列範例會產生 C2059：  
  
```  
// C2059d.cpp  
// compile with: /c  
namespace A.B {}   // C2059  
  
// OK  
namespace A  {  
   namespace B {}  
}  
```  
  
 C2059 也可能會發生在可以限定名稱的運算子 \(`::`、 `->`和 `.`\) 後面都必須接著關鍵字 `template`，如下列範例所示：  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::Rebind<X>::Other AX; // error C2059  
};  
  
```  
  
 根據預設， C\+\+ 假設`AY::Rebind` 不是範本；因此下列 `<` 會解譯成小於的符號。您必須明確地呼叫編譯器 `Rebind` 為樣板，以便它可以正確地解析角括弧。  若要更正這個錯誤，請在相依型別名稱使用 `template` 關鍵字，如下所示：  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::template Rebind<X>::Other AX; // correct  
};  
  
```