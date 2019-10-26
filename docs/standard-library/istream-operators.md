---
title: '&lt;istream&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 5ac5c61488530f99cdad38ca1bfca365b6ac0f8c
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890167"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 運算子

## <a name="op_gt_gt"></a>  運算子&gt;&gt;

從資料流中擷取字元和字串。

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>參數

*Ch* \
字元。

*Istr*\
資料流。

*str* \
字串。

*val* \
類型。

### <a name="return-value"></a>傳回值

資料流

### <a name="remarks"></a>備註

`basic_istream` 類別也會定義數個擷取運算子。 如需詳細資訊，請參閱 [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt)。

函數範本：

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

會解壓縮到 `N - 1` 的元素，並將它們儲存在以*str*起始的陣列中。 如果 `Istr.`[寬度](../standard-library/ios-base-class.md#width)大於零，則會 `Istr.width`*N* ;否則，它是可以宣告的最大 `Elem` 陣列的大小。 函式一律會將值儲存在所儲存的任何已解壓縮元素之後 `Elem()`。 解壓縮會在檔案結尾、值 `Elem(0)` 的字元（未解壓縮），或任何將由[ws](../standard-library/istream-functions.md#ws)捨棄的元素（未解壓縮）上及早停止。 如果函式未解壓縮任何元素，則會呼叫 `Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情況下，它都會呼叫 `Istr.width(0)` 並傳回*Istr*。

**安全性注意事項**從輸入資料流程解壓縮的以 null 結束的字串不得超過目的緩衝區*str*的大小。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

函數範本：

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

盡可能解壓縮專案，並將它儲存在*Ch*中。 否則，它會呼叫 `is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情況下，它會傳回*Istr*。

函數範本：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

傳回 `Istr >> ( char * ) str`。

函數範本：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

傳回 `Istr >> ( char& ) Ch`。

函數範本：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

傳回 `Istr >> ( char * ) str`。

函數範本：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

傳回 `Istr >> ( char& ) Ch`。

函數範本：

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

傳回 `Istr >> val` （並將右值參考轉換成進程中的左值） `Istr`。

### <a name="example"></a>範例

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>請參閱

[\<istream>](../standard-library/istream.md)
