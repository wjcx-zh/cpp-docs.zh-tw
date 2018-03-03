---
title: "登錄和 TypeLib 全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dbb919cb2fe4d91f5665fbea3dcfd2140d178341
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="registry-and-typelib-global-functions"></a>登錄和 TypeLib 全域函式
這些函式提供載入及註冊類型程式庫支援。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。  
  
|||  
|-|-|  
|[AfxRegCreateKey](#afxrefcreatekey)|建立指定的登錄機碼。|
|[AfxRegDeleteKey](#afxrefdeletekey)|刪除指定的登錄機碼。|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|註冊預覽處理常式的協助程式。|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| 用來取消註冊預覽處理常式的協助程式。 |
|[AtlRegisterTypeLib](#atlregistertypelib)|呼叫此函式可註冊類型程式庫。|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|若要取消註冊類型程式庫會呼叫此函式|  
|[AfxRegOpenKey](#afxregopenkey)|開啟指定的登錄機碼。|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|開啟指定的登錄機碼。|
|[AtlLoadTypeLib](#atlloadtypelib)|呼叫此函式可載入類型程式庫。|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|呼叫此函式可更新所提供資源的登錄。|  
|[RegistryDataExchange](#registrydataexchange)|呼叫此函式可對系統登錄執行讀取或寫入。 由呼叫[登錄資料交換巨集](../../atl/reference/registry-data-exchange-macros.md)。|  
  
 這些函式會控制哪些程式會使用將資訊儲存在登錄中的節點。  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|擷取應用程式將登錄存取重新導向是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。|  
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|設定應用程式將登錄存取重新導向是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。|  

### <a name="requirements"></a>需求  
 **標頭：** atlbase.h

## <a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration
使用此函數來判斷應用程式是否將登錄存取重新導向**HKEY_CURRENT_USER** (**HKCU**) 節點。  
  
### <a name="syntax"></a>語法  
  
```  
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `pEnabled`  
 `TRUE`指出登錄資訊的重新導向至**HKCU**節點。`FALSE`表示，應用程式登錄資訊寫入預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** (**HKCR**)。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果方法成功，否則`HRESULT`如果發生錯誤的錯誤碼。  
  
### <a name="remarks"></a>備註  
 預設不啟用登錄重新導向。 如果您啟用此選項，重新導向至的登錄存取**HKEY_CURRENT_USER\Software\Classes**。  
  
 重新導向不是全域的。 僅適用的 MFC 和 ATL 架構會受到登錄重新導向。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlbase.h  

 ## <a name="afxregcreatekey"></a>AfxRegCreateKey
 建立指定的登錄機碼。  
  
### <a name="syntax"></a>語法  
  
```  
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>參數  
 `hKey`  
 開啟登錄機碼的控制代碼。  
  
 `lpSubKey`  
 此函式會開啟或建立索引鍵名稱。  
  
 `phkResult`  
 此變數會接收到已開啟或建立機碼的控制代碼指標。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回值會是 Winerror.h 中定義的非零的錯誤代碼。  

### <a name="requirements"></a>需求  
 **Header:** afxpriv.h  

## <a name="afxregdeletekey"></a>AfxRegDeleteKey
刪除指定的登錄機碼。  
  
### <a name="syntax"></a>語法  
  
```  
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>參數  
 `hKey`  
 開啟登錄機碼的控制代碼。  
  
 `lpSubKey`  
 要刪除之索引鍵名稱。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回值會是 Winerror.h 中定義的非零的錯誤代碼。  
  
### <a name="requirements"></a>需求  
 **Header:** afxpriv.h  

## <a name="afxregisterpreviewhandler"></a>
註冊預覽處理常式的協助程式。  
  
### <a name="syntax"></a>語法  
  
```  
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);  
```  
  
### <a name="parameters"></a>參數  
 `lpszCLSID`  
 指定處理常式的 CLSID。  
  
 `lpszShortTypeName`  
 指定處理常式的 ProgID。  
  
 `lpszFilterExt`  
 指定已向此處理常式註冊的副檔名。  
  
### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h   

##  <a name="atlregistertypelib"></a>AtlRegisterTypeLib  
 呼叫此函式可註冊類型程式庫。  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>參數  
 `hInstTypeLib`  
 模組執行個體控制代碼。  
  
 `lpszIndex`  
 格式字串"\\\N"，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式使用[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)和[CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)。  
### <a name="requirements"></a>需求  
 **標頭：** atlbase.h

 ## <a name="afxregopenkey"></a>AfxRegOpenKey
 開啟指定的登錄機碼。  
  
### <a name="syntax"></a>語法  
  
```  
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>參數  
 `hKey`  
 開啟登錄機碼的控制代碼。  
  
 `lpSubKey`  
 此函式會開啟或建立索引鍵名稱。  
  
 `phkResult`  
 收到建立的機碼的控制代碼變數的指標。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回值會是 Winerror.h 中定義的非零的錯誤代碼。  
  
### <a name="requirements"></a>需求  
 **Header:** afxpriv.h  

## <a name="afxregopenkeyex"></a>AfxRegOpenKeyEx
開啟指定的登錄機碼。 

### <a name="syntax"></a>語法  
  
```  
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>參數  
 `hKey`  
 開啟登錄機碼的控制代碼。  
  
 `lpSubKey`  
 此函式會開啟或建立索引鍵名稱。  
  
 `ulOptions`  
 這個參數已保留，而且必須是零。  
  
 `samDesired`  
 遮罩，指定索引鍵的所需的存取權限。  
  
 `phkResult`  
 此變數會接收已開啟的索引鍵的控制代碼指標。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則傳回的值會是 ERROR_SUCCESS。 如果函式失敗，傳回值會是 Winerror.h 中定義的非零的錯誤代碼。  
  
### <a name="requirements"></a>需求  
 **Header:** afxpriv.h  

 ## <a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler
 用來取消註冊預覽處理常式的協助程式。  
  
### <a name="syntax"></a>語法  
  
```  
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);  
```  
  
### <a name="parameters"></a>參數  
 `lpszCLSID`  
 指定要取消註冊之處理常式的 CLSID。  
  
### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  

## <a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration
設定應用程式將登錄存取重新導向是否**HKEY_CURRENT_USER** (**HKCU**) 節點。  
  
### <a name="syntax"></a>語法  
  
```  
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 `TRUE`指出登錄資訊的重新導向至**HKCU**節點。`FALSE`表示，應用程式登錄資訊寫入預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** (**HKCR**)。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果方法成功，否則`HRESULT`如果發生錯誤的錯誤碼。  
  
### <a name="remarks"></a>備註  
 預設不啟用登錄重新導向。 如果您啟用此選項，重新導向至的登錄存取**HKEY_CURRENT_USER\Software\Classes**。  
  
 重新導向不是全域的。 僅適用的 MFC 和 ATL 架構會受到登錄重新導向。  
### <a name="requirements"></a>需求  
 **標頭：** atlbase.h  

##  <a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib  
 呼叫此函式可解除類型程式庫的註冊。  
  
### <a name="syntax"></a>語法  
```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib, 
    LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>參數  
 `hInstTypeLib`  
 模組執行個體控制代碼。  
  
 `lpszIndex`  
 格式字串"\\\N"，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式使用[CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib)和[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)。  
### <a name="requirements"></a>需求  
 **標頭：** atlbase.h

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
 `hInstTypeLib`  
 類型程式庫相關聯的模組的控制代碼。  
  
 `lpszIndex`  
 格式字串"\\\N"，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。  
  
 *pbstrPath*  
 在成功傳回時，包含型別程式庫相關聯的模組的完整路徑。  
  
 `ppTypeLib`  
 在成功傳回時，包含要載入的型別程式庫指標的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式使用[AtlRegisterTypeLib](#atlregistertypelib)和[AtlUnRegisterTypeLib](#atlunregistertypelib)。  
  
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
 *pT*  
 目前物件的指標。  
  
 *rdxOp*  
 列舉值，指出哪一項作業應該執行此函式。 請參閱 < 備註 > 一節的允許值的資料表。  
  
 `pItem`  
 要讀取或寫入登錄的資料指標。 資料也可以代表要刪除的登錄機碼。 預設值是 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 巨集[BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)和[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)呼叫的函式展開`RegistryDataExchange`。  
  
 可能的列舉值，指出應執行作業的函式是下表所示：  
  
|列舉值|運算|  
|----------------|---------------|  
|eReadFromReg|從登錄讀取資料。|  
|eWriteToReg|資料寫入登錄。|  
|eDeleteFromReg|從登錄刪除機碼。|  
  
### <a name="requirements"></a>需求  
 **標頭：** atlbase.h

## <a name="see-also"></a>請參閱  
 [函式](atl-functions.md)[登錄資料交換巨集](registry-data-exchange-macros.md)





