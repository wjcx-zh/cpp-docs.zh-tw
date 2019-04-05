---
title: ActivatableClass 巨集
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: 7d38db9e7d3fa94c89195b6379e14692f26f7ee5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037590"
---
# <a name="activatableclass-macros"></a>ActivatableClass 巨集

擴展內部快取，其中包含可以建立指定類別的執行個體的處理站。

## <a name="syntax"></a>語法

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>參數

*className*<br/>
要建立之類別的名稱。

*處理站*<br/>
將會建立指定類別的執行個體的 factory。

*serverName*<br/>
指定模組中的處理站的子集的名稱。

## <a name="remarks"></a>備註

請勿使用這些巨集與傳統 COM 除非您使用`#undef`指示詞，以確保`__WRL_WINRT_STRICT__`會移除巨集定義。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft:: wrl

## <a name="see-also"></a>另請參閱

[Module 類別](module-class.md)