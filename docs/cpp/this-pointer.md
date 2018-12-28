---
title: this 指標
ms.date: 11/04/2016
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
ms.openlocfilehash: c90a843ba978a98c1c61d9e096d62b85256ab0c4
ms.sourcegitcommit: d441305fb19131afbd7fc259d8cda63ea26f2343
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51678323"
---
# <a name="this-pointer"></a>this 指標

**這**指標是只能在非靜態成員函式中存取指標**類別**，**結構**，或**union**型別。 它會指向針對其呼叫成員函式的物件。 靜態成員函式沒有**這**指標。

## <a name="syntax"></a>語法

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>備註

物件的**這**指標不屬於物件本身，它將不會反映結果**sizeof**物件上的陳述式。 不過，呼叫物件的非靜態成員函式時，編譯器會將物件的位址當做隱藏的引數傳遞至函式。 例如，下列函式呼叫：

```cpp
myDate.setMonth( 3 );
```

可以用這種方式解譯：

```cpp
setMonth( &myDate, 3 );
```

物件的位址可從成員函式內**這**指標。 用法大多**這**是隱含的。 它是合法的但不必要的若要明確地使用**這**參考類別的成員時。 例如: 

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

**這**指標也會用於防範自我參考：

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
>  因為**這**指標是不可修改，指派給**這**不允許。 舊版 c + + 實作允許指派給**這**。

偶爾**這**指標會直接使用 — 比方說，來操作自我參考的資料結構，需要目前物件的位址的情況。

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

## <a name="type-of-the-this-pointer"></a>this 指標的類型

**這**指標的類型可以在函式宣告中，藉由修改**const**並**volatile**關鍵字。 若要將函式宣告為擁有一個或多個這些關鍵字的屬性，請在函式引數清單後面加入關鍵字。

請考量以下範例：

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

上述程式碼會宣告成員函式`X`，在其中**這**指標會視為**const**指標**const**物件。 組合*cv mod 清單*可用選項，但它們隨時修改所指向的物件**這**，而非**這**指標本身。 因此，下列宣告會宣告函式`X`;**這**指標**const**指標**const**物件：

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

型別**這**成員中函式以下列語法描述，其中*cv 限定詞清單*決定從成員函式宣告子，而且可以是**const**或是**volatile** （或兩者），並*類別型別*是類別的名稱：

*[cv 限定詞-清單] 類別型別* **&#42; const 這**

亦即**這**永遠是 const 的指標; 它不能重新指派。  **Const**或是**volatile**成員函式宣告中所使用的限定詞適用於所指的類別執行個體**這**該函式的範圍內。

下表將進一步說明這些修飾詞的運作方式。

### <a name="semantics-of-this-modifiers"></a>修飾詞的語意

|修飾詞|意義|
|--------------|-------------|
|**const**|無法變更成員資料;無法叫用成員函式不是**const**。|
|**volatile**|每次存取成員時，就會從記憶體載入成員資料，而且會停用某些最佳化。|

它會將錯誤**const**不是成員函式的物件**const**。 同樣地，它是要傳遞錯誤**volatile**不是成員函式的物件**volatile**。

成員函式宣告為**const**無法變更成員資料 — 這類函式，在**這**指標是一個指向**const**物件。

> [!NOTE]
>  建構函式和解構函式不可以宣告為**const**或是**volatile**。 可以不過，其上叫用**const**或**volatile**物件。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)