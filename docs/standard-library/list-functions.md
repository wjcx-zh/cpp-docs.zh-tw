---
title: '&lt;清單&gt;函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269020"
---
# <a name="ltlistgt-functions"></a>&lt;清單&gt;函式

## <a name="swap"></a> 交換

交換兩個清單的項目。

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>參數

*左邊*\
`list` 類型的物件。

*權限*\
`list` 類型的物件。

### <a name="remarks"></a>備註

此範本函式會執行 `left.swap(right)`。
