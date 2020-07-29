---
title: 數值、布林值和指標常值（c + +）
description: 整數、浮點數、布林值和指標常值的 c + + 標準語言格式。
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: def223682b58f3d0c8bd3dd88f6d54fc5aa8b8a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186447"
---
# <a name="numeric-boolean-and-pointer-literals"></a>數值、布林值和指標常值

常值是直接代表值的程式項目。 本文涵蓋類型為整數、浮點數、布林值和指標的常值。 如需字串和字元常值的相關資訊，請參閱[字串和字元常值（c + +）](../cpp/string-and-character-literals-cpp.md)。 您也可以根據上述任何類別來定義您自己的常值。 如需詳細資訊，請參閱[使用者定義常值（c + +）](../cpp/user-defined-literals-cpp.md)

. 您可以在許多內容中使用常值，但最常見的是初始化具名變數，以及將引數傳遞給函式：

```cpp
const int answer = 42;      // integer literal
double d = sin(108.87);     // floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

有時，重要的是告訴編譯器如何解譯常值，或提供給它哪個特定類型。 其做法是將前置詞或尾碼附加至常值。 例如，前置詞 `0x` 會指示編譯器將其後的數位解讀為十六進位值，例如 `0x35` 。 `ULL`尾碼會指示編譯器將值視為 **`unsigned long long`** 類型，如中所示 `5894345ULL` 。 如需每個常值類型之前置詞和後置詞的完整清單，請參閱下列各節。

## <a name="integer-literals"></a>整數常值

整數常值的開頭是數字，而且沒有小數部分或指數。 您可以指定十進位、八進位或十六進位格式的整數常值。 您可以指定帶正負號或不帶正負號的類型，以及 long 或 short 類型。

當沒有前置詞或後置詞時，如果值符合，則編譯器會提供整數常數值型別 **`int`** （32位），否則它會提供類型 **`long long`** （64位）。

若要指定十進位整數常值，請使用非零數字開始指定。 例如：

```cpp
int i = 157;        // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
```

若要指定八進位整數常值，請使用 0 開始指定，後接範圍 0 到 7 的一連串數字。 數字 8 和 9 是在指定八進位常值中的錯誤。 例如：

```cpp
int i = 0377;   // Octal literal
int j = 0397;   // Error: 9 is not an octal digit
```

若要指定十六進位整數常值，請使用 `0x` 或 `0X` （"x" 的大小寫不重要）來開始規格，後面接著範圍中 `0` 透過 `9` 和 `a` （或 `A` ）到 `f` （或 `F` ）的一連串數位。 十六進位數字 `a` (或  `A`) 到 `f` (或  `F`) 代表範圍 10 到 15 的值。 例如：

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;   // Equal to i
```

若要指定不帶正負號的類型，請使用 `u` 或 `U` 尾碼。 若要指定 long 類型，請使用 `l` 或 `L` 尾碼。 若要指定 64 位元整數類型，請使用 LL 或 ll 後置詞。 仍然支援 i64 尾碼，但我們不建議您這麼做。 這是專為 Microsoft 所指定，不可移植。 例如：

```cpp
unsigned val_1 = 328u;                  // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**數位分隔符號**：您可以使用單引號字元（單引號）分隔較大數位的位置值，讓人們更容易閱讀。 分隔符號對於編譯沒有作用。

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>浮點常值

浮點常值指定必須有小數部分的值。 這些值包含小數點（ **`.`** ），而且可以包含指數。

浮點常值具有*有效位數*（有時稱為「*尾數*」），它會指定數位的值。 它們具有*指數*，用來指定數位的大小。 而且，它們具有指定常數值型別的選擇性尾碼。 有效位數會指定為一連串的數位，後面接著一個句號，後面接著一個選擇性的數位序列，代表數位的小數部分。 例如：

```cpp
18.46
38.
```

如果有指數，指數會以 10 的次方指定數字的大小，如下列範例所示：

```cpp
18.46e0      // 18.46
18.46e1      // 184.6
```

您可以使用或指定指數 `e` `E` ，其意義相同，後面接著選擇性正負號（+ 或-）和一連串的數位。  如果有指數，`18E0` 之類的整數就不需要尾端的小數點。

浮點常值預設為類型 **`double`** 。 藉由使用尾碼 `f` 或 `l` 或 `F` 或 `L` （尾碼不區分大小寫），可以將常值指定為 **`float`** 或 **`long double`** 。

雖然 **`long double`** 和 **`double`** 具有相同的標記法，但它們不是相同的類型。 例如，您可以有多載函式，例如

```cpp
void func( double );
```

和

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>布林常值

布林常值為 **`true`** 和 **`false`** 。

## <a name="pointer-literal-c11"></a>指標常值 (C++11)

C + + 引進 [`nullptr`](../cpp/nullptr.md) 常值來指定零初始化的指標。 在可移植程式碼中， **`nullptr`** 應該使用，而不是整數類型零或宏（例如） `NULL` 。

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

在上述範例中，較好的作法是使用可傳達清楚意義的命名常數，例如「MAXIMUM_ERROR_THRESHOLD」。 而且，如果使用者看到傳回值「成功」，則使用已命名的字串常數可能會更好。 您可以將字串常數保留在檔案中可當地語系化為其他語言的單一位置。 使用已命名的常數可協助您自己和其他人瞭解程式碼的意圖。

## <a name="see-also"></a>另請參閱

[語彙慣例](../cpp/lexical-conventions.md)<br/>
[C + + 字串常值](../cpp/string-and-character-literals-cpp.md)<br/>
[C + + 使用者定義常值](../cpp/user-defined-literals-cpp.md)
