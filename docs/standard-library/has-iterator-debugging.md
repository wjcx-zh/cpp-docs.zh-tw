---
title: _HAS_ITERATOR_DEBUGGING | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _HAS_ITERATOR_DEBUGGING
dev_langs:
- C++
helpviewer_keywords:
- _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81f0509c6230020b586c0341e1de608981c05476
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965974"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

此巨集 (已被 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代) 定義偵錯組建中是否啟用迭代器偵錯功能。 預設會在「偵錯」組建中啟用迭代器偵錯功能，而在「零售」組建中停用此功能。 如需詳細資訊，請參閱[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。

> [!IMPORTANT]
> 直接使用 _HAS_ITERATOR_DEBUGGING 巨集已被取代。 請改用 _ITERATOR_DEBUG_LEVEL 來控制迭代器偵錯設定。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>備註

若要啟用偵錯組建中的偵錯迭代器，設定為 2 的 _ITERATOR_DEBUG_LEVEL。 這相當於將 _HAS_ITERATOR_DEBUGGING 如果設定為 1，或啟用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

_ITERATOR_DEBUG_LEVEL 不能設定為 2 （和 _HAS_ITERATOR_DEBUGGING 無法設為 1） 偵錯組建中。

若要停用偵錯組建中的偵錯迭代器，請設定 _ITERATOR_DEBUG_LEVEL 為 0 或 1。 這相當於將 _HAS_ITERATOR_DEBUGGING 若設定為 0，或停用：

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>另請參閱

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
