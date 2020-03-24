---
title: FactoryCacheFlags 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 250c8c8e7ade72bd1a9cd63f0b515774058f0723
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214002"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags 列舉

判斷是否快取 factory 物件。

## <a name="syntax"></a>語法

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>備註

根據預設，當您建立[模組](module-class.md)物件時，factory 快取原則會指定為[ModuleType](moduletype-enumeration.md)範本參數。 若要覆寫此原則，當您建立 factory 物件時，請指定**FactoryCacheFlags**值。

|||
|-|-|
|`FactoryCacheDefault`|會使用 `Module` 物件的快取原則。|
|`FactoryCacheEnabled`|啟用 factory 快取，而不論用來建立 `Module` 物件的 `ModuleType` 範本參數。|
|`FactoryCacheDisabled`|不論用來建立 `Module` 物件的 `ModuleType` 範本參數為何，都會停用 factory 快取。|

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)
