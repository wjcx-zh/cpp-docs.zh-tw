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
ms.openlocfilehash: fa498f4acbb151eab4321bcddc6af027ee266237
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636770"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函式

這些是定義的通用範本函式&lt;ostream&gt;。 成員函式，請參閱[basic_ostream 類別](basic-ostream-class.md)文件。

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

*Elem*<br/>
元素類型。

*Ostr*<br/>
型別的物件**basic_ostream**。

*Tr*<br/>
字元特性。

### <a name="return-value"></a>傳回值

型別的物件**basic_ostream**。

### <a name="remarks"></a>備註

操作工具呼叫*Ostr*。[放](../standard-library/basic-ostream-class.md#put)(*Ostr*。[widen](../standard-library/basic-ios-class.md#widen)('\n'))，然後呼叫*Ostr*。[排清](../standard-library/basic-ostream-class.md#flush)。 它會傳回*Ostr*。

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

*Elem*<br/>
元素類型。

*Ostr*<br/>
`basic_ostream` 類型的物件。

*Tr*<br/>
字元特性。

### <a name="return-value"></a>傳回值

`basic_ostream` 類型的物件。

### <a name="remarks"></a>備註

操作工具呼叫*Ostr*。[放](../standard-library/basic-ostream-class.md#put)(*Elem*('\0'))。 它會傳回*Ostr*。

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

*Elem*<br/>
元素類型。

*Ostr*<br/>
`basic_ostream` 類型的物件。

*Tr*<br/>
字元特性。

### <a name="return-value"></a>傳回值

`basic_ostream` 類型的物件。

### <a name="remarks"></a>備註

操作工具呼叫*Ostr*。[排清](../standard-library/basic-ostream-class.md#flush)。 它會傳回*Ostr*。

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

*Elem*<br/>
元素類型。

*Tr*<br/>
字元特性。

*left*<br/>
`basic_ostream` 物件的 lvalue 參考。

*right*<br/>
`basic_ostream` 物件的 lvalue 參考。

### <a name="remarks"></a>備註

樣板函式 `swap` 會執行 `left.swap(right)`。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)
