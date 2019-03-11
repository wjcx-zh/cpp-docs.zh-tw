---
title: begin 函式
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: 1b95e4d32321aadf7de65ecb25109fbecd9eb614
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741402"
---
# <a name="begin-function"></a>begin 函式

傳回迭代器，指向指定的介面參數所存取之集合的開頭。

## <a name="syntax"></a>語法

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    begin(
          IVector<T>^ v         );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    begin(
          IVectorView<T>^ v
         );

template <typename T>
    ::Platform::Collections::InputIterator<T>
    begin(
          IIterable<T>^ i         );
```

#### <a name="parameters"></a>參數

*T*<br/>
樣板類型參數。

*v*<br/>
向量的集合\<T > 或 VectorView\<T > 物件存取的 IVector\<T > 或 IVectorView\<T > 介面。

*i*<br/>
任意物件集合的 Windows 執行階段存取的 IIterable\<T > 介面。

### <a name="return-value"></a>傳回值

指向集合開頭的迭代器。

### <a name="remarks"></a>備註

前兩個樣板函式會傳回迭代器，第三個樣板函式會傳回輸入迭代器。

VectorIterator 開始所傳回的物件會儲存類型 VectorProxy 項目的 proxy 迭代器\<T >。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Windows::Foundation::Collections

## <a name="see-also"></a>另請參閱

[Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)
