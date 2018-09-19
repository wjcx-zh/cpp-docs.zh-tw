---
title: CComModule 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: faf3080c6363ef0227b71e550ff658b1790d37b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090694"
---
# <a name="ccommodule-class"></a>CComModule 類別

ATL 7.0 截至`CComModule`已被取代： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|建立指定的 CLSID 的物件。 適用於僅 Dll。|
|[CComModule::GetModuleInstance](#getmoduleinstance)|傳回 `m_hInst`。|
|[CComModule::GetResourceInstance](#getresourceinstance)|傳回 `m_hInstResource`。|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|傳回 `m_hInstTypeLib`。|
|[Init](#init)|初始化資料成員。|
|[CComModule::RegisterClassHelper](#registerclasshelper)|輸入物件的標準的類別註冊系統登錄中。|
|[CComModule::RegisterClassObjects](#registerclassobjects)|註冊類別物件。 針對只有 Exe。|
|[CComModule::RegisterServer](#registerserver)|更新系統登錄的物件對應中每個物件。|
|[CComModule::RegisterTypeLib](#registertypelib)|註冊類型程式庫。|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|撤銷類別物件。 針對只有 Exe。|
|[Ccommodule:: Term](#term)|釋放資料成員。|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|從系統登錄中移除物件的標準類別註冊。|
|[CComModule::UnregisterServer](#unregisterserver)|取消註冊物件對應中的每個物件。|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|註冊或取消註冊物件的標準的類別註冊。|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|執行指令碼包含在指定的資源，以註冊或取消登錄的物件。|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|靜態連結 ATL 登錄元件。 執行指令碼包含在指定的資源，以註冊或取消登錄的物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|可確保同步處理的存取權的物件對應資訊。|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|可確保同步處理的資訊的存取權類型程式庫。|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|可確保視窗類別資訊和視窗建立期間使用的靜態資料的同步的存取。|
|[CComModule::m_hInst](#m_hinst)|包含模組執行個體的控制代碼。|
|[CComModule::m_hInstResource](#m_hinstresource)|根據預設，包含模組執行個體的控制代碼。|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|根據預設，包含模組執行個體的控制代碼。|
|[CComModule::m_pObjMap](#m_pobjmap)|模組執行個體所維護的物件對應至點。|

## <a name="remarks"></a>備註

> [!NOTE]
>  此類別已被取代，，和 ATL 程式碼產生精靈現在會使用[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)並[CAtlModule](../../atl/reference/catlmodule-class.md)衍生的類別。 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。 接下來的資訊適用於建立使用 ATL 的版本還舊的應用程式 `CComModule` 仍屬於適用於 ATL 回溯功能。

`CComModule` 會實作 COM 伺服器模組，可讓用戶端存取模組的元件。 `CComModule` 支援 （同處理序） 的 DLL 及 EXE (local) 的模組。

A`CComModule`執行個體會維護一組類別物件定義使用物件對應。 此物件對應會實作為陣列`_ATL_OBJMAP_ENTRY`結構，和包含的資訊：

- 輸入，並在系統登錄中移除物件的描述。

- Class factory 具現化物件。

- 在元件中建立用戶端與根物件之間的通訊。

- 正在執行類別物件的存留期的管理。

當您執行 ATL COM AppWizard 時，精靈會自動產生`_Module`，全域執行個體`CComModule`或從它衍生的類別。 如需 ATL 專案精靈 的詳細資訊，請參閱文章[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)。

除了`CComModule`，提供 ATL [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，它會實作 Exe 和 Windows 服務的 apartment model 模組。 衍生您的模組從`CComAutoThreadModule`想要在多個 apartment 中建立物件時。

## <a name="inheritance-hierarchy"></a>繼承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="getclassobject"></a>  CComModule::GetClassObject

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>參數

*rclsid*<br/>
[in]若要建立之物件的 CLSID。

*riid*<br/>
[in]要求的介面 IID。

*ppv*<br/>
[out]所識別之介面指標的指標*riid*。 如果物件不支援這個介面， *ppv*設為 NULL。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

建立指定的 CLSID 的物件，並擷取此物件的介面指標。

`GetClassObject` 只有使用 dll。

##  <a name="getmoduleinstance"></a>  CComModule::GetModuleInstance

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>傳回值

此模組用來識別 HINSTANCE。

### <a name="remarks"></a>備註

傳回[m_hInst](#m_hinst)資料成員。

##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>傳回值

的 HINSTANCE。

### <a name="remarks"></a>備註

傳回[m_hInstResource](#m_hinstresource)資料成員。

##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>傳回值

的 HINSTANCE。

### <a name="remarks"></a>備註

傳回[m_hInstTypeLib](#m_hinsttypelib)資料成員。

##  <a name="init"></a>  Init

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
[in]物件的對應項目的陣列的指標。

*h*<br/>
[in]的 HINSTANCE 傳遞給`DLLMain`或`WinMain`。

*plibid*<br/>
[in]與專案相關聯的類型程式庫的 LIBID 指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

所有資料成員都初始化。

##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>備註

可確保同步處理的存取權的物件對應。

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>備註

可確保同步處理型別程式庫的存取。

##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>備註

可確保視窗類別資訊並在視窗的建立期間使用的靜態資料的同步的存取。

##  <a name="m_hinst"></a>  CComModule::m_hInst

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>備註

包含模組執行個體的控制代碼。

[Init](#init)方法會設定`m_hInst`至控制代碼傳遞給`DLLMain`或`WinMain`。

##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>備註

根據預設，包含模組執行個體的控制代碼。

[Init](#init)方法會設定`m_hInstResource`至控制代碼傳遞給`DLLMain`或`WinMain`。 您可以明確設定`m_hInstResource`資源控制代碼。

[GetResourceInstance](#getresourceinstance)方法傳回的控制代碼儲存在`m_hInstResource`。

##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>備註

根據預設，包含模組執行個體的控制代碼。

[Init](#init)方法會設定`m_hInstTypeLib`至控制代碼傳遞給`DLLMain`或`WinMain`。 您可以明確設定`m_hInstTypeLib`至控制代碼型別程式庫。

[GetTypeLibInstance](#gettypelibinstance)方法傳回的控制代碼儲存在`m_hInstTypeLib`。

##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>備註

模組執行個體所維護的物件對應至點。

##  <a name="registerclasshelper"></a>  CComModule::RegisterClassHelper

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

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
[in]若要註冊之物件的 CLSID。

*lpszProgID*<br/>
[in]與物件相關的 ProgID。

*lpszVerIndProgID*<br/>
[in]版本無關的 ProgID，與物件相關聯。

*nDescID*<br/>
[in]物件的描述的字串資源識別碼。

*dwFlags*<br/>
[in]指定要在登錄中輸入的執行緒模型。 可能的值為 THREADFLAGS_APARTMENT、 THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

輸入物件的標準的類別註冊系統登錄中。

[UpdateRegistryClass](#updateregistryclass)方法呼叫`RegisterClassHelper`。

##  <a name="registerclassobjects"></a>  CComModule::RegisterClassObjects

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>參數

*dwClsContext*<br/>
[in]指定要執行的類別物件的內容。 可能的值為 CLSCTX_INPROC_SERVER、 CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。 如需這些值的說明，請參閱 < [CLSCTX](https://msdn.microsoft.com/library/windows/desktop/ms693716) Windows SDK 中。

*dwFlags*<br/>
[in]決定類別物件的連接類型。 可能的值為 REGCLS_SINGLEUSE、 REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。 如需這些值的說明，請參閱 < [REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls) Windows SDK 中。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

讓其他應用程式可以連線到它，則您可以向 OLE EXE 類別物件。 只有使用 Exe 以這個方法。

##  <a name="registerserver"></a>  CComModule::RegisterServer

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
[in]表示是否將已註冊型別程式庫。 預設值為 FALSE。

*Createtable*<br/>
[in]要註冊之物件的 clsid 點。 若要註冊 NULL （預設值），在物件對應中的所有物件。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

取決於*Createtable*參數，會更新系統登錄單一類別物件或物件對應中的所有物件。

如果*bRegTypeLib*為 TRUE，類型程式庫資訊也會一併更新。

請參閱[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)如需有關如何將物件對應中的項目資訊。

`RegisterServer` 將會自動呼叫`DLLRegisterServer`dll 或由`WinMain`以執行 exe`/RegServer`命令列選項。

##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
[in]格式字串`"\\N"`，其中`N`是型別程式庫資源的整數索引。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

將類型程式庫的相關資訊加入至系統登錄中。

如果模組執行個體包含多個型別程式庫，請指定應該使用哪一個型別程式庫中使用這個方法的第二個版本。

##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

移除類別的物件。 只有使用 Exe 以這個方法。

##  <a name="term"></a>  Ccommodule:: Term

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
void Term() throw();
```

### <a name="remarks"></a>備註

釋放所有的資料成員。

##  <a name="unregisterclasshelper"></a>  CComModule::UnregisterClassHelper

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>參數

*clsid*<br/>
[in]要移除註冊之物件的 CLSID。

*lpszProgID*<br/>
[in]與物件相關的 ProgID。

*lpszVerIndProgID*<br/>
[in]版本無關的 ProgID，與物件相關聯。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

從系統登錄中移除物件的標準類別註冊。

[UpdateRegistryClass](#updateregistryclass)方法呼叫`UnregisterClassHelper`。

##  <a name="unregisterserver"></a>  CComModule::UnregisterServer

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>參數

*bUnRegTypeLib*<br/>
如果為 TRUE，類型程式庫還有未註冊。

*Createtable*<br/>
要移除註冊物件的 clsid 點。 如果 NULL （預設值），在物件對應中的所有物件就會取消註冊。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

取決於*Createtable*參數，取消登錄單一類別的物件或物件對應中的所有物件。

`UnregisterServer` 將會自動呼叫`DLLUnregisterServer`dll 或由`WinMain`以執行 exe`/UnregServer`命令列選項。

請參閱[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)如需有關如何將物件對應中的項目資訊。

##  <a name="updateregistryclass"></a>  CComModule::UpdateRegistryClass

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

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
註冊或取消登錄該物件的 CLSID。

*lpszProgID*<br/>
與物件相關的 ProgID。

*lpszVerIndProgID*<br/>
版本無關的 ProgID，與物件相關聯。

*nDescID*<br/>
物件的描述的字串資源識別碼。

*szDesc*<br/>
字串，包含物件的描述。

*dwFlags*<br/>
指定要在登錄中輸入的執行緒模型。 可能的值為 THREADFLAGS_APARTMENT、 THREADFLAGS_BOTH 或 AUTPRXFLAG。

*bRegister*<br/>
表示是否應該註冊的物件。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果*bRegister*為 TRUE 時，這個方法會進入物件的標準的類別註冊系統登錄中。

如果*bRegister*為 FALSE 時，它會移除物件的註冊。

值而定*bRegister*，`UpdateRegistryClass`撥打[RegisterClassHelper](#registerclasshelper)或是[UnregisterClassHelper](#unregisterclasshelper)。

藉由指定[DECLARE_REGISTRY](registry-macros.md#declare_registry)巨集，`UpdateRegistryClass`會叫用自動當處理物件對應。

##  <a name="updateregistryfromresourced"></a>  CComModule::UpdateRegistryFromResourceD

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

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
[in]資源名稱。

*nResID*<br/>
[in]資源識別碼。

*bRegister*<br/>
[in]表示是否應該註冊的物件。

*pMapEntries*<br/>
[in]儲存指令碼的可置換的參數相關聯的值取代對應指標。 會自動使用 ATL `%MODULE%`。 若要使用其他可置換的參數，請參閱 「 備註 」，如需詳細資訊。 否則，請使用 NULL 預設值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

執行指令碼包含在所指定的資源*lpszRes*或是*nResID*。

如果*bRegister*為 TRUE 時，這個方法會註冊在系統登錄中的物件; 否則取消註冊的物件。

藉由指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或是[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)巨集，`UpdateRegistryFromResourceD`會叫用自動當處理物件對應。

> [!NOTE]
>  若要取代取代值，在執行階段，請勿指定 DECLARE_REGISTRY_RESOURCE 或 DECLARE_REGISTRY_RESOURCEID 巨集。 相反地，建立陣列`_ATL_REGMAP_ENTRIES`配對來取代預留位置，在執行階段值的結構，其中每個項目包含變數的預留位置。 然後呼叫`UpdateRegistryFromResourceD`，將陣列傳遞*pMapEntries*參數。 這會將新增內所有的取代值`_ATL_REGMAP_ENTRIES`註冊機構的取代對應的結構。

> [!NOTE]
>  若要以靜態方式連結至 ATL 登錄元件 （登錄器），請參閱[UpdateRegistryFromResourceS](#updateregistryfromresources)。

如需有關可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。

##  <a name="updateregistryfromresources"></a>  CComModule::UpdateRegistryFromResourceS

ATL 7.0 截至`CComModule`已淘汰： 請參閱 < [ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。

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
[in]資源名稱。

*nResID*<br/>
[in]資源識別碼。

*bRegister*<br/>
[in]表示是否應該註冊資源指令碼。

*pMapEntries*<br/>
[in]儲存指令碼的可置換的參數相關聯的值取代對應指標。 會自動使用 ATL `%MODULE%`。 若要使用其他可置換的參數，請參閱 「 備註 」，如需詳細資訊。 否則，請使用 NULL 預設值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

類似於[UpdateRegistryFromResourceD](#updateregistryfromresourced)除了`UpdateRegistryFromResourceS`建立靜態連結 ATL 登錄元件 （登錄器）。

`UpdateRegistryFromResourceS` 將會叫用會自動處理物件對應時，提供您加入`#define _ATL_STATIC_REGISTRY`為您的 stdafx.h。

> [!NOTE]
>  若要取代取代值，在執行階段，未指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或是[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)巨集。 相反地，建立陣列`_ATL_REGMAP_ENTRIES`配對來取代預留位置，在執行階段值的結構，其中每個項目包含變數的預留位置。 然後呼叫`UpdateRegistryFromResourceS`，將陣列傳遞*pMapEntries*參數。 這會將新增內所有的取代值`_ATL_REGMAP_ENTRIES`註冊機構的取代對應的結構。

如需有關可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
