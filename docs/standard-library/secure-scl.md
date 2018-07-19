---
title: _SECURE_SCL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _SECURE_SCL
dev_langs:
- C++
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6a9fa05a4cb8c421a511a30fd62310d69003fde
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966429"
---
# <a name="securescl"></a>_SECURE_SCL

已由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 所取代，這個巨集會定義是否要啟用[已檢查的迭代器](../standard-library/checked-iterators.md)。 預設會在偵錯組建中啟用已檢查的迭代器，並在零售組建中停用。

> [!IMPORTANT]
> 直接使用 _SECURE_SCL 巨集已被取代。 請改用 _ITERATOR_DEBUG_LEVEL 控制檢查迭代器設定。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>備註

若啟用了已檢查的迭代器，則使用不安全的迭代器會造成執行階段錯誤，並終止程式。 若要啟用已檢查的迭代器，設定為 1 或 2 的 _ITERATOR_DEBUG_LEVEL。 這相當於 _SECURE_SCL 如果設定為 1，或啟用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 1
```

若要停用已檢查的迭代器，請設定 _ITERATOR_DEBUG_LEVEL 設為 0。 這相當於 _SECURE_SCL 若設定為 0，或停用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

如需了解如何停用已檢查迭代器的相關警告，請參閱 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

## <a name="see-also"></a>另請參閱

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
