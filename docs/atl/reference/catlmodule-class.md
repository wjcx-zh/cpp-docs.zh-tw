---
title: CAtlModule 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: 10658b118c97afe99144c3a4d25e0297aba3727f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168011"
---
# <a name="catlmodule-class"></a>CAtlModule 類別

這個類別提供數個 ATL 模組類別所使用的方法。

## <a name="syntax"></a>語法

```cpp
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|建構函式。|
|[CAtlModule：： ~ CAtlModule](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|覆寫這個方法，將參數加入至 ATL 登錄元件（註冊機構）取代對應。|
|[CAtlModule::AddTermFunc](#addtermfunc)|新增要在模組終止時呼叫的新函數。|
|[CAtlModule::GetGITPtr](#getgitptr)|傳回全域介面指標。|
|[CAtlModule::GetLockCount](#getlockcount)|傳回鎖定計數。|
|[CAtlModule：： Lock](#lock)|遞增鎖定計數。|
|[CAtlModule：： Term](#term)|釋放所有資料成員。|
|[CAtlModule：： Unlock](#unlock)|減量鎖定計數。|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|執行包含在指定資源中的腳本，以註冊或取消註冊物件。|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|這個方法是由所`UpdateRegistryFromResourceD`呼叫，用來執行登錄更新。|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|執行包含在指定資源中的腳本，以註冊或取消註冊物件。 這個方法會以靜態方式連結至 ATL 登錄元件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlModule：： m_libid](#m_libid)|包含目前模組的 GUID。|
|[CAtlModule：： m_pGIT](#m_pgit)|全域介面資料表的指標。|

## <a name="remarks"></a>備註

這個類別是由[CAtlDllModuleT 類別](../../atl/reference/catldllmodulet-class.md)、 [CAtlExeModuleT 類別](../../atl/reference/catlexemodulet-class.md)和[CAtlServiceModuleT 類別](../../atl/reference/catlservicemodulet-class.md)使用，分別提供 DLL 應用程式、EXE 應用程式和 Windows 服務的支援。

如需 ATL 中模組的詳細資訊，請參閱[Atl 模組類別](../../atl/atl-module-classes.md)。

這個類別會取代舊版 ATL 中使用的過時[CComModule 類別](../../atl/reference/ccommodule-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements

覆寫這個方法，將參數加入至 ATL 登錄元件（註冊機構）取代對應。

```cpp
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>參數

*pRegistrar*<br/>
已保留。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

可取代的參數允許註冊機構的用戶端指定執行時間資料。 為此，註冊機構會維護一個取代對應，在其中輸入與您的腳本中可取代參數相關聯的值。 註冊機構會在執行時間建立這些專案。

如需詳細資訊，請參閱[使用可取代的參數（註冊機構的預處理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)主題。

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtlModule::AddTermFunc

新增要在模組終止時呼叫的新函數。

```cpp
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>參數

*pFunc*<br/>
要加入之函式的指標。

*dw*<br/>
使用者定義的資料，傳遞至函數。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtlModule::CAtlModule

建構函式。

```cpp
CAtlModule() throw();
```

### <a name="remarks"></a>備註

初始化資料成員，並起始模組執行緒周圍的重要區段。

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtlModule：： ~ CAtlModule

解構函式。

```cpp
~CAtlModule() throw();
```

### <a name="remarks"></a>備註

釋放所有資料成員。

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtlModule::GetGITPtr

抓取全域介面資料表的指標。

```cpp
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>參數

*ppGIT*<br/>
變數的指標，將會接收全域介面資料表的指標。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，否則會傳回錯誤的錯誤碼。 如果*ppGIT*等於 Null，就會傳回 E_POINTER。

### <a name="remarks"></a>備註

