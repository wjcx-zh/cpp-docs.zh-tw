---
title: CAtlAutoThreadModuleT 類
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: e7b7a327d7c47c4472b43ed58fbe9ad0556a7620
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321547"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT 類

此類提供了實現線程池、單元模型 COM 伺服器的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>參數

*T*<br/>
將實現 COM 伺服器的類。

*執行緒定位器*<br/>
管理線程選擇的類。 預設值為[CcomSimpleThreadallocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

*dwWait*<br/>
指定超時間隔(以毫秒為單位)。 默認值為"INFINITE",這意味著該方法的超時間隔永遠不會過去。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlAutoThreadModuleT::獲取預設線程](#getdefaultthreads)|此靜態函數根據處理器數動態計算並返回 EXE 模組的最大線程數。|

## <a name="remarks"></a>備註

[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)`CAtlAutoThreadModuleT`源自 ,以便實現線程池、單元模型 COM 伺服器。 它取代了過時的類[CComAutoThreadModule。](../../atl/reference/ccomautothreadmodule-class.md)

> [!NOTE]
> 此類不應在 DLL 中使用,因為卸載 DLL 時,INFINITE 的預設*dwWait*值將導致死鎖。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::獲取預設線程

此靜態函數根據處理器數動態計算並返回 EXE 模組的最大線程數。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>傳回值

要在 EXE 模組中創建的線程數。

### <a name="remarks"></a>備註

如果要使用其他方法來計算線程數,則重寫此方法。 默認情況下,線程數基於處理器數。

## <a name="see-also"></a>另請參閱

[IAtl 自動執行緒模組類別](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[IAtl 自動執行緒模組類別](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[模組類](../../atl/atl-module-classes.md)
