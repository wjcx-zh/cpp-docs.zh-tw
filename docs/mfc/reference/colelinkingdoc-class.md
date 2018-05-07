---
title: COleLinkingDoc 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
dev_langs:
- C++
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe37e1a159fa0138c237b58ffbd622292dcba714
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc 類別
支援連結至所包含內嵌項目之 OLE 容器文件的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class COleLinkingDoc : public COleDocument  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|建構 `COleLinkingDoc` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleLinkingDoc::Register](#register)|使用 OLE 系統 Dll，註冊文件。|  
|[COleLinkingDoc::Revoke](#revoke)|撤銷文件的註冊。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|尋找指定的內嵌項目。|  
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|尋找指定的連結項目。|  
  
## <a name="remarks"></a>備註  
 容器應用程式支援將連結到內嵌的項目稱為 「 連結容器 >。 [OCLIENT](../../visual-cpp-samples.md)範例應用程式是連結容器的範例。  
  
 其他文件中的內嵌項目連結項目來源時，包含文件必須載入可供編輯內嵌項目的順序。 基於這個理由，連結容器必須能夠啟動另一個容器應用程式，當使用者想要編輯連結的項目來源。 您的應用程式也必須使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)類別，使它能夠建立文件時以程式設計方式啟動。  
  
 若要讓您的容器連結容器，衍生您的文件類別，從`COleLinkingDoc`而不是[COleDocument](../../mfc/reference/coledocument-class.md)。 如同其他任何 OLE 容器，則必須設計您的類別來儲存應用程式的原生資料，以及內嵌或連結項目。 此外，您必須設計來儲存您的原生資料的資料結構。 如果您定義`CDocItem`-衍生類別，用於您的應用程式的原生資料，您可以使用所定義的介面`COleDocument`來儲存您的原生資料，以及 OLE 資料。  
  
 若要允許您的應用程式以程式設計方式啟動另一個容器，宣告`COleTemplateServer`物件做為您的應用程式的成員`CWinApp`-衍生的類別：  
  
 [!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]  
  
 在`InitInstance`成員函式您`CWinApp`-衍生的類別，建立的文件範本，並指定您`COleLinkingDoc`-衍生的類別為文件類別：  
  
 [!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]  
  
 連接您`COleTemplateServer`要藉由呼叫物件的文件範本物件`ConnectTemplate`成員函式，並註冊所有類別藉由呼叫都物件以 OLE 系統**coletemplateserver:: Registerall**:  
  
 [!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]  
  
 如需範例`CWinApp`-衍生類別定義和`InitInstance`函式，請參閱 OCLIENT。H 和 OCLIENT。在 MFC 範例 CPP [OCLIENT](../../visual-cpp-samples.md)。  
  
 如需有關使用`COleLinkingDoc`，請參閱文章[容器： 實作容器](../../mfc/containers-implementing-a-container.md)和[容器： 進階功能](../../mfc/containers-advanced-features.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 `COleLinkingDoc`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc  
 建構`COleLinkingDoc`沒有開始與 OLE 系統 Dll 的通訊物件。  
  
```  
COleLinkingDoc();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫`Register`成員函式以通知 OLE 文件開啟時。  
  
##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem  
 由架構呼叫以判斷文件是否包含具有指定名稱內嵌的 OLE 項目。  
  
```  
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>參數  
 `lpszItemName`  
 內嵌 OLE 項目要求的名稱指標。  
  
### <a name="return-value"></a>傳回值  
 指定的項目; 指標**NULL**如果找不到項目。  
  
### <a name="remarks"></a>備註  
 預設實作會搜尋具有指定之名稱 （此名稱比較不區分大小寫的） 項目的內嵌項目清單。 如果您有自己的方法來儲存或命名內嵌的 OLE 項目，請覆寫這個函式。  
  
##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem  
 由架構呼叫以檢查文件是否包含具有指定名稱的連結的伺服器項目。  
  
```  
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>參數  
 `lpszItemName`  
 連結的 OLE 項目要求的名稱指標。  
  
### <a name="return-value"></a>傳回值  
 指定的項目; 指標**NULL**如果找不到項目。  
  
### <a name="remarks"></a>備註  
 預設值`COleLinkingDoc`實作一律會傳回**NULL**。 此函式是在衍生類別中的覆寫`COleServerDoc`来搜尋的 OLE 連結的項目具有指定之名稱 （此名稱比較不區分大小寫的） 的伺服器項目清單。 如果您已實作您自己的方法來儲存或擷取連結的伺服器項目，請覆寫這個函式。  
  
##  <a name="register"></a>  COleLinkingDoc::Register  
 文件開啟時通知 OLE 系統 Dll。  
  
```  
BOOL Register(
    COleObjectFactory* pFactory,  
    LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>參數  
 *pFactory*  
 OLE factory 物件指標 (可以是**NULL**)。  
  
 `lpszPathName`  
 容器文件的完整路徑的指標。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功註冊文件。否則便是 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式，建立或開啟文件向 OLE 系統 Dll 命名的檔案。 沒有需要呼叫此函式，如果文件代表內嵌項目。  
  
 如果您使用`COleTemplateServer`應用程式中`Register`會為您呼叫`COleLinkingDoc`的實作`OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。  
  
##  <a name="revoke"></a>  COleLinkingDoc::Revoke  
 文件不再開啟通知 OLE 系統 Dll。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>備註  
 呼叫此函式來撤銷文件的註冊，在 OLE 系統 Dll。  
  
 命名的檔案，在關閉時，應該呼叫此函式，但您通常不必直接呼叫它。 `Revoke` 為您呼叫`COleLinkingDoc`的實作`OnCloseDocument`， `OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDocument 類別](../../mfc/reference/coledocument-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)
