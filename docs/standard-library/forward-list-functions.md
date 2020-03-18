---
title: '&lt;forward_list&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 78b1eaa44ed464de67d8ec45fab3241179bb94b9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419095"
---
# <a name="ltforward_listgt-functions"></a>&lt;forward_list&gt; 函式

## <a name="swap"></a>調換

交換兩個轉送清單的項目。

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`forward_list` 類型的物件。

*right*\
`forward_list` 類型的物件。

### <a name="remarks"></a>備註

此範本函式會執行 `left.swap(right)`。
