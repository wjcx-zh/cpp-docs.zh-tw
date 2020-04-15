---
title: '&lt;ostream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 82539a3fdadf10d340ca957756e235e8ae00b267
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373574"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>ostream

從basic_ostream建立一個類型,該類型專門用於**字元**,並且`char_traits`專門用於**字元**。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_ostream](../standard-library/basic-ostream-class.md)的同義詞,專門用於具有預設字元特徵的類型**字元**的元素。

## <a name="wostream"></a><a name="wostream"></a>沃溪

從專門用於**wchar_t**和`char_traits`專門wchar_t的basic_ostream創建**類型。**

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_ostream](../standard-library/basic-ostream-class.md)的同義詞,專門用於具有預設字元特徵的類型**wchar_t**元素。

## <a name="see-also"></a>另請參閱

[\<流>](../standard-library/ostream.md)
