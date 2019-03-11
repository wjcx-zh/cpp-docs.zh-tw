---
title: back_inserter 函式
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
ms.openlocfilehash: 82df6b06389fa9f1c3ab83fa7b1da3bab092c68d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750737"
---
# <a name="backinserter-function"></a>back_inserter 函式

傳回迭代器，用來在指定的集合結尾插入元素。

## <a name="syntax"></a>語法

```

template <typename T>
Platform::BackInsertIterator<T>
    back_inserter(IVector<T>^ v);

template<typename T>
Platform::BackInsertIterator<T>
   back_inserter(IObservableVector<T>^ v);
```

#### <a name="parameters"></a>參數

*T*<br/>
樣板類型參數。

*v*<br/>
提供存取基礎集合的介面指標。

### <a name="return-value"></a>傳回值

迭代器。

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Windows::Foundation::Collections

## <a name="see-also"></a>另請參閱

[Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)
