---
title: "COleServerDoc 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleServerDoc
dev_langs:
- C++
helpviewer_keywords:
- servers, OLE
- OLE server applications, managing server documents
- container/server applications
- OLE server documents
- COleServerDoc class
- server documents, OLE
- OLE containers, server documents
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
caps.latest.revision: 24
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
ms.openlocfilehash: db50c2a5709fbc07d0e0db99a4cffc733c4b6ead
ms.lasthandoff: 02/24/2017

---
# <a name="coleserverdoc-class"></a>COleServerDoc 類別
OLE 伺服器文件的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleServerDoc::COleServerDoc](#coleserverdoc)|建構 `COleServerDoc` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleServerDoc::ActivateDocObject](#activatedocobject)|啟動相關聯的 DocObject 文件。|  
|[COleServerDoc::ActivateInPlace](#activateinplace)|啟動就地編輯文的件。|  
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|停用伺服器的使用者介面。|  
|[COleServerDoc::DiscardUndoState](#discardundostate)|捨棄復原狀態資訊。|  
|[COleServerDoc::GetClientSite](#getclientsite)|擷取基礎的指標`IOleClientSite`介面。|  
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|傳回項目代表整個文件的指標。|  
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|傳回目前裁剪方框就地編輯。|  
|[COleServerDoc::GetItemPosition](#getitemposition)|傳回目前的位置矩形，相對於就地編輯容器應用程式的用戶端區域。|  
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|傳回像素為單位的縮放因數。|  
|[COleServerDoc::IsDocObject](#isdocobject)|決定文件是 DocObject。|  
|[COleServerDoc::IsEmbedded](#isembedded)|指出是否內嵌在容器文件或執行獨立文件。|  
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|傳回`TRUE`如果目前項目就地啟動。|  
|[COleServerDoc::NotifyChanged](#notifychanged)|通知使用者已變更文件容器。|  
|[COleServerDoc::NotifyClosed](#notifyclosed)|通知使用者已關閉文件容器。|  
|[COleServerDoc::NotifyRename](#notifyrename)|通知使用者已重新命名文件容器。|  
|[COleServerDoc::NotifySaved](#notifysaved)|告知使用者儲存文件容器。|  
|[COleServerDoc::OnDeactivate](#ondeactivate)|當使用者停用的項目就地啟動時，由架構呼叫。|  
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|要終結控制項和其他使用者介面項目就地啟動建立架構呼叫。|  
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|架構容器的文件框架視窗是啟用或停用時呼叫。|  
|[COleServerDoc::OnResizeBorder](#onresizeborder)|容器應用程式的框架視窗或文件視窗調整大小時，由架構呼叫。|  
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|顯示或隱藏在就地編輯的控制列架構呼叫。|  
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|儲存伺服器文件是內嵌的項目時，更新的項目容器的副本，由架構呼叫。|  
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|變更在就地編輯框架的位置。|  
|[COleServerDoc::SaveEmbedding](#saveembedding)|會告知儲存文件容器應用程式。|  
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|捲動容器文件。|  
|[COleServerDoc::UpdateAllItems](#updateallitems)|通知使用者已變更文件容器。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|若要建立就地編輯框架視窗架構呼叫。|  
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|終結就地編輯框架視窗，架構呼叫。|  
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|覆寫這個函式來建立新的`CDocObjectServer`物件，表示此文件是 DocObject 容器。|  
|[COleServerDoc::OnClose](#onclose)|架構容器要求關閉文件時呼叫。|  
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|執行指定的命令，則會顯示命令的說明。|  
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|架構容器的框架視窗是啟用或停用時呼叫。|  
|[Coleserveritem](#ongetembeddeditem)|呼叫以取得`COleServerItem`代表整份文件，用來取得內嵌項目。 所需的實作。|  
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|若要復原在就地編輯期間所做的變更架構呼叫。|  
|[COleServerDoc::OnSetHostNames](#onsethostnames)|架構容器設定視窗標題的內嵌物件時呼叫。|  
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|容器應用程式的視窗內放置在就地編輯框架視窗的架構所呼叫。|  
|[COleServerDoc::OnShowDocument](#onshowdocument)|若要顯示或隱藏文件架構呼叫。|  
  
## <a name="remarks"></a>備註  
 伺服器文件可以包含[COleServerItem](../../mfc/reference/coleserveritem-class.md)內嵌或連結項目代表伺服器介面的物件。 若要編輯內嵌項目容器啟動伺服器應用程式時，為自己的伺服器文件; 載入項目`COleServerDoc`物件包含其中一個`COleServerItem`整份文件所組成的物件。 若要編輯連結的項目容器啟動伺服器應用程式時，從磁碟; 載入現有的文件部分文件的內容會反白顯示，表示連結的項目。  
  
 `COleServerDoc`物件也可以包含的項目[COleClientItem](../../mfc/reference/coleclientitem-class.md)類別。 這可讓您建立容器伺服器應用程式。 架構提供函式來適當地儲存`COleClientItem`項目，在服務時`COleServerItem`物件。  
  
 如果您的伺服器應用程式不支援的連結，伺服器文件將一律包含只有一個伺服器項目代表整個內嵌的物件做為文件。 如果伺服器應用程式支援的連結，它必須在每次選取範圍複製到剪貼簿時建立的伺服器項目。  
  
 若要使用`COleServerDoc`、 衍生的類別和實作[OnGetEmbeddedItem](#ongetembeddeditem)成員函式，可讓您的伺服器支援內嵌項目。 自`COleServerItem`實作文件中的項目，並傳回物件，從該類別的`OnGetEmbeddedItem`。  
  
 若要支援連結的項目`COleServerDoc`提供[OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem)成員函式。 您可以使用的預設實作，或覆寫它，如果您有自己的方法來管理文件項目。  
  
 您需要一個`COleServerDoc`-衍生類別的每一種伺服器文件的應用程式支援。 例如，如果應用程式伺服器所支援的工作表和圖表，您需要兩個`COleServerDoc`-衍生的類別。  
  
 如需有關伺服器的詳細資訊，請參閱文章[伺服器︰ 實作伺服器](../../mfc/servers-implementing-a-server.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="a-nameactivatedocobjecta--coleserverdocactivatedocobject"></a><a name="activatedocobject"></a>COleServerDoc::ActivateDocObject  
 啟動相關聯的 DocObject 文件。  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>備註  
 根據預設，`COleServerDoc`不支援主動式文件 （也稱為 DocObjects）。 若要啟用這項支援，請參閱[GetDocObjectServer](#getdocobjectserver)和類別[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)。  
  
##  <a name="a-nameactivateinplacea--coleserverdocactivateinplace"></a><a name="activateinplace"></a>COleServerDoc::ActivateInPlace  
 啟動就地編輯的項目。  
  
```  
BOOL ActivateInPlace();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0，表示項目是完全開啟。  
  
### <a name="remarks"></a>備註  
 此函式會執行就地啟動所需的所有作業。 它會建立一個就地框架視窗、 加以啟動和大小的項目、 設定共用的功能表和其他控制項、 將項目捲動到檢視中，並將焦點設在就地框架視窗。  
  
 預設實作會呼叫此函式[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。 如果您的應用程式支援就地啟用 （例如播放） 另一個動作，請呼叫此函式。  
  
##  <a name="a-namecoleserverdoca--coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a>COleServerDoc::COleServerDoc  
 建構`COleServerDoc`物件，而不使用 OLE 系統 Dll 連接。  
  
```  
COleServerDoc();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫[COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) OLE 以開啟通訊。 如果您使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)應用程式中`COleLinkingDoc::Register`會為您呼叫`COleLinkingDoc`的實作`OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。  
  
##  <a name="a-namecreateinplaceframea--coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame  
 架構會呼叫此函式建立就地編輯框架視窗。  
  
```  
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 容器應用程式的父視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 就地框架視窗時，指標或**NULL**如果不成功。  
  
### <a name="remarks"></a>備註  
 預設實作會使用文件範本中指定的資訊來建立框架。 使用檢視是建立文件的第一個檢視。 此檢視會暫時從原來的框架中卸離和附加至新建立的框架。  
  
 這是進階可覆寫。  
  
##  <a name="a-namedeactivateandundoa--coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a>COleServerDoc::DeactivateAndUndo  
 如果您的應用程式支援復原和使用者選擇復原之後啟用項目，但編輯之前，請呼叫此函式。  
  
```  
BOOL DeactivateAndUndo();
```  
  
### <a name="return-value"></a>傳回值  
 非零成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果容器應用程式寫入使用 Mfc 程式庫，呼叫此函式會導致[COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo)呼叫，這會停用伺服器的使用者介面。  
  
##  <a name="a-namedestroyinplaceframea--coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame  
 架構會呼叫此函式可摧毀就地框架視窗，並將伺服器應用程式的文件視窗還原成之前在就地啟用的狀態。  
  
```  
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>參數  
 `pFrameWnd`  
 終結就地框架視窗的指標。  
  
### <a name="remarks"></a>備註  
 這是進階可覆寫。  
  
##  <a name="a-namediscardundostatea--coleserverdocdiscardundostate"></a><a name="discardundostate"></a>COleServerDoc::DiscardUndoState  
 如果使用者執行的動作無法復原的編輯作業時，呼叫此函式強制容器應用程式，以捨棄復原狀態資訊。  
  
```  
BOOL DiscardUndoState();
```  
  
### <a name="return-value"></a>傳回值  
 非零成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 提供這個函式，使支援復原伺服器可以釋放資源，否則會由復原狀態資訊無法使用。  
  
##  <a name="a-namegetclientsitea--coleserverdocgetclientsite"></a><a name="getclientsite"></a>COleServerDoc::GetClientSite  
 擷取基礎的指標`IOleClientSite`介面。  
  
```  
LPOLECLIENTSITE GetClientSite() const;  
```  
  
### <a name="return-value"></a>傳回值  
 擷取基礎的指標[IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706)介面。  
  
##  <a name="a-namegetdocobjectservera--coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer  
 覆寫這個函式來建立新的`CDocObjectServer`項目，然後傳回的指標。  
  
```  
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```  
  
### <a name="parameters"></a>參數  
 `pDocSite`  
 指標`IOleDocumentSite`會連接到伺服器的這份文件的介面。  
  
### <a name="return-value"></a>傳回值  
 指標`CDocObjectServer`;**NULL**作業失敗。  
  
### <a name="remarks"></a>備註  
 DocObject 伺服器啟動時，傳回非**NULL**指標會顯示在用戶端可支援 DocObjects。 預設實作會傳回**NULL**。  
  
 典型的實作中支援 DocObjects 文件只會配置新`CDocObjectServer`物件，並傳回給呼叫者。 例如:   
  
 [!code-cpp[NVC_MFCOleServer #&3;](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]  
  
##  <a name="a-namegetembeddeditema--coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem  
 呼叫此函式可取得項目代表整個文件的指標。  
  
```  
COleServerItem* GetEmbeddedItem();
```  
  
### <a name="return-value"></a>傳回值  
 指向項目代表整個文件。**NULL**作業失敗。  
  
### <a name="remarks"></a>備註  
 它會呼叫[Coleserveritem](#ongetembeddeditem)，沒有預設實作的虛擬函式。  
  
##  <a name="a-namegetitemcliprecta--coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect  
 呼叫`GetItemClipRect`成員函式來取得的裁剪矩形座標正在編輯之項目的位置。  
  
```  
void GetItemClipRect(LPRECT lpClipRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpClipRect`  
 指標`RECT`結構或`CRect`物件，以擷取項目的裁剪矩形座標。  
  
### <a name="remarks"></a>備註  
 座標是相對於容器應用程式視窗的用戶端區域的像素為單位。  
  
 裁剪矩形外，不應該進行繪圖。 通常，繪圖會自動限制。 使用此函數來判斷使用者是否已捲動外部可見的部分文件。如果是的話，請視需要透過呼叫捲動容器文件[ScrollContainerBy](#scrollcontainerby)。  
  
##  <a name="a-namegetitempositiona--coleserverdocgetitemposition"></a><a name="getitemposition"></a>COleServerDoc::GetItemPosition  
 呼叫`GetItemPosition`成員函式來取得其座標的就地編輯的項目。  
  
```  
void GetItemPosition(LPRECT lpPosRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpPosRect`  
 指標`RECT`結構或`CRect`接收項目的座標的物件。  
  
### <a name="remarks"></a>備註  
 座標是相對於容器應用程式視窗的用戶端區域的像素為單位。  
  
 與目前的裁剪矩形來判斷項目可見 （或不可見） 的程度，就可以比較的項目位置在螢幕上。  
  
##  <a name="a-namegetzoomfactora--coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor  
 `GetZoomFactor`成員函式判斷 「 比例 」 已啟用就地編輯的項目。  
  
```  
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,  
    LPSIZE lpSizeDenom = NULL,  
    LPCRECT lpPosRect = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 *lpSizeNum*  
 類別的物件指標`CSize`將保留比例分子。 可以是**NULL**。  
  
 *lpSizeDenom*  
 類別的物件指標`CSize`將保留比例分母。 可以是**NULL**。  
  
 `lpPosRect`  
 類別的物件指標`CRect`描述項目的新位置。 如果這個引數是**NULL**，此函數會使用的項目目前的位置。  
  
### <a name="return-value"></a>傳回值  
 如果項目就地啟動為非零編輯和其縮放比例不是 100%(1:1);否則為 0。  
  
### <a name="remarks"></a>備註  
 縮放因數，單位為像素就其目前的範圍內的項目大小的比例。 如果容器應用程式尚未設定的項目範圍內，其自然範圍 (由[COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) 使用。  
  
 函式會設定前兩個引數的分子和分母的項目 」 縮放因數。 」 如果不就地編輯項目，函數會將這些引數設定為預設值是 100%（或 1:1），並傳回零。 如需詳細資訊，請參閱技術附註 40， [MFC/OLE 就地調整大小和縮放](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。  
  
##  <a name="a-nameisdocobjecta--coleserverdocisdocobject"></a><a name="isdocobject"></a>COleServerDoc::IsDocObject  
 決定文件是 DocObject。  
  
```  
BOOL IsDocObject() const;  
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**文件是 DocObject; 否則**FALSE**。  
  
##  <a name="a-nameisembeddeda--coleserverdocisembedded"></a><a name="isembedded"></a>COleServerDoc::IsEmbedded  
 呼叫`IsEmbedded`成員函式來判斷文件是否代表容器中的內嵌物件。  
  
```  
BOOL IsEmbedded() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`COleServerDoc`物件是代表物件的文件內嵌在容器中，否則為 0。  
  
### <a name="remarks"></a>備註  
 從檔案載入的文件不會內嵌，雖然可能會由容器應用程式的連結來管理。 內嵌在容器文件中的文件會被視為內嵌。  
  
##  <a name="a-nameisinplaceactivea--coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive  
 呼叫`IsInPlaceActive`成員函式，以判斷項目目前是否處於就地使用中狀態。  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`COleServerDoc`物件會就地使用中，否則為 0。  
  
##  <a name="a-namenotifychangeda--coleserverdocnotifychanged"></a><a name="notifychanged"></a>COleServerDoc::NotifyChanged  
 呼叫此函式以通知所有連接到已變更的文件的文件的連結項目。  
  
```  
void NotifyChanged();
```  
  
### <a name="remarks"></a>備註  
 一般而言，您呼叫此函式之後使用者變更一些通用的屬性，例如伺服器文件的維度。 如果 OLE 項目自動連結至文件，以反映所做的變更更新項目。 在容器應用程式使用 Microsoft Foundation 類別庫中，撰寫[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式`COleClientItem`呼叫。  
  
> [!NOTE]
>  此函式會包含 OLE 1 與相容性。 新的應用程式應使用[UpdateAllItems](#updateallitems)。  
  
##  <a name="a-namenotifycloseda--coleserverdocnotifyclosed"></a><a name="notifyclosed"></a>COleServerDoc::NotifyClosed  
 呼叫此函式以通知容器文件已關閉。  
  
```  
void NotifyClosed();
```  
  
### <a name="remarks"></a>備註  
 當使用者從 [檔案] 功能表中，選擇 [關閉] 命令`NotifyClosed`由呼叫`COleServerDoc`的實作[OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument)成員函式。 在容器應用程式使用 Microsoft Foundation 類別庫中，撰寫[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式`COleClientItem`呼叫。  
  
##  <a name="a-namenotifyrenamea--coleserverdocnotifyrename"></a><a name="notifyrename"></a>COleServerDoc::NotifyRename  
 使用者會重新命名伺服器文件之後，請呼叫此函式。  
  
```  
void NotifyRename(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>參數  
 `lpszNewName`  
 字串，指定伺服器文件的新名稱的指標這通常是完整的路徑。  
  
### <a name="remarks"></a>備註  
 當使用者從 [檔案] 功能表中，選擇 [另存新檔] 命令`NotifyRename`由呼叫`COleServerDoc`的實作[OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)成員函式。 此函式會通知 OLE 系統 Dll，依次通知容器。 在容器應用程式使用 Microsoft Foundation 類別庫中，撰寫[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式`COleClientItem`呼叫。  
  
##  <a name="a-namenotifysaveda--coleserverdocnotifysaved"></a><a name="notifysaved"></a>COleServerDoc::NotifySaved  
 使用者會將儲存在伺服器文件之後，請呼叫此函式。  
  
```  
void NotifySaved();
```  
  
### <a name="remarks"></a>備註  
 當使用者從 [檔案] 功能表中，選擇 [儲存] 命令`NotifySaved`會為您呼叫`COleServerDoc`的實作[OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)。 此函式會通知 OLE 系統 Dll，依次通知容器。 在容器應用程式使用 Microsoft Foundation 類別庫中，撰寫[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式`COleClientItem`呼叫。  
  
##  <a name="a-nameonclosea--coleserverdoconclose"></a><a name="onclose"></a>COleServerDoc::OnClose  
 架構容器要求關閉伺服器文件時呼叫。  
  
```  
virtual void OnClose(OLECLOSE dwCloseOption);
```  
  
### <a name="parameters"></a>參數  
 `dwCloseOption`  
 列舉值`OLECLOSE`。 這個參數的值可以是下列其中一個：  
  
- `OLECLOSE_SAVEIFDIRTY`如果已修改，檔案會儲存。  
  
- `OLECLOSE_NOSAVE`關閉檔案而不會儲存。  
  
- `OLECLOSE_PROMPTSAVE`如果已修改了檔案，儲存它的相關提示使用者。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫`CDocument::OnCloseDocument`。  
  
 如需詳細資訊和其他值，請參閱[OLECLOSE](http://msdn.microsoft.com/library/windows/desktop/ms680623)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameondeactivatea--coleserverdocondeactivate"></a><a name="ondeactivate"></a>COleServerDoc::OnDeactivate  
 當使用者停用的是目前就地啟用作用中的內嵌或連結項目時，由架構呼叫。  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>備註  
 此函式將容器應用程式的使用者介面還原成原始狀態，並終結任何功能表和就地啟動時建立其他控制項。  
  
 復原狀態資訊的無條件地釋放這個時候。  
  
 如需詳細資訊，請參閱文章[啟用](../../mfc/activation-cpp.md)...  
  
##  <a name="a-nameondeactivateuia--coleserverdocondeactivateui"></a><a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI  
 當使用者停用就地啟動時的項目時呼叫。  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>參數  
 `bUndoable`  
 指定是否可以復原編輯的變更。  
  
### <a name="remarks"></a>備註  
 此函式會還原為其原始狀態，隱藏任何功能表和就地啟動時建立其他控制項容器應用程式的使用者介面。  
  
 架構一定會設定`bUndoable`至**FALSE**。 如果伺服器支援復原，因此沒有可以復原作業，會呼叫基底類別實作`bUndoable`設**TRUE**。  
  
##  <a name="a-nameondocwindowactivatea--coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate  
 架構會呼叫此函式可啟用或停用就地編輯的文件視窗。  
  
```  
virtual void OnDocWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 `bActivate`  
 指定是否要啟用或停用文件視窗。  
  
### <a name="remarks"></a>備註  
 預設實作移除，或視需要將框架層級的使用者介面項目。 如果您想要啟用或停用的文件包含您的項目時執行其他動作，請覆寫這個函式。  
  
 如需詳細資訊，請參閱文章[啟用](../../mfc/activation-cpp.md)...  
  
##  <a name="a-nameonexecolecmda--coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd  
 架構會呼叫此函式來執行指定的命令，或顯示命令的說明。  
  
```  
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,  
    DWORD nCmdID,  
    DWORD nCmdExecOpt,  
    VARIANTARG* pvarargIn,  
    VARIANTARG* pvarargOut);
```  
  
### <a name="parameters"></a>參數  
 `pguidCmdGroup`  
 識別一組命令的 GUID 指標。 可以是**NULL**表示預設的命令群組。  
  
 `nCmdID`  
 要執行的命令。 所識別的群組中必須是`pguidCmdGroup`。  
  
 *nCmdExecOut*  
 方法的物件應該執行命令、 一或多個下列值從**OLECMDEXECOPT**列舉型別︰  
  
 **OLECMDEXECOPT_DODEFAULT**  
  
 **OLECMDEXECOPT_PROMPTUSER**  
  
 **OLECMDEXECOPT_DONTPROMPTUSER**  
  
 **OLECMDEXECOPT_SHOWHELP**  
  
 `pvarargIn`  
 指標**VARIANTARG**包含命令的輸入引數。 可以是**NULL**。  
  
 `pvarargOut`  
 指標**VARIANTARG**來接收命令的輸出傳回值。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功，否則其中下列錯誤碼︰  
  
|值|說明|  
|-----------|-----------------|  
|**E_UNEXPECTED**|發生意外的錯誤|  
|**E_FAIL**|發生錯誤|  
|**E_NOTIMPL**|表示 MFC 本身應該嘗試轉譯和分派命令|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup`為非**NULL** ，但未指定可辨識的命令群組|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID`無法辨識為有效的命令群組中`pguidCmdGroup`|  
|**OLECMDERR_DISABLED**|由命令`nCmdID`已停用，無法執行|  
|**OLECMDERR_NOHELP**|呼叫端所識別的指令上要求協助`nCmdID`但沒有說明|  
|**OLECMDERR_CANCELED**|使用者已取消執行|  
  
### <a name="remarks"></a>備註  
 `COleCmdUI`可用來啟用、 更新和設定其他屬性的 DocObject 使用者介面的命令。 在初始化命令之後，您可以執行它們與`OnExecOleCmd`。  
  
 架構會呼叫函式，然後再嘗試將轉譯和分派 OLE 文件 命令。 您不需要覆寫這個函式來處理的標準 OLE 文件的命令，但如果您想要處理自訂命令或處理命令會接受參數或傳回結果，您必須提供這個函式覆寫。  
  
 大部分的命令執行不接受引數或傳回值。 大部分的命令呼叫端可以傳遞**NULL**s`pvarargIn`和`pvarargOut`。 預期的輸入的值的命令，呼叫端可以宣告和初始化**VARIANTARG**變數並將指標傳遞給中的變數`pvarargIn`。 針對需要單一值的命令，引數可以直接存放在**VARIANTARG**並傳遞至函式。 多個引數必須封裝在內**VARIANTARG**使用其中一種支援的型別 (例如`IDispatch`和**SAFEARRAY** )。  
  
 同樣地，如果命令傳回引數呼叫端所要宣告**VARIANTARG**，將它初始化來`VT_EMPTY`，並將其位址中的傳遞`pvarargOut`。 如果命令傳回單一值，直接在值可以儲存物件`pvarargOut`。 多個輸出值必須以某種方式適用於封裝**VARIANTARG**。  
  
 此函式的基底類別實作將逐步引導**OLE_COMMAND_MAP**結構相關聯的命令目標，然後再次嘗試將分派到適當的處理常式的命令。 基底類別實作只適用於命令不接受引數或傳回值。 如果您需要處理的命令，不要接受引數或傳回值，您必須覆寫這個函式，並使用`pvarargIn`和`pvarargOut`參數自己。  
  
##  <a name="a-nameonframewindowactivatea--coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate  
 當容器應用程式的框架視窗是啟用或停用時，架構會呼叫此函式。  
  
```  
virtual void OnFrameWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 `bActivate`  
 指定是否要啟用或停用框架視窗。  
  
### <a name="remarks"></a>備註  
 預設實作會取消任何可能在框架視窗的說明模式。 如果您想要執行特殊處理的框架視窗是啟用或停用時，覆寫這個函式。  
  
 如需詳細資訊，請參閱文章[啟用](../../mfc/activation-cpp.md)...  
  
##  <a name="a-nameongetembeddeditema--coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a>Coleserveritem  
 當容器應用程式呼叫伺服器應用程式來建立或編輯內嵌項目時，由架構呼叫。  
  
```  
virtual COleServerItem* OnGetEmbeddedItem() = 0;  
```  
  
### <a name="return-value"></a>傳回值  
 指向項目代表整個文件。**NULL**作業失敗。  
  
### <a name="remarks"></a>備註  
 沒有預設的實作。 您必須覆寫這個函式來傳回代表整個文件的項目。 這個傳回的值應該是物件的`COleServerItem`-衍生的類別。  
  
##  <a name="a-nameonreactivateandundoa--coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo  
 當使用者選擇要復原已就地啟動，變更，而且之後停用的項目所做的變更時，架構會呼叫此函式。  
  
```  
virtual BOOL OnReactivateAndUndo();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作不傳回除了**FALSE**表示失敗。  
  
 如果您的應用程式支援復原，請覆寫這個函式。 通常您可在其中執行復原作業，再啟動項目，藉由呼叫`ActivateInPlace`。 如果容器應用程式撰寫與 Mfc 程式庫，呼叫`COleClientItem::ReactivateAndUndo`會導致呼叫此函式。  
  
##  <a name="a-nameonresizebordera--coleserverdoconresizeborder"></a><a name="onresizeborder"></a>COleServerDoc::OnResizeBorder  
 當容器應用程式的框架視窗大小變更時，架構會呼叫此函式。  
  
```  
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,  
    LPOLEINPLACEUIWINDOW lpUIWindow,  
    BOOL bFrame);
```  
  
### <a name="parameters"></a>參數  
 `lpRectBorder`  
 指標`RECT`結構或`CRect`物件，指定框線的座標。  
  
 `lpUIWindow`  
 類別的物件指標**IOleInPlaceUIWindow**擁有目前就地編輯工作階段。  
  
 *bFrame*  
 **TRUE**如果`lpUIWindow`指向容器應用程式的最上層框架視窗，或**FALSE**如果`lpUIWindow`指向容器應用程式的文件層級框架視窗。  
  
### <a name="remarks"></a>備註  
 此函式會調整大小，並調整工具列和其他使用者介面項目，根據新的視窗大小。  
  
 如需詳細資訊，請參閱[IOleInPlaceUIWindow](http://msdn.microsoft.com/library/windows/desktop/ms680716)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 這是進階可覆寫。  
  
##  <a name="a-nameonsethostnamesa--coleserverdoconsethostnames"></a><a name="onsethostnames"></a>COleServerDoc::OnSetHostNames  
 當容器設定或變更主機名稱，這份文件時，由架構呼叫。  
  
```  
virtual void OnSetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>參數  
 `lpszHost`  
 指定的容器應用程式名稱的字串指標。  
  
 `lpszHostObj`  
 指定文件的容器名稱的字串指標。  
  
### <a name="remarks"></a>備註  
 預設實作會變更參考這份文件的所有檢視的文件標題。  
  
 如果您的應用程式設定項目，透過不同的機制，請覆寫這個函式。  
  
##  <a name="a-nameonsetitemrectsa--coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects  
 架構會呼叫此函式可將容器應用程式的框架視窗內就地編輯框架視窗。  
  
```  
virtual void OnSetItemRects(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>參數  
 `lpPosRect`  
 指標`RECT`結構或`CRect`物件，指定相對於容器應用程式的用戶端區域的就地框架視窗的位置。  
  
 `lpClipRect`  
 指標`RECT`結構或`CRect`物件，指定相對於容器應用程式的用戶端區域的就地框架視窗的裁剪方框。  
  
### <a name="remarks"></a>備註  
 視需要覆寫此函式可更新檢視的縮放比例。  
  
 此函式通常稱為以回應`RequestPositionChange`呼叫，雖然可以在任何時間中呼叫容器要求位置變更為就地項目。  
  
##  <a name="a-nameonshowcontrolbarsa--coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars  
 架構會呼叫此函式來顯示或隱藏與框架視窗來識別相關聯的伺服器應用程式的控制列`pFrameWnd`。  
  
```  
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 `pFrameWnd`  
 框架視窗的控制列應該要隱藏或顯示的指標。  
  
 `bShow`  
 決定是否顯示或隱藏控制列。  
  
### <a name="remarks"></a>備註  
 預設實作會列舉該框架視窗所擁有的所有控制列和隱藏或顯示它們。  
  
##  <a name="a-nameonshowdocumenta--coleserverdoconshowdocument"></a><a name="onshowdocument"></a>COleServerDoc::OnShowDocument  
 這個架構會呼叫`OnShowDocument`函式時必須隱藏或顯示伺服器文件。  
  
```  
virtual void OnShowDocument(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 `bShow`  
 指定是否要顯示或隱藏文件的使用者介面。  
  
### <a name="remarks"></a>備註  
 如果`bShow`是**TRUE**，預設實作會啟動伺服器應用程式，如有必要，並造成捲動視窗，以便顯示此項目容器應用程式。 如果`bShow`是**FALSE**，預設實作會停用的項目，透過呼叫`OnDeactivate`，然後終結或隱藏文件中，除了第一個已建立的所有框架視窗。 如果沒有看到文件仍會保留，預設實作會隱藏伺服器應用程式。  
  
##  <a name="a-nameonupdatedocumenta--coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument  
 儲存文件是在複合文件中的內嵌項目時，由架構呼叫。  
  
```  
virtual BOOL OnUpdateDocument();
```  
  
### <a name="return-value"></a>傳回值  
 已成功更新文件; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫[COleServerDoc::NotifySaved](#notifysaved)和[COleServerDoc::SaveEmbedding](#saveembedding)成員函式和隨後會將標示為全新的文件。 如果您想要執行特殊處理更新內嵌項目時，請覆寫這個函式。  
  
##  <a name="a-namerequestpositionchangea--coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange  
 呼叫此成員函式已變更的項目位置的容器應用程式。  
  
```  
void RequestPositionChange(LPCRECT lpPosRect);
```  
  
### <a name="parameters"></a>參數  
 `lpPosRect`  
 指標`RECT`結構或`CRect`物件，其中包含項目的新位置。  
  
### <a name="remarks"></a>備註  
 通常會呼叫此函式 (搭配`UpdateAllItems`) 就地使用中的項目中的資料已變更時。 遵循這個呼叫，容器可能會或可能無法執行變更藉由呼叫`OnSetItemRects`。 產生的位置可能是不同的要求。  
  
##  <a name="a-namesaveembeddinga--coleserverdocsaveembedding"></a><a name="saveembedding"></a>COleServerDoc::SaveEmbedding  
 呼叫此函式來得知容器應用程式用來儲存內嵌的物件。  
  
```  
void SaveEmbedding();
```  
  
### <a name="remarks"></a>備註  
 從自動呼叫此函式`OnUpdateDocument`。 請注意，此函式會導致要更新的項目在磁碟上，因此它通常會呼叫特定的使用者動作所造成。  
  
##  <a name="a-namescrollcontainerbya--coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy  
 呼叫`ScrollContainerBy`成員函式來捲動量，單位為像素，以在容器文件以`sizeScroll`。  
  
```  
BOOL ScrollContainerBy(CSize sizeScroll);
```  
  
### <a name="parameters"></a>參數  
 `sizeScroll`  
 表示容器文件捲動多遠。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 正值表示捲動往下及往右。負值表示向上及向左捲動。  
  
##  <a name="a-nameupdateallitemsa--coleserverdocupdateallitems"></a><a name="updateallitems"></a>COleServerDoc::UpdateAllItems  
 呼叫此函式以通知所有連接到已變更的文件的文件的連結項目。  
  
```  
void UpdateAllItems(
    COleServerItem* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>參數  
 `pSender`  
 修改文件中，項目的指標或**NULL**如果所有項目更新。  
  
 `lHint`  
 包含有關修改資訊。  
  
 `pHint`  
 儲存修改的相關資訊的物件指標。  
  
 `nDrawAspect`  
 決定如何繪製項目。 這是介於`DVASPECT`列舉型別。 這個參數的值可以是下列其中一個：  
  
- `DVASPECT_CONTENT`項目表示的方式，可以顯示為其容器內的內嵌物件。  
  
- `DVASPECT_THUMBNAIL`「 縮圖 」 表示法中呈現項目，使它可以顯示在瀏覽工具。  
  
- `DVASPECT_ICON`項目是以一個圖示表示。  
  
- `DVASPECT_DOCPRINT`項目被表示，如同它已使用 [檔案] 功能表的 [列印] 命令來列印。  
  
### <a name="remarks"></a>備註  
 使用者變更伺服器文件後，通常會呼叫此函式。 如果 OLE 項目自動連結至文件，以反映所做的變更更新項目。 在容器應用程式使用 Microsoft Foundation 類別庫中，撰寫[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式`COleClientItem`呼叫。  
  
 此函數會呼叫`OnUpdate`成員函式的每個文件的項目，除了傳送項目，傳遞`pHint`， `lHint`，和`nDrawAspect`。 使用這些參數將資訊傳遞至相關文件所做的修改項目。 您可以編碼資訊使用`lHint`或者您也可以定義`CObject`-衍生類別，以儲存修改的相關資訊，並傳遞物件，該類別使用的`pHint`。 覆寫`OnUpdate`成員函式中的您`COleServerItem`-衍生的類別，以最佳化每個項目，根據它的呈現是否已變更的更新。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [COleLinkingDoc 類別](../../mfc/reference/colelinkingdoc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDocument 類別](../../mfc/reference/coledocument-class.md)   
 [COleLinkingDoc 類別](../../mfc/reference/colelinkingdoc-class.md)   
 [COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)

