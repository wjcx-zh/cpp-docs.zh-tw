---
title: "COleObjectFactory 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleObjectFactory
dev_langs:
- C++
helpviewer_keywords:
- OLE, class factory
- OLE class factory
- COleObjectFactory class
- objects [C++], creating OLE
- OLE objects
- object creation, OLE objects
- class factories, COleObjectFactory class
- OLE objects, creating
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
caps.latest.revision: 21
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
ms.openlocfilehash: 643d17ccdefb60b561e7e5488753a6dbf778c69f
ms.lasthandoff: 02/24/2017

---
# <a name="coleobjectfactory-class"></a>COleObjectFactory 類別
實作建立 OLE 物件 (例如伺服器、Automation 物件和文件) 的 OLE Class Factory。  
  
## <a name="syntax"></a>語法  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|建構 `COleObjectFactory` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|傳回 OLE 類別 ID 的這個處理站所建立的物件。|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|判斷控制項的授權是否有效。|  
|[COleObjectFactory::IsRegistered](#isregistered)|表示的物件 factory 已向 OLE 系統 Dll。|  
|[COleObjectFactory::Register](#register)|此物件處理站會向 OLE 系統 Dll。|  
|[COleObjectFactory::RegisterAll](#registerall)|向應用程式的物件處理站的所有 OLE 系統 Dll。|  
|[COleObjectFactory::Revoke](#revoke)|撤銷此物件 factory OLE 系統 Dll 登錄。|  
|[COleObjectFactory::RevokeAll](#revokeall)|撤銷具有 OLE 系統 Dll 的應用程式的物件 factory 的註冊。|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|取消登錄所有的應用程式的物件 factory。|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|使用 OLE 系統登錄中註冊此物件 factory。|  
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|向應用程式的物件處理站的所有 OLE 系統登錄。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|要求的唯一索引鍵，從控制項的 DLL。|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|若要建立新的物件，此處理站類型架構呼叫。|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|確認內嵌在控制項中的索引鍵符合內嵌在容器中的索引鍵。|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|驗證控制項獲得授權的設計階段使用。|  
  
## <a name="remarks"></a>備註  
 `COleObjectFactory`類別有成員函式，執行下列功能︰  
  
-   管理物件的註冊。  
  
-   正在更新 OLE 系統暫存器，以及執行階段註冊，以通知 OLE 物件正在執行，而且已準備好接收訊息。  
  
-   強制執行限制控制項授權的開發人員在設計階段，並在執行階段授權的應用程式使用方式的授權。  
  
-   OLE 系統登錄中登錄控制物件 factory。  
  
 如需建立物件的詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)和[資料物件和資料來源︰ 建立和解構](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。 如需有關註冊的詳細資訊，請參閱文章[註冊](../../mfc/registration.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="a-namecoleobjectfactorya--coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory  
 建構`COleObjectFactory`物件，作為未註冊的物件處理站，將它初始化，並將其加入處理站的清單。  
  
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
 `clsid`  
 參考這個物件處理站所代表的 OLE 類別 ID。  
  
 `pRuntimeClass`  
 此處理站可以建立的 c + + 物件的執行階段類別的指標。  
  
 `bMultiInstance`  
 指出應用程式的單一執行個體是否可以支援多個執行個體。 如果**TRUE**，針對每個要求來建立物件啟動應用程式的多個執行個體。  
  
 `nFlags`  
 包含一或多個下列旗標︰  
  
- **afxRegDefault**將執行緒模型設定為 ThreadingModel = Apartment。  
  
- **afxRegInsertable**讓控制項出現在**插入物件**OLE 物件 對話方塊。  
  
- `afxRegApartmentThreading`在 ThreadingModel 登錄中設定執行緒模型 = Apartment。  
  
- **afxRegFreeThreading** ThreadingModel 登錄中設定執行緒模型 = 免費。  
  
     您可以結合兩個旗標`afxRegApartmentThreading`和`afxRegFreeThreading`設定 ThreadingModel = Both。 請參閱[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的執行緒模型註冊的詳細資訊。  
  
 `lpszProgID`  
 字串，包含動詞化的程式識別項，例如 「 Microsoft Excel。 」 的指標  
  
### <a name="remarks"></a>備註  
 若要使用的物件，不過，您必須註冊它。  
  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetclassida--coleobjectfactorygetclassid"></a><a name="getclassid"></a>COleObjectFactory::GetClassID  
 傳回這個處理站所代表的 OLE 類別 ID 的參考。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 表示此處理站的 OLE 類別 ID 的參考。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetlicensekeya--coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey  
 從控制項的 DLL 要求的唯一授權金鑰，並將其儲存在`BSTR`指向`pbstrKey`。  
  
```  
virtual BOOL GetLicenseKey(
    DWORD dwReserved,  
    BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>參數  
 `dwReserved`  
 保留供未來使用。  
  
 `pbstrKey`  
 指標`BSTR`將儲存的授權金鑰。  
  
### <a name="return-value"></a>傳回值  
 如果授權識別碼字串不會為非零**NULL**，否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會傳回 0，而且會儲存在中為 nothing `BSTR`。 如果您使用 MFC ActiveX ControlWizard 來建立專案時，ControlWizard 提供覆寫可擷取控制項的授權金鑰。  
  
##  <a name="a-nameislicensevalida--coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid  
 判斷控制項的授權是否有效。  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>傳回值  
 TRUE 如果 successul;否則為 false。  
  
##  <a name="a-nameisregistereda--coleobjectfactoryisregistered"></a><a name="isregistered"></a>COleObjectFactory::IsRegistered  
 如果在處理站已向 OLE 系統 Dll，則傳回非零值。  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>傳回值  
 已註冊之處理站; 如果為非零否則為 0。  
  
##  <a name="a-nameoncreateobjecta--coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a>COleObjectFactory::OnCreateObject  
 若要建立新的物件架構呼叫。  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>傳回值  
 建立物件的指標。 如果失敗，仍會擲回記憶體例外狀況。  
  
### <a name="remarks"></a>備註  
 覆寫此函式以外的其他項目從建立物件[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)傳遞至建構函式。  
  
##  <a name="a-nameregistera--coleobjectfactoryregister"></a><a name="register"></a>COleObjectFactory::Register  
 此物件處理站會向 OLE 系統 Dll。  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>傳回值  
 成功註冊之處理站; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式通常會由呼叫[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="a-nameregisteralla--coleobjectfactoryregisterall"></a><a name="registerall"></a>COleObjectFactory::RegisterAll  
 向應用程式的物件處理站的所有 OLE 系統 Dll。  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>傳回值  
 已成功註冊之處理站; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式通常會由呼叫[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="a-namerevokea--coleobjectfactoryrevoke"></a><a name="revoke"></a>COleObjectFactory::Revoke  
 撤銷此物件 factory OLE 系統 Dll 登錄。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>備註  
 架構會在應用程式終止之前自動呼叫此函式。 必要時，呼叫它的覆寫從[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="a-namerevokealla--coleobjectfactoryrevokeall"></a><a name="revokeall"></a>COleObjectFactory::RevokeAll  
 撤銷所有具有 OLE 系統 Dll 的應用程式的物件 factory 的註冊。  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>備註  
 架構會在應用程式終止之前自動呼叫此函式。 必要時，呼叫它的覆寫從[CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)。  
  
##  <a name="a-nameunregisteralla--coleobjectfactoryunregisterall"></a><a name="unregisterall"></a>COleObjectFactory::UnregisterAll  
 取消登錄所有的應用程式的物件 factory。  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
##  <a name="a-nameupdateregistrya--coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a>COleObjectFactory::UpdateRegistry  
 向應用程式的物件處理站的所有 OLE 系統登錄。  
  
```  
void UpdateRegistry(LPCTSTR lpszProgID = NULL);  
virtual BOOL UpdateRegistry(BOOL bRegister);
```  
  
### <a name="parameters"></a>參數  
 `lpszProgID`  
 包含字串指標的人們可讀取的程式識別項，例如 「 Excel.Document.5 」。  
  
 `bRegister`  
 判斷是否要註冊控制項類別的物件 factory。  
  
### <a name="remarks"></a>備註  
 請依照下列兩種格式，這個函式的簡短討論︰  
  
- **UpdateRegistry (** `lpszProgID` **)** OLE 系統登錄會向此物件 factory。 此函式通常會由呼叫[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
- **UpdateRegistry (** `bRegister` **)**這種形式的函式是可覆寫。 如果`bRegister`是**TRUE**，此函式會向系統登錄中的控制項類別。 否則，它會移除註冊類別。  
  
     如果您使用 MFC ActiveX ControlWizard 來建立專案時，ControlWizard 提供覆寫，此純虛擬函式。  
  
##  <a name="a-nameupdateregistryalla--coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a>COleObjectFactory::UpdateRegistryAll  
 向應用程式的物件處理站的所有 OLE 系統登錄。  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bRegister`  
 判斷是否要註冊控制項類別的物件 factory。  
  
### <a name="return-value"></a>傳回值  
 成功地更新之處理站; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式通常會由呼叫[cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)應用程式啟動時。  
  
##  <a name="a-nameverifylicensekeya--coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a>COleObjectFactory::VerifyLicenseKey  
 確認容器已授權可使用 OLE 控制項。  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>參數  
 `bstrKey`  
 A`BSTR`儲存授權字串的容器的版本。  
  
### <a name="return-value"></a>傳回值  
 如果執行階段授權無效，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設版本呼叫[GetLicenseKey](#getlicensekey)取得控制項的複本的授權字串，並在字串比較`bstrKey`。 如果兩個字串相符，函數會傳回非零值。否則便傳回 0。  
  
 您可以覆寫這個函式，以提供自訂的驗證的授權。  
  
 函式[VerifyUserLicense](#verifyuserlicense)確認設計階段授權。  
  
##  <a name="a-nameverifyuserlicensea--coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a>COleObjectFactory::VerifyUserLicense  
 確認 OLE 控制項的設計階段授權。  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>傳回值  
 如果在設計階段授權無效，則為非零否則為 0。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)

