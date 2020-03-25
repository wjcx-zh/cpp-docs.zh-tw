---
title: EnableIf 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 44c6293b56e9e03c23d0d8cebf2a112e6fcf3664
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214028"
---
# <a name="enableif-structure"></a>EnableIf 結構

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>參數

*T*<br/>
類型。

*b*<br/>
布林運算式。

## <a name="remarks"></a>備註

定義第二個樣板參數所指定之類型的資料成員（如果第一個樣板參數評估為**true**）。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`type`|如果範本參數*b*評估為**true**，部分特製化會將資料成員 `type` 定義為 `T`類型。|

## <a name="inheritance-hierarchy"></a>繼承階層

`EnableIf`

## <a name="requirements"></a>需求

**標頭：** 內部。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
