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
ms.openlocfilehash: 7bc3d789d6c0d304aa170d59dff23a97a67061d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214259"
---
# <a name="activatableclass-macros"></a>ActivatableClass 巨集

填入內部快取，其中包含可建立指定類別之實例的 factory。

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

*名*<br/>
要建立的類別名稱。

*工廠*<br/>
將建立指定類別之實例的 Factory。

*serverName*<br/>
指定模組中工廠子集的名稱。

## <a name="remarks"></a>備註

除非您使用 `#undef` 指示詞來確保移除 `__WRL_WINRT_STRICT__` 巨集定義，否則請不要將這些宏與傳統 COM 搭配使用。

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Module 類別](module-class.md)
