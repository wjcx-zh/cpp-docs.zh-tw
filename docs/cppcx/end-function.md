---
title: end 函式
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::end
helpviewer_keywords:
- end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
ms.openlocfilehash: 83e575ae29ca083642e1cf6296d6ffc8a989c316
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445986"
---
# <a name="end-function"></a>end 函式

傳回迭代器，指向指定的介面參數所存取之集合的結尾之外。

## <a name="syntax"></a>語法

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    end(
        IVector<T>^ v       );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    end(
        IVectorView<T>^ v
       );
template <typename T>
    ::Platform::Collections::InputIterator<T>
    end(
        IIterable<T>^ i
       );
```

#### <a name="parameters"></a>參數

*T*<br/>
樣板類型參數。

*v*<br/>
向量的集合\<T > 或 VectorView\<T > 物件存取的 IVector\<T >，或 IVectorView\<T > 介面。

*i*<br/>
Iiterable<t> Windows 執行階段的集合物件所存取 IIterable\<T > 介面。

### <a name="return-value"></a>傳回值

指向集合結尾之外的迭代器。

### <a name="remarks"></a>備註

前兩個樣板函式會傳回迭代器，第三個樣板函式會傳回輸入迭代器。

[傳回的](../cppcx/platform-collections-vectorviewiterator-class.md) Platform::Collections::VectorViewIterator `end` 物件是會儲存 `VectorProxy<T>`類型項目的 Proxy 迭代器。 不過，對使用者程式碼來說，Proxy 物件永遠都像是不存在一樣。 如需詳細資訊，請參閱 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="requirements"></a>需求

**標頭：** collection.h

**命名空間：** Windows::Foundation::Collections

## <a name="see-also"></a>另請參閱

[Collections 命名空間](../cppcx/windows-foundation-collections-namespace-c-cx.md)