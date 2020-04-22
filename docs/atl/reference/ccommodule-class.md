---
title: CComModule 類別
ms.date: 08/19/2019
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
ms.openlocfilehash: 5e30f847ff99a80ab19b880728472a339fd4cbe5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747937"
---
# <a name="ccommodule-class"></a>CComModule 類別

自 ATL 7.0`CComModule`起,已棄用:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom 模組:取得類別](#getclassobject)|建立指定 CLSID 的物件。 僅適用於 DLL。|
|[CCom 模組:抓取模組實體](#getmoduleinstance)|傳回 `m_hInst`。|
|[CCom 模組:抓取資源實體](#getresourceinstance)|傳回 `m_hInstResource`。|
|[CCom 模組:取得類型 Lib實例](#gettypelibinstance)|傳回 `m_hInstTypeLib`。|
|[CCom模組::Init](#init)|初始化數據成員。|
|[CCom模組::註冊類説明者](#registerclasshelper)|在系統註冊表中輸入物件的標準類註冊。|
|[CCom 模組::註冊類物件](#registerclassobjects)|註冊類物件。 僅適用於 EXEs。|
|[CCom 模組::註冊伺服器](#registerserver)|更新物件映射中每個物件的系統註冊表。|
|[CCom模組::註冊類型Lib](#registertypelib)|註冊類型程式庫。|
|[CCom 模組::撤銷類別](#revokeclassobjects)|撤銷類物件。 僅適用於 EXEs。|
|[CCom 模組::學期](#term)|釋放數據成員。|
|[CCom 模組::未註冊類幫助程式](#unregisterclasshelper)|從系統註冊表中刪除物件的標準類註冊。|
|[CCom 模組::取消註冊伺服器](#unregisterserver)|取消註冊物件映射中的每個物件。|
|[CCom 模組::更新註冊表類](#updateregistryclass)|註冊或取消註冊對象的標準類註冊。|
|[CCom 模組::從資源中更新註冊表](#updateregistryfromresourced)|運行指定資源中包含的腳本以註冊或取消註冊物件。|
|[CCom模組::從資源更新註冊表](#updateregistryfromresources)|靜態連結到 ATL 註冊表元件。 運行指定資源中包含的腳本以註冊或取消註冊物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCom模組:m_csObjMap](#m_csobjmap)|確保同步訪問物件映射資訊。|
|[CCom模組::m_csTypeInfoHolder](#m_cstypeinfoholder)|確保同步存取類型庫資訊。|
|[CCom模組:m_csWindowCreate](#m_cswindowcreate)|確保同步存取視窗創建期間使用的視窗類資訊和靜態資料。|
|[CCom模組::m_hInst](#m_hinst)|包含模組實例的句柄。|
|[CCom模組:m_hInstResource](#m_hinstresource)|默認情況下,包含模組實例的句柄。|
|[CCom模組::m_hInstTypeLib](#m_hinsttypelib)|默認情況下,包含模組實例的句柄。|
|[CCom模組:m_pObjMap](#m_pobjmap)|指向模組實例維護的物件映射。|

## <a name="remarks"></a>備註

> [!NOTE]
> 此類被棄用,ATL 代碼生成嚮導現在使用[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)派生類。 有關詳細資訊[,請參閱 ATL 模組課程](../../atl/atl-module-classes.md)。 以下資訊適用於使用舊版本的 ATL 創建的應用程式。 `CComModule`仍然是 ATL 的一部分,用於向後功能。

`CComModule`實現 COM 伺服器模組,允許用戶端訪問模組的元件。 `CComModule`支援 DLL(在位)和 EXE(本地)模組。

實例`CComModule`使用物件映射來維護一組類物件定義。 此物件對應為結構列來`_ATL_OBJMAP_ENTRY`實現,並包含用於:

- 在系統註冊表中輸入和刪除物件描述。

- 通過類工廠實例化物件。

- 建立用戶端和元件中的根對象之間的通信。

- 執行類物件的存留期管理。

運行 ATL COM 應用精靈時,嚮導會`_Module`自動`CComModule`生成的全域實例或派生自它的類。 有關 ATL 專案精靈的詳細資訊,請參閱創建[ATL 專案](../../atl/reference/creating-an-atl-project.md)的文章。

此外,ATL`CComModule`還提供[CComAutoThread 模組](../../atl/reference/ccomautothreadmodule-class.md),該模組為 EXEs 和 Windows 服務實現了單元模型模組。 從`CComAutoThreadModule`要在多個單元中創建物件時派生模組。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a>CCom 模組:取得類別

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>參數

*rclsid*<br/>
[在]要建立的物件的 CLSID。

*riid*<br/>
[在]請求介面的 IID。

*Ppv*<br/>
[出]指向*riid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppv*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

建立指定的 CLSID 的物件並檢索指向此物件的介面指標。

`GetClassObject`僅適用於 DLL。

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CCom 模組:抓取模組實體

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>傳回值

識別此模組的 HINSTANCE。

### <a name="remarks"></a>備註

返回[m_hInst](#m_hinst)數據成員。

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a>CCom 模組:抓取資源實體

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>傳回值

一個哈普。

### <a name="remarks"></a>備註

返回[m_hInstResource](#m_hinstresource)數據成員。

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a>CCom 模組:取得類型 Lib實例

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>傳回值

一個哈普。

### <a name="remarks"></a>備註

返回[m_hInstTypeLib](#m_hinsttypelib)數據成員。

## <a name="ccommoduleinit"></a><a name="init"></a>CCom模組::Init

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向物件映射條目陣列的指標。

*H*<br/>
[在]傳遞給`DLLMain``WinMain`或的 HINSTANCE。

*普利比德*<br/>
[在]指向與專案關聯的類型庫的 LIBID 的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

初始化所有數據成員。

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a>CCom模組:m_csObjMap

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>備註

確保同步訪問對象映射。

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a>CCom模組::m_csTypeInfoHolder

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>備註

確保同步存取類型庫。

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a>CCom模組:m_csWindowCreate

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>備註

確保同步存取視窗類資訊和視窗創建期間使用的靜態資料。

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a>CCom模組::m_hInst

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>備註

包含模組實例的句柄。

[Init](#init)方法`m_hInst`集 到`DLLMain`傳遞`WinMain`給 或 的句柄。

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a>CCom模組:m_hInstResource

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>備註

默認情況下,包含模組實例的句柄。

[Init](#init)方法`m_hInstResource`集 到`DLLMain`傳遞`WinMain`給 或 的句柄。 您可以顯式設置為`m_hInstResource`資源的句柄。

[GetResourceInstance](#getresourceinstance)方法返回存儲在`m_hInstResource`中的句柄。

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a>CCom模組::m_hInstTypeLib

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>備註

默認情況下,包含模組實例的句柄。

[Init](#init)方法`m_hInstTypeLib`集 到`DLLMain`傳遞`WinMain`給 或 的句柄。 您可以顯式設定為`m_hInstTypeLib`類型庫的句柄。

[GetTypeLibinstance](#gettypelibinstance)方法返回存儲在`m_hInstTypeLib`中的句柄。

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a>CCom模組:m_pObjMap

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>備註

指向模組實例維護的物件映射。

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a>CCom模組::註冊類説明者

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>參數

*Clsid*<br/>
[在]要註冊的物件的 CLSID。

*lpszProgID*<br/>
[在]與物件關聯的 ProgID。

*lpszVerindProgID*<br/>
[在]與物件關聯的版本無關的 ProgID。

*nDescID*<br/>
[在]物件描述的字串資源的標識碼。

*dwFlags*<br/>
[在]指定要在註冊表中輸入的線程模型。 可能的值是THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

在系統註冊表中輸入物件的標準類註冊。

[更新註冊表類別](#updateregistryclass)方法呼`RegisterClassHelper`叫 。

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a>CCom 模組::註冊類物件

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>參數

*dwCls 上下文*<br/>
[在]指定要在其中運行類物件的上下文。 可能的值是CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER或CLSCTX_LOCAL_SERVER。 有關這些值的說明,請參閱 Windows SDK 中的[CLSCTX。](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx)

*dwFlags*<br/>
[在]確定與類對象的連接類型。 可能的值是REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE 或REGCLS_MULTI_SEPARATE。 有關這些值的說明,請參閱 Windows SDK 中的[REGCLS。](/windows/win32/api/combaseapi/ne-combaseapi-regcls)

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

將 EXE 類物件註冊到 OLE,以便其他應用程式可以連接到它。 此方法僅適用於 EXEs。

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a>CCom 模組::註冊伺服器

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>參數

*bRegTypeLib*<br/>
[在]指示類型庫是否將註冊。 預設值為 FALSE。

*pCLSID*<br/>
[在]指向要註冊的物件的 CLSID。 如果 NULL(預設值),則將註冊物件映射中的所有物件。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

根據*pCLSID*參數,更新單個類物件或物件映射中的所有物件的系統註冊表。

如果*bRegTypeLib*為 TRUE,則類型庫資訊也將更新。

有關如何向物件映射添加條目的資訊,請參閱[OBJECT_ENTRY_AUTO。](object-map-macros.md#object_entry_auto)

`RegisterServer`將自動呼叫`DLLRegisterServer`DLL`WinMain`或使用 命令列`/RegServer`選項執行的 EXE。

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a>CCom模組::註冊類型Lib

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
[在]格式`"\\N"`的字串,`N`其中是 TYPELIB 資源的整數索引。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

將有關類型庫的資訊添加到系統註冊表。

如果模組實例包含多個類型庫,請使用此方法的第二個版本指定應使用的類型庫。

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a>CCom 模組::撤銷類別

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

刪除類物件。 此方法僅適用於 EXEs。

## <a name="ccommoduleterm"></a><a name="term"></a>CCom 模組::學期

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```cpp
void Term() throw();
```

### <a name="remarks"></a>備註

釋放所有數據成員。

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a>CCom 模組::未註冊類幫助程式

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>參數

*Clsid*<br/>
[在]要未註冊的物件的 CLSID。

*lpszProgID*<br/>
[在]與物件關聯的 ProgID。

*lpszVerindProgID*<br/>
[在]與物件關聯的版本無關的 ProgID。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

從系統註冊表中刪除物件的標準類註冊。

[更新註冊表類別](#updateregistryclass)方法呼`UnregisterClassHelper`叫 。

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a>CCom 模組::取消註冊伺服器

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>參數

*bUnRegTypeLib*<br/>
如果為 TRUE,則類型庫也未註冊。

*pCLSID*<br/>
指向要未註冊的物件的 CLSID。 如果 NULL(預設值),則物件映射中的所有物件都將取消註冊。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

根據*pCLSID*參數,取消註冊單個類物件或物件映射中的所有物件。

`UnregisterServer`將自動呼叫`DLLUnregisterServer`DLL`WinMain`或使用 命令列`/UnregServer`選項執行的 EXE。

有關如何向物件映射添加條目的資訊,請參閱[OBJECT_ENTRY_AUTO。](object-map-macros.md#object_entry_auto)

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a>CCom 模組::更新註冊表類

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

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

*Clsid*<br/>
要註冊或未註冊的物件的 CLSID。

*lpszProgID*<br/>
與物件關聯的 ProgID。

*lpszVerindProgID*<br/>
與物件關聯的版本無關的 ProgID。

*nDescID*<br/>
物件描述的字串資源的標識碼。

*什德斯茨*<br/>
包含物件描述的字串。

*dwFlags*<br/>
指定要在註冊表中輸入的線程模型。 可能的值是THREADFLAGS_APARTMENT、THREADFLAGS_BOTH 或 AUTPRXFLAG。

*b 註冊*<br/>
指示是否應註冊物件。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果*b寄存器*為 TRUE,則此方法在系統註冊表中輸入對象的標準類註冊。

如果*b 註冊*為 FALSE,則刪除物件的註冊。

從*b 寄存器*的`UpdateRegistryClass`值, 呼叫[註冊類別說明程式](#registerclasshelper)或[取消註冊類別說明程式](#unregisterclasshelper)。

通過指定[DECLARE_REGISTRY](registry-macros.md#declare_registry)`UpdateRegistryClass`宏, 將在處理物件映射時自動調用。

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CCom 模組::從資源中更新註冊表

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

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
[在]資源名稱。

*nResID*<br/>
[在]資源識別碼。

*b 註冊*<br/>
[在]指示是否應註冊物件。

*pMap 項目*<br/>
[在]指向替換映射的指標,儲存與腳本的可替換參數關聯的值。 ATL`%MODULE%`自動 使用 。 要使用其他可替換參數,請參閱備註瞭解詳細資訊。 否則,請使用 NULL 預設值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

執行*lpszRes*或*nResID*指定的資源中包含的文稿。

如果*b寄存器*為 TRUE,則此方法將註冊系統註冊表中的物件;如果 b 寄存器為 TRUE,則此方法將註冊到系統註冊表中的物件。否則,它將取消註冊該物件。

通過指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或`UpdateRegistryFromResourceD`[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)宏, 將在處理物件映射時自動調用。

> [!NOTE]
> 要在運行時替換替換值,請不要指定DECLARE_REGISTRY_RESOURCE或DECLARE_REGISTRY_RESOURCEID宏。 相反,請創建一個`_ATL_REGMAP_ENTRIES`結構陣列,其中每個條目包含一個變數占位符,該占位符與值配對,以在運行時替換佔位符。 然後調用`UpdateRegistryFromResourceD`,傳遞*pMapEntries*參數的陣列。 這會將結構中的所有`_ATL_REGMAP_ENTRIES`替換值添加到註冊器的替換映射中。

> [!NOTE]
> 要靜態連結到 ATL 註冊表元件 (註冊),請參閱[從資源更新註冊表 。](#updateregistryfromresources)

有關可替換參數和腳本的詳細資訊,請參閱[ATL 註冊表元件 (註冊) 一](../../atl/atl-registry-component-registrar.md)文。

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CCom模組::從資源更新註冊表

從 ATL 7.0`CComModule`起,已過時:有關詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

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
[在]資源名稱。

*nResID*<br/>
[在]資源識別碼。

*b 註冊*<br/>
[在]指示是否應註冊資源腳本。

*pMap 項目*<br/>
[在]指向替換映射的指標,儲存與腳本的可替換參數關聯的值。 ATL`%MODULE%`自動 使用 。 要使用其他可替換參數,請參閱備註瞭解詳細資訊。 否則,請使用 NULL 預設值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

類似於[更新註冊器資源D,](#updateregistryfromresourced)但`UpdateRegistryFromResourceS`創建指向 ATL 註冊表元件 (註冊器) 的靜態連結除外。

`UpdateRegistryFromResourceS`處理物件映射時將自動調用物件映射,前提是您添加到`#define _ATL_STATIC_REGISTRY` *pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)。*

> [!NOTE]
> 要在運行時替換替換值,請不要指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)宏。 相反,請創建一個`_ATL_REGMAP_ENTRIES`結構陣列,其中每個條目包含一個變數占位符,該占位符與值配對,以在運行時替換佔位符。 然後調用`UpdateRegistryFromResourceS`,傳遞*pMapEntries*參數的陣列。 這會將結構中的所有`_ATL_REGMAP_ENTRIES`替換值添加到註冊器的替換映射中。

有關可替換參數和腳本的詳細資訊,請參閱[ATL 註冊表元件 (註冊) 一](../../atl/atl-registry-component-registrar.md)文。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
