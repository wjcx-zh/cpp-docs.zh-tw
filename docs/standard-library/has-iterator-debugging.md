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
ms.openlocfilehash: ab2de61df8c4e22b1955e9fd4798b5128a3e12be
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845891"
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING

此巨集 (已被 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代) 定義偵錯組建中是否啟用迭代器偵錯功能。 預設會在「偵錯」組建中啟用迭代器偵錯功能，而在「零售」組建中停用此功能。 如需詳細資訊，請參閱[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。

> [!IMPORTANT]
> 目前已不再直接使用 `_HAS_ITERATOR_DEBUGGING` 巨集。 請改用 `_ITERATOR_DEBUG_LEVEL` 來控制迭代器偵錯設定。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。

## <a name="remarks"></a>備註

若要在偵錯組建中啟用迭代器偵錯功能，請將 `_ITERATOR_DEBUG_LEVEL` 設定為 2。 這等同於將 `_HAS_ITERATOR_DEBUGGING` 設定為 1 或 enabled：

```cpp
#define _ITERATOR_DEBUG_LEVEL 2
```

在偵錯組建中，`_ITERATOR_DEBUG_LEVEL` 不能設定為 2 (且 `_HAS_ITERATOR_DEBUGGING` 不能設定為 1)。

若要在偵錯組建中停用偵錯迭代器，請將 `_ITERATOR_DEBUG_LEVEL` 設定為 0 或 1。 這等同於將 `_HAS_ITERATOR_DEBUGGING` 設為 0 或 disabled：

```cpp
#define _ITERATOR_DEBUG_LEVEL 0
```

## <a name="see-also"></a>另請參閱

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
