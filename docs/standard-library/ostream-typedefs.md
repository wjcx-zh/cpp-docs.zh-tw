---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: d0ceae12069712c7a124990d0f81968c21bc683a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687236"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

從 basic_ostream 建立型別，並在 char 上特製化 **，並 `char_traits`** 在**char**上特製化。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_ostream](../standard-library/basic-ostream-class.md)的同義字，專門用於具有預設字元特性之**char**類型的元素。

## <a name="wostream"></a>  wostream

從 basic_ostream 建立型別，並在 wchar_t**上特製化，並 `char_traits`** 在**wchar_t**上特製化。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_ostream](../standard-library/basic-ostream-class.md)的同義字，專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="see-also"></a>請參閱

[\<ostream>](../standard-library/ostream.md)
