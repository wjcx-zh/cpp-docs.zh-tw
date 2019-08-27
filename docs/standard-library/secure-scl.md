---
title: _SECURE_SCL
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
ms.openlocfilehash: 1af084363fc0d6d1723a9af7b633779f92ed2b38
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450534"
---
# <a name="securescl"></a>_SECURE_SCL

已由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 所取代，這個巨集會定義是否要啟用[已檢查的迭代器](../standard-library/checked-iterators.md)。 預設會在偵錯組建中啟用已檢查的迭代器，並在零售組建中停用。

> [!IMPORTANT]
> _SECURE_SCL 宏的直接使用已被取代。 相反地, 請使用 _ITERATOR_DEBUG_LEVEL 來控制已檢查的反覆運算器設定。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>備註

若啟用了已檢查的迭代器，則使用不安全的迭代器會造成執行階段錯誤，並終止程式。 若要啟用已檢查的反覆運算器, 請將 _ITERATOR_DEBUG_LEVEL 設定為1或2。 這相當於 _SECURE_SCL 設定1或 enabled:

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

若要停用已檢查的反覆運算器, 請將 _ITERATOR_DEBUG_LEVEL 設定為0。 這相當於 _SECURE_SCL 設定為0或已停用:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

如需了解如何停用已檢查迭代器的相關警告，請參閱 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

## <a name="see-also"></a>另請參閱

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[已檢查的迭代器](../standard-library/checked-iterators.md)\
[偵錯迭代器支援](../standard-library/debug-iterator-support.md)\
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)
