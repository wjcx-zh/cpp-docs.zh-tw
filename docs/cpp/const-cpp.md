---
title: const （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cpp
dev_langs:
- C++
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f765e2b10de5685e011a44326664459a47a6ae22
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060183"
---
# <a name="const-c"></a>const (C++)

修改資料宣告時**const**關鍵字可讓您指定的物件或變數不是可修改。

## <a name="syntax"></a>語法

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>const 值

**Const**關鍵字指定變數的值保持不變，並告知編譯器禁止程式設計人員對其進行修改。

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

在 c + +，您可以使用**const**而不是關鍵字[#define](../preprocessor/hash-define-directive-c-cpp.md)來定義常數值的前置處理器指示詞。 以定義的值**const**必須接受類型檢查，並可用來取代常數運算式。 在 c + + 中，您可以指定不含陣列的大小**const**變數，如下所示：

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

在 C 中，常數值預設為外部連結，因此只能出現在原始程式檔中。 在 C++ 中，常數值預設為內部連結，所以可以出現在標頭檔中。

**Const**關鍵字也可以用於指標宣告。

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

宣告為變數的指標**const**可以只指派給同樣宣告為指標**const**。

```cpp
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

宣告為物件**const**，您可以只呼叫常數成員函式。 這樣可以確保該常數物件永不會遭到修改。

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

您可以呼叫非常數物件的常數或非常數成員函式。 您也可以多載成員函式，使用**const**關鍵字; 這可讓不同版本的常數和非常數物件呼叫的函式。

您無法宣告建構函式或解構函式與**const**關鍵字。

## <a name="const-member-functions"></a>const 成員函式

宣告成員函式**const**關鍵字會指定函式是 「 唯讀 」 函式，不會修改為其呼叫的物件。 常數成員函式無法修改任何非靜態資料成員，或呼叫任何成員並不是固定的函式。若要宣告常數成員函式，將置於**const**關鍵字之後的引數清單的右括號。 **Const**關鍵字，才宣告和定義中。

```cpp
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

## <a name="c-and-c-const-differences"></a>C 和 c + + 常數的差異

當您宣告一個變數**const** C 原始程式碼檔案，在您這麼做：

```cpp
const int i = 2;
```

然後，您可以在其他模組中使用此變數，例如：

```cpp
extern const int i;
```

若要取得相同的行為，在 c + + 中，您必須宣告，但您**const**變數設定為：

```cpp
extern const int i = 2;
```

如果您想要宣告**extern**變數以用於 C 原始程式碼檔案，使用程式碼 c + + 原始程式檔中：

```cpp
extern "C" const int x=10;
```

以避免 C++ 編譯器改變名稱。

## <a name="remarks"></a>備註

下列成員函式的參數清單中，當**const**關鍵字會指定函式不會修改它叫用的物件。

如需詳細資訊**const**，請參閱下列主題：

- [const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)

- [類型限定詞 （C 語言參考）](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)