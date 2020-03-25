---
title: InterfaceList 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 7fd06f71bc4d8097366dc0e87d7ff92c5a12a790
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213859"
---
# <a name="interfacelist-structure"></a>InterfaceList 結構

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>參數

*T*<br/>
介面名稱;遞迴清單中的第一個介面。

*U*<br/>
介面名稱;遞迴清單中的其餘介面。

## <a name="remarks"></a>備註

用來建立介面的遞迴清單。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`FirstT`|樣板參數*T*的同義字。|
|`RestT`|樣板參數*U*的同義字。|

## <a name="inheritance-hierarchy"></a>繼承階層

`InterfaceList`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)
