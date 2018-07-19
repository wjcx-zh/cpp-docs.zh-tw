---
title: COleObjectFactory 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d2ac698466709931259f1df28d6c75aa38b30f2
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850702"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory 類別
實作建立 OLE 物件 (例如伺服器、Automation 物件和文件) 的 OLE Class Factory。  
  
## <a name="syntax"></a>語法  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|建構 `COleObjectFactory` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|傳回 OLE 類別這個處理站所建立的物件的識別碼。|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|判斷控制項的授權是否有效。|  
|[COleObjectFactory::IsRegistered](#isregistered)|指出在 OLE 系統 Dll 是否已註冊的物件 factory。|  
|[COleObjectFactory::Register](#register)|此物件的處理站會向 OLE 系統 Dll。|  
|[COleObjectFactory::RegisterAll](#registerall)|使用 OLE 系統 Dll，註冊所有的應用程式的物件 factory。|  
|[COleObjectFactory::Revoke](#revoke)|撤銷此物件 factory 登錄 OLE 系統 Dll。|  
|[COleObjectFactory::RevokeAll](#revokeall)|撤銷具有 OLE 系統 Dll 的應用程式的物件 factory 的註冊。|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|取消註冊所有的應用程式的物件 factory。|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|使用 OLE 系統登錄中註冊這個物件 factory。|  
|[登錄下列項目](#updateregistryall)|使用 OLE 系統登錄，註冊所有的應用程式的物件 factory。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|要求的唯一索引鍵，從控制項的 DLL。|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|由架構呼叫以建立新的物件，此處理站型別。|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|驗證內嵌在控制項中的索引鍵符合索引鍵內嵌於容器中。|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|驗證控制項用於設計階段授權。|  
  
## <a name="remarks"></a>備註  
 `COleObjectFactory`類別有成員函式，執行下列功能：  
  
-   管理註冊的物件。  
  
-   正在更新 OLE 系統暫存器，以及執行階段註冊，以通知 OLE 物件正在執行，並準備好接收訊息。  
  
-   強制執行限制控制項授權的開發人員在設計階段和執行階段授權的應用程式的使用授權。  
  
-   使用 OLE 系統登錄中註冊控制項的物件 factory。  
  
 如需有關建立物件的詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)並[的資料物件和資料來源： 建立和解構](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。 如需有關註冊的詳細資訊，請參閱文章[註冊](../../mfc/registration.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory  
 建構`COleObjectFactory`物件，做為取消註冊的物件 factory，將它初始化，並將其加入的處理站清單。  
  
```  
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    LPCTSTR lpszProgID);

 
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    int nFlags,  
    LPCTSTR lpszProgID);
```  
  
### <a name="parameters"></a>參數  
 *clsid*  
 此物件的 factory 代表 OLE 類別 ID 的參考。  
  
 *pRuntimeClass*  
 此處理站可以建立的 c + + 物件的執行階段類別的指標。  
  
 *bMultiInstance*  
 指出應用程式的單一執行個體是否可以支援多個具現化。 如果為 TRUE，針對每個要求建立物件啟動應用程式的多個執行個體。  
  
 *nFlags*  
 包含一或多個下列旗標：  
  
- `afxRegDefault` 執行緒模型設 ThreadingModel = Apartment。  
  
- `afxRegInsertable` 可讓控制項出現在**插入物件**OLE 物件的對話方塊。  
  
- `afxRegApartmentThreading` ThreadingModel 登錄中設定執行緒模型 = Apartment。  
  
- `afxRegFreeThreading` ThreadingModel 登錄中設定執行緒模型 = 免費。  
  
     您可以結合兩個旗標`afxRegApartmentThreading`和`afxRegFreeThreading`設 ThreadingModel = Both。 請參閱[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)的執行緒模型註冊的更多有關 Windows SDK 中。  
  
 *lpszProgID*  
 指向字串，包含動詞化程式識別碼，例如 「 Microsoft Excel。 」  
  
### <a name="remarks"></a>備註  
 若要使用的物件，不過，您必須註冊它。  
  
 如需詳細資訊，請參閱 < [CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getclassid"></a>  COleObjectFactory::GetClassID  
 傳回表示此 factory OLE 類別 ID 的參考。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 OLE 類別識別碼此處理站的參考表示。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey  
 要求的唯一授權金鑰，從控制項的 DLL，並將它儲存在所指的 BSTR *pbstrKey*。  
  
```  
virtual BOOL GetLicenseKey(
    DWORD dwReserved,  
    BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>參數  
 *dwReserved*  
 保留供未來使用。  
  
 *pbstrKey*  
 BSTR，其中會儲存授權金鑰的指標。  
  
### <a name="return-value"></a>傳回值  
 授權金鑰字串不是 NULL; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會傳回 0，並將執行任何動作的 BSTR。 如果您要建立您的專案使用 MFC ActiveX ControlWizard，ControlWizard 會提供擷取控制項的授權金鑰的覆寫。  
  
##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid  
 判斷控制項的授權是否有效。  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>傳回值  
 如果 successul;否則為 false。  
  
##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered  
 如果 factory 已向 OLE 系統 Dll，則傳回非零值。  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果已註冊的 factory;否則為 0。  
  
##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject  
 由架構呼叫以建立新的物件。  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>傳回值  
 建立物件的指標。 如果失敗，它會擲回記憶體例外狀況。  
  
### <a name="remarks"></a>備註  
 此函式可從建立物件，而不會覆寫[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)傳遞至建構函式。  
  
##  <a name="register"></a>  COleObjectFactory::Register  
 此物件的處理站會向 OLE 系統 Dll。  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功註冊的 factory;，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="registerall"></a>  COleObjectFactory::RegisterAll  
 使用 OLE 系統 Dll，註冊所有的應用程式的物件 factory。  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果已成功註冊的 factory;否則為 0。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="revoke"></a>  COleObjectFactory::Revoke  
 撤銷此物件 factory 登錄 OLE 系統 Dll。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>備註  
 架構會在應用程式終止之前自動呼叫此函式。 如有需要，從呼叫的覆寫[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll  
 撤銷所有具有 OLE 系統 Dll 的應用程式的物件 factory 的註冊。  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>備註  
 架構會在應用程式終止之前自動呼叫此函式。 如有需要，從呼叫的覆寫[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll  
 取消註冊所有的應用程式的物件 factory。  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry  
 使用 OLE 系統登錄，註冊所有的應用程式的物件 factory。  
  
```  
void UpdateRegistry(LPCTSTR lpszProgID = NULL);  
virtual BOOL UpdateRegistry(BOOL bRegister);
```  
  
### <a name="parameters"></a>參數  
 *lpszProgID*  
 指向字串，包含人類看得懂的程式識別項，例如"Excel.Document.5"。  
  
 *bRegister*  
 判斷是否要註冊的控制項類別的物件 factory。  
  
### <a name="remarks"></a>備註  
 請依照下列兩種形式，此函式的簡短討論：  
  
- **UpdateRegistry (** `lpszProgID` **)** 向 OLE 系統登錄中的此物件 factory。 通常會呼叫此函式[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
- **UpdateRegistry (** `bRegister` **)** 這種形式的函式是可覆寫。 如果*bRegister*為 TRUE 時，此控制項類別系統登錄的函式暫存器。 否則，它會取消註冊類別。  
  
     如果您要建立您的專案使用 MFC ActiveX ControlWizard，ControlWizard 提供覆寫，此純虛擬函式。  
  
##  <a name="updateregistryall"></a>  登錄下列項目  
 使用 OLE 系統登錄，註冊所有的應用程式的物件 factory。  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bRegister*  
 判斷是否要註冊的控制項類別的物件 factory。  
  
### <a name="return-value"></a>傳回值  
 已成功更新之處理站; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey  
 確認容器已授權給使用 OLE 控制項。  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>參數  
 *bstrKey*  
 BSTR，儲存的授權字串的容器的版本。  
  
### <a name="return-value"></a>傳回值  
 如果執行階段授權無效，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設版本呼叫[GetLicenseKey](#getlicensekey)來取得控制項的複本的授權字串，並將它與中的字串進行比較*bstrKey*。 如果兩個字串相符，函數會傳回非零值;否則會傳回 0。  
  
 您可以覆寫這個函式，以提供自訂的驗證的授權。  
  
 此函式[VerifyUserLicense](#verifyuserlicense)確認設計階段授權。  
  
##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense  
 確認 OLE 控制項的設計階段授權。  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>傳回值  
 如果設計階段授權無效，則為非零否則為 0。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
