---
title: ':::no-loc(this)::: 指標'
description: :::no-loc(this):::指標是在非靜態成員函式中，以編譯器產生的目前物件指標。
ms.date: 01/22/2020
f1_keywords:
- :::no-loc(this):::_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- 'pointers, to :::no-loc(class)::: instance'
- ':::no-loc(this)::: pointer'
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- ':::no-loc(this):::'
- ':::no-loc(class):::'
- ':::no-loc(struct):::'
- ':::no-loc(union):::'
- ':::no-loc(sizeof):::'
- ':::no-loc(const):::'
- ':::no-loc(volatile):::'
ms.openlocfilehash: c851beaba7fe1091ffd7827714f90307303058c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225822"
---
# <a name="no-locthis-pointer"></a>:::no-loc(this)::: 指標

**`:::no-loc(this):::`** 指標是只能在 **`:::no-loc(class):::`** 、或類型的非靜態成員函式中存取的指標 **`:::no-loc(struct):::`** **`:::no-loc(union):::`** 。 它會指向針對其呼叫成員函式的物件。 靜態成員函式沒有 **`:::no-loc(this):::`** 指標。

## <a name="syntax"></a>語法

```cpp
:::no-loc(this):::
:::no-loc(this):::->member-identifier
```

## <a name="remarks"></a>備註

物件的 **`:::no-loc(this):::`** 指標不是物件本身的一部分。 它不會反映在 **`:::no-loc(sizeof):::`** 物件上的語句結果中。 針對物件呼叫非靜態成員函式時，編譯器會將物件的位址以隱藏引數的形式傳遞至函數。 例如，下列函式呼叫：

```cpp
myDate.setMonth( 3 );
```

可以解讀為：

```cpp
setMonth( &myDate, 3 );
```

物件的位址可從成員函式中當做指標來取得 **`:::no-loc(this):::`** 。 大部分 **`:::no-loc(this):::`** 的指標使用都是隱含的。 雖然不必要，但是 **`:::no-loc(this):::`** 在參考的成員時，還是要使用明確的 :::no-loc(class)::: 。 例如：

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   :::no-loc(this):::->month = mn;      // are equivalent
   (*:::no-loc(this):::).month = mn;
}
```

運算式 **`*:::no-loc(this):::`** 通常用來從成員函式傳回目前的物件：

```cpp
return *:::no-loc(this):::;
```

**`:::no-loc(this):::`** 指標也用來防範自我參考：

```cpp
if (&Object != :::no-loc(this):::) {
// do not execute in cases of self-reference
```

> [!NOTE]
> 因為指標是不可修改的 **`:::no-loc(this):::`** ，所以 **`:::no-loc(this):::`** 不允許對指標的指派。 舊版 c + + 允許指派至 **`:::no-loc(this):::`** 。

有時候， **`:::no-loc(this):::`** 指標會直接使用，例如，若要操控自我參考資料 :::no-loc(struct)::: ures，其中需要目前物件的位址。

## <a name="example"></a>範例

```cpp
// :::no-loc(this):::_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

:::no-loc(class)::: Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( :::no-loc(const)::: Buf & );
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

Buf& Buf::operator=( :::no-loc(const)::: Buf &otherbuf )
{
    if( &otherbuf != :::no-loc(this)::: )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *:::no-loc(this):::;
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

## <a name="type-of-the-no-locthis-pointer"></a>指標的類型 :::no-loc(this):::

**`:::no-loc(this):::`** 指標的型別可以在函式宣告中，由 **`:::no-loc(const):::`** 和關鍵字修改 **`:::no-loc(volatile):::`** 。 若要宣告具有其中一個屬性的函式，請在函式引數清單之後新增關鍵字。

假設有一個範例：

```cpp
// type_of_:::no-loc(this):::_pointer1.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

上述程式碼會宣告成員函式， `X` 其中 **`:::no-loc(this):::`** 指標會被視為 **`:::no-loc(const):::`** 物件的指標 **`:::no-loc(const):::`** 。 您可以使用*cv-mod-list*選項的組合，但它們一律會修改指標所指向的物件 **`:::no-loc(this):::`** ，而不是指標本身。 下列宣告會宣告 function `X` ，其中 **`:::no-loc(this):::`** 指標是物件的 **`:::no-loc(const):::`** 指標 **`:::no-loc(const):::`** ：

```cpp
// type_of_:::no-loc(this):::_pointer2.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

成員函式 **`:::no-loc(this):::`** 中的類型是由下列語法所描述。 *Cv 限定詞清單*是由成員函式的宣告子所決定。 它可以是 **`:::no-loc(const):::`** 或 **`:::no-loc(volatile):::`** （或兩者）。 * :::no-loc(class)::: -type*是的名稱 :::no-loc(class)::: ：

[*cv-辨識符號-清單*]* :::no-loc(class)::: -類型* ** \* :::no-loc(const)::: :::no-loc(this)::: **

換句話說， **`:::no-loc(this):::`** 指標一律是 :::no-loc(const)::: 指標。 無法重新指派。  成員函式宣告 **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** 中使用的或限定詞適用于 :::no-loc(class)::: 指標指向的實例 **`:::no-loc(this):::`** （在該函式的範圍內）。

下表將進一步說明這些修飾詞的運作方式。

### <a name="semantics-of-no-locthis-modifiers"></a>修飾詞 :::no-loc(this)::: 的語法

|修飾詞|意義|
|--------------|-------------|
|**`:::no-loc(const):::`**|無法變更成員資料;無法叫用不是的成員函式 **`:::no-loc(const):::`** 。|
|**`:::no-loc(volatile):::`**|成員資料會在每次存取時從記憶體載入;停用特定的優化。|

將物件傳遞至不是的成員函式是錯誤的 **`:::no-loc(const):::`** **`:::no-loc(const):::`** 。

同樣地，將物件傳遞至不是的成員函式也是錯誤 **`:::no-loc(volatile):::`** **`:::no-loc(volatile):::`** 。

宣告為 **`:::no-loc(const):::`** 無法變更成員資料的成員函式-在這類函式中， **`:::no-loc(this):::`** 指標是 **`:::no-loc(const):::`** 物件的指標。

> [!NOTE]
> Con :::no-loc(struct)::: or 和 de :::no-loc(struct)::: or 不能宣告為 **`:::no-loc(const):::`** 或 **`:::no-loc(volatile):::`** 。 不過，它們可以在或物件上叫用 **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** 。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
