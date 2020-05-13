---
title: CAtlAutoThreadModule 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: f4bd1071380bf3e31c69c593c5db81112fdf21de
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168302"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule 類別

這個類別會執行執行緒集區式的單元模型 COM 伺服器。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>備註

`CAtlAutoThreadModule`衍生自[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) ，並執行執行緒集區的單元模型 COM 伺服器。 `CAtlAutoThreadModule`會使用[CComApartment](../../atl/reference/ccomapartment-class.md)來管理模組中每個執行緒的公寓。

您必須在物件的類別定義中使用[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏，將[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)指定為 Class Factory。 接著，您應該加入衍生自`CAtlAutoThreadModuleT`的類別的單一實例，例如`CAtlAutoThreadModule`。 例如：

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> 這個類別會取代過時的[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)類別。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="see-also"></a>另請參閱

[CAtlAutoThreadModuleT 類別](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[IAtlAutoThreadModule 類別](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
