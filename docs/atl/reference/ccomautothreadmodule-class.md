---
title: CComAutoThreadModule 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b00b9966ed4d9833e885a03e4b5f380ac307f08
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule 類別
為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class ThreadAllocator = CComSimpleThreadAllocator>  
class CComAutoThreadModule : public CComModule
```  
  
#### <a name="parameters"></a>參數  
 `ThreadAllocator`  
 [in]管理執行緒的選取項目類別。 預設值是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CreateInstance](#createinstance)|選取一個執行緒，然後在相關聯的 apartment 中建立的物件。|  
|[GetDefaultThreads](#getdefaultthreads)|（靜態）動態計算模組，根據處理器數目的執行緒的數目。|  
|[Init](#init)|建立模組的執行緒。|  
|[鎖定](#lock)|在模組上與目前執行緒的鎖定計數遞增。|  
|[解除鎖定](#unlock)|減量鎖定計數模組與目前的執行緒。|  
  
### <a name="data-members"></a>資料成員  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[dwThreadID](#dwthreadid)|包含目前執行緒的識別項。|  
|[m_Allocator](#m_allocator)|管理執行緒的選取項目。|  
|[m_nThreads](#m_nthreads)|包含模組中的執行緒的數目。|  
|[m_pApartments](#m_papartments)|管理模組的 apartment。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個類別已經過時，已被[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)衍生的類別。 遵循的資訊是使用在舊版的 ATL  
  
 `CComAutoThreadModule` 衍生自[CComModule](../../atl/reference/ccommodule-class.md)實作 Exe 和 Windows 服務的執行緒集區、 apartment model COM 伺服器。 `CComAutoThreadModule` 使用[CComApartment](../../atl/reference/ccomapartment-class.md)管理模組中的每個執行緒的 apartment。  
  
 衍生您的模組，從`CComAutoThreadModule`當您想要在多個 apartment 中建立物件。 您也必須包括[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)巨集來指定物件的類別定義中[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)做為 class factory。  
  
 根據預設，ATL COM AppWizard （ATL 專案精靈 Visual Studio.NET 中） 會衍生您的模組，從`CComModule`。 若要使用`CComAutoThreadModule`，修改的類別定義。 例如:   
  
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
 **標頭：** atlbase.h  
  
##  <a name="createinstance"></a>  CComAutoThreadModule::CreateInstance  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>參數  
 *pfnCreateInstance*  
 [in]建立者函式指標。  
  
 `riid`  
 [in]所要求介面的 IID。  
  
 `ppvObj`  
 [out]所識別的介面指標的指標`riid`。 如果物件不支援這個介面，`ppvObj`設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 選取一個執行緒，然後在相關聯的 apartment 中建立的物件。  
  
##  <a name="dwthreadid"></a>  CComAutoThreadModule::dwThreadID  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
DWORD dwThreadID;
```  
  
### <a name="remarks"></a>備註  
 包含目前執行緒的識別項。  
  
##  <a name="getdefaultthreads"></a>  CComAutoThreadModule::GetDefaultThreads  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>傳回值  
 要建立 EXE 模組中的執行緒數目。  
  
### <a name="remarks"></a>備註  
 此靜態函式會動態計算 EXE 模組，根據處理器數目的執行緒的數目上限。 根據預設，這個傳回值傳遞至[Init](#init)方法來建立執行緒。  
  
##  <a name="init"></a>  CComAutoThreadModule::Init  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]物件的對應項目的陣列的指標。  
  
 `h`  
 [in]`HINSTANCE`傳遞至**DLLMain**或`WinMain`。  
  
 `plibid`  
 [in]與專案相關聯的類型程式庫的 LIBID 指標。  
  
 `nThreads`  
 [in]若要建立的執行緒數目。 根據預設，`nThreads`是所傳回的值[GetDefaultThreads](#getdefaultthreads)。  
  
### <a name="remarks"></a>備註  
 初始化資料成員，並建立所指定的執行緒數目`nThreads`。  
  
##  <a name="lock"></a>  CComAutoThreadModule::Lock  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
### <a name="remarks"></a>備註  
 執行不可部分完成的增量模組與目前執行緒的鎖定計數。 `CComAutoThreadModule` 若要判斷任何用戶端是否正在存取模組使用模組鎖定計數。 目前的執行緒上的鎖定計數是基於統計目的使用。  
  
##  <a name="m_allocator"></a>  CComAutoThreadModule::m_Allocator  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
ThreadAllocator  m_Allocator;
```     
  
### <a name="remarks"></a>備註  
 管理執行緒的選取範圍的物件。 根據預設，`ThreadAllocator`類別樣板參數是[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
##  <a name="m_nthreads"></a>  CComAutoThreadModule::m_nThreads  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
int m_nThreads;
```  
  
### <a name="remarks"></a>備註  
 包含 EXE 模組中的執行緒的數目。 當[Init](#init)呼叫時，`m_nThreads`設`nThreads`參數值。 每個執行緒相關聯的 apartment 受[CComApartment](../../atl/reference/ccomapartment-class.md)物件。  
  
##  <a name="m_papartments"></a>  CComAutoThreadModule::m_pApartments  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
CComApartment* m_pApartments;
```  
  
### <a name="remarks"></a>備註  
 指向陣列[CComApartment](../../atl/reference/ccomapartment-class.md)物件，其中每個管理模組中的 apartment。 陣列中的項目數目根據[m_nThreads](#m_nthreads)成員。  
  
##  <a name="unlock"></a>  CComAutoThreadModule::Unlock  
 為準，ATL 7.0`CComAutoThreadModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>傳回值  
 值，可用於診斷或測試。  
  
### <a name="remarks"></a>備註  
 執行不可部分完成的遞減模組與目前執行緒的鎖定計數。 `CComAutoThreadModule` 若要判斷任何用戶端是否正在存取模組使用模組鎖定計數。 目前的執行緒上的鎖定計數是基於統計目的使用。  
  
 模組鎖定計數為零時，模組可以卸載。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)
