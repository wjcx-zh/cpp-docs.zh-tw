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
ms.openlocfilehash: 8e75ec5c00c614a225a059a2b3cf97a7a307c61c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753783"
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
|[COleServerDoc:COleServerDoc](#coleserverdoc)|建構 `COleServerDoc` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleServerDoc::啟動文件物件](#activatedocobject)|啟動關聯的文件對象文件。|
|[COleServerDoc::啟動原位](#activateinplace)|啟動文件進行就地編輯。|
|[COleServerDoc::D](#deactivateandundo)|停用伺服器的用戶介面。|
|[COleServerDoc::DiscardUndoState](#discardundostate)|丟棄撤消狀態資訊。|
|[COleServerDoc:取得用戶端網站](#getclientsite)|檢索指向基礎`IOleClientSite`介面的指標。|
|[COleServerDoc:取得嵌入式項目](#getembeddeditem)|返回指向表示整個文檔的項的指標。|
|[COleServerDoc:取得項目剪輯](#getitemcliprect)|返回當前裁剪矩形以進行就地編輯。|
|[COleServerDoc:取得項目位置](#getitemposition)|返回當前位置矩形(相對於容器應用程式的工作區),以便進行就地編輯。|
|[COleServerDoc:取得ZoomFactor](#getzoomfactor)|返回以像素為單位的縮放係數。|
|[COleServerDoc:isDocObject](#isdocobject)|確定文檔是否為文件物件。|
|[COleServerDoc:是嵌入式](#isembedded)|指示文檔是嵌入容器文件還是獨立運行。|
|[COleServerDoc:即處於主動狀態](#isinplaceactive)|如果專案當前已啟動到位,則返回 TRUE。|
|[COleServerDoc:通知已變更](#notifychanged)|通知容器使用者已更改文檔。|
|[COleServerDoc::通知已關閉](#notifyclosed)|通知容器使用者已關閉文檔。|
|[COleServerDoc:通知重新命名](#notifyrename)|通知容器使用者已重新命名文件。|
|[COleServerDoc:通知已儲存](#notifysaved)|通知容器使用者已保存文檔。|
|[COleServerDoc:開啟啟動](#ondeactivate)|當使用者停用就地啟動的專案時,由框架調用。|
|[COleServerDoc::打開停用UI](#ondeactivateui)|由框架呼叫以銷毀為就地啟動創建的控制項和其他使用者介面元素。|
|[COleServerDoc::在DocWindow啟動](#ondocwindowactivate)|當容器的文檔框視窗啟動或停用時,由框架調用。|
|[COleServerDoc::在重調整邊界](#onresizeborder)|調整容器應用程式的框架視窗或文檔視窗的大小時,由框架調用。|
|[COleServerDoc::在顯示控制列](#onshowcontrolbars)|框架調用以顯示或隱藏控制欄進行就地編輯。|
|[COleServerDoc:更新文件](#onupdatedocument)|在保存作為嵌入項的伺服器文件時,由框架調用,更新容器的項副本。|
|[COleServerDoc::請求位置變更](#requestpositionchange)|更改就地編輯框架的位置。|
|[COleServerDoc::儲存嵌入](#saveembedding)|告訴容器應用程式保存文檔。|
|[COleServerDoc::滾動容器By](#scrollcontainerby)|滾動容器文件。|
|[COleServerDoc:更新所有專案](#updateallitems)|通知容器使用者已更改文檔。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COleServerDoc::建立在位幀](#createinplaceframe)|框架呼叫以建立用於就地編輯的框架視窗。|
|[COleServerDoc::D](#destroyinplaceframe)|框架調用以銷毀用於就地編輯的框架視窗。|
|[COleServerDoc:取得Doc物件伺服器](#getdocobjectserver)|重寫此函數以創建新`CDocObjectServer`物件,並指示此文檔是 DocObject 容器。|
|[COleServerDoc:關閉](#onclose)|當容器請求關閉文檔時,由框架調用。|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|執行指定的命令或顯示該命令的説明。|
|[COleServerDoc:在框架視窗啟動](#onframewindowactivate)|當容器的幀視窗啟動或停用時,由框架調用。|
|[COleServerDoc::在嵌入式專案上](#ongetembeddeditem)|呼叫 以`COleServerItem`取得 表示整個文件的 ;用於獲取嵌入項。 需要實施。|
|[COleServerDoc::重新啟動和Undo](#onreactivateandundo)|由框架調用以撤銷在就地編輯期間所做的更改。|
|[COleServerDoc::打開主機名](#onsethostnames)|當容器設置嵌入物件的視窗標題時,由框架調用。|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|由框架調用,將就地編輯框架視窗放置在容器應用程式的視窗內。|
|[COleServerDoc:在顯示文件上](#onshowdocument)|由框架呼叫以顯示或隱藏文檔。|

## <a name="remarks"></a>備註

伺服器文件可以包含[COleServerItem 物件](../../mfc/reference/coleserveritem-class.md),這些物件表示嵌入或連結項的伺服器介面。 當容器啟動伺服器應用程式以編輯嵌入的專案時,該專案將載入為其自己的伺服器文檔;當容器啟動伺服器應用程式以編輯嵌入項時,該項將載入為其自己的伺服器文檔。物件`COleServerDoc`僅包含一`COleServerItem`個 物件,由整個文檔組成。 當容器啟動伺服器應用程式以編輯連結項時,將從磁碟載入現有文檔;當伺服器應用程式透過容器啟動時,將從磁碟載入現有文件。文件內容的一部分突出顯示以指示連結項。

`COleServerDoc`物件還可以包含[COleClientItem](../../mfc/reference/coleclientitem-class.md)類的專案。 這允許您創建容器伺服器應用程式。 框架提供函數,用於在為`COleClientItem``COleServerItem`物件提供服務時正確存儲項。

如果伺服器應用程式不支援連結,則伺服器文檔將始終只包含一個伺服器項,該伺服器項將整個嵌入物件表示為文檔。 如果伺服器應用程式確實支援連結,則必須在每次將所選內容複製到剪貼簿時創建伺服器項。

要使用`COleServerDoc`,從派生類並實現[OnGetEmbeddedItem](#ongetembeddeditem)成員函數,該函數允許伺服器支援嵌入項。 衍生`COleServerItem`類別以以文件中的項目,並從傳回該類別的物件`OnGetEmbeddedItem`。

要支援連結的專案,`COleServerDoc`提供[OnGetLinkItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem)成員功能。 如果您有自己的方法來管理文檔項,則可以使用預設實現或重寫它。

對於應用程式支援的`COleServerDoc`每種伺服器文件類型,都需要一個派生類。 例如,如果伺服器應用程式支援工作表和圖表,則需要兩`COleServerDoc`個派生類。

有關伺服器的詳細資訊,請參閱文章[「伺服器:實現伺服器](../../mfc/servers-implementing-a-server.md)」。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coleserverdocactivatedocobject"></a><a name="activatedocobject"></a>COleServerDoc::啟動文件物件

啟動關聯的文件對象文件。

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>備註

默認情況下,`COleServerDoc`不支援活動文檔(也稱為文檔物件)。 要啟用此支援,請參閱[GetDocObjectServer](#getdocobjectserver)和類別[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)。

## <a name="coleserverdocactivateinplace"></a><a name="activateinplace"></a>COleServerDoc::啟動原位

啟動項目進行就地編輯。

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>傳回值

如果成功,則非零;否則 0,表示專案已完全打開。

### <a name="remarks"></a>備註

此函數執行就地啟動所需的所有操作。 它創建一個就地框架視窗,啟動它並將其大小調整到專案,設置共用功能表和其他控制項,將專案滾動到檢視中,並將焦點設置到就地框架視窗。

此函數由[COleServerItem 的預設執行呼叫::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。 如果應用程式支援另一個用於就地啟動的謂詞(如 Play),請調用此函數。

## <a name="coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a>COleServerDoc:COleServerDoc

建構`COleServerDoc`物件而不與 OLE 系統 DLL 連接。

```
COleServerDoc();
```

### <a name="remarks"></a>備註

您必須致電[COle 連結Doc:註冊](../../mfc/reference/colelinkingdoc-class.md#register)才能打開與 OLE 的通信。 如果您在應用程式中使用[COleTemplateServer,](../../mfc/reference/coletemplateserver-class.md)`COleLinkingDoc::Register``COleLinkingDoc`則呼叫`OnNewDocument`的`OnSaveDocument``OnOpenDocument`實作的實作 。

## <a name="coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a>COleServerDoc::建立在位幀

框架呼叫此函數以創建用於就地編輯的框架視窗。

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向容器應用程式的父視窗的指標。

### <a name="return-value"></a>傳回值

指向就地幀視窗的指標,如果失敗,則指向 NULL。

### <a name="remarks"></a>備註

預設實現使用文檔範本中指定的資訊來創建框架。 使用的檢視是為文檔創建的第一個檢視。 此視圖暫時與原始幀分離,並附加到新創建的幀。

這是一個高級的可重寫。

## <a name="coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a>COleServerDoc::D

如果應用程式支援"撤銷",並且使用者在啟動專案後但在編輯專案之前選擇"撤銷",請調用此函數。

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

如果容器應用程式是使用 Microsoft 基礎類庫編寫的,則調用此函數會導致調用[COleClientItem::ondeactivate 和Undo,](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo)從而停用伺服器的用戶介面。

## <a name="coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a>COleServerDoc::D

框架調用此函數以銷毀就地幀視窗,並在就地啟動之前將伺服器應用程式的文檔視窗返回到其狀態。

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>參數

*pFramewnd*<br/>
指向要銷毀的就地幀視窗的指標。

### <a name="remarks"></a>備註

這是一個高級的可重寫。

## <a name="coleserverdocdiscardundostate"></a><a name="discardundostate"></a>COleServerDoc::DiscardUndoState

如果使用者執行無法撤銷的編輯操作,請呼叫此函數以強制容器應用程式放棄其撤消狀態資訊。

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>傳回值

非零成功，否則為 0。

### <a name="remarks"></a>備註

提供此函數,以便支援撤銷的伺服器可以釋放資源,否則這些資源將被無法使用的撤銷狀態資訊所消耗。

## <a name="coleserverdocgetclientsite"></a><a name="getclientsite"></a>COleServerDoc:取得用戶端網站

檢索指向基礎`IOleClientSite`介面的指標。

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>傳回值

檢索指向基礎[IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)介面的指標。

## <a name="coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a>COleServerDoc:取得Doc物件伺服器

重寫此函數以創建新`CDocObjectServer`項並返回指向它的指標。

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>參數

*pDocSite*<br/>
指向將此`IOleDocumentSite`文件連接到伺服器的介面的指標。

### <a name="return-value"></a>傳回值

指向的`CDocObjectServer`指標 。如果操作失敗,則為 NULL。

### <a name="remarks"></a>備註

啟動 DocObject 伺服器時,傳回非 NULL 指標將顯示用戶端可以支援文件物件。 預設實現返回 NULL。

支持文檔文件的典型實現將只分配一個`CDocObjectServer`新 物件並將其返回到調用方。 例如：

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

## <a name="coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a>COleServerDoc:取得嵌入式項目

呼叫此函數以獲取指向表示整個文件的項的指標。

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>傳回值

指向表示整個文檔的項的指標;如果操作失敗,則為 NULL。

### <a name="remarks"></a>備註

它調用[COleServerDoc:onGetEmbeddedItem,](#ongetembeddeditem)一個沒有預設實現的虛擬函數。

## <a name="coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a>COleServerDoc:取得項目剪輯

呼叫`GetItemClipRect`成員函數,獲取正在編輯的項目的裁剪矩形座標。

```cpp
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>參數

*lpClipRect*<br/>
指向`RECT`結構或物件以`CRect`接收專案的裁剪矩形座標的指標。

### <a name="remarks"></a>備註

坐標相對於容器應用程式視窗的工作區以像素為單位。

不應在裁剪矩形之外進行繪圖。 通常,繪圖會自動受到限制。 使用此函數可以確定使用者是否已在文檔的可見部分之外滾動;因此,如果使用者在文檔的可見部分之外滾動過滾動。如果是這樣,請根據需要通過調用[ScrollContainerBy](#scrollcontainerby)滾動容器文檔。

## <a name="coleserverdocgetitemposition"></a><a name="getitemposition"></a>COleServerDoc:取得項目位置

呼叫`GetItemPosition`成員函數,獲取正在編輯的項目的座標。

```cpp
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
指向`RECT`結構或物件以`CRect`接收項座標的指標。

### <a name="remarks"></a>備註

坐標相對於容器應用程式視窗的工作區以像素為單位。

可以將專案的位置與當前裁剪矩形進行比較,以確定專案在螢幕上可見(或不可見)的程度。

## <a name="coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a>COleServerDoc:取得ZoomFactor

成員`GetZoomFactor`函數確定已啟動用於就地編輯的專案的「縮放係數」。

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>參數

*lpSizeNum*<br/>
指向將保存縮放因子分子`CSize`的類物件的指標。 可以是 NULL。

*lpSizeDenom*<br/>
指向將保存縮放因數分`CSize`母的類物件的指標。 可以是 NULL。

*lpPosRect*<br/>
指向描述項新位置的`CRect`類物件的指標。 如果此參數為 NULL,則函數使用項的當前位置。

### <a name="return-value"></a>傳回值

如果專案被啟動進行就地編輯,並且其縮放係數超過 100%(1:1),則非零;否則 0。

### <a name="remarks"></a>備註

縮放係數(以像素為單位)是專案大小與其當前範圍的比例。 如果容器應用程式未設置項的範圍,則使用其自然範圍(由[COleServerItem::onGet 範圍](../../mfc/reference/coleserveritem-class.md#ongetextent))確定。

函數將其前兩個參數設置到項"縮放因數"的分子和分母。 如果未就位編輯專案,則函數將這些參數設置為預設值 100%(或 1:1),並返回零。 有關詳細資訊,請參閱技術說明[40、MFC/OLE 就地調整大小和縮放](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)。

## <a name="coleserverdocisdocobject"></a><a name="isdocobject"></a>COleServerDoc:isDocObject

確定文檔是否為文件物件。

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>傳回值

如果文件是文件物件,則為 TRUE;如果文檔為文檔物件,則為 TRUE。否則 FALSE。

## <a name="coleserverdocisembedded"></a><a name="isembedded"></a>COleServerDoc:是嵌入式

調用`IsEmbedded`成員函數以確定文檔是否表示嵌入在容器中的物件。

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>傳回值

如果對像是表示`COleServerDoc`嵌入在容器中的物件的文件,則非零;否則 0。

### <a name="remarks"></a>備註

從檔載入的文件不會嵌入,儘管容器應用程式可能會將其作為連結進行操作。 嵌入在容器文件中的文檔被視為嵌入。

## <a name="coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a>COleServerDoc:即處於主動狀態

調用`IsInPlaceActive`成員函數以確定專案當前是否處於就地活動狀態。

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>傳回值

如果`COleServerDoc`物件處於活動狀態,則非零;否則 0。

## <a name="coleserverdocnotifychanged"></a><a name="notifychanged"></a>COleServerDoc:通知已變更

呼叫此函數以通知連接到文檔的所有連結項的文檔已更改。

```cpp
void NotifyChanged();
```

### <a name="remarks"></a>備註

通常,在使用者更改某些全域屬性(如伺服器文檔的尺寸)後調用此函數。 如果 OLE 項連結到具有自動連結的文檔,則該項將更新以反映更改。 在使用 Microsoft 基礎類庫編寫的容器應用程式中,調`COleClientItem`用的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函數。

> [!NOTE]
> 此函數包含在與 OLE 1 相容時。 新應用程式應使用[UpdateAllItem](#updateallitems)。

## <a name="coleserverdocnotifyclosed"></a><a name="notifyclosed"></a>COleServerDoc::通知已關閉

呼叫此函數以通知容器文件已關閉。

```cpp
void NotifyClosed();
```

### <a name="remarks"></a>備註

當使用者從「檔」功能表中選擇「關閉」命令時,`NotifyClosed``COleServerDoc`由[OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument)成員函數的實現呼叫。 在使用 Microsoft 基礎類庫編寫的容器應用程式中,調`COleClientItem`用的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函數。

## <a name="coleserverdocnotifyrename"></a><a name="notifyrename"></a>COleServerDoc:通知重新命名

在使用者重新命名伺服器文件後呼叫此功能。

```cpp
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>參數

*lpsz 新名稱*<br/>
指定伺服器文件新名稱的字串;這通常是完全限定的路徑。

### <a name="remarks"></a>備註

當使用者從「檔」功能表中選擇「保存為」命令時,`NotifyRename``COleServerDoc`由[OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)成員函數的實現調用。 此功能通知 OLE 系統 DLL,後者又通知容器。 在使用 Microsoft 基礎類庫編寫的容器應用程式中,調`COleClientItem`用的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函數。

## <a name="coleserverdocnotifysaved"></a><a name="notifysaved"></a>COleServerDoc:通知已儲存

在使用者保存伺服器文件後調用此功能。

```cpp
void NotifySaved();
```

### <a name="remarks"></a>備註

當使用者從「檔」功能表中選擇「保存」命令時,`NotifySaved``COleServerDoc`由[OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument)的實現來調用。 此功能通知 OLE 系統 DLL,後者又通知容器。 在使用 Microsoft 基礎類庫編寫的容器應用程式中,調`COleClientItem`用的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函數。

## <a name="coleserverdoconclose"></a><a name="onclose"></a>COleServerDoc:關閉

當容器請求關閉伺服器文檔時,由框架調用。

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>參數

*dwCloseOption*<br/>
枚舉 OLECLOSE 中的值。 這個參數的值可以是下列其中一個：

- OLECLOSE_SAVEIFDIRTY如果檔已被修改,則保存該檔。

- OLECLOSE_NOSAVE檔已關閉而不保存。

- OLECLOSE_PROMPTSAVE如果檔已被修改,系統將提示使用者保存該檔。

### <a name="remarks"></a>備註

預設執行呼叫`CDocument::OnCloseDocument`。

有關詳細資訊和其他值,請參閱 Windows SDK 中的[OLECLOSE。](/windows/win32/api/oleidl/ne-oleidl-oleclose)

## <a name="coleserverdocondeactivate"></a><a name="ondeactivate"></a>COleServerDoc:開啟啟動

當使用者停用當前處於活動狀態的嵌入或連結項時,由框架調用。

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>備註

此函數將容器應用程式的用戶介面還原到其原始狀態,並銷毀為就地啟動而創建的任何功能表和其他控制項。

此時應無條件釋放撤銷狀態資訊。

有關詳細資訊,請參閱文章[「啟動](../../mfc/activation-cpp.md)」。。

## <a name="coleserverdocondeactivateui"></a><a name="ondeactivateui"></a>COleServerDoc::打開停用UI

當使用者停用就地啟動的專案時調用。

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>參數

*不可多做*<br/>
指定是否可以復原編輯變更。

### <a name="remarks"></a>備註

此函數將容器應用程式的用戶介面還原到其原始狀態,隱藏為就地啟動而創建的任何功能表和其他控制項。

框架始終設置*不可執行*的 FALSE。 如果伺服器支援撤銷,並且有一個可以撤銷的操作,請調用基類實現,將*bUndo 設置為*TRUE。

## <a name="coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a>COleServerDoc::在DocWindow啟動

框架呼叫此函數以啟動或停用文件視窗以進行就地編輯。

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>參數

*b 啟動*<br/>
指定文件視窗是啟動還是停用。

### <a name="remarks"></a>備註

預設實現根據需要刪除或添加框架級用戶介面元素。 如果要在啟動或停用包含專案的文檔時執行其他操作,請覆蓋此函數。

有關詳細資訊,請參閱文章[「啟動](../../mfc/activation-cpp.md)」。。

## <a name="coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

框架呼叫此函數以執行指定的命令或顯示命令的説明。

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>參數

*普吉德集團*<br/>
指向標識一組命令的 GUID 的指標。 可以為 NULL 以指示預設命令組。

*nCmdID*<br/>
要執行的命令。 必須位於*pguidCmdGroup*標識的組中。

*nCmdExecOut*<br/>
物件執行命令的方式,從 OLECMDEXECOPT 枚舉中執行以下一個或多個值:

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*普瓦拉金*<br/>
指向包含命令的輸入參數的 VARIANTARG 的指標。 可以是 NULL。

*普瓦拉格*<br/>
指向 VARIANTARG 的指標,以接收命令中的輸出返回值。 可以是 NULL。

### <a name="return-value"></a>傳回值

如果成功,返回S_OK;否則,以下錯誤代碼之一:

|值|描述|
|-----------|-----------------|
|E_UNEXPECTED|發生意外錯誤|
|E_FAIL|發生錯誤|
|E_NOTIMPL|指示 MFC 本身應嘗試轉換和調度指令|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup*是非 NULL,但不指定已識別的指令群組|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID*未在群組*pguidCmdGroup*中識別為有效命令|
|OLECMDERR_DISABLED|*nCmdID*識別的指令已關閉且無法執行|
|OLECMDERR_NOHELP|呼叫者請求*nCmdID*識別的指令的説明,但沒有可用的説明|
|OLECMDERR_CANCELED|使用者取消執行|

### <a name="remarks"></a>備註

`COleCmdUI`可用於啟用、更新和設置 DocObject 使用者介面命令的其他屬性。 初始化指令後,可以使用 執行這些`OnExecOleCmd`指令 。

在嘗試轉換和調度 OLE 文件命令之前,框架調用該函數。 不需要重寫此函數來處理標準 OLE 文檔命令,但如果要處理自己的自定義命令或處理接受參數或返回結果的命令,則必須為此函數提供覆蓋。

大多數命令不採用參數或返回值。 對於大多數命令,調用方可以通過*NULL 進行pvarargIn*和*pvarargOut。* 對於預期輸入值的命令,調用方可以聲明和初始化 VARIANTARG 變數,並將指標傳遞給*pvarargIn*中的變數。 對於需要單個值的命令,參數可以直接存儲在 VARIANTARG 中並傳遞給函數。 多個參數必須使用受支援的類型之一(如`IDispatch`和 SAFEARRAY)打包到 VARIANTARG 中。

同樣,如果命令返回參數,則調用方應聲明 VARIANTARG,將其初始化到VT_EMPTY,並在*pvarargOut*中傳遞其位址。 如果命令返回單個值,則物件可以直接將該值存儲在*pvarargOut*中。 必須以某種方式打包多個輸出值,以適合 VARIANTARG 的方式。

此函數的基類實現將遍歷與命令目標關聯的OLE_COMMAND_MAP結構,並嘗試將命令調度到相應的處理程式。 基類實現僅適用於不接受參數或返回值的命令。 如果需要處理接受參數或返回值的命令,則必須重寫此函數,並自行使用*pvarargIn*和*pvarargOut*參數。

## <a name="coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a>COleServerDoc:在框架視窗啟動

當容器應用程式的幀視窗被啟動或停用時,框架將調用此功能。

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>參數

*b 啟動*<br/>
指定是啟動還是停用框架視窗。

### <a name="remarks"></a>備註

默認實現將取消幀視窗可能位於的任何説明模式。 如果要在幀視窗啟動或停用時執行特殊處理,則重寫此函數。

有關詳細資訊,請參閱文章[「啟動](../../mfc/activation-cpp.md)」。。

## <a name="coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a>COleServerDoc::在嵌入式專案上

當容器應用程式呼叫伺服器應用程式建立或編輯嵌入項時,由框架呼叫。

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>傳回值

指向表示整個文檔的項的指標;如果操作失敗,則為 NULL。

### <a name="remarks"></a>備註

沒有預設的實作。 必須重寫此函數才能返回表示整個文檔的項。 此返回值應是`COleServerItem`派生類的物件。

## <a name="coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a>COleServerDoc::重新啟動和Undo

當使用者選擇撤消對已啟動、更改並隨後停用的項所做的更改時,框架將調用此函數。

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

默認實現除了返回 FALSE 以指示失敗外,不執行任何操作。

如果應用程式支援撤銷,請覆蓋此函數。 通常,您將執行撤銷操作,然後通過調用`ActivateInPlace`來啟動該專案。 如果容器應用程式是使用 Microsoft 基礎類庫編寫的`COleClientItem::ReactivateAndUndo`,則調用會導致調用此函數。

## <a name="coleserverdoconresizeborder"></a><a name="onresizeborder"></a>COleServerDoc::在重調整邊界

當容器應用程式的框架視窗更改大小時,框架將調用此功能。

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>參數

*lprect邊框*<br/>
指向指定邊框`RECT`座標的結構`CRect`或 物件。

*lpUI 視窗*<br/>
指向擁有當前就地編輯`IOleInPlaceUIWindow`會話的類物件的指標。

*bFrame*<br/>
如果*lpUIWindow*指向容器應用程式的頂層框架視窗,則為 TRUE,如果*lpUIWindow*指向容器應用程式的文檔級框架視窗,則為 FALSE。

### <a name="remarks"></a>備註

此函數根據新的視窗大小調整和調整工具列和其他用戶介面元素。

有關詳細資訊,請參閱 Windows SDK 中的[IOleInPlaceUIWindow。](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow)

這是一個高級的可重寫。

## <a name="coleserverdoconsethostnames"></a><a name="onsethostnames"></a>COleServerDoc::打開主機名

當容器設置或更改本文檔的主機名時,由框架調用。

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>參數

*lpszHost*<br/>
指定容器應用程式名稱的字串的指標。

*lpszHostObj*<br/>
指定文件容器名稱的字串的指標。

### <a name="remarks"></a>備註

預設實現更改引用本文件的所有檢視的文件標題。

如果應用程式通過其他機制設置標題,請覆蓋此函數。

## <a name="coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a>COleServerDoc::在設定項目

框架調用此函數將就地編輯幀視窗放置在容器應用程式的幀視窗中。

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
指向`RECT`指定就地幀`CRect`視窗 相對於容器應用程式工作區的位置的結構或物件的指標。

*lpClipRect*<br/>
指向`RECT`指定相對於容器應用程式的工作`CRect`區 的就地框架視窗的裁剪矩形的結構或物件的指標。

### <a name="remarks"></a>備註

如有必要,重寫此函數以更新視圖的縮放係數。

此函數通常是為了回應`RequestPositionChange`調用而調用的,儘管容器可以隨時調用該函數,以請求對就地物料進行位置更改。

## <a name="coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleServerDoc::在顯示控制列

框架調用此函數以顯示或隱藏伺服器應用程式的控制欄,這些控制欄與*pFrameWnd*標識的框架視窗相關聯。

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>參數

*pFramewnd*<br/>
指向其控制欄應隱藏或顯示的幀視窗的指標。

*b 顯示*<br/>
確定控制條是顯示還是隱藏。

### <a name="remarks"></a>備註

默認實現枚舉該幀視窗擁有的所有控制欄,並隱藏或顯示它們。

## <a name="coleserverdoconshowdocument"></a><a name="onshowdocument"></a>COleServerDoc:在顯示文件上

當必須隱藏或`OnShowDocument`顯示伺服器文檔時,框架將調用該函數。

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
指定是顯示還是隱藏文檔的使用者介面。

### <a name="remarks"></a>備註

如果*bShow*為 TRUE,則預設實現將啟動伺服器應用程式(如有必要)並導致容器應用程式滾動其視窗,以便項可見。 如果*bShow*是 FALSE,則預設實現`OnDeactivate`透過調用 停用項,然後銷毀或隱藏為文檔創建的所有框架視窗,但第一個視窗除外。 如果沒有可見的文檔保留,則默認實現將隱藏伺服器應用程式。

## <a name="coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a>COleServerDoc:更新文件

在將作為嵌入項的文件保存在複合文檔中的文檔時,由框架調用。

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>傳回值

如果文檔已成功更新,則非零;否則 0。

### <a name="remarks"></a>備註

預設實現調用[COleServerDoc::通知已儲存](#notifysaved)和[COleServerDoc:保存嵌入](#saveembedding)成員函數,然後將文檔標記為乾淨。 如果要在更新嵌入項時執行特殊處理,則重寫此函數。

## <a name="coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a>COleServerDoc::請求位置變更

呼叫此成員函數,讓容器應用程式更改專案的位置。

```cpp
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>參數

*lpPosRect*<br/>
指向包含項`RECT`新位置的`CRect`結構 或物件的指標。

### <a name="remarks"></a>備註

當就地活動項中的數據發生更改`UpdateAllItems`時,通常調用(與) 結合。 在此調用之後,容器可能通過調用 來執行更改,也可能`OnSetItemRects`不執行更改。 結果位置可能與請求的位置不同。

## <a name="coleserverdocsaveembedding"></a><a name="saveembedding"></a>COleServerDoc::儲存嵌入

呼叫此函數以告訴容器應用程式保存嵌入的物件。

```cpp
void SaveEmbedding();
```

### <a name="remarks"></a>備註

此函式從`OnUpdateDocument`自動呼叫 。 請注意,此函數會導致在磁碟上更新專案,因此通常僅由於特定使用者操作而調用該專案。

## <a name="coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a>COleServerDoc::滾動容器By

調用`ScrollContainerBy`成員函數按 指示的數量(以像素為`sizeScroll`單位) 滾動容器文檔。

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>參數

*大小捲動*<br/>
指示容器文件滾動的遠。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

正值表示向下和向右滾動;負值表示向上和向左滾動。

## <a name="coleserverdocupdateallitems"></a><a name="updateallitems"></a>COleServerDoc:更新所有專案

呼叫此函數以通知連接到文檔的所有連結項的文檔已更改。

```cpp
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>參數

*pSender*<br/>
指標指向修改文件的項,如果要更新所有專案,則指向 NULL。

*lHint*<br/>
包含有關修改的資訊。

*pHint*<br/>
指向存儲有關修改資訊的物件的指標。

*nDrawAspect*<br/>
確定如何繪製專案。 這是 DVASPECT 枚舉中的值。 這個參數的值可以是下列其中一個：

- DVASPECT_CONTENT項的表示方式可以將其顯示為容器內的嵌入物件。

- DVASPECT_THUMBNAIL專案以「縮略圖」表示形式呈現,以便它可以顯示在流覽工具中。

- DVASPECT_ICON項由圖示表示。

- DVASPECT_DOCPRINT項表示,就好像它是使用「檔」功能表中的「列印」命令一樣。

### <a name="remarks"></a>備註

通常在使用者更改伺服器文件後調用此功能。 如果 OLE 項連結到具有自動連結的文檔,則該項將更新以反映更改。 在使用 Microsoft 基礎類庫編寫的容器應用程式中,調`COleClientItem`用的[OnChange](../../mfc/reference/coleclientitem-class.md#onchange)成員函數。

此函數調用除`OnUpdate`發送項、傳遞*pHint、lHint*和*nDrawAspect*之外的每個*lHint*文件項的成員函數。 使用這些參數將有關文檔修改的資訊傳遞給項。 您可以使用*lHint*對資訊進行編`CObject`碼, 也可以定義派生類以儲存有關修改的資訊,並使用*pHint*傳遞該類的物件。 覆蓋`COleServerItem`派`OnUpdate`生 類中的成員函數,以根據專案的表示是否已更改來優化每個專案的更新。

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc 類別](../../mfc/reference/colelinkingdoc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 類別](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc 類別](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer 類別](../../mfc/reference/coletemplateserver-class.md)
