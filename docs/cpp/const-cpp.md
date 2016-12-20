---
title: "const (C++) | Microsoft Docs"
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
  - "const_cpp"
  - "const"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const 關鍵字 [C++]"
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# const (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在修改資料宣告時，**const** 關鍵字指定物件或變數是不可修改的。  
  
## 語法  
  
```  
  
        const declaration ;  
member-function const ;  
```  
  
## const 值  
 **const** 關鍵字指定變數值為常數，並告知編譯器禁止程式設計人員修改該值。  
  
```  
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 在 C\+\+ 中，您可以使用 **const** 關鍵字取代 [\#define](../preprocessor/hash-define-directive-c-cpp.md) 前置處理器指示詞來定義常數值。  以 **const** 定義的值必須接受類型檢查，並且可以取代常數運算式。  在 C\+\+ 中，您可以使用 **const** 變數指定陣列的大小，如下所示：  
  
```  
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 在 C 中，常數值預設為外部連結，因此只能出現在原始程式檔中。  在 C\+\+ 中，常數值預設為內部連結，所以可以出現在標頭檔中。  
  
 **const** 關鍵字也可以用於指標宣告中。  
  
```  
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 宣告為 **const** 之變數的指標只能指派給同樣宣告為**const** 的指標。  
  
```  
// constant_values4.cpp  
#include <stdio.h>  
int main() {  
   const char *mybuf = "test";  
   char *yourbuf = "test2";  
   printf_s("%s\n", mybuf);  
  
   const char *bptr = mybuf;   // Pointer to constant data  
   printf_s("%s\n", bptr);  
  
   // *bptr = 'a';   // Error  
}  
```  
  
 您可以將常數資料指標當做函式參數使用，以防止函式修改透過指標傳遞的參數。  
  
 對於宣告為 **const** 的物件，您只能呼叫 [常數成員函式](../misc/constant-member-functions.md)。  這樣可以確保該常數物件永不會遭到修改。  
  
```  
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 您可以呼叫非常數物件的常數或非常數成員函式。  您也可以使用 **const** 關鍵字多載成員函式；這樣可以針對常數和非常數物件呼叫不同版本的函式。  
  
 您不能以 **const** 關鍵字宣告建構函式或解構函式。  
  
## const 成員函式  
 使用 **const** 關鍵字宣告成員函式會指定函式為「唯讀」函式，該函式不會修改針對其呼叫函式的物件。  常數成員函式無法修改任何非靜態資料成員，或是呼叫任何不是常數的成員函式。若要宣告常數成員函式，請將 **const** 關鍵字放在引數清單的右括號後面。  宣告和定義中都需要 **const** 關鍵字。  
  
```  
// constant_member_function.cpp  
class Date  
{  
public:  
   Date( int mn, int dy, int yr );  
   int getMonth() const;     // A read-only function  
   void setMonth( int mn );   // A write function; can't be const  
private:  
   int month;  
};  
  
int Date::getMonth() const  
{  
   return month;        // Doesn't modify anything  
}  
void Date::setMonth( int mn )  
{  
   month = mn;          // Modifies data member  
}  
int main()  
{  
   Date MyDate( 7, 4, 1998 );  
   const Date BirthDate( 1, 18, 1953 );  
   MyDate.setMonth( 4 );    // Okay  
   BirthDate.getMonth();    // Okay  
   BirthDate.setMonth( 4 ); // C2662 Error  
}  
```  
  
## C 和 C\+\+ 常數的差異  
 當您在 C 原始程式碼檔案中將變數宣告為 **const** 時，可以這麼做：  
  
```  
const int i = 2;  
```  
  
 然後，您可以在其他模組中使用此變數，例如：  
  
```  
extern const int i;  
```  
  
 不過，若要在 C\+\+ 中得到相同行為，您必須將 **const** 變數宣告為：  
  
```  
extern const int i = 2;  
```  
  
 如果您希望在 C \+\+ 原始程式碼檔案中宣告 `extern` 變數，以用於 C 原始程式碼檔案中，請使用：  
  
```  
extern "C" const int x=10;  
```  
  
 以避免 C\+\+ 編譯器改變名稱。  
  
## 備註  
 若在成員函式參數清單之後，**const** 關鍵字指定函式不會修改函式叫用的目標物件。  
  
 如需**const** 的詳細資訊，請參閱下列主題：  
  
-   [常數值](../misc/constant-values.md)  
  
-   [常數成員函式](../misc/constant-member-functions.md)  
  
-   [const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)  
  
-   [類型限定詞 \(C 語言參考\)](../c-language/type-qualifiers.md)  
  
-   [volatile](../cpp/volatile-cpp.md)  
  
-   [\#define](../preprocessor/hash-define-directive-c-cpp.md)。  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)