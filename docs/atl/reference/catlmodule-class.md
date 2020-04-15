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
ms.openlocfilehash: 378c8634e00935c622f0bf5d06a4f6c50cc60cb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321430"
---
# <a name="catlmodule-class"></a>CAtlModule 類別

此類提供多個 ATL 模組類使用的方法。

## <a name="syntax"></a>語法

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtl 模組:CAtl 模組](#catlmodule)|建構函式。|
|[CAtl 模組:_CAtl 模組](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtl 模組:新增公共 RGS 取代](#addcommonrgsreplacements)|重寫此方法以將參數添加到 ATL 註冊表元件 (註冊商) 替換映射。|
|[CAtl 模組::添加TermFunc](#addtermfunc)|添加在模組終止時要調用的新功能。|
|[CAtl 模組:取得 GITPtr](#getgitptr)|返回全域介面指標。|
|[CAtl 模組::取得鎖定計數](#getlockcount)|返回鎖計數。|
|[CAtl 模組:鎖定](#lock)|增加鎖計數。|
|[CAtl 模組::學期](#term)|釋放所有數據成員。|
|[CAtl 模組:解鎖](#unlock)|減量鎖定計數。|
|[CAtlModule::更新註冊從資源D](#updateregistryfromresourced)|運行指定資源中包含的腳本以註冊或取消註冊物件。|
|[CAtlModule:從資源説明程式更新註冊](#updateregistryfromresourcedhelper)|調用此方法`UpdateRegistryFromResourceD`以執行註冊表更新。|
|[CAtlModule:從資源更新註冊](#updateregistryfromresources)|運行指定資源中包含的腳本以註冊或取消註冊物件。 此方法靜態連結到 ATL 註冊表元件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlModule:m_libid](#m_libid)|包含當前模組的 GUID。|
|[CAtlModule:m_pGIT](#m_pgit)|指向全域介面表的指標。|

## <a name="remarks"></a>備註

此類分別由[CAtlDllModuleT 類](../../atl/reference/catldllmodulet-class.md)[、CAtlExeModuleT 類](../../atl/reference/catlexemodulet-class.md)和[CAtl ServiceModuleT 類](../../atl/reference/catlservicemodulet-class.md)使用,分別為 DLL 應用程式、EXE 應用程式和 Windows 服務提供支援。

有關 ATL 中的模組的詳細資訊,請參閱[ATL 模組類](../../atl/atl-module-classes.md)。

此會取代早期版本的 ATL 中使用的過時的[CComModule 類別](../../atl/reference/ccommodule-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtl 模組:新增公共 RGS 取代

重寫此方法以將參數添加到 ATL 註冊表元件 (註冊商) 替換映射。

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>參數

*p 註冊商*<br/>
已保留。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

可替換參數允許註冊器的用戶端指定運行時數據。 為此,註冊器維護一個替換映射,在其中輸入與腳本中可替換參數關聯的值。 註冊器在運行時進行這些條目。

有關詳細資訊,請參閱["使用可替換參數(註冊器的預處理器)"](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)主題。

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtl 模組::添加TermFunc

添加在模組終止時要調用的新功能。

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>參數

*普豐克*<br/>
指向要添加的函數的指標。

*dw*<br/>
使用者定義的數據,傳遞給函數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtl 模組:CAtl 模組

建構函式。

```
CAtlModule() throw();
```

### <a name="remarks"></a>備註

初始化數據成員並圍繞模組的線程啟動關鍵部分。

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtl 模組:_CAtl 模組

解構函式。

```
~CAtlModule() throw();
```

### <a name="remarks"></a>備註

釋放所有數據成員。

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtl 模組:取得 GITPtr

檢索指向全域介面表的指標。

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>參數

*ppGIT*<br/>
指向將接收指向全域介面表的指標的變數的指標。

### <a name="return-value"></a>傳回值

返回成功時S_OK,或失敗時返回錯誤代碼。 如果*ppGIT*等於 NULL,則返回E_POINTER。

### <a name="remarks"></a>備註

如果全域介面表物件不存在,則創建該物件,其位址儲存在成員變數[CAtlModule:::m_pGIT](#m_pgit)。

在除錯產生中,如果*ppGIT*等於NULL,或者無法取得全域介面表指標,則會發生斷言錯誤。

有關全域介面表的資訊,請參閱[IGlobal 介面表](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable)。

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtl 模組::取得鎖定計數

返回鎖計數。

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>傳回值

返回鎖計數。 此值可用於診斷和調試。

## <a name="catlmodulelock"></a><a name="lock"></a>CAtl 模組:鎖定

增加鎖計數。

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>傳回值

增加鎖計數並返回更新的值。 此值可用於診斷和調試。

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModule:m_libid

包含當前模組的 GUID。

```
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModule:m_pGIT

指向全域介面表的指標。

```
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtl 模組::學期

釋放所有數據成員。

```
void Term() throw();
```

### <a name="remarks"></a>備註

釋放所有數據成員。 此方法由析構函數調用。

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtl 模組:解鎖

減量鎖定計數。

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>傳回值

正在撤銷鎖計數並返回更新的值。 此值可用於診斷和調試。

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::更新註冊從資源D

運行指定資源中包含的腳本以註冊或取消註冊物件。

```
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

*b 註冊*<br/>
如果應註冊物件,則為 TRUE;否則。

*pMap 項目*<br/>
指向替換映射的指標,儲存與腳本的可替換參數關聯的值。 ATL 自動使用 %MODULE%。 要使用其他可取代參數,請參閱[CAtlModule:: 新增通用 RGS 取代](#addcommonrgsreplacements)項目 。 否則,請使用 NULL 預設值。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

執行*lpszRes 或 nResID*指定的資源中包含的文稿。 如果*b寄存器*為 TRUE,則此方法將註冊系統註冊表中的物件;如果 b 寄存器為 TRUE,則此方法將註冊到系統註冊表中的物件。否則,它將物件從註冊表中刪除。

要靜態連結到 ATL 註冊表元件 (註冊),請參閱[CAtlModule::更新註冊表來自資源](#updateregistryfromresources)。

此方法呼叫[CAtlModule::從資源DHelper](#updateregistryfromresourcedhelper)和 IRegistrar 更新註冊[::資源未註冊](iregistrar-class.md#resourceunregister)。

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule:從資源説明程式更新註冊

調用此方法`UpdateRegistryFromResourceD`以執行註冊表更新。

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>參數

*lpszRes*<br/>
資源名稱。

*b 註冊*<br/>
指示是否應註冊物件。

*pMap 項目*<br/>
指向替換映射的指標,儲存與腳本的可替換參數關聯的值。 ATL 自動使用 %MODULE%。 要使用其他可取代參數,請參閱[CAtlModule:: 新增通用 RGS 取代](#addcommonrgsreplacements)項目 。 否則,請使用 NULL 預設值。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此方法提供[CAtlModule 的實現::更新註冊從資源D。](#updateregistryfromresourced)

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule:從資源更新註冊

運行指定資源中包含的腳本以註冊或取消註冊物件。 此方法靜態連結到 ATL 註冊表元件。

```
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

*b 註冊*<br/>
指示是否應註冊資源腳本。

*pMap 項目*<br/>
指向替換映射的指標,儲存與腳本的可替換參數關聯的值。 ATL 自動使用 %MODULE%。 要使用其他可取代參數,請參閱[CAtlModule:: 新增通用 RGS 取代](#addcommonrgsreplacements)項目 。 否則,請使用 NULL 預設值。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

類似於[CAtlModule::更新註冊註冊從資源D,](#updateregistryfromresourced)除了`CAtlModule::UpdateRegistryFromResourceS`創建一個靜態連結到 ATL 註冊表元件 (註冊)。

## <a name="see-also"></a>另請參閱

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[模組類](../../atl/atl-module-classes.md)<br/>
[登錄元件 (登錄器)](../../atl/atl-registry-component-registrar.md)
