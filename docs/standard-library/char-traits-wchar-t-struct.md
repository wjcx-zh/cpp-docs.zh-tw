---
title: char_traits&lt;wchar_t&gt; 結構
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: 3b2504dbb124ccca7f9b27619585abb2b5795f92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219166"
---
# <a name="char_traitsltwchar_tgt-struct"></a>char_traits&lt;wchar_t&gt; 結構

類別，這是樣板結構的特製化**char_traits \<CharType> **至類型的專案 **`wchar_t`** 。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用操作此類型物件的程式庫函數 **`wchar_t`** 。

## <a name="requirements"></a>需求

**標頭：**\<string>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[char_traits 結構](../standard-library/char-traits-struct.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
