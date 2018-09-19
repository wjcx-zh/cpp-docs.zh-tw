---
title: CAtlAutoThreadModuleT 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46198390ce25cb655b94c0ca4769321fc3e9362d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099694"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT 類別

這個類別提供方法實作在執行緒集區的 apartment model COM 伺服器。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>參數

*T*<br/>
類別會實作 COM 伺服器。

*ThreadAllocator*<br/>
管理執行緒的選取項目類別。 預設值是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

*dwWait*<br/>
指定逾時間隔，以毫秒為單位。 預設值為 INFINITE，這表示永遠不會超過方法的逾時間隔。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|此靜態函式會動態計算，並傳回 EXE 模組，根據處理器數目的執行緒數目上限。|

## <a name="remarks"></a>備註

此類別[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)衍生自`CAtlAutoThreadModuleT`才能實作在執行緒集區的 apartment model COM 伺服器。 它取代了過時的類別[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。

> [!NOTE]
>  這個類別不應在 DLL 中，為預設值*dwWait*的無限值在卸載 DLL 時，會造成死結。

## <a name="inheritance-hierarchy"></a>繼承階層

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="getdefaultthreads"></a>  CAtlAutoThreadModuleT::GetDefaultThreads

此靜態函式會動態計算，並傳回 EXE 模組，根據處理器數目的執行緒數目上限。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>傳回值

在 EXE 模組中建立的執行緒數目。

### <a name="remarks"></a>備註

如果您想要使用不同的方法來計算執行緒數目，請覆寫這個方法。 根據預設，執行緒數目根據處理器數目。

## <a name="see-also"></a>另請參閱

[IAtlAutoThreadModule 類別](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule 類別](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
