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
ms.openlocfilehash: 9b0fa685bf9a7de94b158bd62b00161c1b58562d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866169"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule 類別

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>參數

*ThreadAllocator*<br/>
在管理執行緒選取範圍的類別。 預設值為[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CreateInstance](#createinstance)|選取執行緒，然後在相關聯的單元中建立物件。|
|[GetDefaultThreads](#getdefaultthreads)|靜止根據處理器數目，動態計算模組的執行緒數目。|
|[Init](#init)|建立模組的執行緒。|
|[狀](#lock)|遞增模組和目前線程上的鎖定計數。|
|[解除鎖定](#unlock)|遞減模組和目前線程上的鎖定計數。|

### <a name="data-members"></a>資料成員

### <a name="data-members"></a>資料成員

|||
|-|-|
|[dwThreadID](#dwthreadid)|包含目前線程的識別碼。|
|[m_Allocator](#m_allocator)|管理執行緒選取專案。|
|[m_nThreads](#m_nthreads)|包含模組中的執行緒數目。|
|[m_pApartments](#m_papartments)|管理模組的單元。|

## <a name="remarks"></a>備註

> [!NOTE]
>  這個類別已過時，已由[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)衍生類別取代。 接下來的資訊適用于較舊版本的 ATL。

`CComAutoThreadModule` 衍生自[CComModule](../../atl/reference/ccommodule-class.md) ，以針對 Exe 和 Windows 服務執行執行緒集區的單元模型 COM 伺服器。 `CComAutoThreadModule` 使用[CComApartment](../../atl/reference/ccomapartment-class.md)來管理模組中每個執行緒的公寓。

當您想要在多個單元中建立物件時，請從 `CComAutoThreadModule` 衍生您的模組。 您也必須在物件的類別定義中包含[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏，以將[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)指定為 Class Factory。

根據預設，ATL COM 程式（Visual Studio .NET 中的 ATL 專案 Wizard）會從 `CComModule`衍生您的模組。 若要使用 `CComAutoThreadModule`，請修改類別定義。 例如：

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="createinstance"></a>CComAutoThreadModule：： CreateInstance

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>參數

*pfnCreateInstance*<br/>
在建立者函式的指標。

*riid*<br/>
在所要求介面的 IID。

*ppvObj*<br/>
脫銷由*riid*識別之介面指標的指標。 如果物件不支援這個介面， *ppvObj*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

選取執行緒，然後在相關聯的單元中建立物件。

##  <a name="dwthreadid"></a>CComAutoThreadModule：:d wThreadID

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
DWORD dwThreadID;
```

### <a name="remarks"></a>備註

包含目前線程的識別碼。

##  <a name="getdefaultthreads"></a>CComAutoThreadModule：： GetDefaultThreads

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>傳回值

要在 EXE 模組中建立的執行緒數目。

### <a name="remarks"></a>備註

這個靜態函式會根據處理器數目，以動態方式計算 EXE 模組的執行緒數目上限。 根據預設，此傳回值會傳遞至[Init](#init)方法來建立執行緒。

##  <a name="init"></a>CComAutoThreadModule：： Init

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>參數

*p*<br/>
在物件對應專案陣列的指標。

*h*<br/>
在傳遞至 `DLLMain` 或 `WinMain`的 HINSTANCE。

*plibid*<br/>
在與專案相關聯之類型程式庫的 LIBID 指標。

*nThreads*<br/>
在要建立的執行緒數目。 根據預設， *nThreads*是由[GetDefaultThreads](#getdefaultthreads)所傳回的值。

### <a name="remarks"></a>備註

初始化資料成員，並建立*nThreads*所指定的執行緒數目。

##  <a name="lock"></a>CComAutoThreadModule：： Lock

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
LONG Lock();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

### <a name="remarks"></a>備註

針對模組和目前線程的鎖定計數執行不可部分完成的增量。 `CComAutoThreadModule` 使用模組鎖定計數來判斷是否有任何用戶端正在存取模組。 目前線程上的鎖定計數用於統計用途。

##  <a name="m_allocator"></a>CComAutoThreadModule：： m_Allocator

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>備註

管理執行緒選取專案的物件。 根據預設，`ThreadAllocator` 類別樣板參數為[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

##  <a name="m_nthreads"></a>CComAutoThreadModule：： m_nThreads

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
int m_nThreads;
```

### <a name="remarks"></a>備註

包含 EXE 模組中的執行緒數目。 呼叫[Init](#init)時，`m_nThreads` 會設定為*nThreads*參數值。 每個執行緒的相關聯的公寓都是由[CComApartment](../../atl/reference/ccomapartment-class.md)物件所管理。

##  <a name="m_papartments"></a>CComAutoThreadModule：： m_pApartments

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>備註

指向[CComApartment](../../atl/reference/ccomapartment-class.md)物件的陣列，每個物件都會管理模組中的一個單元。 陣列中的元素數目是以[m_nThreads](#m_nthreads)成員為基礎。

##  <a name="unlock"></a>CComAutoThreadModule：： Unlock

從 ATL 7.0，`CComAutoThreadModule` 已過時：如需詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

```
LONG Unlock();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

### <a name="remarks"></a>備註

針對模組和目前線程的鎖定計數執行不可部分完成的遞減。 `CComAutoThreadModule` 使用模組鎖定計數來判斷是否有任何用戶端正在存取模組。 目前線程上的鎖定計數用於統計用途。

當模組鎖定計數達到零時，就可以卸載模組。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)
