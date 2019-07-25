---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 18f30a12a6f4d2b97cb5dca3ace98e6241d856a7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447171"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

從 basic_ostream 建立類型, 並在**char**上特製化`char_traits`並在**char**上特製化。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>備註

此類型與範本類別[basic_ostream](../standard-library/basic-ostream-class.md)同義, 專門用於具有預設字元特性之**char**類型的元素。

## <a name="wostream"></a>  wostream

從 basic_ostream 建立的類型是在**wchar_t**上特製化`char_traits` , 並在**wchar_t**上特製化。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_ostream](../standard-library/basic-ostream-class.md)同義, 專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)
