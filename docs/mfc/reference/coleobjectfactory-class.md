---
title: COleObjectFactory 類別 |Microsoft 文件
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
ms.openlocfilehash: 706cc03e3f0a074e68d0e92acdce5a747552819b
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038204"
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
|[COleObjectFactory::GetClassID](#getclassid)|傳回 OLE 類別的這個處理站會建立物件的識別碼。|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|判斷控制項的授權是否有效。|  
|[COleObjectFactory::IsRegistered](#isregistered)|表示的物件 factory 是否已向 OLE 系統 Dll。|  
|[COleObjectFactory::Register](#register)|使用 OLE 系統 Dll，註冊此物件 factory。|  
|[COleObjectFactory::RegisterAll](#registerall)|使用 OLE 系統 Dll，註冊所有的應用程式的物件 factory。|  
|[COleObjectFactory::Revoke](#revoke)|撤銷此物件 factory OLE 系統 Dll 登錄。|  
|[COleObjectFactory::RevokeAll](#revokeall)|撤銷與 OLE 系統 Dll 的應用程式的物件 factory 註冊。|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|取消登錄所有的應用程式的物件 factory。|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|使用 OLE 系統登錄中註冊這個物件 factory。|  
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|註冊 OLE 系統登錄的所有應用程式的物件 factory。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|要求從控制項之 DLL 的唯一索引鍵。|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|由架構呼叫以建立新的物件，這個處理站類型。|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|確認內嵌在控制項中的索引鍵符合內嵌在容器中的索引鍵。|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|確認控制項係供設計階段使用。|  
  
## <a name="remarks"></a>備註  
 `COleObjectFactory`類別具有成員函式用於執行下列功能：  
  
-   管理物件的註冊。  
  
-   正在更新 OLE 系統暫存器，以及執行階段註冊，以通知 OLE 物件正在執行，並準備好接收訊息。  
  
-   強制執行限制控制項授權的開發人員在設計階段，並在執行階段授權的應用程式使用方式的授權。  
  
-   向 OLE 系統登錄中的控制項物件 factory。  
  
 如需建立物件的詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)和[資料物件和資料來源： 建立和解構](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。 如需詳細資訊註冊，請參閱文章[註冊](../../mfc/registration.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory  
 建構`COleObjectFactory`物件，作為取消註冊的物件處理站，將它初始化，並將其加入清單的 factory。  
  
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
 代表此物件 factory 的 OLE 類別 ID 的參考。  
  
 *pRuntimeClass*  
 此處理站可建立的 c + + 物件的執行階段類別的指標。  
  
 *bMultiInstance*  
 表示應用程式的單一執行個體是否可以支援多個具現化。 如果**TRUE**，針對每個要求建立物件啟動應用程式的多個執行個體。  
  
 *nFlags*  
 包含一或多個下列旗標：  
  
- **afxRegDefault**的執行緒模式設為 ThreadingModel = Apartment。  
  
- **afxRegInsertable**讓控制項出現在**插入物件**OLE 物件 對話方塊。  
  
- **afxRegApartmentThreading** ThreadingModel 登錄中設定執行緒模型 = Apartment。  
  
- **afxRegFreeThreading** ThreadingModel 登錄中設定執行緒模型 = 可用。  
  
     您可以結合兩個旗標`afxRegApartmentThreading`和`afxRegFreeThreading`設定 ThreadingModel = Both。 請參閱[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)執行緒模型註冊的詳細資訊的 Windows SDK 中。  
  
 *lpszProgID*  
 指向字串，包含動詞化的程式識別項，例如"Microsoft Excel"。  
  
### <a name="remarks"></a>備註  
 若要使用的物件，不過，您必須註冊它。  
  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getclassid"></a>  COleObjectFactory::GetClassID  
 傳回此處理站所代表的 OLE 類別 ID 的參考。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 表示此 factory 的 OLE 類別 ID 的參考。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey  
 從控制項之 DLL 要求一個唯一的授權金鑰，並將其儲存在`BSTR`指向*pbstrKey*。  
  
```  
virtual BOOL GetLicenseKey(
    DWORD dwReserved,  
    BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>參數  
 *dwReserved*  
 保留供未來使用。  
  
 *pbstrKey*  
 指標`BSTR`將儲存的授權金鑰。  
  
### <a name="return-value"></a>傳回值  
 如果授權金鑰字串不會為非零**NULL**; 否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會傳回 0，並將儲存在中為 nothing `BSTR`。 如果您使用 MFC ActiveX ControlWizard 來建立專案時，ControlWizard 可提供擷取控制項的授權金鑰的覆寫。  
  
##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid  
 判斷控制項的授權是否有效。  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>傳回值  
 TRUE，否則 successul;否則為 false。  
  
##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered  
 如果此處理站已向 OLE 系統 Dll，則傳回非零值。  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已註冊之處理站;否則便是 0。  
  
##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject  
 由架構呼叫以建立新的物件。  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>傳回值  
 建立物件的指標。 如果失敗，它可以擲回記憶體例外狀況。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式以外建立的物件從某項目[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)傳遞至建構函式。  
  
##  <a name="register"></a>  COleObjectFactory::Register  
 使用 OLE 系統 Dll，註冊此物件 factory。  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>傳回值  
 已成功註冊之處理站; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式[Afxenablecontrolcontainer](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="registerall"></a>  COleObjectFactory::RegisterAll  
 使用 OLE 系統 Dll，註冊所有的應用程式的物件 factory。  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>傳回值  
 已成功註冊之處理站; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式[Afxenablecontrolcontainer](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="revoke"></a>  COleObjectFactory::Revoke  
 撤銷此物件 factory OLE 系統 Dll 登錄。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>備註  
 架構會在應用程式終止前自動呼叫此函式。 如果有必要，請呼叫它的覆寫從[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll  
 撤銷所有與 OLE 系統 Dll 的應用程式的物件 factory 註冊。  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>備註  
 架構會在應用程式終止前自動呼叫此函式。 如果有必要，請呼叫它的覆寫從[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll  
 取消登錄所有的應用程式的物件 factory。  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry  
 註冊 OLE 系統登錄的所有應用程式的物件 factory。  
  
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
 請依照下列兩種格式，這個函式的簡短討論：  
  
- **UpdateRegistry (** `lpszProgID` **)** OLE 系統登錄中註冊這個物件 factory。 通常會呼叫此函式[Afxenablecontrolcontainer](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
- **UpdateRegistry (** `bRegister` **)** 這種形式的函式是可覆寫。 如果*bRegister*是**TRUE**，此函式會向系統登錄註冊控制項類別。 否則，它會移除註冊類別。  
  
     如果您使用 MFC ActiveX ControlWizard 來建立專案時，ControlWizard 提供覆寫，此純虛擬函式。  
  
##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll  
 註冊 OLE 系統登錄的所有應用程式的物件 factory。  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bRegister*  
 判斷是否要註冊的控制項類別的物件 factory。  
  
### <a name="return-value"></a>傳回值  
 已成功更新之處理站; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式[Afxenablecontrolcontainer](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey  
 驗證容器已授權可使用 OLE 控制項。  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>參數  
 *bstrKey*  
 A`BSTR`儲存授權字串的容器的版本。  
  
### <a name="return-value"></a>傳回值  
 如果執行階段授權有效，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 預設版本呼叫[GetLicenseKey](#getlicensekey)取得控制項的副本的授權字串並比較它與中的字串*bstrKey*。 如果兩個字串相符，函數會傳回非零值;否則會傳回 0。  
  
 您可以覆寫此函式可提供自訂的驗證的授權。  
  
 此函式[VerifyUserLicense](#verifyuserlicense)確認設計階段授權。  
  
##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense  
 確認 OLE 控制項的設計階段授權。  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>傳回值  
 如果設計階段授權有效，則為非零否則便是 0。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
