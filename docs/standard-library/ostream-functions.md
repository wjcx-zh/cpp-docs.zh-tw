---
title: "&lt;ostream&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 4693e33563048807cdef1c81cb4d47d4fb455137
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函式

這些是全域範本函式中定義&lt;ostream&gt;。 成員函式，請參閱[basic_ostream 類別](basic-ostream-class.md)文件。

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

*Elem*  
元素類型。

*Ostr*  
型別的物件**basic_ostream**。

*Tr*  
字元特性。

### <a name="return-value"></a>傳回值

型別的物件**basic_ostream**。

### <a name="remarks"></a>備註

操作工具呼叫*Ostr*。[put](../standard-library/basic-ostream-class.md#put)(*Ostr*。[加寬](../standard-library/basic-ios-class.md#widen)('\n'))，然後再呼叫*Ostr*。[排清](../standard-library/basic-ostream-class.md#flush)。 它會傳回*Ostr*。

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

*Elem*  
元素類型。

*Ostr*  
型別的物件**basic_ostream**。

*Tr*  
字元特性。

### <a name="return-value"></a>傳回值

型別的物件**basic_ostream**。

### <a name="remarks"></a>備註

操作工具呼叫*Ostr*。[put](../standard-library/basic-ostream-class.md#put)(*Elem*('\0'))。 它會傳回*Ostr*。

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

*Elem*  
元素類型。

*Ostr*  
型別的物件**basic_ostream**。

*Tr*  
字元特性。

### <a name="return-value"></a>傳回值

型別的物件**basic_ostream**。

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

交換兩個值**basic_ostream**物件。

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>參數

*Elem*  
元素類型。

*Tr*  
字元特性。

*left*  
左值參考**basic_ostream**物件。

*right*  
左值參考**basic_ostream**物件。

### <a name="remarks"></a>備註

樣板函式**交換**執行`left.swap(right)`。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)  
