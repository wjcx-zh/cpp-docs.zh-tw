---
title: to_vector 函式
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
ms.openlocfilehash: 4fa4e9c620519cc6bb2f96d346ded88b6cc826ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404620"
---
# <a name="tovector-function"></a>to_vector 函式

傳回 `std::vector` ，其值與指定的 IVector 或 IVectorView 參數的基礎集合相同。

## <a name="syntax"></a>語法

```
template <typename T>
inline ::std::vector<T> to_vector(IVector<T>^ v);

template <typename T>
inline ::std::vector<T> to_vector(IVectorView<T>^ v);
```

#### <a name="parameters"></a>參數

*T*<br/>
樣板類型參數。

*v*<br/>
IVector 或 IVectorView 介面，提供對基礎 Vector 或 VectorView 物件的存取。

### <a name="return-value"></a>傳回值

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Windows::Foundation::Collections

## <a name="see-also"></a>另請參閱

[Windows::Foundation::Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)
