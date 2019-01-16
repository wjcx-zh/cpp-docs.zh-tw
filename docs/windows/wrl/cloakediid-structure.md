---
title: CloakedIid 結構
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: a47b9e5fdb4a6e7f49b9704244b4e62e3647a04e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335722"
---
# <a name="cloakediid-structure"></a>CloakedIid 結構

若要指出`RuntimeClass`，`Implements`和`ChainInterfaces`範本指定的介面不是在 IID 清單中存取。

## <a name="syntax"></a>語法

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>參數

*T*<br/>
介面隱藏的 （「 隱匿 」）。

## <a name="remarks"></a>備註

以下是如何的範例**CloakedIid**使用： `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`。

## <a name="inheritance-hierarchy"></a>繼承階層

`T`

`CloakedIid`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft:: wrl

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)