---
title: COleServerDoc 類別
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: eec94a32fa0963d4cf2eccae0fb9e2423e75ffdc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421692"
---
# <a name="coleserverdoc-class"></a>COleServerDoc 類別

OLE 伺服器文件的基底類別。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleServerDoc：： COleServerDoc](#coleserverdoc)|建構 `COleServerDoc` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleServerDoc：： ActivateDocObject](#activatedocobject)|啟用相關聯的 DocObject 檔。|
|[COleServerDoc：： ActivateInPlace](#activateinplace)|啟用就地編輯的檔。|
|[COleServerDoc：:D eactivateAndUndo](#deactivateandundo)|停用伺服器的使用者介面。|
|[COleServerDoc：:D iscardUndoState](#discardundostate)|捨棄復原狀態資訊。|
|[COleServerDoc：： GetClientSite](#getclientsite)|抓取基礎 `IOleClientSite` 介面的指標。|
|[COleServerDoc：： GetEmbeddedItem](#getembeddeditem)|傳回代表整個檔之專案的指標。|
|[COleServerDoc：： GetItemClipRect](#getitemcliprect)|傳回目前的裁剪矩形以進行就地編輯。|
|[COleServerDoc：： GetItemPosition](#getitemposition)|傳回目前的位置矩形，相對於容器應用程式的工作區，以進行就地編輯。|
|[COleServerDoc：： GetZoomFactor](#getzoomfactor)|傳回以圖元為單位的縮放因數。|
|[COleServerDoc：： IsDocObject](#isdocobject)|判斷檔是否為 DocObject。|
|[COleServerDoc：： IsEmbedded](#isembedded)|指出檔是內嵌在容器檔案中，還是獨立執行。|
|[COleServerDoc：： IsInPlaceActive](#isinplaceactive)|如果專案目前已就地啟用，則傳回 TRUE。|
|[COleServerDoc：： NotifyChanged](#notifychanged)|通知容器使用者已變更檔。|
|[COleServerDoc：： NotifyClosed](#notifyclosed)|通知容器使用者已關閉檔。|
|[COleServerDoc：： NotifyRename](#notifyrename)|通知容器使用者已將檔重新命名。|
|[COleServerDoc：： NotifySaved](#notifysaved)|通知容器使用者已儲存檔。|
|[COleServerDoc：： OnDeactivate](#ondeactivate)|當使用者停用就地啟用的專案時，由架構呼叫。|
|[COleServerDoc：： OnDeactivateUI](#ondeactivateui)|由架構呼叫，以終結為就地啟用而建立的控制項和其他使用者介面元素。|
|[COleServerDoc：： Ondocwindowactivate 呼叫](#ondocwindowactivate)|當容器的檔框架視窗已啟用或停用時，由架構呼叫。|
|[COleServerDoc：： OnResizeBorder](#onresizeborder)|當容器應用程式的框架視窗或文件視窗調整大小時，由架構呼叫。|
|[COleServerDoc：： OnShowControlBars](#onshowcontrolbars)|由架構呼叫，以顯示或隱藏就地編輯的控制列。|
|[COleServerDoc：： OnUpdateDocument](#onupdatedocument)|當儲存內嵌專案的伺服器檔時，由架構呼叫，以更新容器的專案複本。|
|[COleServerDoc：： RequestPositionChange](#requestpositionchange)|變更就地編輯方塊架的位置。|
|[COleServerDoc：： SaveEmbedding](#saveembedding)|告訴容器應用程式儲存檔。|
|[COleServerDoc：： ScrollContainerBy](#scrollcontainerby)|滾動容器檔案。|
|[COleServerDoc：： UpdateAllItems](#updateallitems)|通知容器使用者已變更檔。|

### <a name="protected-methods"></a>受保護的方法

|名稱|描述|
|----------|-----------------|
|[COleServerDoc：： CreateInPlaceFrame](#createinplaceframe)|由架構呼叫以建立就地編輯的框架視窗。|
|[COleServerDoc：:D estroyInPlaceFrame](#destroyinplaceframe)|由架構呼叫，以終結用於就地編輯的框架視窗。|
|[COleServerDoc：： GetDocObjectServer](#getdocobjectserver)|覆寫此函式以建立新的 `CDocObjectServer` 物件，並指出此檔為 DocObject 容器。|
|[COleServerDoc：： OnClose](#onclose)|當容器要求關閉檔時，由架構呼叫。|
|[COleServerDoc：： OnExecOleCmd](#onexecolecmd)|執行指定的命令，或顯示命令的說明。|
|[COleServerDoc：： Onframewindowactivate 呼叫](#onframewindowactivate)|當容器的框架視窗啟動或停用時，由架構呼叫。|
|[COleServerDoc：： OnGetEmbeddedItem](#ongetembeddeditem)|呼叫以取得代表整個檔的 `COleServerItem`;用來取得內嵌專案。 需要執行。|
|[COleServerDoc：： OnReactivateAndUndo](#onreactivateandundo)|由架構呼叫來復原就地編輯期間所做的變更。|
|[COleServerDoc：： OnSetHostNames](#onsethostnames)|當容器設定内嵌物件的視窗標題時，由架構呼叫。|
|[COleServerDoc：： OnSetItemRects](#onsetitemrects)|由架構呼叫，以定位容器應用程式視窗內的就地編輯方塊架視窗。|
|[COleServerDoc：： OnShowDocument](#onshowdocument)|由架構呼叫以顯示或隱藏檔。|

## <a name="remarks"></a>備註

伺服器檔可以包含[COleServerItem](../../mfc/reference/coleserveritem-class.md)物件，其代表內嵌或連結專案的伺服器介面。 當容器啟動伺服器應用程式以編輯內嵌專案時，該專案會載入為它自己的伺服器檔。`COleServerDoc` 物件只包含一個 `COleServerItem` 物件，由整個檔組成。 當容器啟動伺服器應用程式以編輯連結的專案時，會從磁片載入現有的檔。部分檔的內容會反白顯示，以指出連結的專案。

`COleServerDoc` 物件也可以包含[COleClientItem](../../mfc/reference/coleclientitem-class.md)類別的專案。 這可讓您建立容器伺服器應用程式。 架構會提供函式，以便在服務 `COleServerItem` 物件時適當地儲存 `COleClientItem` 專案。

如果您的伺服器應用程式不支援連結，伺服器檔一律只會包含一個伺服器專案，這會將整個内嵌物件表示為檔。 如果您的伺服器應用程式支援連結，則每次選擇複製到剪貼簿時，都必須建立伺服器專案。

若要使用 `COleServerDoc`，請從它衍生一個類別，並執行[OnGetEmbeddedItem](#ongetembeddeditem)成員函式，讓您的伺服器支援內嵌專案。 從 `COleServerItem` 衍生類別，以在您的檔中執行專案，並從 `OnGetEmbeddedItem`傳回該類別的物件。

為了支援連結的專案，`COleServerDoc` 提供[OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem)成員函式。 如果您有自己管理檔專案的方式，您可以使用預設的實作為，或覆寫它。

您的應用程式支援的每個伺服器檔案類型都需要一個 `COleServerDoc`衍生的類別。 例如，如果您的伺服器應用程式支援工作表和圖表，則您需要兩個 `COleServerDoc`衍生的類別。

如需伺服器的詳細資訊，請參閱[伺服器：執行伺服器一](../../mfc/servers-implementing-a-server.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>需求

**標頭：** afxole。h

##  <a name="activatedocobject"></a>COleServerDoc：： ActivateDocObject

啟用相關聯的 DocObject 檔。

```
void ActivateDocObject();
```

### <a name="remarks"></a>備註

根據預設，`COleServerDoc` 不支援使用中的檔案（也稱為 DocObjects）。 若要啟用這種支援，請參閱[GetDocObjectServer](#getdocobjectserver)和類別[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)。

##  <a name="activateinplace"></a>COleServerDoc：： ActivateInPlace

啟用就地編輯的專案。

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>傳回值

如果成功，則為非零;否則為0，表示專案已完全開啟。

### <a name="remarks"></a>備註

此函式會執行就地啟用所需的所有作業。 它會建立一個就地的框架視窗、啟動它，並將它調整為專案、設定共用功能表和其他控制項、將專案滾動到視野中，以及將焦點設定為就地框架視窗。

此函式是由[COleServerItem：： OnShow](../../mfc/reference/coleserveritem-class.md#onshow)的預設實作為呼叫。 如果您的應用程式支援就地啟用的另一個動詞（例如「播放」），請呼叫此函式。

##  <a name="coleserverdoc"></a>COleServerDoc：： COleServerDoc

在不連接 OLE 系統 Dll 的情況下，構造 `COleServerDoc` 物件。

```
COleServerDoc();
```

### <a name="remarks"></a>備註

您必須呼叫[COleLinkingDoc：： Register](../../mfc/reference/colelinkingdoc-class.md#register) ，才能開啟與 OLE 的通訊。 如果您在應用程式中使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) ，`COleLinkingDoc`的 `OnNewDocument`、`OnOpenDocument`和 `OnSaveDocument`的執行，就會為您呼叫 `COleLinkingDoc::Register`。

##  <a name="createinplaceframe"></a>COleServerDoc：： CreateInPlaceFrame

架構會呼叫這個函式來建立就地編輯的框架視窗。

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
容器應用程式父視窗的指標。

### <a name="return-value"></a>傳回值

就地框架視窗的指標，如果不成功則為 Null。

### <a name="remarks"></a>備註

預設的執行會使用檔範本中指定的資訊來建立框架。 使用的視圖是為檔建立的第一個視圖。 這個視圖會暫時從原始框架中斷連結，並附加至新建立的框架。

這是一個先進的可覆寫。

##  <a name="deactivateandundo"></a>COleServerDoc：:D eactivateAndUndo

如果您的應用程式支援復原，而且使用者在啟用專案之後，但在編輯之前選擇 [復原]，請呼叫此函式。

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式是使用 MFC 程式庫所撰寫，則呼叫此函式會導致呼叫[COleClientItem：： OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) ，這會停用伺服器的使用者介面。

##  <a name="destroyinplaceframe"></a>COleServerDoc：:D estroyInPlaceFrame

此架構會呼叫這個函式，以終結就地框架視窗，並將伺服器應用程式的文件視窗還原至就地啟用之前的狀態。

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>參數

*pFrameWnd*<br/>
要終結之就地框架視窗的指標。

### <a name="remarks"></a>備註

這是一個先進的可覆寫。

##  <a name="discardundostate"></a>COleServerDoc：:D iscardUndoState

如果使用者執行無法復原的編輯作業，請呼叫此函式來強制容器應用程式捨棄其復原狀態資訊。

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

提供此函式的目的，是為了讓支援復原的伺服器能夠釋放無法使用的復原狀態資訊所使用的資源。

##  <a name="getclientsite"></a>COleServerDoc：： GetClientSite

抓取基礎 `IOleClientSite` 介面的指標。

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>傳回值

抓取基礎[IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)介面的指標。

##  <a name="getdocobjectserver"></a>COleServerDoc：： GetDocObjectServer

覆寫此函式以建立新的 `CDocObjectServer` 專案，並傳回其指標。

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>參數

*pDocSite*<br/>
將此檔連接到伺服器之 `IOleDocumentSite` 介面的指標。

### <a name="return-value"></a>傳回值

`CDocObjectServer`的指標;如果作業失敗，則為 Null。

### <a name="remarks"></a>備註

啟用 DocObject 伺服器時，傳回非 Null 指標會顯示用戶端可以支援 DocObjects。 預設的實值會傳回 Null。

支援 DocObjects 之檔的一般執行只會配置新的 `CDocObjectServer` 物件，並將它傳回給呼叫者。 例如，

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>COleServerDoc：： GetEmbeddedItem

呼叫此函式可取得代表整個檔之專案的指標。

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>傳回值

代表整個檔之專案的指標;如果作業失敗，則為 Null。

### <a name="remarks"></a>備註

它會呼叫[COleServerDoc：： OnGetEmbeddedItem](#ongetembeddeditem)，這是沒有預設實作為的虛擬函式。

##  <a name="getitemcliprect"></a>COleServerDoc：： GetItemClipRect

呼叫 `GetItemClipRect` 成員函式，以取得就地編輯之專案的裁剪矩形座標。

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>參數

*lpClipRect*<br/>
要接收專案之裁剪矩形座標的 `RECT` 結構或 `CRect` 物件的指標。

### <a name="remarks"></a>備註

座標是以圖元為單位，相對於容器應用程式視窗的工作區。

繪製不應出現在裁剪矩形之外。 通常會自動限制繪圖。 使用此函式來判斷使用者是否已滾動到檔的可見部分之外;若是如此，請透過呼叫[ScrollContainerBy](#scrollcontainerby)，視需要來滾動容器檔案。

##  <a name="getitemposition"></a>COleServerDoc：： GetItemPosition

呼叫 `GetItemPosition` 成員函式，以取得就地編輯之專案的座標。

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
`RECT` 結構或 `CRect` 物件的指標，以接收專案的座標。

### <a name="remarks"></a>備註

座標是以圖元為單位，相對於容器應用程式視窗的工作區。

專案的位置可以與目前的裁剪矩形進行比較，以判斷專案在螢幕上可見（或不可見）的範圍。

##  <a name="getzoomfactor"></a>COleServerDoc：： GetZoomFactor

`GetZoomFactor` 成員函式會決定已針對就地編輯啟用之專案的「縮放因數」。

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>參數

*lpSizeNum*<br/>
指向類別 `CSize` 的指標，該物件將會保存縮放因數的分子。 可以是 NULL。

*lpSizeDenom*<br/>
指向類別 `CSize` 的指標，該物件將會保存縮放因數的分母。 可以是 NULL。

*lpPosRect*<br/>
類別之物件的指標，`CRect` 描述專案的新位置。 如果這個引數為 Null，則函式會使用專案的目前位置。

### <a name="return-value"></a>傳回值

如果專案已啟動進行就地編輯，而且其縮放因數不是100% （1:1），則為非零值;否則為0。

### <a name="remarks"></a>備註

縮放因數（以圖元為單位）是專案大小與目前範圍的比例。 如果容器應用程式尚未設定專案的範圍，則會使用其自然範圍（如[COleServerItem：： OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)所決定）。

函式會將它的前兩個引數設定為專案的「縮放因數」的分子和分母。 如果未就地編輯專案，函數會將這些引數設定為預設值100% （或1:1），並傳回零。 如需進一步資訊，請參閱技術提示40， [MFC/OLE 就地調整大小和縮放](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。

##  <a name="isdocobject"></a>COleServerDoc：： IsDocObject

判斷檔是否為 DocObject。

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>傳回值

如果檔是 DocObject，則為 TRUE;否則為 FALSE。

##  <a name="isembedded"></a>COleServerDoc：： IsEmbedded

呼叫 `IsEmbedded` 成員函式，以判斷檔是否代表內嵌在容器中的物件。

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>傳回值

如果 `COleServerDoc` 物件是代表內嵌在容器中之物件的檔，則為非零值;否則為0。

### <a name="remarks"></a>備註

從檔案載入的檔不會內嵌，雖然容器應用程式可以將它當做連結來操作。 內嵌在容器檔案中的檔會被視為內嵌。

##  <a name="isinplaceactive"></a>COleServerDoc：： IsInPlaceActive

呼叫 `IsInPlaceActive` 成員函式，以判斷專案目前是否為就地作用中狀態。

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>傳回值

如果 `COleServerDoc` 物件就地作用中，則為非零;否則為0。

##  <a name="notifychanged"></a>COleServerDoc：： NotifyChanged

呼叫此函式可通知連接至檔已變更之檔的所有連結專案。

```
void NotifyChanged();
```

### <a name="remarks"></a>備註

一般而言，您會在使用者變更某些全域屬性（例如伺服器檔的維度）之後呼叫此函式。 如果 OLE 專案已連結至具有自動連結的檔，則會更新專案以反映變更。 在以 MFC 程式庫撰寫的容器應用程式中，會呼叫 `COleClientItem` 的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式。

> [!NOTE]
>  包含此函數是為了與 OLE 1 相容。 新的應用程式應該使用[UpdateAllItems](#updateallitems)。

##  <a name="notifyclosed"></a>COleServerDoc：： NotifyClosed

呼叫此函式可通知容器檔案已關閉。

```
void NotifyClosed();
```

### <a name="remarks"></a>備註

當使用者從 [檔案] 功能表選擇 [關閉] 命令時，`NotifyClosed` 是由 `COleServerDoc`的[OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument)成員函式的實作為呼叫。 在以 MFC 程式庫撰寫的容器應用程式中，會呼叫 `COleClientItem` 的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式。

##  <a name="notifyrename"></a>COleServerDoc：： NotifyRename

使用者重新命名伺服器檔之後，請呼叫此函式。

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>參數

*lpszNewName*<br/>
字串的指標，指定伺服器檔的新名稱;這通常是完整的路徑。

### <a name="remarks"></a>備註

當使用者從 [檔案] 功能表選擇 [另存新檔] 命令時，`NotifyRename` 是由 `COleServerDoc`的[OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)成員函式的執行所呼叫。 此函式會通知 OLE 系統 Dll，進而通知容器。 在以 MFC 程式庫撰寫的容器應用程式中，會呼叫 `COleClientItem` 的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式。

##  <a name="notifysaved"></a>COleServerDoc：： NotifySaved

在使用者儲存伺服器檔之後，呼叫此函式。

```
void NotifySaved();
```

### <a name="remarks"></a>備註

當使用者從 [檔案] 功能表中選擇 [儲存] 命令時，`COleServerDoc`的[OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)的執行會為您呼叫 `NotifySaved`。 此函式會通知 OLE 系統 Dll，進而通知容器。 在以 MFC 程式庫撰寫的容器應用程式中，會呼叫 `COleClientItem` 的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式。

##  <a name="onclose"></a>COleServerDoc：： OnClose

當容器要求關閉伺服器檔時由架構呼叫。

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>參數

*dwCloseOption*<br/>
列舉 OLECLOSE 中的值。 這個參數的值可以是下列其中一個：

- 如果檔案已遭修改，OLECLOSE_SAVEIFDIRTY 儲存檔案。

- OLECLOSE_NOSAVE 檔案關閉而不儲存。

- OLECLOSE_PROMPTSAVE 如果檔案已修改，系統會提示使用者儲存該檔案。

### <a name="remarks"></a>備註

預設的實值 `CDocument::OnCloseDocument`會呼叫。

如需詳細資訊和其他值，請參閱 Windows SDK 中的[OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) 。

##  <a name="ondeactivate"></a>COleServerDoc：： OnDeactivate

當使用者停用目前就地作用中的內嵌或連結專案時，由架構呼叫。

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>備註

此函式會將容器應用程式的使用者介面還原成其原始狀態，並終結為就地啟用而建立的任何功能表和其他控制項。

此時應該會無條件地釋放「復原狀態」資訊。

如需詳細資訊，請參閱文章[啟用](../../mfc/activation-cpp.md)。

##  <a name="ondeactivateui"></a>COleServerDoc：： OnDeactivateUI

當使用者停用就地啟用的專案時呼叫。

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>參數

*bUndoable*<br/>
指定是否可以復原編輯變更。

### <a name="remarks"></a>備註

此函式會將容器應用程式的使用者介面還原成其原始狀態，並隱藏任何針對就地啟用而建立的功能表和其他控制項。

架構一律會將*bUndoable*設定為 FALSE。 如果伺服器支援復原，而且有可以復原的作業，請呼叫*bUndoable*設定為 TRUE 的基類實作為運算。

##  <a name="ondocwindowactivate"></a>COleServerDoc：： Ondocwindowactivate 呼叫

架構會呼叫這個函式來啟用或停用就地編輯的文件視窗。

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>參數

*bActivate*<br/>
指定是否要啟用或停用文件視窗。

### <a name="remarks"></a>備註

預設的實作為視情況移除或加入框架層級的使用者介面專案。 如果您想要在包含專案的檔已啟用或停用時執行其他動作，請覆寫此函式。

如需詳細資訊，請參閱文章[啟用](../../mfc/activation-cpp.md)。

##  <a name="onexecolecmd"></a>COleServerDoc：： OnExecOleCmd

架構會呼叫這個函式來執行指定的命令，或顯示命令的說明。

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>參數

*pguidCmdGroup*<br/>
識別一組命令之 GUID 的指標。 可以是 Null，表示預設的命令群組。

*nCmdID*<br/>
要執行的命令。 必須位於*pguidCmdGroup*所識別的群組中。

*nCmdExecOut*<br/>
物件執行命令的方式，是 OLECMDEXECOPT 列舉中的一個或多個下列值：

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
VARIANTARG 的指標，其中包含命令的輸入引數。 可以是 NULL。

*pvarargOut*<br/>
VARIANTARG 的指標，用來接收命令的輸出傳回值。 可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功，則傳回 S_OK;否則，下列其中一個錯誤碼：

|值|描述|
|-----------|-----------------|
|E_UNEXPECTED|發生未預期的錯誤|
|E_FAIL|發生錯誤|
|E_NOTIMPL|指出 MFC 本身應該嘗試轉譯和分派命令|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*為非 Null，但未指定可辨識的命令群組|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*在群組*pguidCmdGroup*中無法辨識為有效的命令|
|OLECMDERR_DISABLED|*NCmdID*所識別的命令已停用且無法執行|
|OLECMDERR_NOHELP|呼叫端在*nCmdID*所識別的命令上尋求協助，但沒有可用的說明|
|OLECMDERR_CANCELED|使用者已取消執行|

### <a name="remarks"></a>備註

`COleCmdUI` 可以用來啟用、更新及設定 DocObject 使用者介面命令的其他屬性。 初始化命令之後，您可以使用 `OnExecOleCmd`來執行它們。

架構會在嘗試轉譯和分派 OLE 檔命令之前呼叫函式。 您不需要覆寫此函式來處理標準 OLE 檔命令，但如果您想要處理自己的自訂命令，或處理接受參數或傳回結果的命令，則必須提供此函式的覆寫功能。

大部分的命令都不接受引數或傳回值。 對於大部分的命令，呼叫者可以針對*pvarargIn*和*pvarargOut*傳遞 null。 對於預期輸入值的命令，呼叫者可以宣告和初始化 VARIANTARG 變數，並將指標傳遞至*pvarargIn*中的變數。 針對需要單一值的命令，引數可以直接儲存在 VARIANTARG 中，並傳遞至函數。 您必須使用其中一個支援的類型（例如 `IDispatch` 和 SAFEARRAY），將多個引數封裝在 VARIANTARG 內。

同樣地，如果命令傳回引數，則呼叫端應宣告 VARIANTARG，將它初始化為 VT_EMPTY，並在*pvarargOut*中傳遞其位址。 如果命令傳回單一值，物件可以直接將該值儲存在*pvarargOut*中。 多個輸出值必須以適合 VARIANTARG 的某種方式封裝。

此函式的基類執行會引導與命令目標相關聯的 OLE_COMMAND_MAP 結構，並嘗試將命令分派給適當的處理常式。 基類的執行僅適用于不接受引數或傳回值的命令。 如果您需要處理接受引數或傳回值的命令，您必須覆寫此函式，並自行使用*pvarargIn*和*pvarargOut*參數。

##  <a name="onframewindowactivate"></a>COleServerDoc：： Onframewindowactivate 呼叫

當容器應用程式的框架視窗已啟動或停用時，架構會呼叫這個函式。

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>參數

*bActivate*<br/>
指定是否要啟用或停用框架視窗。

### <a name="remarks"></a>備註

預設的執行會取消框架視窗可能所在的任何說明模式。 如果您想要在框架視窗啟動或停用時執行特殊處理，請覆寫此函數。

如需詳細資訊，請參閱文章[啟用](../../mfc/activation-cpp.md)。

##  <a name="ongetembeddeditem"></a>COleServerDoc：： OnGetEmbeddedItem

在容器應用程式呼叫伺服器應用程式以建立或編輯內嵌專案時，由架構呼叫。

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>傳回值

代表整個檔之專案的指標;如果作業失敗，則為 Null。

### <a name="remarks"></a>備註

沒有預設的實作。 您必須覆寫這個函式，以傳回代表整份檔的專案。 這個傳回值應該是 `COleServerItem`衍生類別的物件。

##  <a name="onreactivateandundo"></a>COleServerDoc：： OnReactivateAndUndo

當使用者選擇復原對已啟動、已變更，且後續停用的專案所做的變更時，架構會呼叫這個函式。

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

預設的執行不會執行任何操作，除非傳回 FALSE 表示失敗。

如果您的應用程式支援復原，請覆寫此函式。 通常您會執行復原作業，然後藉由呼叫 `ActivateInPlace`來啟動專案。 如果容器應用程式是以 MFC 程式庫撰寫，則呼叫 `COleClientItem::ReactivateAndUndo` 會導致呼叫此函式。

##  <a name="onresizeborder"></a>COleServerDoc：： OnResizeBorder

當容器應用程式的框架視窗變更大小時，此架構會呼叫這個函式。

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>參數

*lpRectBorder*<br/>
`RECT` 結構的指標，或指定框線座標的 `CRect` 物件。

*lpUIWindow*<br/>
擁有目前就地編輯會話之類別 `IOleInPlaceUIWindow` 物件的指標。

*bFrame*<br/>
如果*lpUIWindow*指向容器應用程式的最上層框架視窗，則為 TRUE，如果*lpUIWindow*指向容器應用程式的檔層級框架視窗，則為 FALSE。

### <a name="remarks"></a>備註

此函式會根據新的視窗大小調整工具列和其他使用者介面元素的大小。

如需詳細資訊，請參閱 Windows SDK 中的[IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) 。

這是一個先進的可覆寫。

##  <a name="onsethostnames"></a>COleServerDoc：： OnSetHostNames

當容器設定或變更此檔的主機名稱時，由架構呼叫。

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>參數

*lpszHost*<br/>
指定容器應用程式名稱之字串的指標。

*lpszHostObj*<br/>
字串的指標，指定檔的容器名稱。

### <a name="remarks"></a>備註

預設的執行會變更所有參考此檔之視圖的檔標題。

如果您的應用程式透過不同的機制設定標題，則覆寫此函式。

##  <a name="onsetitemrects"></a>COleServerDoc：： OnSetItemRects

架構會呼叫這個函式，將就地編輯方塊架視窗放在容器應用程式的框架視窗內。

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
`RECT` 結構或 `CRect` 物件的指標，指定相對於容器應用程式之工作區的就地框架視窗位置。

*lpClipRect*<br/>
`RECT` 結構或 `CRect` 物件的指標，指定相對於容器應用程式之工作區的就地框架視窗裁剪矩形。

### <a name="remarks"></a>備註

如有需要，請覆寫此函式以更新視圖的縮放因數。

通常會呼叫這個函式以回應 `RequestPositionChange` 呼叫，雖然容器可以隨時呼叫此函式來要求就地專案的位置變更。

##  <a name="onshowcontrolbars"></a>COleServerDoc：： OnShowControlBars

此架構會呼叫這個函式，以顯示或隱藏與*pFrameWnd*所識別之框架視窗相關聯的伺服器應用程式控制列。

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>參數

*pFrameWnd*<br/>
框架視窗的指標，其控制列應隱藏或顯示。

*bShow*<br/>
決定是否要顯示或隱藏控制列。

### <a name="remarks"></a>備註

預設的實值會列舉該框架視窗所擁有的所有控制列，並隱藏或顯示它們。

##  <a name="onshowdocument"></a>COleServerDoc：： OnShowDocument

當伺服器檔必須隱藏或顯示時，架構會呼叫 `OnShowDocument` 函數。

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
指定是否要顯示或隱藏檔的使用者介面。

### <a name="remarks"></a>備註

如果*bShow*為 TRUE，則預設的執行會啟動伺服器應用程式（如有必要），並讓容器應用程式滾動其視窗，讓專案可見。 如果*bShow*為 FALSE，則預設的實值會透過對 `OnDeactivate`的呼叫來停用專案，然後損毀或隱藏已為檔建立的所有框架視窗（第一部除外）。 如果沒有可見的檔，則預設的執行會隱藏伺服器應用程式。

##  <a name="onupdatedocument"></a>COleServerDoc：： OnUpdateDocument

在儲存複合檔案中內嵌專案的檔時，由架構呼叫。

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>傳回值

如果已成功更新檔，則為非零。否則為0。

### <a name="remarks"></a>備註

預設的實值會呼叫[COleServerDoc：： NotifySaved](#notifysaved)和[COleServerDoc：： SaveEmbedding](#saveembedding)成員函式，然後將檔標記為清除。 如果您想要在更新內嵌專案時執行特殊處理，請覆寫這個函式。

##  <a name="requestpositionchange"></a>COleServerDoc：： RequestPositionChange

呼叫這個成員函式，讓容器應用程式變更專案的位置。

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
`RECT` 結構或包含專案新位置之 `CRect` 物件的指標。

### <a name="remarks"></a>備註

當就地作用中專案的資料已變更時，通常會呼叫這個函式（搭配 `UpdateAllItems`）。 在此呼叫之後，容器不一定會藉由呼叫 `OnSetItemRects`來執行變更。 產生的位置可能與要求的位置不同。

##  <a name="saveembedding"></a>COleServerDoc：： SaveEmbedding

呼叫此函式可告知容器應用程式儲存内嵌物件。

```
void SaveEmbedding();
```

### <a name="remarks"></a>備註

此函式會從 `OnUpdateDocument`自動呼叫。 請注意，此函式會在磁片上更新專案，因此通常只會呼叫為特定使用者動作的結果。

##  <a name="scrollcontainerby"></a>COleServerDoc：： ScrollContainerBy

呼叫 `ScrollContainerBy` 成員函式，依 `sizeScroll`所表示的數量（以圖元為單位）來滾動容器檔案。

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>參數

*sizeScroll*<br/>
表示容器檔案要滾動到的距離。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

正數值表示向下和向右滾動;負數值表示向上和向左滾動。

##  <a name="updateallitems"></a>COleServerDoc：： UpdateAllItems

呼叫此函式可通知連接至檔已變更之檔的所有連結專案。

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>參數

*pSender*<br/>
修改檔之專案的指標，如果要更新所有專案，則為 Null。

*lHint*<br/>
包含修改的相關資訊。

*pHint*<br/>
物件的指標，儲存修改的相關資訊。

*nDrawAspect*<br/>
決定專案的繪製方式。 這是來自 DVASPECT 列舉的值。 這個參數的值可以是下列其中一個：

- DVASPECT_CONTENT 專案的表示方式，可以在其容器內顯示為内嵌物件。

- DVASPECT_THUMBNAIL 專案會以「縮圖」標記法呈現，使其可以在流覽工具中顯示。

- DVASPECT_ICON 專案是以圖示表示。

- DVASPECT_DOCPRINT 專案的表示方式，就如同使用 [檔案] 功能表中的 [列印] 命令來列印一樣。

### <a name="remarks"></a>備註

您通常會在使用者變更伺服器檔後呼叫此函式。 如果 OLE 專案已連結至具有自動連結的檔，則會更新專案以反映變更。 在以 MFC 程式庫撰寫的容器應用程式中，會呼叫 `COleClientItem` 的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函式。

此函式會針對每個檔專案呼叫 `OnUpdate` 成員函式，但傳送專案、傳遞*pHint*、 *lHint*和*nDrawAspect*除外。 使用這些參數，將資訊傳遞至對檔所做之修改的相關專案。 您可以使用*lHint*來編碼資訊，也可以定義 `CObject`衍生的類別來儲存修改的相關資訊，並使用*pHint*傳遞該類別的物件。 覆寫 `COleServerItem`衍生類別中的 `OnUpdate` 成員函式，根據其簡報是否已變更，將每個專案的更新優化。

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc 類別](../../mfc/reference/colelinkingdoc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 類別](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc 類別](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
