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
ms.openlocfilehash: 8d93e46b0323058d93c6d0bd8c1ee566998aef61
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874792"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函式

這些是 &lt;ostream&gt;中定義的全域範本函數。 如需成員函式，請參閱[Basic_ostream 類別](basic-ostream-class.md)檔。

||||
|-|-|-|
|[endl](#endl)|[ends](#ends)|[flush](#flush)|
|[swap](#swap)|

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

操作工具會呼叫*Ostr*。[put](../standard-library/basic-ostream-class.md#put)（*Ostr*。[加寬](../standard-library/basic-ios-class.md#widen)（' \n '）），然後呼叫*Ostr*。[flush](../standard-library/basic-ostream-class.md#flush)。 它會傳回*Ostr*。

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

操作工具會呼叫*Ostr*。[put](../standard-library/basic-ostream-class.md#put)（*Elem*（' \ 0 '））。 它會傳回*Ostr*。

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

## <a name="flush"></a>排清

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

操作工具會呼叫*Ostr*。[flush](../standard-library/basic-ostream-class.md#flush)。 它會傳回*Ostr*。

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

## <a name="swap"></a>交換

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

*左方*\
`basic_ostream` 物件的 lvalue 參考。

*right*\
`basic_ostream` 物件的 lvalue 參考。

### <a name="remarks"></a>備註

樣板函式 `swap` 會執行 `left.swap(right)`。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)
