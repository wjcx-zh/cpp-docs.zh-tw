---
title: RemoveIUnknown 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: cfcdefbb8d7cd12d2ebf99710f595fdd2fc16f76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213612"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown 類別

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>參數

*T*<br/>
類別。

## <a name="remarks"></a>備註

使類型等同于以 `IUnknown`為基礎的類型，但具有非虛擬 `QueryInterface`、`AddRef`和 `Release` 成員函式。

根據預設，COM 方法會提供虛擬 `QueryInterface`、`AddRef`和 `Release` 方法。 不過，`ComPtr` 不需要虛擬方法的額外負荷。 `RemoveIUnknown` 藉由提供私用、非虛擬 `QueryInterface`、`AddRef`和 `Release` 方法，消除了這項額外負荷。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`ReturnType`|等同于樣板參數*T*但具有非虛擬 `IUnknown` 成員之類型的同義字。|

## <a name="inheritance-hierarchy"></a>繼承階層

`T`

`RemoveIUnknown`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
