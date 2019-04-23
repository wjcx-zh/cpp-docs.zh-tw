---
title: RemoveIUnknown 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
ms.openlocfilehash: 3b54f6a3072d82d40db4ac698503f0939e745472
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036769"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
struct RemoveIUnknown;

template <typename T>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>參數

*T*<br/>
類別中。

## <a name="remarks"></a>備註

建立類型，相當於`IUnknown`為基礎的類型，但有非虛擬`QueryInterface`， `AddRef`，和`Release`成員函式。

根據預設，COM 方法提供虛擬`QueryInterface`， `AddRef`，和`Release`方法。 不過，`ComPtr`不需要虛擬方法的額外負荷。 `RemoveIUnknown` 藉由提供私用、 非虛擬消除該額外負荷`QueryInterface`， `AddRef`，和`Release`方法。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`ReturnType`|相當於範本參數類型的同義字*T*但有非虛擬`IUnknown`成員。|

## <a name="inheritance-hierarchy"></a>繼承階層

`T`

`RemoveIUnknown`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)