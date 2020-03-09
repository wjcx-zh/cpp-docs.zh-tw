---
title: '&lt;清單&gt; 函數 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874415"
---
# <a name="ltlistgt-functions"></a>&lt;清單&gt; 函數

## <a name="swap"></a>調換

交換兩個清單的項目。

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>參數

*左方*\
`list` 類型的物件。

*right*\
`list` 類型的物件。

### <a name="remarks"></a>備註

此範本函式會執行 `left.swap(right)`。
