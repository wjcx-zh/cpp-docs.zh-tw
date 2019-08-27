---
title: '&lt;istream&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 864854fa2697a76c2f3476bcb050d5f5d084dc9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458753"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

在`basic_iostream` **char**上特製化的類型。

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>備註

此類型與範本類別[basic_iostream](../standard-library/basic-iostream-class.md)同義, 專門用於具有預設字元特性之**char**類型的元素。

## <a name="istream"></a>  istream

在`basic_istream` **char**上特製化的類型。

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>備註

此類型與範本類別[basic_istream](../standard-library/basic-istream-class.md)同義, 專門用於具有預設字元特性之**char**類型的元素。

## <a name="wiostream"></a>  wiostream

在`basic_iostream` **wchar_t**上特製化的類型。

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_iostream](../standard-library/basic-iostream-class.md)同義, 專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="wistream"></a>  wistream

在`basic_istream` **wchar_t**上特製化的類型。

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_istream](../standard-library/basic-istream-class.md)同義, 專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="see-also"></a>另請參閱

[\<istream>](../standard-library/istream.md)
