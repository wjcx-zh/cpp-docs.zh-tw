---
title: 登錄和 TypeLib 全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af2780c8b7fb332cd739416e5051a57a8bc7f765
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073528"
---
# <a name="registry-and-typelib-global-functions"></a>登錄和 TypeLib 全域函式

這些函式會提供載入及註冊類型程式庫的支援。

> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AfxRegCreateKey](#afxrefcreatekey)|建立指定的登錄機碼。|
|[AfxRegDeleteKey](#afxrefdeletekey)|刪除指定的登錄機碼。|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|註冊預覽處理常式的協助程式。|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| 用來取消註冊預覽處理常式的協助程式。 |
|[AtlRegisterTypeLib](#atlregistertypelib)|呼叫此函式可註冊類型程式庫。|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|若要取消註冊類型程式庫呼叫此函式|
|[AfxRegOpenKey](#afxregopenkey)|開啟指定的登錄機碼。|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|開啟指定的登錄機碼。|
|[AtlLoadTypeLib](#atlloadtypelib)|呼叫此函式可載入類型程式庫。|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|呼叫此函式可更新所提供資源的登錄。|
|[RegistryDataExchange](#registrydataexchange)|呼叫此函式可對系統登錄執行讀取或寫入。 由呼叫[登錄資料交換巨集](../../atl/reference/registry-data-exchange-macros.md)。|

這些函式會控制哪一個程式用來存放資訊的登錄中的節點。

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|擷取應用程式重新導向登錄存取權是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|設定應用程式重新導向登錄存取權是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。|

### <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration

使用此函式來判斷應用程式是否將登錄存取重新導向**HKEY_CURRENT_USER** (**HKCU**) 節點。

### <a name="syntax"></a>語法

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>參數

*pEnabled*<br/>
[out]TRUE 表示登錄資訊會導向至**HKCU**節點;FALSE 表示，應用程式會將登錄資訊寫入至預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** (**HKCR**)。

### <a name="return-value"></a>傳回值

如果方法成功 s_ok 時，否則 HRESULT 錯誤的程式碼發生錯誤。

### <a name="remarks"></a>備註

預設不啟用登錄重新導向。 如果您啟用此選項，重新導向至的登錄存取權**HKEY_CURRENT_USER\Software\Classes**。

重新導向不是全域的。 只有 MFC 和 ATL 架構會受到此登錄重新導向。

### <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="afxregcreatekey"></a> AfxRegCreateKey

建立指定的登錄機碼。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制代碼。

*lpSubKey*<br/>
此函式會開啟或建立的索引鍵名稱。

*phkResult*<br/>
收到的開啟或建立金鑰的控制代碼變數的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果此函數成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回的值就會為 Winerror.h 中定義的非零的錯誤碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxregdeletekey"></a> AfxRegDeleteKey

刪除指定的登錄機碼。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制代碼。

*lpSubKey*<br/>
要刪除的金鑰名稱。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果此函數成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回的值就會為 Winerror.h 中定義的非零的錯誤碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

註冊預覽處理常式的協助程式。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>參數

*lpszCLSID*<br/>
指定處理常式的 CLSID。

*lpszShortTypeName*<br/>
指定處理常式的 ProgID。

*lpszFilterExt*<br/>
指定已向此處理常式註冊的副檔名。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="atlregistertypelib"></a>  AtlRegisterTypeLib

呼叫此函式可註冊類型程式庫。

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>參數

*hInstTypeLib*<br/>
模組執行個體控制代碼。

*lpszIndex*<br/>
格式字串"\\\N 」，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

此協助程式函式會利用[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)並[CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)。

### <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="afxregopenkey"></a> AfxRegOpenKey

開啟指定的登錄機碼。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制代碼。

*lpSubKey*<br/>
此函式會開啟或建立的索引鍵名稱。

*phkResult*<br/>
收到建立的索引鍵的控制代碼變數的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果此函數成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回的值就會為 Winerror.h 中定義的非零的錯誤碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxregopenkeyex"></a>  AfxRegOpenKeyEx

開啟指定的登錄機碼。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制代碼。

*lpSubKey*<br/>
此函式會開啟或建立的索引鍵名稱。

*ulOptions*<br/>
這個參數已保留，而且必須為零。

*samDesired*<br/>
遮罩，指定索引鍵的所需的存取權限。

*phkResult*<br/>
此變數會接收開啟金鑰的控制代碼指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果此函數成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回的值就會為 Winerror.h 中定義的非零的錯誤碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler

用來取消註冊預覽處理常式的協助程式。

### <a name="syntax"></a>語法

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>參數

*lpszCLSID*<br/>
指定要取消註冊之處理常式的 CLSID。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration

設定應用程式重新導向登錄存取權是否**HKEY_CURRENT_USER** (**HKCU**) 節點。

### <a name="syntax"></a>語法

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]TRUE 表示登錄資訊會導向至**HKCU**節點;FALSE 表示，應用程式會將登錄資訊寫入至預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** (**HKCR**)。

### <a name="return-value"></a>傳回值

如果方法成功 s_ok 時，否則 HRESULT 錯誤的程式碼發生錯誤。

### <a name="remarks"></a>備註

預設不啟用登錄重新導向。 如果您啟用此選項，重新導向至的登錄存取權**HKEY_CURRENT_USER\Software\Classes**。

重新導向不是全域的。 只有 MFC 和 ATL 架構會受到此登錄重新導向。

### <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="atlunregistertypelib"></a>  AtlUnRegisterTypeLib

呼叫此函式可解除類型程式庫的註冊。

### <a name="syntax"></a>語法

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>參數

*hInstTypeLib*<br/>
模組執行個體控制代碼。

*lpszIndex*<br/>
格式字串"\\\N 」，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

此協助程式函式會利用[CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib)並[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)。

### <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="atlloadtypelib"></a>  AtlLoadTypeLib

呼叫此函式可載入類型程式庫。

### <a name="syntax"></a>語法

```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```

### <a name="parameters"></a>參數

*hInstTypeLib*<br/>
型別程式庫相關聯的模組的控制代碼。

*lpszIndex*<br/>
格式字串"\\\N 」，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。

*pbstrPath*<br/>
在成功傳回時，包含與型別程式庫相關聯的模組的完整路徑。

*ppTypeLib*<br/>
在成功傳回時，包含要載入的型別程式庫指標的指標。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

此協助程式函式會利用[AtlRegisterTypeLib](#atlregistertypelib)並[AtlUnRegisterTypeLib](#atlunregistertypelib)。

##  <a name="atlupdateregistryfromresourced"></a>  AtlUpdateRegistryFromResourceD

此函式在 Visual Studio 2013 中已被取代並在 Visual Studio 2015 中移除。

```
<removed>
```

##  <a name="registrydataexchange"></a>  RegistryDataExchange

呼叫此函式可對系統登錄執行讀取或寫入。

### <a name="syntax"></a>語法

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>參數

*太平洋時間*<br/>
目前物件的指標。

*rdxOp*<br/>
列舉值，指出哪一個作業應該執行的函式。 請參閱 < 備註 > 一節針對允許的值。

*pItem*<br/>
要讀取或寫入登錄的資料指標。 資料也可以代表要刪除的登錄機碼。 預設值是 NULL。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

巨集會[BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)並[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)呼叫的函式展開`RegistryDataExchange`。

下表會顯示可能的列舉值，指出應執行作業的函式：

|列舉值|運算|
|----------------|---------------|
|eReadFromReg|從登錄讀取資料。|
|eWriteToReg|將資料寫入至登錄。|
|eDeleteFromReg|從登錄中刪除金鑰。|

### <a name="requirements"></a>需求

**標頭：** atlbase.h

## <a name="see-also"></a>另請參閱

[函式](atl-functions.md)<br/>
[登錄資料交換巨集](registry-data-exchange-macros.md)
