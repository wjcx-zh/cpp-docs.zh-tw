---
title: const (C++)
ms.date: 11/04/2016
f1_keywords:
- const_cpp
helpviewer_keywords:
- const keyword [C++]
ms.assetid: b21c0271-1ad0-40a0-b21c-5e812bba0318
ms.openlocfilehash: cc1f117cc5f26edf9cd85461281b925c97fa5225
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180300"
---
# <a name="const-c"></a>const (C++)

修改資料宣告時， **const**關鍵字會指定物件或變數無法修改。

## <a name="syntax"></a>語法

```
const declaration ;
member-function const ;
```

## <a name="const-values"></a>const 值

**Const**關鍵字會指定變數的值為常數，並告知編譯器防止程式設計人員修改它。

```cpp
// constant_values1.cpp
int main() {
   const int i = 5;
   i = 10;   // C3892
   i++;   // C2105
}
```

在C++中，您可以使用**const**關鍵字，而不是[#define](../preprocessor/hash-define-directive-c-cpp.md)預處理器指示詞來定義常數值。 以**const**定義的值會受到類型檢查的限制，而且可以用來取代常數運算式。 在C++中，您可以使用**const**變數指定陣列的大小，如下所示：

```cpp
// constant_values2.cpp
// compile with: /c
const int maxarray = 255;
char store_char[maxarray];  // allowed in C++; not allowed in C
```

在 C 中，常數值預設為外部連結，因此只能出現在原始程式檔中。 在 C++ 中，常數值預設為內部連結，所以可以出現在標頭檔中。

**Const**關鍵字也可以用在指標宣告中。

```cpp
// constant_values3.cpp
int main() {
   char *mybuf = 0, *yourbuf;
   char *const aptr = mybuf;
   *aptr = 'a';   // OK
   aptr = yourbuf;   // C3892
}
```

宣告為**const**之變數的指標只能指派給也宣告為**const**的指標。

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

如果是宣告為**const**的物件，您只能呼叫常數成員函式。 這樣可以確保該常數物件永不會遭到修改。

```cpp
birthday.getMonth();    // Okay
birthday.setMonth( 4 ); // Error
```

您可以呼叫非常數物件的常數或非常數成員函式。 您也可以使用**const**關鍵字多載成員函式。這可針對常數和非常數物件呼叫不同版本的函式。

您不能使用**const**關鍵字宣告函數或析構函式。

## <a name="const-member-functions"></a>const 成員函式

使用**const**關鍵字宣告成員函式會指定函式為「唯讀」函式，而不會修改呼叫它的物件。 常數成員函式無法修改任何非靜態資料成員，或呼叫不是常數的任何成員函式。若要宣告常數成員函式，請將**const**關鍵字放在引數清單的右括弧後面。 宣告和定義中都必須有**const**關鍵字。

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

## <a name="c-and-c-const-differences"></a>C 和C++ const 差異

當您在 C 原始程式碼檔案中將變數宣告為**const**時，您會這麼做：

```cpp
const int i = 2;
```

然後，您可以在其他模組中使用此變數，例如：

```cpp
extern const int i;
```

但是，若要在中C++取得相同的行為，您必須將**const**變數宣告為：

```cpp
extern const int i = 2;
```

如果您想要在C++原始程式碼檔案中宣告**外部**變數以用於 C 原始程式碼檔，請使用：

```cpp
extern "C" const int x=10;
```

以避免 C++ 編譯器改變名稱。

## <a name="remarks"></a>備註

當您遵循成員函式的參數清單時， **const**關鍵字會指定函式不會修改叫用它的物件。

如需**const**的詳細資訊，請參閱下列主題：

- [const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)

- [類型限定詞（C 語言參考）](../c-language/type-qualifiers.md)

- [volatile](../cpp/volatile-cpp.md)

- [#define](../preprocessor/hash-define-directive-c-cpp.md)

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