如果全域介面資料表物件不存在，則會建立它，而且其位址會儲存在成員變數[CAtlModule：： m_pGIT](#m_pgit)中。

在 debug build 中，如果*ppGIT*等於 Null，或是無法取得全域介面資料表指標，就會發生判斷提示錯誤。

如需全域介面資料表的詳細資訊，請參閱[IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) 。

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtlModule::GetLockCount

傳回鎖定計數。

```cpp
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>傳回值

傳回鎖定計數。 這個值可能有助於診斷和偵錯工具。

## <a name="catlmodulelock"></a><a name="lock"></a>CAtlModule：： Lock

遞增鎖定計數。

```cpp
virtual LONG Lock() throw();
```

### <a name="return-value"></a>傳回值

遞增鎖定計數，並傳回更新的值。 這個值可能有助於診斷和偵錯工具。

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModule：： m_libid

包含目前模組的 GUID。

```cpp
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModule：： m_pGIT

全域介面資料表的指標。

```cpp
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtlModule：： Term

釋放所有資料成員。

```cpp
void Term() throw();
```

### <a name="remarks"></a>備註

釋放所有資料成員。 這個方法是由「析構函式」呼叫。

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtlModule：： Unlock

減量鎖定計數。

```cpp
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>傳回值

遞減鎖定計數，並傳回更新的值。 這個值可能有助於診斷和偵錯工具。

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

執行包含在指定資源中的腳本，以註冊或取消註冊物件。

```cpp
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>參數

*lpszRes*<br/>
資源名稱。

*nResID*<br/>
資源識別碼。

*bRegister*<br/>
如果應該註冊物件，則為 TRUE;否則為 FALSE。

*pMapEntries*<br/>
取代對應的指標，儲存與腳本可取代參數相關聯的值。 ATL 會自動使用% MODULE%。 若要使用其他可取代的參數，請參閱[CAtlModule：： AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用 Null 預設值。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

執行包含在*lpszRes 或 nResID*所指定之資源中的腳本。 如果*bRegister*為 TRUE，這個方法會在系統登錄中註冊物件;否則，它會從登錄中移除物件。

若要以靜態方式連結至 ATL 登錄元件（註冊機構），請參閱[CAtlModule：： UpdateRegistryFromResourceS](#updateregistryfromresources)。

這個方法會呼叫[CAtlModule：： UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)和[IRegistrar：： ResourceUnregister](iregistrar-class.md#resourceunregister)。

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

這個方法是由所`UpdateRegistryFromResourceD`呼叫，用來執行登錄更新。

```cpp
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>參數

*lpszRes*<br/>
資源名稱。

*bRegister*<br/>
指出是否應該註冊物件。

*pMapEntries*<br/>
取代對應的指標，儲存與腳本可取代參數相關聯的值。 ATL 會自動使用% MODULE%。 若要使用其他可取代的參數，請參閱[CAtlModule：： AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用 Null 預設值。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

這個方法會提供[CAtlModule：： UpdateRegistryFromResourceD](#updateregistryfromresourced)的執行。

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

執行包含在指定資源中的腳本，以註冊或取消註冊物件。 這個方法會以靜態方式連結至 ATL 登錄元件。

```cpp
HRESULT WINAPI UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>參數

*nResID*<br/>
資源識別碼。

*lpszRes*<br/>
資源名稱。

*bRegister*<br/>
指出是否應該註冊資源腳本。

*pMapEntries*<br/>
取代對應的指標，儲存與腳本可取代參數相關聯的值。 ATL 會自動使用% MODULE%。 若要使用其他可取代的參數，請參閱[CAtlModule：： AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用 Null 預設值。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

類似于[CAtlModule：： UpdateRegistryFromResourceD](#updateregistryfromresourced) ， `CAtlModule::UpdateRegistryFromResourceS`但會建立與 ATL 登錄元件（註冊機構）的靜態連結。

## <a name="see-also"></a>另請參閱

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類別](../../atl/atl-module-classes.md)<br/>
[登錄元件 (登錄器)](../../atl/atl-registry-component-registrar.md)
