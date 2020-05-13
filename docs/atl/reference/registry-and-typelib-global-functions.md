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
ms.openlocfilehash: 69df927ddd04c19d10703854aa8c8948894309d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326083"
---
# <a name="registry-and-typelib-global-functions"></a>登錄和 TypeLib 全域函式

這些函數支援載入和註冊類型庫。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|創建指定的註冊表項。|
|[AfxRegDeleteKey](#afxregdeletekey)|刪除指定的註冊表項。|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|註冊預覽處理常式的協助程式。|
|[AfxUn寄存器預覽處理程式](#afxunregisterpreviewhandler)| 用來取消註冊預覽處理常式的協助程式。 |
|[AtlRegisterTypeLib](#atlregistertypelib)|呼叫此函式可註冊類型程式庫。|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|呼叫此功能以取消註冊型態庫|
|[AfxRegOpenKey](#afxregopenkey)|打開指定的註冊表項。|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|打開指定的註冊表項。|
|[AtlLoadTypeLib](#atlloadtypelib)|呼叫此函式可載入類型程式庫。|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|呼叫此函式可更新所提供資源的登錄。|
|[RegistryDataExchange](#registrydataexchange)|呼叫此函式可對系統登錄執行讀取或寫入。 由[註冊表資料交換巨集](../../atl/reference/registry-data-exchange-macros.md)呼叫 。|

這些函數控制程式用於存儲資訊的註冊表中的哪個節點。

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|檢索應用程式是否重定向註冊表訪問**HKEY_CURRENT_USER** ( **HKCU**) 節點。|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|設置應用程式是否重定向註冊表訪問**HKEY_CURRENT_USER** ( **HKCU**) 節點。|

### <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>AtlGetPer使用者註冊

使用此函數可確定應用程式是否重定向註冊表訪問**HKEY_CURRENT_USER** (**HKCU**) 節點。

### <a name="syntax"></a>語法

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>參數

*p 開啟*<br/>
[出]TRUE 表示註冊表資訊定向到**HKCU**節點;FALSE 表示應用程式將註冊表資訊寫入預設節點。 默認節點為**HKEY_CLASSES_ROOT** **(HKCR**)。

### <a name="return-value"></a>傳回值

如果該方法成功,S_OK,否則發生錯誤時為 HRESULT 錯誤代碼。

### <a name="remarks"></a>備註

默認情況下,未啟用註冊表重定向。 開啟這個選項,註冊表存取到**HKEY_CURRENT_USER\軟體\類別**。

重定向不是全域的。 只有 MFC 和 ATL 框架受此註冊表重定向的影響。

### <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a>AfxReg建立鍵

創建指定的註冊表項。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*h鍵*<br/>
打開註冊表項的句柄。

*lpSubkey*<br/>
此函數打開或創建的鍵的名稱。

*phkResult*<br/>
指向接收打開或創建的鍵的句柄的變數的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值ERROR_SUCCESS。 如果函數失敗,返回值是在 Winerror.h 中定義的非零錯誤代碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a>AfxReg 移除鍵

刪除指定的註冊表項。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*h鍵*<br/>
打開註冊表項的句柄。

*lpSubkey*<br/>
要刪除的鍵的名稱。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值ERROR_SUCCESS。 如果函數失敗,返回值是在 Winerror.h 中定義的非零錯誤代碼。

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

*lpsz短類型名稱*<br/>
指定處理常式的 ProgID。

*lpszFilterExt*<br/>
指定已向此處理常式註冊的副檔名。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib

呼叫此函式可註冊類型程式庫。

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>參數

*hInstTypeLib*<br/>
模組實例的句柄。

*lpszIndex*<br/>
格式為"\N"\\的字串,其中 N 是類型庫資源的整數索引。 如果不需要索引,則可以為 NULL。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此說明程式功能由[AtlComModuleUn 寄存器伺服器](server-registration-global-functions.md#atlcommoduleunregisterserver)與[CAtlComModule 使用:寄存器類型Lib](../../atl/reference/catlcommodule-class.md#registertypelib)。

### <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a>AfxRegOpenKey

打開指定的註冊表項。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*h鍵*<br/>
打開註冊表項的句柄。

*lpSubkey*<br/>
此函數打開或創建的鍵的名稱。

*phkResult*<br/>
指向接收已建立金鑰句柄的變數的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值ERROR_SUCCESS。 如果函數失敗,返回值是在 Winerror.h 中定義的非零錯誤代碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

打開指定的註冊表項。

### <a name="syntax"></a>語法

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>參數

*h鍵*<br/>
打開註冊表項的句柄。

*lpSubkey*<br/>
此函數打開或創建的鍵的名稱。

*ulOptions*<br/>
此參數已保留,必須為零。

*薩姆·阿喬*<br/>
指定對金鑰的所需存取許可權的掩碼。

*phkResult*<br/>
指向接收打開的鍵句柄的變數的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果函數成功,則返回值ERROR_SUCCESS。 如果函數失敗,返回值是在 Winerror.h 中定義的非零錯誤代碼。

### <a name="requirements"></a>需求

**Header:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a>AfxUn寄存器預覽處理程式

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

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>AtlSetPer使用者註冊

設置應用程式是否重定向註冊表訪問**HKEY_CURRENT_USER** (**HKCU**) 節點。

### <a name="syntax"></a>語法

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 表示註冊表資訊定向到**HKCU**節點;FALSE 表示應用程式將註冊表資訊寫入預設節點。 默認節點為**HKEY_CLASSES_ROOT** **(HKCR**)。

### <a name="return-value"></a>傳回值

如果該方法成功,S_OK,否則發生錯誤時為 HRESULT 錯誤代碼。

### <a name="remarks"></a>備註

默認情況下,未啟用註冊表重定向。 開啟這個選項,註冊表存取到**HKEY_CURRENT_USER\軟體\類別**。

重定向不是全域的。 只有 MFC 和 ATL 框架受此註冊表重定向的影響。

### <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUn註冊類型Lib

呼叫此函式可解除類型程式庫的註冊。

### <a name="syntax"></a>語法

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>參數

*hInstTypeLib*<br/>
模組實例的句柄。

*lpszIndex*<br/>
格式為"\N"\\的字串,其中 N 是類型庫資源的整數索引。 如果不需要索引,則可以為 NULL。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

CAtlComModule 使用此說明器功能[::未註冊類型Lib](../../atl/reference/catlcommodule-class.md#unregistertypelib)和[AtlcomModuleUn 寄存器伺服器](server-registration-global-functions.md#atlcommoduleunregisterserver)。

### <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib

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
處理與類型庫關聯的模組。

*lpszIndex*<br/>
格式為"\N"\\的字串,其中 N 是類型庫資源的整數索引。 如果不需要索引,則可以為 NULL。

*pbstrPath*<br/>
成功返回時,包含與類型庫關聯的模組的完整路徑。

*ppTypeLib*<br/>
成功返回時,包含指向載入類型庫的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

此説明器功能由[AtlRegisterTypeLib](#atlregistertypelib)和[AtlunRegisterTypeLib](#atlunregistertypelib)使用。

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdate註冊中心

此函式在 Visual Studio 2013 中已被取代並在 Visual Studio 2015 中移除。

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a>登錄資料交換

呼叫此函式可對系統登錄執行讀取或寫入。

### <a name="syntax"></a>語法

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>參數

*鉑*<br/>
指向當前對象的指標。

*rdxOp*<br/>
指示函數應執行的操作的枚舉值。 有關允許的值,請參閱"備註"部分中的表。

*pItem*<br/>
指向要從註冊表讀取或寫入註冊表的數據的指標。 數據還可以表示要從註冊表中刪除的鍵。 預設值是 NULL。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

宏[BEGIN_RDX_MAP,END_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)擴展[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)到調`RegistryDataExchange`用 的函數。

指示函數應執行的操作的可能枚舉值顯示在下表中:

|Enlt|作業|
|----------------|---------------|
|eRead 從雷格|從註冊表讀取數據。|
|eWriteToreg|將數據寫入註冊表。|
|e 刪除從雷格|從註冊表中刪除金鑰。|

### <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="see-also"></a>另請參閱

[函式](atl-functions.md)<br/>
[註冊表資料交換巨集](registry-data-exchange-macros.md)
