---
title: "登錄和型別程式庫全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9d454f2eac1b29785fe40a480fc43c7c34a861a3
ms.lasthandoff: 02/24/2017

---
# <a name="registry-and-typelib-global-functions"></a>登錄和 TypeLib 全域函式
這些函式提供載入及註冊類型程式庫支援。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlRegisterTypeLib](#atlregistertypelib)|呼叫此函式可註冊類型程式庫。|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|若要取消註冊類型程式庫會呼叫此函數|  
|[AtlLoadTypeLib](#atlloadtypelib)|呼叫此函式可載入類型程式庫。|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|呼叫此函式可更新所提供資源的登錄。|  
|[RegistryDataExchange](#registrydataexchange)|呼叫此函式可對系統登錄執行讀取或寫入。 由呼叫[登錄資料交換巨集](../../atl/reference/registry-data-exchange-macros.md)。|  
  
 這些函式來控制哪些程式用來存放資訊的登錄中的節點。  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|擷取應用程式將登錄存取重新導向是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。|  
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|設定應用程式將登錄存取重新導向是否**HKEY_CURRENT_USER** ( **HKCU**) 節點。|  

### <a name="requirements"></a>需求  
 **標頭︰** atlbase.h

## <a name="a-nameatlgetperuserregistrationa-atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration
使用此函數來判斷應用程式是否將登錄存取重新導向**HKEY_CURRENT_USER** (**HKCU**) 節點。  
  
### <a name="syntax"></a>語法  
  
```  
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `pEnabled`  
 `TRUE`表示登錄資訊的重新導向至**HKCU**節點。`FALSE`表示，應用程式會將登錄資訊寫入至預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** (**HKCR**)。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果方法成功，否則`HRESULT`發生錯誤的錯誤碼。  
  
### <a name="remarks"></a>備註  
 預設不啟用登錄重新導向。 如果您啟用此選項，重新導向到的登錄存取**HKEY_CURRENT_USER\Software\Classes**。  
  
 重新導向不是全域範圍。 只有 MFC 和 ATL 架構會受到此登錄重新導向。  
  
### <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  

##  <a name="a-nameatlregistertypeliba--atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib  
 呼叫此函式可註冊類型程式庫。  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>參數  
 `hInstTypeLib`  
 模組執行個體控制代碼。  
  
 `lpszIndex`  
 格式字串"\\\N 」，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式利用[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)和[CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)。  
### <a name="requirements"></a>需求  
 **標頭︰** atlbase.h

## <a name="a-nameatlsetperuserregistrationa-atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration
設定應用程式將登錄存取重新導向是否**HKEY_CURRENT_USER** (**HKCU**) 節點。  
  
### <a name="syntax"></a>語法  
  
```  
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);  
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`表示登錄資訊的重新導向至**HKCU**節點。`FALSE`表示，應用程式會將登錄資訊寫入至預設的節點。 預設的節點是**HKEY_CLASSES_ROOT** (**HKCR**)。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果方法成功，否則`HRESULT`發生錯誤的錯誤碼。  
  
### <a name="remarks"></a>備註  
 預設不啟用登錄重新導向。 如果您啟用此選項，重新導向到的登錄存取**HKEY_CURRENT_USER\Software\Classes**。  
  
 重新導向不是全域範圍。 只有 MFC 和 ATL 架構會受到此登錄重新導向。  
### <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  

##  <a name="a-nameatlunregistertypeliba--atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib  
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
 格式字串"\\\N 」，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式利用[CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib)和[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)。  
### <a name="requirements"></a>需求  
 **標頭︰** atlbase.h

##  <a name="a-nameatlloadtypeliba--atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib  
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
 型別程式庫相關聯的模組的控制代碼。  
  
 `lpszIndex`  
 格式字串"\\\N 」，其中 N 是整數索引的類型程式庫資源。 如果沒有索引鍵為必要，可以是 NULL。  
  
 *pbstrPath*  
 在成功傳回時，包含型別程式庫相關聯的模組的完整路徑。  
  
 `ppTypeLib`  
 在成功傳回時，包含要載入的型別程式庫指標的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式利用[AtlRegisterTypeLib](#atlregistertypelib)和[AtlUnRegisterTypeLib](#atlunregistertypelib)。  
  
##  <a name="a-nameatlupdateregistryfromresourceda--atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD  
 此函式在 Visual Studio 2013 中已被取代並在 Visual Studio 2015 中移除。  
  
```
<removed>
```  
  
### <a name="parameters"></a>參數  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameregistrydataexchangea--registrydataexchange"></a><a name="registrydataexchange"></a>RegistryDataExchange  
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
 列舉值，表示作業應該執行函式。 請參閱 < 備註 > 一節，取得允許的值。  
  
 `pItem`  
 若要讀取或寫入登錄的資料指標。 資料也可以代表要刪除的登錄機碼。 預設值是 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 巨集[BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)和[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)呼叫的函式展開`RegistryDataExchange`。  
  
 可能的列舉值，表示應該執行作業的函式會顯示下表中︰  
  
|列舉值|運算|  
|----------------|---------------|  
|eReadFromReg|從登錄讀取資料。|  
|eWriteToReg|將資料寫入至登錄。|  
|eDeleteFromReg|從登錄刪除機碼。|  
  
### <a name="requirements"></a>需求  
 **標頭︰** atlbase.h

## <a name="see-also"></a>另請參閱  
 [函式](atl-functions.md)
 [登錄資料交換巨集](registry-data-exchange-macros.md)






