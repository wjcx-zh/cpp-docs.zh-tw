---
title: "數值、布林值和指標常值 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常數, 常值"
  - "常值"
  - "常值, C++"
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 數值、布林值和指標常值 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常值是直接代表值的程式項目。  本文涵蓋整數、浮點、布林值和指標類型的常值。  如需字串和字元常值的相關資訊，請參閱[字串和字元常值 \(C\+\+\)](../cpp/string-and-character-literals-cpp.md)。  您也可以根據其中的任何分類來定義專屬常值；如需詳細資訊，請參閱[使用者定義常值 \(C\+\+\)](../cpp/user-defined-literals-cpp.md)  
  
 .  您可以在許多內容中使用常值，但最常見的是初始化具名變數，以及將引數傳遞給函式：  
  
```  
const int answer = 42; // integer literal  
double d = sin(108.87);     //floating point literal passed to sin function  
bool b = true;              // boolean literal  
MyClass* mc = nullptr;      // pointer literal  
  
```  
  
 有時，重要的是告訴編譯器如何解譯常值，或提供給它哪個特定類型。  做法是將前置詞或後置詞附加到常值。  例如，前置詞 0x 告訴編譯器將其後的數字解譯為十六進位值 \(例如 0x35\)。  ULL 後置詞告訴編譯器將值視為 `unsigned long long` 類型 \(例如 5894345ULL\)。  如需每個常值類型之前置詞和後置詞的完整清單，請參閱下列各節。  
  
## 語法  
  
## 整數常值  
 整數常值的開頭是數字，而且沒有小數部分或指數。  您可以指定十進位、八進位或十六進位格式的整數常值。  它們可以指定帶正負號或不帶正負號的類型以及長或短類型。  
  
 沒有前置詞或後置詞時，如果值符合，則編譯器會為整數提供常值型別 `int` \(32 位元\)，否則它會提供 `long long` \(64 位元\)。  
  
 若要指定十進位整數常值，請使用非零數字開始指定。  例如：  
  
```  
int i = 157;   // Decimal literal  
int j = 0198;       // Not a decimal number; erroneous octal literal  
int k = 0365;       // Leading zero specifies octal literal, not decimal  
int m = 36'000'000  // digit separators make large values more readable  
int   
```  
  
 若要指定八進位整數常值，請使用 0 開始指定，後接範圍 0 到 7 的一連串數字。  數字 8 和 9 是在指定八進位常值中的錯誤。  例如：  
  
```  
int i = 0377;   // Octal literal  
int j = 0397;        // Error: 9 is not an octal digit  
```  
  
 若要指定十六進位整數常值，請使用 `0x` 或 `0X` \("x" 不區分大小寫\) 開始指定，後接範圍 `0` 到 `9` 和 `a` \(或 `A`\) 到 `f` \(或 `F`\) 的一連串數字。  十六進位數字 `a` \(或  `A`\) 到 `f` \(或  `F`\) 代表範圍 10 到 15 的值。  例如：  
  
```  
int i = 0x3fff;   // Hexadecimal literal  
int j = 0X3FFF;        // Equal to i  
```  
  
 若要指定不帶正負號的類型，請使用 **u** 或 **U** 後置詞。  若要指定長類型，請使用 **l** 或 **L** 後置詞。  若要指定 64 位元整數類型，請使用 LL 或 ll 後置詞。  i64 後置詞仍予以支援，但應該避免使用，因為它專屬於 Microsoft 且為非可攜式。  例如：  
  
```  
unsigned val_1 = 328u;             // Unsigned value  
long val_2 = 0x7FFFFFL;                 // Long value specified   
                                        //  as hex literal  
unsigned long val_3 = 0776745ul;        // Unsigned long value  
auto val_4 = 108LL;                           // signed long long  
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long   
```  
  
 **數字分隔符號**：您可以使用單引號字元來分隔較大之數字中的位值，以方便閱讀。  分隔符號對於編譯沒有作用。  
  
```  
long long i = 24'847'458'121  
```  
  
## 浮點常值  
 浮點常值指定必須有小數部分的值。  這些值包含小數點 \(**.**\)，而且可包含指數。  
  
 浮點常值包含「尾數」\(指定數字的值\)、「指數」\(指定數字的大小範圍\)，以及選擇性的後置詞 \(指定常值類型\)。  尾數的指定方式是數字序列加上句號，再加上選擇性的數字序列，代表該數字的小數部分。  例如：  
  
```  
18.46  
38.  
```  
  
 如果有指數，指數會以 10 的次方指定數字的大小，如下列範例所示：  
  
```  
18.46e0      // 18.46  
18.46e1           // 184.6  
```  
  
 您可以使用 **e** 或 **E** 指定指數，二者意義相同，後面再加上選擇性的符號 \(\+ 或 \-\) 及數字序列。  如果有指數，`18E0` 之類的整數就不需要尾端的小數點。  
  
 浮點常值預設為類型 **double**。  使用後置詞 **f** 或 **l** \(或 **F** 或 **L**，後置詞不區分大小寫\)，可以分別將常值指定為 **float** 或 `long double`。  
  
 雖然 `long double` 和 **double** 的代表方式相同，但二者的類型不同。  例如，您可以有多載函式，例如  
  
```  
void func( double );  
```  
  
 和  
  
```  
void func( long double );  
```  
  
## 布林值常值  
 布林值常值是 `true` 和 `false`。  
  
## 指標常值 \(C\+\+11\)  
 C\+\+ 引進 [nullptr](../cpp/nullptr.md) 常值來指定零初始化指標。  在可攜式程式碼，應該使用 `nullptr`，而非整數類型零或巨集 \(例如 NULL\)。  
  
## 二進位常值 \(C\+\+14\)  
 使用 `0B` 或 `0b` 前置詞，後接一連串的 1 和 0，即可指定二進位常值：  
  
```  
  
auto x = 0B001101 ; // int  
auto y = 0b000001 ; // int  
```  
  
## 請避免使用常值做為「幻方常數」。  
 您可以直接在運算式和陳述式中使用常值，雖然這不一定是好的程式設計做法：  
  
```  
if (num < 100)  
    return "Success";  
  
```  
  
 在先前的範例中，可能最好使用傳達清楚意義的具名常數 \(例如 "MAXIMUM\_ERROR\_THRESHOLD"\)。  而且，如果使用者看到傳回值「成功」，則可能最好使用具名字串常數，而具名字串常數可以儲存於可將其當地語系化為其他語言之檔案的單一位置中。  使用具名常數，可協助他人和您自己了解程式碼的用途。  
  
## 請參閱  
 [語彙慣例](../cpp/lexical-conventions.md)   
 [C\+\+ 整數常數](http://msdn.microsoft.com/zh-tw/1f3b58a4-8346-4533-ba6e-df26d76f8dcf)   
 [C\+\+ 字元常值](http://msdn.microsoft.com/zh-tw/a7901c61-524d-47c6-beb6-d9dacc2e72ed)   
 [C\+\+ 浮點常數](http://msdn.microsoft.com/zh-tw/f6273f24-a876-4484-a7a2-e82275692ad3)   
 [C\+\+ 字串常值](../cpp/string-and-character-literals-cpp.md)   
 [C\+\+ 使用者定義常值](../cpp/user-defined-literals-cpp.md)