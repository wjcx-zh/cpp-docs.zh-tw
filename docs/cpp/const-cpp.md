---
title: "const （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: const_cpp
dev_langs: C++
helpviewer_keywords: const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8290b9c73dbab2c3cc3ab63cfbff10f587e46d7b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="const-c"></a>const (C++)
修改資料宣告時**const**關鍵字指定物件或變數不是可修改。  
  
## <a name="syntax"></a>語法  
  
```  
  
      const declaration ;  
member-function const ;  
```  
  
## <a name="const-values"></a>const 值  
 **Const**關鍵字指定變數的值是常數，並告知編譯器禁止程式設計人員修改該值。  
  
```  
// constant_values1.cpp  
int main() {  
   const int i = 5;  
   i = 10;   // C3892  
   i++;   // C2105  
}  
```  
  
 在 c + +，您可以使用**const**關鍵字取代[#define](../preprocessor/hash-define-directive-c-cpp.md)前置處理器指示詞來定義常數值。 值，以定義**const**受限於類型檢查，而且可用來取代常數運算式。 在 c + +，您可以指定與陣列的大小**const**變數，如下所示：  
  
```  
// constant_values2.cpp  
// compile with: /c  
const int maxarray = 255;  
char store_char[maxarray];  // allowed in C++; not allowed in C  
```  
  
 在 C 中，常數值預設為外部連結，因此只能出現在原始程式檔中。 在 C++ 中，常數值預設為內部連結，所以可以出現在標頭檔中。  
  
 **Const**關鍵字也可以用於指標宣告。  
  
```  
// constant_values3.cpp  
int main() {  
   char *mybuf = 0, *yourbuf;  
   char *const aptr = mybuf;  
   *aptr = 'a';   // OK  
   aptr = yourbuf;   // C3892  
}  
```  
  
 變數宣告為指標**const**可以只指派給同樣宣告為指標**const**。  
  
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
  
 物件宣告為**const**，您可以只呼叫常數成員函式。 這樣可以確保該常數物件永不會遭到修改。  
  
```  
birthday.getMonth();    // Okay  
birthday.setMonth( 4 ); // Error  
```  
  
 您可以呼叫非常數物件的常數或非常數成員函式。 您也可以多載成員函式使用**const**關鍵字; 這樣可以針對常數和非常數物件呼叫函式的不同版本。  
  
 您無法宣告建構函式或解構函式與**const**關鍵字。  
  
## <a name="const-member-functions"></a>const 成員函式  
 宣告成員函式**const**關鍵字指定函式不會修改它會呼叫物件的 「 唯讀 」 函式。 常數成員函式無法修改任何非靜態資料成員，或是呼叫任何成員函式不是常數。若要宣告常數成員函式，將**const**關鍵字之後的引數清單的右括號。 **Const**關鍵字需要宣告和定義中。  
  
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
  
## <a name="c-and-c-const-differences"></a>C 和 C++ 常數的差異  
 當您將變數宣告為**const**在 C 原始程式碼檔案中，可以這麼做：  
  
```  
const int i = 2;  
```  
  
 然後，您可以在其他模組中使用此變數，例如：  
  
```  
extern const int i;  
```  
  
 若要在 c + + 中得到相同行為，您必須宣告，但您**const**變數為：  
  
```  
extern const int i = 2;  
```  
  
 如果您希望在 C ++ 原始程式碼檔案中宣告 `extern` 變數，以用於 C 原始程式碼檔案中，請使用：  
  
```  
extern "C" const int x=10;  
```  
  
 以避免 C++ 編譯器改變名稱。  
  
## <a name="remarks"></a>備註  
 下列成員函式的參數清單中，當**const**關鍵字指定函式不會修改它叫用的物件。  
  
 如需有關**const**，請參閱下列主題：  
    
-   [const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)  
  
-   [類型限定詞 （C 語言參考）](../c-language/type-qualifiers.md)  
  
-   [volatile](../cpp/volatile-cpp.md)  
  
-   [#define](../preprocessor/hash-define-directive-c-cpp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)