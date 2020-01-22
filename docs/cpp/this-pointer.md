---
title: this 指標
description: this 指標是在非靜態成員函式中，以編譯器產生的目前物件指標。
ms.date: 01/22/2020
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- this
- class
- struct
- union
- sizeof
- const
- volatile
ms.openlocfilehash: 58bba2edd7a457c624b747b5a65d209995852848
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518331"
---
# <a name="opno-locthis-pointer"></a>this 指標

**this** 指標是只能在 **class** 、 **struct** 或 **union** 類型的非靜態成員函式中存取的指標。 它會指向針對其呼叫成員函式的物件。 靜態成員函式沒有 **this** 指標。

## <a name="syntax"></a>語法

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>備註

物件的 **this** 指標不是物件本身的一部分。 它不會反映在物件上 **sizeof** 語句的結果中。 針對物件呼叫非靜態成員函式時，編譯器會將物件的位址以隱藏引數的形式傳遞至函數。 例如，下列函式呼叫：

```cpp
myDate.setMonth( 3 );
```

可以解讀為：

```cpp
setMonth( &myDate, 3 );
```

物件的位址可從成員函式內當做 **this** 指標來取得。 大部分的 **this** 指標使用都是隱含的。 雖然不必要，但是在參考 class的成員時，也不需要使用明確的 **this** 。 例如：

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   this->month = mn;      // are equivalent
   (*this).month = mn;
}
```

`*this` 運算式通常用來從成員函式傳回目前物件：

```cpp
return *this;
```

**this** 指標也用來防護自我參考：

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
> 因為 **this** 指標是不可修改的，所以不允許對 **this** 指標的指派。 允許指派給C++ **this** 的舊版。

有時候， **this** 指標會直接使用，例如，若要操控自我參考資料結構，其中需要目前物件的位址。

## <a name="example"></a>範例

```cpp
// this_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

class Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( const Buf & );
    void Display() { cout << buffer << endl; }

private:
    char*   buffer;
    size_t  sizeOfBuffer;
};

Buf::Buf( char* szBuffer, size_t sizeOfBuffer )
{
    sizeOfBuffer++; // account for a NULL terminator

    buffer = new char[ sizeOfBuffer ];
    if (buffer)
    {
        strcpy_s( buffer, sizeOfBuffer, szBuffer );
        sizeOfBuffer = sizeOfBuffer;
    }
}

Buf& Buf::operator=( const Buf &otherbuf )
{
    if( &otherbuf != this )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *this;
}

int main()
{
    Buf myBuf( "my buffer", 10 );
    Buf yourBuf( "your buffer", 12 );

    // Display 'my buffer'
    myBuf.Display();

    // assignment operator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-opno-locthis-pointer"></a>this 指標的類型

**const** 和 **volatile** 關鍵字可以在函式宣告中修改 **this** 指標的類型。 若要宣告具有其中一個屬性的函式，請在函式引數清單之後新增關鍵字。

假設有一個範例：

```cpp
// type_of_this_pointer1.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

上述程式碼會宣告成員函式 `X`，其中 **this** 指標會被視為 **const** 物件的 **const** 指標。 您可以使用*cv-mod-list*選項的組合，但它們一律會修改 **this** 指標所指向的物件，而不是指標本身。 下列宣告會宣告函數 `X`，其中 **this** 指標是 **const** 物件的 **const** 指標：

```cpp
// type_of_this_pointer2.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

成員函式中的 **this** 類型是由下列語法所描述。 *Cv 限定詞清單*是由成員函式的宣告子所決定。 可以是 **const** 或 **volatile** （或兩者）。 *class類型*是 class的名稱：

[*cv-辨識符號-清單*] *class類型* **\* const this**

換句話說， **this** 指標一律是 const 指標。 無法重新指派。  成員函式宣告中所使用的 **const** 或 **volatile** 限定詞，適用于 **this** 指標指向的 class 實例（位於該函式的範圍內）。

下表將進一步說明這些修飾詞的運作方式。

### <a name="semantics-of-opno-locthis-modifiers"></a>this 修飾詞的語義

|Modifier|意義|
|--------------|-------------|
|**const**|無法變更成員資料;無法叫用不 **const** 的成員函式。|
|**volatile**|成員資料會在每次存取時從記憶體載入;停用特定的優化。|

將 **const** 物件傳遞至不 **const** 的成員函式是錯誤的。

同樣地，將 **volatile** 物件傳遞至不 **volatile** 的成員函式也是錯誤。

宣告為 **const** 的成員函式無法變更成員資料-在這類函式中， **this** 指標是指向 **const** 物件的指標。

> [!NOTE]
> 無法將構造函式和析構函式宣告為 **const** 或 **volatile** 。 不過，它們可以在 **const** 或 **volatile** 物件上叫用。

## <a name="see-also"></a>請參閱

[關鍵字](../cpp/keywords-cpp.md)
