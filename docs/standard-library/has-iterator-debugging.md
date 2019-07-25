---
title: _HAS_ITERATOR_DEBUGGING
ms.date: 11/04/2016
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
ms.openlocfilehash: a1e3017ed7c6def18ce02d99dc8253b69c11ab58
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448838"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

此巨集 (已被 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代) 定義偵錯組建中是否啟用迭代器偵錯功能。 預設會在「偵錯」組建中啟用迭代器偵錯功能，而在「零售」組建中停用此功能。 如需詳細資訊，請參閱[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。

> [!IMPORTANT]
> _HAS_ITERATOR_DEBUGGING 宏的直接使用已被取代。 相反地, 請使用 _ITERATOR_DEBUG_LEVEL 來控制反覆運算器的調試設定。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>備註

若要在 debug build 中啟用反覆運算器的調試功能, 請將 _ITERATOR_DEBUG_LEVEL 設定為2。 這相當於 _HAS_ITERATOR_DEBUGGING 設定1或 enabled:

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

在零售組建中, _ITERATOR_DEBUG_LEVEL 不能設定為 2 (且 _HAS_ITERATOR_DEBUGGING 不能設定為 1)。

若要在 debug build 中停用調試反覆運算器, 請將 _ITERATOR_DEBUG_LEVEL 設定為0或1。 這相當於 _HAS_ITERATOR_DEBUGGING 設定為0或已停用:

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>另請參閱

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)\
[偵錯迭代器支援](../standard-library/debug-iterator-support.md)\
[已檢查的迭代器](../standard-library/checked-iterators.md)\
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)
