---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: ff9f19f56c8d8fdb9e469e6361a5419468fe7e67
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846403"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

[ostream](#ostream)\
[wostream](#wostream)

## <a name="ostream"></a><a name="ostream"></a> ostream

從 basic_ostream 建立型別， **`char`** 並 `char_traits` 在上特製化 **`char`** 。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_ostream](../standard-library/basic-ostream-class.md)的同義字，專為 **`char`** 具有預設字元特性之類型的元素所特製化。

## <a name="wostream"></a><a name="wostream"></a> wostream

從 basic_ostream 建立型別， **`wchar_t`** 並 `char_traits` 在上特製化 **`wchar_t`** 。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_ostream](../standard-library/basic-ostream-class.md)的同義字，專為 **`wchar_t`** 具有預設字元特性之類型的元素所特製化。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)
