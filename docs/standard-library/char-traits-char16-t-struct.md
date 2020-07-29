---
title: char_traits&lt;char16_t&gt; 結構
ms.date: 11/04/2016
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
ms.openlocfilehash: 53a77ff993d3a99cae1ec8e48a06dd7800ce74c7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230216"
---
# <a name="char_traitsltchar16_tgt-struct"></a>char_traits&lt;char16_t&gt; 結構

結構，這是樣板結構的特製化**char_traits \<CharType> **至類型的專案 **`char16_t`** 。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<char16_t>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用可操作類型物件的程式庫函數 **`char16_t`** 。

## <a name="requirements"></a>需求

**標頭：**\<string>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<string>](../standard-library/string.md)\
[char_traits 結構](../standard-library/char-traits-struct.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
