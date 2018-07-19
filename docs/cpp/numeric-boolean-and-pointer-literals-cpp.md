---
title: 數值、 布林值和指標常值 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 178c75efa84ebc7d27c19feb81e81314dc4c5bd7
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942903"
---
# <a name="numeric-boolean-and-pointer-literals--c"></a>數值、 布林值和指標常值 （c + +）
常值是直接代表值的程式項目。 本文涵蓋整數、浮點、布林值和指標類型的常值。 字串和字元常值的相關資訊，請參閱[字串和字元常值 （c + +）](../cpp/string-and-character-literals-cpp.md)。 您也可以定義專屬常值，根據任何兩個類別;如需詳細資訊，請參閱[使用者定義常值 （c + +）](../cpp/user-defined-literals-cpp.md)  
  
 。 您可以在許多內容中使用常值，但最常見的是初始化具名變數，以及將引數傳遞給函式：  
  
```cpp 
const int answer = 42; // integer literal  
double d = sin(108.87);     //floating point literal passed to sin function  
bool b = true;              // boolean literal  
MyClass* mc = nullptr;      // pointer literal  
  
```  
  
 有時，重要的是告訴編譯器如何解譯常值，或提供給它哪個特定類型。 做法是將前置詞或後置詞附加到常值。 例如，前置詞 0x 告訴編譯器將其後的數字解譯為十六進位值 (例如 0x35)。 ULL 後置詞會指示編譯器將值視為**unsigned long long** 5894345ull 的類型。 如需每個常值類型之前置詞和後置詞的完整清單，請參閱下列各節。  
  
## <a name="syntax"></a>語法  
  
## <a name="integer-literals"></a>整數常值  
 整數常值的開頭是數字，而且沒有小數部分或指數。 您可以指定十進位、八進位或十六進位格式的整數常值。 它們可以指定帶正負號或不帶正負號的類型以及長或短類型。  
  
 有沒有前置詞或後置詞時，編譯器會提供整數常值的實值型別**int** （32 位元），如果值符合，否則它會提供型別**long long** （64 位元）。  
  
 若要指定十進位整數常值，請使用非零數字開始指定。 例如:   
  
```cpp 
int i = 157;   // Decimal literal  
int j = 0198;       // Not a decimal number; erroneous octal literal  
int k = 0365;       // Leading zero specifies octal literal, not decimal  
int m = 36'000'000  // digit separators make large values more readable  
int   
```  
  
 若要指定八進位整數常值，請使用 0 開始指定，後接範圍 0 到 7 的一連串數字。 數字 8 和 9 是在指定八進位常值中的錯誤。 例如:   
  
```cpp 
int i = 0377;   // Octal literal  
int j = 0397;        // Error: 9 is not an octal digit  
```  
  
 若要指定十六進位整數常值，請使用 `0x` 或 `0X` ("x" 不區分大小寫) 開始指定，後接範圍 `0` 到 `9` 和 `a` (或 `A`) 到 `f` (或 `F`) 的一連串數字。 十六進位數字 `a` (或  `A`) 到 `f` (或  `F`) 代表範圍 10 到 15 的值。 例如:   
  
```cpp 
int i = 0x3fff;   // Hexadecimal literal  
int j = 0X3FFF;        // Equal to i  
```  
  
 若要指定不帶正負號的類型，請使用`u`或`U`後置詞。 若要指定長類型，請使用`l`或`L`後置詞。 若要指定 64 位元整數類型，請使用 LL 或 ll 後置詞。 i64 後置詞仍予以支援，但應該避免使用，因為它專屬於 Microsoft 且為非可攜式。 例如:   
  
```cpp 
unsigned val_1 = 328u;             // Unsigned value  
long val_2 = 0x7FFFFFL;                 // Long value specified   
                                        //  as hex literal  
unsigned long val_3 = 0776745ul;        // Unsigned long value  
auto val_4 = 108LL;                           // signed long long  
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long   
```  
  
 **數字分隔符號**： 您可以使用單引號字元 （縮寫符號） 來分隔中較大的數字，使其更容易閱讀的位置值。 分隔符號對於編譯沒有作用。  
  
```cpp 
long long i = 24'847'458'121  
```  
  
## <a name="floating-point-literals"></a>浮點常值  
 浮點常值指定必須有小數部分的值。 這些值包含小數點 (**。**) 而且可包含指數。  
  
 浮點常值包含「尾數」(指定數字的值)、「指數」(指定數字的大小範圍)，以及選擇性的後置詞 (指定常值類型)。 尾數的指定方式是數字序列加上句號，再加上選擇性的數字序列，代表該數字的小數部分。 例如：  
  
```cpp 
18.46  
38.  
```  
  
 如果有指數，指數會以 10 的次方指定數字的大小，如下列範例所示：  
  
```cpp 
18.46e0      // 18.46  
18.46e1           // 184.6  
```  
  
 可能會使用指定指數`e`或`E`，其中具有相同的意義，後面跟著選擇性正負號 (+ 或-) 和一連串數字。  如果有指數，`18E0` 之類的整數就不需要尾端的小數點。  
  
 浮點常值預設為類型**double**。 使用尾碼`f`或`l`(或`F`或`L`— 後置字元不區分大小寫)，常值可以指定為**float**或是**長雙精度**，分別。  
  
 雖然**長雙精度**並**double**有相同表示法，而不是相同的型別。 例如，您可以有多載函式，例如  
  
```cpp 
void func( double );  
```  
  
 和  
  
```cpp 
void func( long double );  
```  
  
## <a name="boolean-literals"></a>布林值常值  
 布林常值是**真**並**false**。  
  
## <a name="pointer-literal-c11"></a>指標常值 (C++11)  
 C + + 引進[nullptr](../cpp/nullptr.md)常值來指定零初始化指標。 在可攜式的程式碼**nullptr**應該使用而不是整數類型零或巨集，例如 NULL。  
  
## <a name="binary-literals-c14"></a>二進位常值 (C++14)  
 使用 `0B` 或 `0b` 前置詞，後接一連串的 1 和 0，即可指定二進位常值：  
  
```cpp 
  
auto x = 0B001101 ; // int  
auto y = 0b000001 ; // int  
```  
  
## <a name="avoid-using-literals-as-magic-constants"></a>請避免使用常值做為「幻方常數」。  
 您可以直接在運算式和陳述式中使用常值，雖然這不一定是好的程式設計做法：  
  
```cpp 
if (num < 100)  
    return "Success";  
  
```  
  
 在先前的範例中，可能最好使用傳達清楚意義的具名常數 (例如 "MAXIMUM_ERROR_THRESHOLD")。 而且，如果使用者看到傳回值「成功」，則可能最好使用具名字串常數，而具名字串常數可以儲存於可將其當地語系化為其他語言之檔案的單一位置中。 使用具名常數，可協助他人和您自己了解程式碼的用途。  
  
## <a name="see-also"></a>另請參閱  
 [語彙慣例](../cpp/lexical-conventions.md)   
 [C + + 字串常值](../cpp/string-and-character-literals-cpp.md)   
 [C + + 使用者定義常值](../cpp/user-defined-literals-cpp.md)