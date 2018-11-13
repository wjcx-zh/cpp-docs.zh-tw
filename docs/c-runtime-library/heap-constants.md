---
title: 堆積常數
ms.date: 11/04/2016
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
ms.openlocfilehash: 9419ae53cd04812f45f5feeee73fa0f89c408a0c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522294"
---
# <a name="heap-constants"></a>堆積常數

## <a name="syntax"></a>語法

```

#include <malloc.h>
```

## <a name="remarks"></a>備註

這些常數會提供指示堆積狀態的傳回值。

|常數|意義|
|--------------|-------------|
|`_HEAPBADBEGIN`|找不到初始標頭資訊，或標頭資訊不正確。|
|`_HEAPBADNODE`|找到不正確的節點，或堆積已損毀。|
|`_HEAPBADPTR`|**_HEAPINFO** 結構的 **_pentry** 欄位未包含堆積的有效指標 (僅限 `_heapwalk` 常式)。|
|`_HEAPEMPTY`|堆積尚未初始化。|
|`_HEAPEND`|已成功到達堆積的結尾 (僅限 `_heapwalk` 常式)。|
|`_HEAPOK`|堆積一致 (僅限 `_heapset` 和 `_heapchk` 常式)。 目前為止沒有錯誤；**_HEAPINFO** 結構包含下一個項目的相關資訊 (僅限 `_heapwalk` 常式)。|

## <a name="see-also"></a>請參閱

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[全域常數](../c-runtime-library/global-constants.md)