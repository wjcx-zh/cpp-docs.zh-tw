---
title: '&lt;istream&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: c10692194c80051b10ecbe776c7d23a03860d508
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447790"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 運算子

## <a name="op_gt_gt"></a> operator&gt;&gt;

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

*頻道*\
字元。

*Istr*\
資料流。

*str*\
字串。

*初始值*\
類型。

### <a name="return-value"></a>傳回值

資料流

### <a name="remarks"></a>備註

`basic_istream` 類別也會定義數個擷取運算子。 如需詳細資訊，請參閱 [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt)。

範本函式：

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

最多會擷取 *N* - 1 個元素，並將其儲存在開頭為 _ *Str* 的陣列中。 如果 `Istr`. [width](../standard-library/ios-base-class.md#width) 大於零，則 *N* 為 `Istr`. **width**;否則, 它是可以宣告的最大陣列`Elem`的大小。 函式一律會將值`Elem()`儲存在它所儲存的任何已解壓縮的元素之後。 不論是在檔案結尾、在值為 **Elem**(0) (不擷取的值) 的字元上，還是在 [ws](../standard-library/istream-functions.md#ws) 會捨棄的任何元素 (不擷取的元素) 上，都會提前停止擷取。 如果此函式未擷取任何元素，則會呼叫 `Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**)。 在任何情況下，它都會呼叫 `Istr`. **寬度**(0), 並傳回*Istr*。

**安全性注意事項**從輸入資料流程解壓縮的以 null 結束的字串不得超過目的緩衝區*str*的大小。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/desktop/SecBP/avoiding-buffer-overruns)。

範本函式：

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

如果可能的話, 請將專案解壓縮, 並將它儲存在*Ch*中。 否則會呼叫 **is**。 [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 在任何情況下, 它會傳回*Istr*。

範本函式：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

傳回 `Istr >> ( char * ) str`。

範本函式：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

傳回 `Istr >> ( char& ) Ch`。

範本函式：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

傳回 `Istr >> ( char * ) str`。

範本函式：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

傳回 `Istr >> ( char& ) Ch`。

範本函式：

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

傳回 (並將右值`Istr`參考轉換為進程中的左值)。 `Istr >> val`

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

## <a name="see-also"></a>另請參閱

[\<istream>](../standard-library/istream.md)
