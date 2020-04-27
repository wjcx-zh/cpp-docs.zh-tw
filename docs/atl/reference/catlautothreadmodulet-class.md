---
title: CAtlAutoThreadModuleT 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: 7308e3a51c531fbe942e2df326c03273eeb326e2
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168719"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT 類別

這個類別會提供方法來執行執行緒集區式的單元模型 COM 伺服器。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

### <a name="parameters"></a>參數

*T*<br/>
將會執行 COM 伺服器的類別。

*ThreadAllocator*<br/>
管理執行緒選取範圍的類別。 預設值為[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

*dwWait*<br/>
指定逾時間隔（以毫秒為單位）。 預設值是無限的，這表示方法的逾時間隔永遠不會過期。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|這個靜態函式會根據處理器數目，動態計算並傳回 EXE 模組的最大執行緒數目。|

## <a name="remarks"></a>備註

類別[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)衍生自`CAtlAutoThreadModuleT` ，以便執行執行緒集區的單元模型 COM 伺服器。 它會取代過時的類別[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。

> [!NOTE]
> 這個類別不應在 DLL 中使用，因為在卸載 DLL 時，無限的預設*dwWait*值會造成鎖死。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads

這個靜態函式會根據處理器數目，動態計算並傳回 EXE 模組的最大執行緒數目。

```cpp
static int GetDefaultThreads();
```

### <a name="return-value"></a>傳回值

要在 EXE 模組中建立的執行緒數目。

### <a name="remarks"></a>備註

如果您想要使用不同的方法來計算執行緒數目，請覆寫這個方法。 根據預設，執行緒的數目是以處理器數目為基礎。

## <a name="see-also"></a>另請參閱

[IAtlAutoThreadModule 類別](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule 類別](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
