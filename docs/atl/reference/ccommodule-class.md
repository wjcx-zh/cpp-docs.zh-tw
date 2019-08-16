---
title: CComModule 類別
ms.date: 11/04/2016
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: 53138081a6d712f775a2cc8f1e6905c45d95d34d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497112"
---
# <a name="ccommodule-class"></a>CComModule 類別

從 atl 7.0, 已`CComModule`被取代: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|建立指定之 CLSID 的物件。 僅適用于 Dll。|
|[CComModule::GetModuleInstance](#getmoduleinstance)|傳回 `m_hInst`。|
|[CComModule::GetResourceInstance](#getresourceinstance)|傳回 `m_hInstResource`。|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|傳回 `m_hInstTypeLib`。|
|[CComModule::Init](#init)|初始化資料成員。|
|[CComModule::RegisterClassHelper](#registerclasshelper)|在系統登錄中輸入物件的標準類別註冊。|
|[CComModule::RegisterClassObjects](#registerclassobjects)|註冊類別物件。 僅適用于 Exe。|
|[CComModule::RegisterServer](#registerserver)|更新物件對應中每個物件的系統登錄。|
|[CComModule::RegisterTypeLib](#registertypelib)|註冊類型程式庫。|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|撤銷類別物件。 僅適用于 Exe。|
|[CComModule::Term](#term)|發行資料成員。|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|從系統登錄移除物件的標準類別註冊。|
|[CComModule::UnregisterServer](#unregisterserver)|取消註冊物件對應中的每個物件。|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|註冊或取消註冊物件的標準類別註冊。|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|執行包含在指定資源中的腳本, 以註冊或取消註冊物件。|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|以靜態方式連結至 ATL 登錄元件。 執行包含在指定資源中的腳本, 以註冊或取消註冊物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|確保同步存取物件對應資訊。|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|確保對類型程式庫資訊的同步存取。|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|確保同步存取視窗類別資訊, 以及在建立視窗期間所使用的靜態資料。|
|[CComModule::m_hInst](#m_hinst)|包含模組實例的控制碼。|
|[CComModule::m_hInstResource](#m_hinstresource)|根據預設, 會包含模組實例的控制碼。|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|根據預設, 會包含模組實例的控制碼。|
|[CComModule::m_pObjMap](#m_pobjmap)|指向模組實例所維護的物件對應。|

## <a name="remarks"></a>備註

> [!NOTE]
>  這個類別已被取代, 而 ATL 程式碼產生的嚮導現在會使用[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)衍生的類別。 如需詳細資訊, 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)。 接下來的資訊適用于使用舊版 ATL 所建立的應用程式。 `CComModule`仍然是 ATL 的一部分, 以便回溯功能。

`CComModule`會執行 COM 伺服器模組, 讓用戶端可以存取模組的元件。 `CComModule`支援 DLL (同進程) 和 EXE (本機) 模組。

`CComModule`實例會使用物件對應來維護一組類別物件定義。 這個物件對應會實作為結構的`_ATL_OBJMAP_ENTRY`陣列, 並包含下列資訊:

- 在系統登錄中輸入和移除物件描述。

- 透過 Class Factory 來具現化物件。

- 建立用戶端與元件中根物件之間的通訊。

- 執行類別物件的存留期管理。

當您執行 ATL COM 建立嚮導時, 嚮導會自動`_Module`產生、的全域`CComModule`實例或衍生自它的類別。 如需 ATL 專案 Wizard 的詳細資訊, 請參閱[建立 Atl 專案一](../../atl/reference/creating-an-atl-project.md)文。

除了之外`CComModule`, ATL 還提供[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), 它會針對 exe 和 Windows 服務執行單元模型模組。 當您想要`CComAutoThreadModule`在多個單元中建立物件時, 請從衍生您的模組。

## <a name="inheritance-hierarchy"></a>繼承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>需求

**標頭:** atlbase.h。h

##  <a name="getclassobject"></a>CComModule:: GetClassObject

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>參數

*rclsid*<br/>
在要建立之物件的 CLSID。

*riid*<br/>
在所要求介面的 IID。

*ppv*<br/>
脫銷由*riid*識別之介面指標的指標。 如果物件不支援這個介面, *ppv*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

建立指定之 CLSID 的物件, 並抓取這個物件的介面指標。

`GetClassObject`僅適用于 Dll。

##  <a name="getmoduleinstance"></a>CComModule:: GetModuleInstance

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>傳回值

識別此模組的 HINSTANCE。

### <a name="remarks"></a>備註

傳回[m_hInst](#m_hinst)資料成員。

##  <a name="getresourceinstance"></a>CComModule:: GetResourceInstance

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>傳回值

HINSTANCE。

### <a name="remarks"></a>備註

傳回[m_hInstResource](#m_hinstresource)資料成員。

##  <a name="gettypelibinstance"></a>CComModule:: GetTypeLibInstance

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>傳回值

HINSTANCE。

### <a name="remarks"></a>備註

傳回[m_hInstTypeLib](#m_hinsttypelib)資料成員。

##  <a name="init"></a>CComModule:: Init

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
在物件對應專案陣列的指標。

*h*<br/>
在傳遞至`DLLMain`或`WinMain`的 HINSTANCE。

*plibid*<br/>
在與專案相關聯之類型程式庫的 LIBID 指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

初始化所有資料成員。

##  <a name="m_csobjmap"></a>CComModule:: m_csObjMap

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>備註

確保物件對應的同步存取。

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>備註

確保對類型程式庫的同步存取。

##  <a name="m_cswindowcreate"></a>CComModule:: m_csWindowCreate

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>備註

確保同步存取 window 類別資訊, 以及在建立視窗期間所使用的靜態資料。

##  <a name="m_hinst"></a>CComModule:: m_hInst

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>備註

包含模組實例的控制碼。

[Init](#init)方法會將`m_hInst`設定為傳遞至`DLLMain`或`WinMain`的控制碼。

##  <a name="m_hinstresource"></a>CComModule:: m_hInstResource

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>備註

根據預設, 會包含模組實例的控制碼。

[Init](#init)方法會將`m_hInstResource`設定為傳遞至`DLLMain`或`WinMain`的控制碼。 您可以明確地`m_hInstResource`將設定為資源的控制碼。

[GetResourceInstance](#getresourceinstance)方法會傳回儲存在中`m_hInstResource`的控制碼。

##  <a name="m_hinsttypelib"></a>CComModule:: m_hInstTypeLib

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>備註

根據預設, 會包含模組實例的控制碼。

[Init](#init)方法會將`m_hInstTypeLib`設定為傳遞至`DLLMain`或`WinMain`的控制碼。 您可以明確地`m_hInstTypeLib`將設定為類型程式庫的控制碼。

[GetTypeLibInstance](#gettypelibinstance)方法會傳回儲存在中`m_hInstTypeLib`的控制碼。

##  <a name="m_pobjmap"></a>CComModule:: m_pObjMap

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>備註

指向模組實例所維護的物件對應。

##  <a name="registerclasshelper"></a>CComModule:: RegisterClassHelper

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>參數

*clsid*<br/>
在要註冊之物件的 CLSID。

*lpszProgID*<br/>
在與物件相關聯的 ProgID。

*lpszVerIndProgID*<br/>
在與物件相關聯的與版本無關的 ProgID。

*nDescID*<br/>
在物件描述的字串資源識別碼。

*dwFlags*<br/>
在指定要在登錄中輸入的執行緒模型。 可能的值為 THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

在系統登錄中輸入物件的標準類別註冊。

[UpdateRegistryClass](#updateregistryclass)方法會呼叫`RegisterClassHelper`。

##  <a name="registerclassobjects"></a>CComModule:: RegisterClassObjects

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>參數

*dwClsContext*<br/>
在指定要在其中執行類別物件的內容。 可能的值為 CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。 如需這些值的說明, 請參閱 Windows SDK 中的[CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) 。

*dwFlags*<br/>
在判斷類別物件的連線類型。 可能的值為 REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。 如需這些值的說明, 請參閱 Windows SDK 中的[REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) 。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

向 OLE 註冊 EXE 類別物件, 讓其他應用程式可以連接到它。 這個方法僅適用于 Exe。

##  <a name="registerserver"></a>CComModule:: RegisterServer

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
在指出是否將註冊類型程式庫。 預設值為 FALSE。

*pCLSID*<br/>
在指向要註冊之物件的 CLSID。 如果為 Null (預設值), 則會註冊物件對應中的所有物件。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

視*pCLSID*參數而定, 會更新單一類別物件或物件對應中所有物件的系統登錄。

如果*bRegTypeLib*為 TRUE, 則也會更新類型程式庫資訊。

如需如何將專案加入至物件對應的詳細資訊, 請參閱[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 。

`RegisterServer`系統會`DLLRegisterServer`針對 DLL `WinMain`或針對使用`/RegServer`命令列選項執行的 EXE, 自動呼叫。

##  <a name="registertypelib"></a>CComModule:: RegisterTypeLib

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
在格式`"\\N"`的字串, 其中`N`是 TYPELIB 資源的整數索引。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

將類型程式庫的相關資訊新增至系統登錄。

如果模組實例包含多個類型程式庫, 請使用這個方法的第二個版本來指定應該使用的類型程式庫。

##  <a name="revokeclassobjects"></a>CComModule:: RevokeClassObjects

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

移除類別物件。 這個方法僅適用于 Exe。

##  <a name="term"></a>CComModule:: Term

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
void Term() throw();
```

### <a name="remarks"></a>備註

釋放所有資料成員。

##  <a name="unregisterclasshelper"></a>CComModule:: UnregisterClassHelper

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>參數

*clsid*<br/>
在要取消註冊之物件的 CLSID。

*lpszProgID*<br/>
在與物件相關聯的 ProgID。

*lpszVerIndProgID*<br/>
在與物件相關聯的與版本無關的 ProgID。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

從系統登錄移除物件的標準類別註冊。

[UpdateRegistryClass](#updateregistryclass)方法會呼叫`UnregisterClassHelper`。

##  <a name="unregisterserver"></a>CComModule:: UnregisterServer

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>參數

*bUnRegTypeLib*<br/>
若為 TRUE, 則也會取消註冊類型程式庫。

*pCLSID*<br/>
指向要取消註冊之物件的 CLSID。 如果為 Null (預設值), 則會取消註冊物件對應中的所有物件。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

視*pCLSID*參數而定, 會取消註冊單一類別物件或物件對應中的所有物件。

`UnregisterServer`系統會`DLLUnregisterServer`針對 DLL `WinMain`或針對使用`/UnregServer`命令列選項執行的 EXE, 自動呼叫。

如需如何將專案加入至物件對應的詳細資訊, 請參閱[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 。

##  <a name="updateregistryclass"></a>CComModule:: UpdateRegistryClass

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```

### <a name="parameters"></a>參數

*clsid*<br/>
要註冊或取消註冊之物件的 CLSID。

*lpszProgID*<br/>
與物件相關聯的 ProgID。

*lpszVerIndProgID*<br/>
與物件相關聯的與版本無關的 ProgID。

*nDescID*<br/>
物件描述的字串資源識別碼。

*szDesc*<br/>
包含物件描述的字串。

*dwFlags*<br/>
指定要在登錄中輸入的執行緒模型。 可能的值為 THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

*bRegister*<br/>
指出是否應該註冊物件。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果*bRegister*為 TRUE, 則這個方法會在系統登錄中輸入物件的標準類別註冊。

如果*bRegister*為 FALSE, 則會移除物件的註冊。

視*bRegister*的值而定, `UpdateRegistryClass`會呼叫[RegisterClassHelper](#registerclasshelper)或[UnregisterClassHelper](#unregisterclasshelper)。

藉由指定[DECLARE_REGISTRY](registry-macros.md#declare_registry)宏, `UpdateRegistryClass`在處理物件對應時, 將會自動叫用。

##  <a name="updateregistryfromresourced"></a>CComModule:: UpdateRegistryFromResourceD

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
virtual HRESULT UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```

### <a name="parameters"></a>參數

*lpszRes*<br/>
在資源名稱。

*nResID*<br/>
在資源識別碼。

*bRegister*<br/>
在指出是否應該註冊物件。

*pMapEntries*<br/>
在取代對應的指標, 儲存與腳本可取代參數相關聯的值。 ATL 會自動`%MODULE%`使用。 若要使用其他可替換的參數, 請參閱備註以取得詳細資料。 否則, 請使用 Null 預設值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

執行包含在*lpszRes*或*nResID*所指定之資源中的腳本。

如果*bRegister*為 TRUE, 這個方法會在系統登錄中註冊物件;否則, 它會取消註冊物件。

藉由指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)宏, `UpdateRegistryFromResourceD`就會在處理您的物件對應時自動叫用。

> [!NOTE]
>  若要在執行時間取代取代值, 請不要指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 宏。 相反地, 請建立結構`_ATL_REGMAP_ENTRIES`的陣列, 其中每個專案都包含變數預留位置與值配對, 以在執行時間取代預留位置。 然後呼叫`UpdateRegistryFromResourceD`, 傳遞*pMapEntries*參數的陣列。 這會將`_ATL_REGMAP_ENTRIES`結構中的所有取代值新增至註冊機構的取代對應。

> [!NOTE]
>  若要以靜態方式連結至 ATL 登錄元件 (註冊機構), 請參閱[UpdateRegistryFromResourceS](#updateregistryfromresources)。

如需可取代參數和腳本的詳細資訊, 請參閱[ATL 登錄元件 (註冊機構)](../../atl/atl-registry-component-registrar.md)一文。

##  <a name="updateregistryfromresources"></a>CComModule:: UpdateRegistryFromResourceS

從 atl 7.0, 已`CComModule`過時: 如需詳細資訊, 請參閱[atl 模組類別](../../atl/atl-module-classes.md)。

```
virtual HRESULT UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>參數

*lpszRes*<br/>
在資源名稱。

*nResID*<br/>
在資源識別碼。

*bRegister*<br/>
在指出是否應該註冊資源腳本。

*pMapEntries*<br/>
在取代對應的指標, 儲存與腳本可取代參數相關聯的值。 ATL 會自動`%MODULE%`使用。 若要使用其他可替換的參數, 請參閱備註以取得詳細資料。 否則, 請使用 Null 預設值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

類似于[UpdateRegistryFromResourceD](#updateregistryfromresourced) , `UpdateRegistryFromResourceS`但會建立 ATL 登錄元件 (註冊機構) 的靜態連結。

`UpdateRegistryFromResourceS`當您處理物件對應時, 會自動叫用, 前提是`#define _ATL_STATIC_REGISTRY`您會將新增至 stdafx.h。

> [!NOTE]
>  若要在執行時間取代取代值, 請不要指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)宏。 相反地, 請建立結構`_ATL_REGMAP_ENTRIES`的陣列, 其中每個專案都包含變數預留位置與值配對, 以在執行時間取代預留位置。 然後呼叫`UpdateRegistryFromResourceS`, 傳遞*pMapEntries*參數的陣列。 這會將`_ATL_REGMAP_ENTRIES`結構中的所有取代值新增至註冊機構的取代對應。

如需可取代參數和腳本的詳細資訊, 請參閱[ATL 登錄元件 (註冊機構)](../../atl/atl-registry-component-registrar.md)一文。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
