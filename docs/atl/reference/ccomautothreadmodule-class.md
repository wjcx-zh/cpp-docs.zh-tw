---
title: CComAutoThread模組類別
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
ms.openlocfilehash: 391354c5672cf15c0286491619a13c6005493cfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321059"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThread模組類別

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>參數

*執行緒定位器*<br/>
[在]管理線程選擇的類。 預設值為[CcomSimpleThreadallocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[建立實體](#createinstance)|選擇線程,然後在關聯的單元中創建物件。|
|[取得預設線程](#getdefaultthreads)|(靜態)根據處理器數動態計算模組的線程數。|
|[Init](#init)|創建模組的線程。|
|[鎖](#lock)|增加模組和當前線程上的鎖計數。|
|[解除鎖定](#unlock)|在模組和當前線程上重新分配鎖計數。|

### <a name="data-members"></a>資料成員

### <a name="data-members"></a>資料成員

|||
|-|-|
|[dwThreadID](#dwthreadid)|包含當前線程的標識碼。|
|[m_Allocator](#m_allocator)|管理線程選擇。|
|[m_nThreads](#m_nthreads)|包含模組中的線程數。|
|[m_pApartments](#m_papartments)|管理模組的公寓。|

## <a name="remarks"></a>備註

> [!NOTE]
> 此類已過時,已替換為[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)派生類。 以下資訊適用於舊版本的 ATL。

`CComAutoThreadModule`派生自[CComModule,](../../atl/reference/ccommodule-class.md)用於實現用於 EXE 和 Windows 服務的線程池單元式 COM 伺服器。 `CComAutoThreadModule`使用[CCom公寓](../../atl/reference/ccomapartment-class.md)管理模組中每個線程的公寓。

從`CComAutoThreadModule`要在多個單元中創建物件時派生模組。 還必須在物件的類定義中包括[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)宏,以指定[CcomClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)為類工廠。

默認情況下,ATL COM 應用程式精靈(Visual Studio .NET 中的 ATL`CComModule`專案精靈)將從派生您的模組。 要使用`CComAutoThreadModule`,請修改類定義。 例如：

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CCom 模組](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThread模組::建立實例

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>參數

*pfn 建立實體*<br/>
[在]指向創建函數的指標。

*riid*<br/>
[在]請求介面的 IID。

*普夫奧比*<br/>
[出]指向*riid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppvObj*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

選擇線程,然後在關聯的單元中創建物件。

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThread模組::dwThreadID

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
DWORD dwThreadID;
```

### <a name="remarks"></a>備註

包含當前線程的標識碼。

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThread模組::取得預設線程

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>傳回值

要在 EXE 模組中創建的線程數。

### <a name="remarks"></a>備註

此靜態函數根據處理器數動態計算 EXE 模組的最大線程數。 默認情況下,此返回值傳遞給[Init](#init)方法以建立線程。

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThread模組::Init

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向物件映射條目陣列的指標。

*H*<br/>
[在]傳遞給`DLLMain``WinMain`或的 HINSTANCE。

*普利比德*<br/>
[在]指向與專案關聯的類型庫的 LIBID 的指標。

*nThreads*<br/>
[在]要創建的線程數。 默認情況下 *,nThreads*是[GetDefaultThreads](#getdefaultthreads)返回的值。

### <a name="remarks"></a>備註

初始化數據成員並創建*nThreads*指定的線程數。

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThread模組:鎖定

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
LONG Lock();
```

### <a name="return-value"></a>傳回值

可用於診斷或測試的值。

### <a name="remarks"></a>備註

對模組和當前線程的鎖計數執行原子增量。 `CComAutoThreadModule`使用模組鎖計數來確定是否有任何用戶端正在訪問該模組。 當前線程上的鎖計數用於統計目的。

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a>CComAutoThread模組::m_Allocator

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>備註

管理線程選擇的物件。 預設的功能`ThreadAllocator`, 類別樣本參數是[CcomSimpleThreadallocator](../../atl/reference/ccomsimplethreadallocator-class.md)。

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a>CComAutoThread模組:m_nThreads

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
int m_nThreads;
```

### <a name="remarks"></a>備註

包含 EXE 模組中的線程數。 呼叫[Init](#init)時`m_nThreads`,將設定為*nThreads*參數值。 每個線程的關聯單元由[CCom公寓](../../atl/reference/ccomapartment-class.md)物件管理。

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a>CComAutoThread模組::m_pApartments

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>備註

指向[CCom公寓](../../atl/reference/ccomapartment-class.md)物件陣列,每個物件都管理模組中的單元。 陣列中的元素數基於[m_nThreads](#m_nthreads)成員。

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThread模組:解鎖

從 ATL 7.0`CComAutoThreadModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
LONG Unlock();
```

### <a name="return-value"></a>傳回值

可用於診斷或測試的值。

### <a name="remarks"></a>備註

對模組和當前線程的鎖計數執行原子減減。 `CComAutoThreadModule`使用模組鎖計數來確定是否有任何用戶端正在訪問該模組。 當前線程上的鎖計數用於統計目的。

當模組鎖計數達到零時,可以卸載模組。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類](../../atl/atl-module-classes.md)
