---
title: '&lt;forward_list&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 78b1eaa44ed464de67d8ec45fab3241179bb94b9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240675"
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt; 函式

## <a name="swap"></a> 交換

交換兩個轉送清單的項目。

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`forward_list` 類型的物件。

*權限*\
`forward_list` 類型的物件。

### <a name="remarks"></a>備註

此範本函式會執行 `left.swap(right)`。
