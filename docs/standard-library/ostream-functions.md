---
title: '&lt;ostream&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: d30ad23956c978ee47ef447463a0d5422a94d4b9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962318"
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

*Elem*項目類型。

*Ostr*類型的物件**basic_ostream**。

*Tr*字元特性。

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

*Elem*項目類型。

*Ostr*型別的物件`basic_ostream`。

*Tr*字元特性。

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

*Elem*項目類型。

*Ostr*型別的物件`basic_ostream`。

*Tr*字元特性。

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

*Elem*項目類型。

*Tr*字元特性。

*左*左值參考`basic_ostream`物件。

*右*左值參考`basic_ostream`物件。

### <a name="remarks"></a>備註

樣板函式 `swap` 會執行 `left.swap(right)`。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)
