---
title: '&lt;ostream&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 4db966797202b16911aa67b6fda7c81785d98166
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842633"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函式

這些是 ostream 中定義的全域範本 &lt; 函數 &gt; 。 如需成員函式的詳細說明，請參閱 [Basic_ostream 類別](basic-ostream-class.md) 檔。

[endl](#endl)\
[結束](#ends)\
[沖洗](#flush)\
[交換](#swap)

## <a name="endl"></a>endl

結束一行並清除緩衝區。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>參數

*Elem*\
元素類型。

*Ostr*\
**Basic_ostream**類型的物件。

*Tr*\
字元特性。

### <a name="return-value"></a>傳回值

**Basic_ostream**類型的物件。

### <a name="remarks"></a>備註

操作工具會呼叫 *Ostr*。[put](../standard-library/basic-ostream-class.md#put) (*Ostr*。[擴大](../standard-library/basic-ios-class.md#widen) ( ' \n ' ) # A3，然後呼叫 *Ostr*。[flush](../standard-library/basic-ostream-class.md#flush)： 它會傳回 *Ostr*。

### <a name="example"></a>範例

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>結尾

結束字串。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>參數

*Elem*\
元素類型。

*Ostr*\
`basic_ostream` 類型的物件。

*Tr*\
字元特性。

### <a name="return-value"></a>傳回值

`basic_ostream` 類型的物件。

### <a name="remarks"></a>備註

操作工具會呼叫 *Ostr*。[將](../standard-library/basic-ostream-class.md#put) (*Elem* ( ' \ 0 ' ) # A3。 它會傳回 *Ostr*。

### <a name="example"></a>範例

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>flush

清除緩衝區。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>參數

*Elem*\
元素類型。

*Ostr*\
`basic_ostream` 類型的物件。

*Tr*\
字元特性。

### <a name="return-value"></a>傳回值

`basic_ostream` 類型的物件。

### <a name="remarks"></a>備註

操作工具會呼叫 *Ostr*。[flush](../standard-library/basic-ostream-class.md#flush)： 它會傳回 *Ostr*。

### <a name="example"></a>範例

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>swap

交換兩個 `basic_ostream` 物件的值。

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>參數

*Elem*\
元素類型。

*Tr*\
字元特性。

*離開*\
`basic_ostream` 物件的 lvalue 參考。

*對*\
`basic_ostream` 物件的 lvalue 參考。

### <a name="remarks"></a>備註

樣板函式 `swap` 會執行 `left.swap(right)`。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)
