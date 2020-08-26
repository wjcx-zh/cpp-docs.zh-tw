---
title: CComAutoThreadModule 類別
ms.date: 11/04/2016
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: 405b05548cda2b2d379b849d9278293b8d747d2e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833786"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule 類別

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>參數

*ThreadAllocator*<br/>
在管理執行緒選取範圍的類別。 預設值為 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|函式|描述|
|-|-|
|[CreateInstance](#createinstance)|選取執行緒，然後在相關聯的單元中建立物件。|
|[GetDefaultThreads](#getdefaultthreads)| (靜態) 會根據處理器數目，動態計算模組的執行緒數目。|
|[Init](#init)|建立模組的執行緒。|
|[鎖定](#lock)|遞增模組和目前線程上的鎖定計數。|
|[解 鎖](#unlock)|遞減模組和目前線程上的鎖定計數。|

### <a name="data-members"></a>資料成員

|資料成員|描述|
|-|-|
|[dwThreadID](#dwthreadid)|包含目前線程的識別碼。|
|[m_Allocator](#m_allocator)|管理選取的執行緒。|
|[m_nThreads](#m_nthreads)|包含模組中的執行緒數目。|
|[m_pApartments](#m_papartments)|管理模組的單元。|

## <a name="remarks"></a>備註

> [!NOTE]
> 此類別已淘汰，已由 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) 和 [CAtlModule](../../atl/reference/catlmodule-class.md) 衍生類別取代。 下列資訊適用于較舊版本的 ATL。

`CComAutoThreadModule` 衍生自 [CComModule](../../atl/reference/ccommodule-class.md) ，以針對 Exe 和 Windows 服務來執行執行緒集區、單元模型的 COM 伺服器。 `CComAutoThreadModule` 使用 [CComApartment](../../atl/reference/ccomapartment-class.md) 管理模組中每個執行緒的一個單元。

`CComAutoThreadModule`當您想要在多個單元中建立物件時，請從衍生您的模組。 您也必須在物件的類別定義中包含 [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) 宏，以將 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 指定為 class factory。

根據預設，ATL COM 程式程式 (中的 ATL 專案 Wizard Visual Studio .NET) 會從衍生您的模組 `CComModule` 。 若要使用 `CComAutoThreadModule` ，請修改類別定義。 例如：

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>規格需求

**標頭：** atlbase.h。h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a> CComAutoThreadModule：： CreateInstance

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>參數

*pfnCreateInstance*<br/>
在Creator 函式的指標。

*riid*<br/>
在所要求介面的 IID。

*ppvObj*<br/>
擴展由 *riid*識別之介面指標的指標。 如果物件不支援這個介面， *ppvObj* 會設為 Null。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

選取執行緒，然後在相關聯的單元中建立物件。

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a> CComAutoThreadModule：:d wThreadID

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
DWORD dwThreadID;
```

### <a name="remarks"></a>備註

包含目前線程的識別碼。

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a> CComAutoThreadModule：： GetDefaultThreads

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>傳回值

要在 EXE 模組中建立的執行緒數目。

### <a name="remarks"></a>備註

此靜態函式會根據處理器數目，動態計算 EXE 模組的執行緒數目上限。 根據預設，這個傳回值會傳遞至 [Init](#init) 方法來建立執行緒。

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a> CComAutoThreadModule：： Init

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>參數

*P*<br/>
在物件對應專案陣列的指標。

*h*<br/>
在傳遞給或的 `DLLMain` HINSTANCE `WinMain` 。

*plibid*<br/>
在與專案相關聯之類型程式庫的 LIBID 指標。

*nThreads*<br/>
在要建立的執行緒數目。 根據預設， *nThreads* 是 [GetDefaultThreads](#getdefaultthreads)所傳回的值。

### <a name="remarks"></a>備註

初始化資料成員，並建立 *nThreads*指定的執行緒數目。

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a> CComAutoThreadModule：： Lock

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
LONG Lock();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

### <a name="remarks"></a>備註

針對模組和目前線程的鎖定計數執行不可部分完成的增量。 `CComAutoThreadModule` 使用模組鎖定計數來判斷是否有任何用戶端存取模組。 目前線程上的鎖定計數是用於統計用途。

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a> CComAutoThreadModule：： m_Allocator

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>備註

管理執行緒選取專案的物件。 依預設， `ThreadAllocator` 類別樣板參數為 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a> CComAutoThreadModule：： m_nThreads

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
int m_nThreads;
```

### <a name="remarks"></a>備註

包含 EXE 模組中的執行緒數目。 呼叫 [Init](#init) 時， `m_nThreads` 會設定為 *nThreads* 參數值。 每個執行緒的相關聯單元都是由 [CComApartment](../../atl/reference/ccomapartment-class.md) 物件管理。

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a> CComAutoThreadModule：： m_pApartments

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>備註

指向 [CComApartment](../../atl/reference/ccomapartment-class.md) 物件的陣列，其中每個物件都會管理模組中的一個單元。 陣列中的元素數目是根據 [m_nThreads](#m_nthreads) 成員。

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a> CComAutoThreadModule：： Unlock

從 ATL 7.0， `CComAutoThreadModule` 已淘汰：如需詳細資料，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。

```
LONG Unlock();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

### <a name="remarks"></a>備註

針對模組和目前線程的鎖定計數執行不可部分完成遞減。 `CComAutoThreadModule` 使用模組鎖定計數來判斷是否有任何用戶端存取模組。 目前線程上的鎖定計數是用於統計用途。

當模組鎖定計數到達零時，可以卸載模組。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
