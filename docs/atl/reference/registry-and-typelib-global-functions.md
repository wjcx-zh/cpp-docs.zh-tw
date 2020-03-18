---
title: 登錄和 TypeLib 全域函式
ms.date: 03/27/2019
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
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: c5fdaceb47b6cd09dd9d66f26af1337a8dc6bbae
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417492"
---
# <a name="registry-and-typelib-global-functions"></a>登錄和 TypeLib 全域函式

這些函式提供載入和註冊類型程式庫的支援。

> [!IMPORTANT]
>  下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|建立指定的登錄機碼。|
|[AfxRegDeleteKey](#afxregdeletekey)|刪除指定的登錄機碼。|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|註冊預覽處理常式的協助程式。|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| 用來取消註冊預覽處理常式的協助程式。 |
|[AtlRegisterTypeLib](#atlregistertypelib)|呼叫此函式可註冊類型程式庫。|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|呼叫此函式可取消註冊類型程式庫|
|[AfxRegOpenKey](#afxregopenkey)|開啟指定的登錄機碼。|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|開啟指定的登錄機碼。|
|[AtlLoadTypeLib](#atlloadtypelib)|呼叫此函式可載入類型程式庫。|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|呼叫此函式可更新所提供資源的登錄。|
|[RegistryDataExchange](#registrydataexchange)|呼叫此函式可對系統登錄執行讀取或寫入。 由登錄[資料交換宏](../../atl/reference/registry-data-exchange-macros.md)呼叫。|

這些函式可控制程式用來儲存資訊的登錄中的節點。

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|抓取應用程式是否將登錄存取重新導向至**HKEY_CURRENT_USER** （ **HKCU**）節點。|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|設定應用程式是否將登錄存取重新導向至**HKEY_CURRENT_USER** （ **HKCU**）節點。|

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

使用此函式來判斷應用程式是否將登錄存取重新導向至**HKEY_CURRENT_USER** （**HKCU**）節點。

### <a name="syntax"></a>語法

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>參數

*pEnabled*<br/>
脫銷TRUE 表示登錄資訊會導向到**HKCU**節點;FALSE 表示應用程式會將登錄資訊寫入預設節點。 預設節點是**HKEY_CLASSES_ROOT** （**HKCR**）。

### <a name="return-value"></a>傳回值

如果方法成功，則 S_OK，否則為 HRESULT 錯誤碼（如果發生錯誤）。

### <a name="remarks"></a>備註

預設不會啟用登錄重新導向。 如果您啟用此選項，系統會將登錄存取重新導向至**HKEY_CURRENT_USER \software\classes**。

重新導向不是全域的。 只有 MFC 和 ATL 架構會受到此登錄重新導向的影響。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="afxregcreatekey"></a>AfxRegCreateKey

建立指定的登錄機碼。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制碼。

*lpSubKey*<br/>
此函式開啟或建立的索引鍵名稱。

*phkResult*<br/>
可接收已開啟或已建立索引鍵控制碼之變數的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 ERROR_SUCCESS。 如果函式失敗，則傳回值為 Winerror.h 中定義的非零錯誤碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxregdeletekey"></a>AfxRegDeleteKey

刪除指定的登錄機碼。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制碼。

*lpSubKey*<br/>
要刪除之金鑰的名稱。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 ERROR_SUCCESS。 如果函式失敗，則傳回值為 Winerror.h 中定義的非零錯誤碼。

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

##  <a name="atlregistertypelib"></a>AtlRegisterTypeLib

呼叫此函式可註冊類型程式庫。

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>參數

*hInstTypeLib*<br/>
模組實例的控制碼。

*lpszIndex*<br/>
格式為 "\\\N" 的字串，其中 N 是類型程式庫資源的整數索引。 如果不需要索引，則可以是 Null。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)和[CAtlComModule：： RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)會使用此 helper 函數。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="afxregopenkey"></a>AfxRegOpenKey

開啟指定的登錄機碼。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制碼。

*lpSubKey*<br/>
此函式開啟或建立的索引鍵名稱。

*phkResult*<br/>
接收所建立索引鍵控制碼之變數的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 ERROR_SUCCESS。 如果函式失敗，則傳回值為 Winerror.h 中定義的非零錯誤碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

開啟指定的登錄機碼。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*hKey*<br/>
開啟登錄機碼的控制碼。

*lpSubKey*<br/>
此函式開啟或建立的索引鍵名稱。

*ulOptions*<br/>
這個參數是保留的，而且必須為零。

*samDesired*<br/>
遮罩，指定所需的金鑰存取權限。

*phkResult*<br/>
可接收已開啟索引鍵控制碼之變數的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 ERROR_SUCCESS。 如果函式失敗，則傳回值為 Winerror.h 中定義的非零錯誤碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

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

## <a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration

設定應用程式是否將登錄存取重新導向至**HKEY_CURRENT_USER** （**HKCU**）節點。

### <a name="syntax"></a>語法

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示登錄資訊會導向到**HKCU**節點;FALSE 表示應用程式會將登錄資訊寫入預設節點。 預設節點是**HKEY_CLASSES_ROOT** （**HKCR**）。

### <a name="return-value"></a>傳回值

如果方法成功，則 S_OK，否則為 HRESULT 錯誤碼（如果發生錯誤）。

### <a name="remarks"></a>備註

預設不會啟用登錄重新導向。 如果您啟用此選項，系統會將登錄存取重新導向至**HKEY_CURRENT_USER \software\classes**。

重新導向不是全域的。 只有 MFC 和 ATL 架構會受到此登錄重新導向的影響。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

呼叫此函式可解除類型程式庫的註冊。

### <a name="syntax"></a>語法

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>參數

*hInstTypeLib*<br/>
模組實例的控制碼。

*lpszIndex*<br/>
格式為 "\\\N" 的字串，其中 N 是類型程式庫資源的整數索引。 如果不需要索引，則可以是 Null。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CAtlComModule：： UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib)和[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)會使用此 helper 函式。

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="atlloadtypelib"></a>AtlLoadTypeLib

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
與類型程式庫相關聯之模組的控制碼。

*lpszIndex*<br/>
格式為 "\\\N" 的字串，其中 N 是類型程式庫資源的整數索引。 如果不需要索引，則可以是 Null。

*pbstrPath*<br/>
在成功傳回時，包含與類型程式庫相關聯之模組的完整路徑。

*ppTypeLib*<br/>
在成功傳回時，包含已載入之類型程式庫之指標的指標。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[AtlRegisterTypeLib](#atlregistertypelib)和[AtlUnRegisterTypeLib](#atlunregistertypelib)會使用此 helper 函式。

##  <a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

此函式在 Visual Studio 2013 中已被取代並在 Visual Studio 2015 中移除。

```
<removed>
```

##  <a name="registrydataexchange"></a>RegistryDataExchange

呼叫此函式可對系統登錄執行讀取或寫入。

### <a name="syntax"></a>語法

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>參數

*pT*<br/>
目前物件的指標。

*rdxOp*<br/>
列舉值，指出函數應執行的作業。 如需允許的值，請參閱「備註」一節中的表格。

*pItem*<br/>
要在登錄中讀取或寫入之資料的指標。 資料也可以代表要從登錄中刪除的索引鍵。 預設值為 NULL。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

宏[BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)並[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)展開至呼叫 `RegistryDataExchange`的函式。

下表顯示可能的列舉值，指出函數應執行的作業：

|列舉值|作業|
|----------------|---------------|
|eReadFromReg|從登錄讀取資料。|
|eWriteToReg|將資料寫入登錄。|
|eDeleteFromReg|從登錄中刪除金鑰。|

### <a name="requirements"></a>需求

**標頭：** atlbase.h。h

## <a name="see-also"></a>另請參閱

[函數](atl-functions.md)<br/>
[登錄資料交換巨集](registry-data-exchange-macros.md)
