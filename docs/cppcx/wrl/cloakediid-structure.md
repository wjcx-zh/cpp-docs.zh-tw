---
title: CloakedIid 結構
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 1cc9e79384bbf4aae44199c2f35331e3afd8fd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214106"
---
# <a name="cloakediid-structure"></a>CloakedIid 結構

指出在 IID 清單中無法存取指定介面的 `RuntimeClass`、`Implements` 和 `ChainInterfaces` 範本。

## <a name="syntax"></a>語法

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>參數

*T*<br/>
隱藏的介面（已遮蓋）。

## <a name="remarks"></a>備註

以下是使用**CloakedIid**的範例： `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`。

## <a name="inheritance-hierarchy"></a>繼承階層

`T`

`CloakedIid`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)
