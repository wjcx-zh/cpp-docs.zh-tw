---
title: "伺服器註冊全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
dev_langs:
- C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f5cfffbcc47555ee8cff7cd6e18ea54b5524607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="server-registration-global-functions"></a>伺服器註冊全域函式
這些函式可註冊及取消註冊物件對應中的伺服器物件的支援。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。  
  
|||  
|-|-|  
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|呼叫此函式可在物件對應中註冊每個物件。|  
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|呼叫此函式可在物件對應中移除每個物件的註冊。|  
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|呼叫此函式可註冊類別物件。|  
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|您可以呼叫此函式撤銷類別物件，從 COM 模組。|  
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|呼叫此函式，以取得類別物件。|  

## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
   
##  <a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer  
 呼叫此函式可在物件對應中註冊每個物件。  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>參數  
 `pComModule`  
 COM 模組指標。  
  
 `bRegTypeLib`  
 如果類型程式庫註冊，則為 TRUE。  
  
 `pCLSID`  
 指向 CLSID 要註冊的物件。 如果是 NULL，就會註冊在物件對應中的所有物件。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 `AtlComModuleRegisterServer`將逐步引導 ATL 自動產生物件的對應，對應中註冊每個物件。 如果`pCLSID`不是 NULL，則只將所參考的物件`pCLSID`註冊; 否則會註冊的所有物件。  
  
 會呼叫此函式[CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)。  
  
##  <a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer  
 呼叫此函式可在物件對應中移除每個物件的註冊。  
  
```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>參數  
 `pComModule`  
 COM 模組指標。  
  
 `bUnRegTypeLib`  
 如果類型程式庫註冊，則為 TRUE。  
  
 `pCLSID`  
 要移除註冊物件的 clsid 點。 如果是 NULL 的物件對應中的所有物件都將取消登錄。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 `AtlComModuleUnregisterServer`將逐步引導 ATL 物件對應，並取消註冊對應中的每個物件。 如果`pCLSID`不是 NULL，則只將所參考的物件`pCLSID`已取消註冊，否則所有物件會取消註冊。  
  
 會呼叫此函式[CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver)。  
  
##  <a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects  
 呼叫此函式可註冊類別物件。  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>參數  
 `pComModule`  
 COM 模組指標。  
  
 `dwClsContext`  
 指定要執行的類別物件的內容。 可能的值為 CLSCTX_INPROC_SERVER、 CLSCTX_INPROC_HANDLER 或 CLSCTX_LOCAL_SERVER。 請參閱[CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716)如需詳細資訊。  
  
 `dwFlags`  
 決定類別物件的連接類型。 可能的值為 REGCLS_SINGLEUSE、 REGCLS_MULTIPLEUSE 或 REGCLS_MULTI_SEPARATE。 請參閱[REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式使用[CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) （ATL 7.0 中已過時） 和[CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects)。  
  
##  <a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects  
 呼叫此函式可從執行中的物件表格移除 Class Factory。  
  
```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```  
  
### <a name="parameters"></a>參數  
 `pComModule`  
 COM 模組指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式使用[CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) （ATL 7.0 中已過時） 和[CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects)。  
  
##  <a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject  
 呼叫此函式會傳回 Class Factory。  
  
```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```  
  
### <a name="parameters"></a>參數  
 `pComModule`  
 COM 模組指標。  
  
 `rclsid`  
 建立物件的 CLSID。  
  
 `riid`  
 所要求介面的 IID。  
  
 `ppv`  
 所識別的介面指標的指標`riid`。 如果物件不支援這個介面，`ppv`設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個 helper 函式使用[CComModule::GetClassObject](ccommodule-class.md#getclassobject) （ATL 7.0 中已過時） 和[CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject)。  
  
## <a name="see-also"></a>請參閱  
 [函式](../../atl/reference/atl-functions.md)
