---
title: "COleTemplateServer 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
dev_langs:
- C++
helpviewer_keywords:
- Automation servers [C++], implementing
- servers, OLE
- OLE server applications, managing server documents
- link containers [C++]
- visual editing, servers
- OLE link containers
- COleTemplateServer class
- OLE server applications, COleTemplateServer class
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ea82939cd0e8a8ba5612c65d238be8ae9996ef08
ms.lasthandoff: 02/24/2017

---
# <a name="coletemplateserver-class"></a>COleTemplateServer 類別
用於 OLE 視覺化編輯伺服程式、Automation 伺服程式和連結容器 (支援內嵌連結的應用程式)。  
  
## <a name="syntax"></a>語法  
  
```  
class COleTemplateServer : public COleObjectFactory  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|建構 `COleTemplateServer` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|連接到基礎的文件範本`COleObjectFactory`物件。|  
|[COleTemplateServer::Unregister](#unregister)|取消登錄的相關聯的文件範本。|  
|[COleTemplateServer::UpdateRegistry](#updateregistry)|向 OLE 系統登錄中的文件類型。|  
  
## <a name="remarks"></a>備註  
 這個類別衍生自類別[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); 通常，您可以使用`COleTemplateServer`直接而不是衍生您自己的類別。 `COleTemplateServer`使用[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)物件，以管理伺服器文件。 使用`COleTemplateServer`實作完整的伺服器，也就是可以當做獨立應用程式執行的伺服器時。 雖然單一文件介面 (SDI) 應用程式支援完整的伺服器通常是多個文件介面 (MDI) 應用程式。 一個`COleTemplateServer`物件所需的每一種應用程式支援的伺服器文件; 也就是說，如果應用程式伺服器所支援的工作表和圖表，您必須有兩個`COleTemplateServer`物件。  
  
 `COleTemplateServer`覆寫`OnCreateInstance`所定義的成員函式`COleObjectFactory`。 建立正確型別的 c + + 物件架構會呼叫此成員函式。  
  
 如需伺服器的詳細資訊，請參閱文章[伺服器︰ 實作伺服器](../../mfc/servers-implementing-a-server.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer  
 建構 `COleTemplateServer` 物件。  
  
```  
COleTemplateServer();
```  
  
### <a name="remarks"></a>備註  
 使用簡短的`COleTemplateServer`類別，請參閱[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)類別概觀。  
  
##  <a name="connecttemplate"></a>COleTemplateServer::ConnectTemplate  
 連接所指的文件範本`pDocTemplate`基礎[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)物件。  
  
```  
void ConnectTemplate(
    REFCLSID clsid,  
    CDocTemplate* pDocTemplate,  
    BOOL bMultiInstance);
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 參考範本要求的 OLE 類別 ID。  
  
 `pDocTemplate`  
 文件範本的指標。  
  
 `bMultiInstance`  
 指出應用程式的單一執行個體是否可以支援多個執行個體。 如果**TRUE**，針對每個要求來建立物件啟動應用程式的多個執行個體。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="unregister"></a>COleTemplateServer::Unregister  
 取消登錄的相關聯的文件範本。  
  
```  
BOOL Unregister();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 TRUE，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 EnterRemarks  
  
##  <a name="updateregistry"></a>COleTemplateServer::UpdateRegistry  
 載入文件範本字串中的檔案類型資訊，並將該資訊放在 OLE 系統登錄中。  
  
```  
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL,  
    BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nAppType`  
 介於**OLE_APPTYPE** AFXDISP 中所定義的列舉。H. 它可以包含下列值之一︰  
  
- `OAT_INPLACE_SERVER`伺服器具有完整伺服器的使用者介面。  
  
- `OAT_SERVER`只有內嵌伺服器支援。  
  
- `OAT_CONTAINER`容器支援內嵌物件連結。  
  
- `OAT_DISPATCH_OBJECT`物件是`IDispatch`的能力。  
  
- **OAT_DOC_OBJECT_SERVER**伺服器同時支援內嵌和元件的文件物件模型。  
  
 `rglpszRegister`  
 會不有任何項目時，才會寫入到登錄中的項目清單。  
  
 `rglpszOverwrite`  
 不論任何上述項目是否存在登錄中會寫入的項目清單。  
  
 `bRegister`  
 判斷是否要註冊的類別。 如果`bRegister`是**TRUE**，類別會註冊系統登錄。 否則，它會移除註冊類別。  
  
### <a name="remarks"></a>備註  
 註冊資訊會透過呼叫載入[CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)。 擷取子字串是由索引**regFileTypeId**， **regFileTypeName**，和**fileNewName**所述，在`GetDocString`參考頁面。  
  
 如果**regFileTypeId**子字串是空的或是呼叫`GetDocString`失敗，因為其他任何原因，此函式會失敗，且未在登錄中輸入的檔案資訊。  
  
 引數中的資訊`rglpszRegister`和`rglpszOverwrite`透過呼叫登錄寫入[AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass)。 兩個引數都已登錄的預設資訊**NULL**，適用於大部分的應用程式。 如需這些引數中的資訊結構的資訊，請參閱`AfxOleRegisterServerClass`。  
  
 如需詳細資訊，請參閱[實作 IDispatch 介面](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [COleObjectFactory 類別](../../mfc/reference/coleobjectfactory-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)

