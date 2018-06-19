---
title: '&lt;forward_list&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 4585b1998309d7c17c8f02e2b0597cb595b2c4a3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844838"
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt; 函式

||
|-|
|[swap](#swap)|

## <a name="swap"></a>  swap

交換兩個轉送清單的項目。

```cpp
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`left`|`forward_list` 類型的物件。|
|`right`|`forward_list` 類型的物件。|

### <a name="remarks"></a>備註

此範本函式會執行 `left.swap(right)`。

## <a name="see-also"></a>另請參閱

[<forward_list>](../standard-library/forward-list.md)<br/>
