---
title: "CDocObjectServer 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
dev_langs:
- C++
helpviewer_keywords:
- document object server
- CDocObjectServer class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
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
ms.openlocfilehash: 75fb0ba49d105a673e862ed3044e85ac9e990e9c
ms.lasthandoff: 02/24/2017

---
# <a name="cdocobjectserver-class"></a>CDocObjectServer 類別
實作可讓一般 `COleDocument` 伺服器融入完整 DocObject 伺服器所需的其他 OLE 介面： `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`和 `IPrint`。  
  
## <a name="syntax"></a>語法  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|建構 `CDocObjectServer` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|啟用文件物件的伺服器，但不會顯示。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](#onactivateview)|顯示 DocObject 檢視。|  
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|還原 DocObject 檢視的狀態。|  
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|儲存 DocObject 檢視狀態。|  
  
## <a name="remarks"></a>備註  
 `CDocObjectServer`衍生自`CCmdTarget`和與密切`COleServerDoc`公開的介面。  
  
 DocObject 伺服器文件可以包含[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) DocObject 項目代表伺服器介面的物件。  
  
 若要自訂 DocObject 伺服器，衍生您自己從`CDocObjectServer`並覆寫檢視安裝程式功能， [OnActivateView](#onactivateview)， [OnApplyViewState](#onapplyviewstate)，和[OnSaveViewState](#onsaveviewstate)。 您必須提供回應架構會呼叫您類別的新執行個體。  
  
 如需 DocObjects 詳細資訊，請參閱[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 參考*。 另請參閱[網際網路第一個步驟︰ 主動式文件](../../mfc/active-documents-on-the-internet.md)和[主動式文件](../../mfc/active-documents-on-the-internet.md)。  
  
 另請參閱下列知識庫文件︰  
  
-   Q247382: PRB︰ 在 ActiveX 文件伺服器控制項的工具提示隱藏 ActiveX 文件容器  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdocob.h  
  
##  <a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject  
 呼叫此函式文件物件伺服器啟動 （但不顯示）。  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>備註  
 `ActivateDocObject`呼叫`IOleDocumentSite`的**ActivateMe**方法，但不會顯示檢視，因為它會等候如何設定及顯示檢視中，指定的呼叫中的特定指示[CDocObjectServer::OnActivateView](#onactivateview)。  
  
 在一起，`ActivateDocObject`和`OnActivateView`啟動並顯示 DocObject 檢視。 DocObject 啟用不同於其他類型的 OLE 就地啟動。 DocObject 啟動會略過 顯示框線就地規劃和物件 （例如縮放控點） 的裝飾、 略過物件延伸功能，以及將捲軸，而不是外部矩形 （如同一般的就地啟用） 繪製這些檢視矩形內繪製。  
  
##  <a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer  
 建構並初始化 `CDocObjectServer` 物件。  
  
```  
explicit CDocObjectServer(
    COleServerDoc* pOwner,  
    LPOLEDOCUMENTSITE pDocSite = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pOwner*  
 是 DocObject 伺服器的用戶端的用戶端站台文件指標。  
  
 `pDocSite`  
 指標`IOleDocumentSite`容器所實作的介面。  
  
### <a name="remarks"></a>備註  
 當 DocObject 作用時，用戶端站台 OLE 介面 ( `IOleDocumentSite`) 就是允許 DocObject 伺服器與用戶端 （容器） 進行通訊。 DocObject 伺服器啟動時，它會先檢查容器會實作`IOleDocumentSite`介面。 如果是這樣， [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver)稱為容器是否支援 DocObjects。 根據預設，`GetDocObjectServer`傳回**NULL**。 您必須覆寫`COleServerDoc::GetDocObjectServer`建構新`CDocObjectServer`物件或衍生您自己，與指標的物件`COleServerDoc`容器及其`IOleDocumentSite`介面做為引數的建構函式。  
  
##  <a name="onactivateview"></a>CDocObjectServer::OnActivateView  
 呼叫此函式，以顯示 DocObject 檢視。  
  
```  
virtual HRESULT OnActivateView();
```  
  
### <a name="return-value"></a>傳回值  
 傳回錯誤或警告的值。 根據預設，會傳回**NOERROR**如果成功，否則**E_FAIL**。  
  
### <a name="remarks"></a>備註  
 這個函式建立的就地框架視窗、 繪製捲軸檢視中的，設定伺服器以其容器的共用、 加入框架控制項、 設定作用中的物件，則最後就地框架視窗會顯示和設定焦點的功能表。  
  
##  <a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState  
 覆寫這個函式來還原 DocObject 檢視狀態。  
  
```  
virtual void OnApplyViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 A`CArchive`要序列化的檢視狀態的物件。  
  
### <a name="remarks"></a>備註  
 當它具現化之後的第一次顯示的檢視時，會呼叫此函數。 `OnApplyViewState`指示檢視，以根據中重新初始`CArchive`與先前儲存的物件[OnSaveViewState](#onsaveviewstate)。 檢視必須驗證中的資料`CArchive`物件，因為容器並不會嘗試解譯以任何方式的檢視狀態資料。  
  
 您可以使用`OnSaveViewState`來儲存您的檢視狀態的特定的持續性資訊。 如果您覆寫`OnSaveViewState`來儲存資訊，您會想要覆寫`OnApplyViewState`讀取該資訊，並將它套用至您的檢視，剛啟動時。  
  
##  <a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState  
 覆寫此函式可儲存有關 DocObject 檢視額外的狀態資訊。  
  
```  
virtual void OnSaveViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 `ar`  
 A`CArchive`檢視狀態序列化的物件。  
  
### <a name="remarks"></a>備註  
 您的狀態可能包含屬性，例如檢視類型、 比例、 插入和選取範圍點等。 通常，容器會呼叫此函式之前停用檢視。 儲存的狀態之後還原到[OnApplyViewState](#onapplyviewstate)。  
  
 您可以使用`OnSaveViewState`來儲存您的檢視狀態的特定的持續性資訊。 如果您覆寫`OnSaveViewState`來儲存資訊，您會想要覆寫`OnApplyViewState`讀取該資訊，並將它套用至您的檢視，剛啟動時。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem 類別](../../mfc/reference/cdocobjectserveritem-class.md)

