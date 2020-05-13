---
title: '&lt;istream&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 3b9521fde1b5a03389bfc1ad3e35fa407d9d6ac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363031"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 運算子

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>算子&gt;&gt;

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

*Ch*\
字元。

*Istr*\
資料流。

*Str*\
字串。

*瓦爾*\
類型。

### <a name="return-value"></a>傳回值

資料流

### <a name="remarks"></a>備註

`basic_istream` 類別也會定義數個擷取運算子。 如需詳細資訊，請參閱 [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt)。

函數範本:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

提取到`N - 1`元素,並將它們存儲在陣列中,從*str*開始。 如果`Istr.`[寬度](../standard-library/ios-base-class.md#width)大於零,則*N*`Istr.width`是 ;否則,它是可以聲明的最大`Elem`陣列的大小。 該函數始終在它存儲`Elem()`的任何提取元素后存儲該值。 提取在檔案末尾的早期停止,在值`Elem(0)`(未提取)的字元上,或 ws 將丟棄的任何元素(未提取)[ws](../standard-library/istream-functions.md#ws)上停止。 如果函數不提取任何元素,它將呼叫`Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情況下,它呼叫`Istr.width(0)`並傳回*Istr*。

**安全說明**從輸入流中提取的 null 連接端字串不得超過目標緩衝區*str*的大小。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](/windows/win32/SecBP/avoiding-buffer-overruns)。

函數範本:

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

提取元素(如果可能)並將其存儲在*Ch*中。 否則,它將呼叫`is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情況下,它傳回*Istr*。

函數範本:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

傳回 `Istr >> ( char * ) str`。

函數範本:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

傳回 `Istr >> ( char& ) Ch`。

函數範本:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

傳回 `Istr >> ( char * ) str`。

函數範本:

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

傳回 `Istr >> ( char& ) Ch`。

函數範本:

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

返回`Istr >> val`(並將 rvalue 引用`Istr`轉換為進程中的 lvalue)。

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
