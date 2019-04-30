---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 02936fdfc990ea65a99b2875cf7f482eb2ce4ebe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370868"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

特製化的 basic_ostream 從建立類型**char**並`char_traits`特殊化**char**。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_ostream](../standard-library/basic-ostream-class.md)類型的項目所特製化**char**具有預設字元特性。

## <a name="wostream"></a>  wostream

特製化的 basic_ostream 從建立類型**wchar_t**並`char_traits`特殊化**wchar_t**。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_ostream](../standard-library/basic-ostream-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)<br/>
