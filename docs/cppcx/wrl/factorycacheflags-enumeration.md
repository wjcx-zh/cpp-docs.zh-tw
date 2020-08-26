---
title: FactoryCacheFlags 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 3381b2bcfcbf298270b547199ae614291855a2f7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843270"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags 列舉

判斷是否快取 factory 物件。

## <a name="syntax"></a>語法

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>備註

根據預設，當您建立[模組](module-class.md)物件時，會將 factory 快取原則指定為[ModuleType](moduletype-enumeration.md)範本參數。 若要覆寫此原則，請在建立 factory 物件時指定 **FactoryCacheFlags** 值。

| 原則 | 描述 |
|-|-|
|`FactoryCacheDefault`|使用物件的快取原則 `Module` 。|
|`FactoryCacheEnabled`|無論 `ModuleType` 用來建立物件的範本參數為何，都會啟用 factory 快取 `Module` 。|
|`FactoryCacheDisabled`|無論 `ModuleType` 用來建立物件的範本參數為何，都會停用 factory 快取 `Module` 。|

## <a name="requirements"></a>規格需求

**Header：** implements。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft：： WRL 命名空間](microsoft-wrl-namespace.md)
