---
title: char_traits&lt;wchar_t&gt; 結構
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: a2f8a882020ddb3d87436d08b3d85ea9407b1c08
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458970"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; 結構

類別, 它是樣板結構 **\<char_traits CharType**的特製化, > 至**wchar_t**類型的元素。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用程式庫函式, 此函式會操作此**wchar_t**類型的物件。

## <a name="requirements"></a>需求

**標頭：** \<string>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[char_traits 結構](../standard-library/char-traits-struct.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
