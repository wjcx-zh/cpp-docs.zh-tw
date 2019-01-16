---
title: FactoryCacheFlags 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 6fecacd6038d1c41e57515307c1b810d0623d16f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336148"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags 列舉

決定是否要快取 factory 物件。

## <a name="syntax"></a>語法

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>備註

根據預設，處理站快取原則指[ModuleType](moduletype-enumeration.md)當您建立的範本參數[模組](module-class.md)物件。 若要覆寫此原則，請指定**FactoryCacheFlags**時建立的 factory 物件的值。

|||
|-|-|
|`FactoryCacheDefault`|快取原則的`Module`物件使用。|
|`FactoryCacheEnabled`|可讓處理站快取，不論`ModuleType`樣板參數，用來建立`Module`物件。|
|`FactoryCacheDisabled`|停用處理站快取，不論`ModuleType`樣板參數，用來建立`Module`物件。|

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft:: wrl

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)