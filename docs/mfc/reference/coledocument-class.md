---
title: COleDocument 類別
ms.date: 11/04/2016
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
helpviewer_keywords:
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
ms.openlocfilehash: b92c796fdaa972966dcbfa85b1e34f267b6c629c
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741602"
---
# <a name="coledocument-class"></a>COleDocument 類別

支援視覺化編輯之 OLE 文件的基底類別。

## <a name="syntax"></a>語法

```
class COleDocument : public CDocument
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDocument::COleDocument](#coledocument)|建構 `COleDocument` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDocument::AddItem](#additem)|將專案加入至檔所維護的專案清單。|
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|為檔中的所有用戶端專案設定列印目標裝置。|
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|會使用 OLE 結構化儲存體檔案格式來儲存檔。|
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|傳回目前就地作用中的 OLE 專案。|
|[COleDocument::GetNextClientItem](#getnextclientitem)|取得用於反覆運算的下一個用戶端專案。|
|[COleDocument::GetNextItem](#getnextitem)|取得要逐一查看的下一個檔專案。|
|[COleDocument::GetNextServerItem](#getnextserveritem)|取得用於反覆運算的下一個伺服器專案。|
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|傳回檔中主要選取的 OLE 專案。|
|[COleDocument::GetStartPosition](#getstartposition)|取得開始反復專案的初始位置。|
|[COleDocument::HasBlankItems](#hasblankitems)|檢查檔中的空白專案。|
|[COleDocument::OnShowViews](#onshowviews)|當檔變成可見或不可見時呼叫。|
|[COleDocument::RemoveItem](#removeitem)|從檔所維護的專案清單中移除專案。|
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|如果已修改任何包含的 OLE 專案，則將檔標記為已修改。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|處理變更圖示功能表命令中的事件。|
|[COleDocument::OnEditConvert](#oneditconvert)|處理從一個類型轉換成另一個類型的內嵌或連結化物件。|
|[COleDocument::OnEditLinks](#oneditlinks)|處理 [編輯] 功能表上 [連結] 命令中的事件。|
|[COleDocument::OnFileSendMail](#onfilesendmail)|傳送附有附加檔的郵件訊息。|
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|由架構呼叫，以更新 [編輯]/[變更] 圖示功能表選項的命令 UI。|
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|由架構呼叫，以更新 [編輯/連結] 功能表選項的命令 UI。|
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|由架構呼叫，以更新編輯/ *objectname*功能表選項的命令 UI，以及從編輯/ *Objectname*存取的動詞子功能表。|
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|由架構呼叫，以更新 [貼上特殊功能表] 選項的命令 UI。|
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|由架構呼叫，以更新 [貼上] 功能表選項的命令 UI。|

## <a name="remarks"></a>備註

`COleDocument`衍生自`CDocument`，可讓您的 OLE 應用程式使用 MFC 程式庫所提供的檔/視圖架構。

`COleDocument`將檔視為[CDocItem](../../mfc/reference/cdocitem-class.md)物件的集合，以處理 OLE 專案。 容器和伺服器應用程式都需要這類架構，因為其檔必須能夠包含 OLE 專案。 [COleServerItem](../../mfc/reference/coleserveritem-class.md)和[COleClientItem](../../mfc/reference/coleclientitem-class.md)類別（兩者都是衍生`CDocItem`自）會管理應用程式與 OLE 專案之間的互動。

如果您要撰寫簡單的容器應用程式，請從`COleDocument`衍生您的檔類別。 如果您要撰寫的容器應用程式支援連結至其檔所包含的內嵌專案，請從[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)衍生您的檔類別。 如果您要撰寫伺服器應用程式或組合容器/伺服器，請從[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)衍生您的檔類別。 `COleLinkingDoc`和`COleServerDoc`衍生自`COleDocument`，因此這些類別會繼承和`CDocument`中`COleDocument`可用的所有服務。

若要`COleDocument`使用，請從它衍生類別並新增功能，以管理應用程式的非 OLE 資料，以及內嵌或連結的專案。 如果您定義`CDocItem`衍生的類別來儲存應用程式的原生資料，則可以使用所`COleDocument`定義的預設實值來儲存您的 ole 和非 ole 資料。 您也可以設計自己的資料結構，以便與 OLE 專案分開儲存非 OLE 資料。 如需詳細資訊，請參閱[容器：複合檔案](../../mfc/containers-compound-files.md)。

`CDocument`支援透過 mail 傳送您的檔（若有郵件支援（MAPI））。 `COleDocument`已更新[OnFileSendMail](#onfilesendmail)來正確處理複合檔案。 如需詳細資訊，請參閱 MFC 中的[mapi](../../mfc/mapi.md)和[mapi 支援](../../mfc/mapi-support-in-mfc.md)文章。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>需求

**標頭：** afxole。h

##  <a name="additem"></a>COleDocument：： AddItem

呼叫此函式可將專案新增至檔。

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
要加入之檔專案的指標。

### <a name="remarks"></a>備註

您不需要明確地呼叫此函式，方法是由`COleClientItem`接受檔指標的或`COleServerItem`函式呼叫。

##  <a name="applyprintdevice"></a>COleDocument：： ApplyPrintDevice

呼叫此函式可針對應用程式容器檔案中所有內嵌的[COleClientItem](../../mfc/reference/coleclientitem-class.md)專案變更列印目標裝置。

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>參數

*ptd*<br/>
`DVTARGETDEVICE`資料結構的指標，其中包含新列印目標裝置的相關資訊。 可以是 Null。

*ppd*<br/>
`PRINTDLG`資料結構的指標，其中包含新列印目標裝置的相關資訊。 可以是 Null。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0。

### <a name="remarks"></a>備註

此函式會更新所有專案的列印目標裝置，但不會重新整理這些專案的呈現快取。 若要更新專案的呈現快取，請呼叫[COleClientItem：： UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)。

此函式的引數包含 OLE 用來識別目標裝置的資訊。 [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)結構包含 Windows 用來初始化一般 [列印] 對話方塊的資訊。 在使用者關閉對話方塊之後，Windows 會傳回此結構中使用者選取專案的相關資訊。 [CPrintDialog 物件](../../mfc/reference/cprintdialog-class.md)的`PRINTDLG`成員是一個結構。 `m_pd`

如需詳細資訊，請參閱 Windows SDK 中的[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)結構。

如需詳細資訊，請參閱 Windows SDK 中的[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)結構。

##  <a name="coledocument"></a>COleDocument：： COleDocument

建構 `COleDocument` 物件。

```
COleDocument();
```

##  <a name="enablecompoundfile"></a>COleDocument：： EnableCompoundFile

如果您想要使用複合檔案格式來儲存檔，請呼叫此函式。

```
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定複合檔案支援是否已啟用或停用。

### <a name="remarks"></a>備註

這也稱為結構化儲存體。 您通常會從衍生類別的`COleDocument`函式中呼叫此函數。 如需複合檔案的詳細資訊，請參閱[容器：複合檔案](../../mfc/containers-compound-files.md)。

如果您未呼叫此成員函式，檔將會以非結構化（「一般」）檔案格式儲存。

啟用或停用檔的複合檔案支援之後，此設定不應在檔的存留期間變更。

##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem

呼叫此函式，以在包含*pWnd*所識別之視圖的框架視窗中，取得目前已啟用的 OLE 專案。

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
顯示容器檔案之視窗的指標。

### <a name="return-value"></a>傳回值

指向單一位置的現用 OLE 專案的指標;如果目前沒有任何 OLE 專案處於「就地作用中」狀態，則為 Null。

##  <a name="getnextclientitem"></a>COleDocument：： GetNextClientItem

重複呼叫此函式，以存取檔中的每個用戶端專案。

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*採購*<br/>
先前呼叫`GetNextClientItem`所設定之位置值的參考; 此初始值是`GetStartPosition`由成員函式傳回。

### <a name="return-value"></a>傳回值

檔中下一個用戶端專案的指標，如果沒有其他用戶端專案，則為 Null。

### <a name="remarks"></a>備註

在每次呼叫之後，會針對檔中的下一個專案設定*pos*的值，這可能是或可能不是用戶端專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

##  <a name="getnextitem"></a>COleDocument：： GetNextItem

重複呼叫此函式，以存取檔中的每個專案。

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*採購*<br/>
先前呼叫`GetNextItem`所設定之位置值的參考; 此初始值是`GetStartPosition`由成員函式傳回。

### <a name="return-value"></a>傳回值

位於指定位置之檔專案的指標。

### <a name="remarks"></a>備註

在每次呼叫之後， *pos*的值會設定為檔中下一個專案的位置值。 如果所抓取的元素是檔中的最後一個元素，則*pos*的新值會是 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

##  <a name="getnextserveritem"></a>COleDocument：： GetNextServerItem

重複呼叫此函式，以存取檔中的每個伺服器專案。

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*採購*<br/>
先前呼叫`GetNextServerItem`所設定之位置值的參考; 此初始值是`GetStartPosition`由成員函式傳回。

### <a name="return-value"></a>傳回值

檔中下一個伺服器專案的指標，如果沒有其他伺服器專案，則為 Null。

### <a name="remarks"></a>備註

在每次呼叫之後，會針對檔中的下一個專案設定*pos*的值，這可能是或可能不是伺服器專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

##  <a name="getprimaryselecteditem"></a>COleDocument：： GetPrimarySelectedItem

由架構呼叫，以在指定的視圖中取出目前選取的 OLE 專案。

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>參數

*pView*<br/>
顯示檔之現用 view 物件的指標。

### <a name="return-value"></a>傳回值

單一選取之 OLE 專案的指標;如果未選取任何 OLE 專案，或選取了多個，則為 Null。

### <a name="remarks"></a>備註

預設的實值會在包含的 OLE 專案清單中搜尋單一選取的專案，並傳回它的指標。 如果未選取任何專案，或如果選取了多個專案，此函數會傳回 Null。 您必須覆寫`CView::IsSelected` view 類別中的成員函式，此函式才能正常運作。 如果您有自己儲存包含的 OLE 專案的方法，請覆寫此函式。

##  <a name="getstartposition"></a>COleDocument：： GetStartPosition

呼叫此函式可取得檔中第一個專案的位置。

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

可用於開始逐一查看檔專案的位置值;如果檔沒有任何專案，則為 Null。

### <a name="remarks"></a>備註

將傳回的值傳遞`GetNextItem`給`GetNextClientItem`、或`GetNextServerItem`。

##  <a name="hasblankitems"></a>COleDocument：： HasBlankItems

呼叫此函式，以判斷檔是否包含任何空白專案。

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>傳回值

如果檔包含任何空白專案，則為非零值;否則為0。

### <a name="remarks"></a>備註

空白專案是其矩形是空的。

##  <a name="oneditchangeicon"></a>COleDocument：： OnEditChangeIcon

顯示 [OLE 變更圖示] 對話方塊，並將代表目前選取之 OLE 專案的圖示，變更為使用者在對話方塊中選取的圖示。

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>備註

`OnEditChangeIcon`建立並啟動`COleChangeIconDialog` [變更圖示] 對話方塊。

##  <a name="oneditconvert"></a>COleDocument：： OnEditConvert

顯示 [OLE 轉換] 對話方塊，並根據對話方塊中的使用者選項，轉換或啟用目前選取的 OLE 專案。

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>備註

`OnEditConvert`建立並啟動`COleConvertDialog` [轉換] 對話方塊。

轉換的範例是將 Microsoft Word 檔轉換成 WordPad 檔。

##  <a name="oneditlinks"></a>COleDocument：： OnEditLinks

顯示 [OLE 編輯/連結] 對話方塊。

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>備註

`OnEditLinks`建立並啟動`COleLinksDialog` [連結] 對話方塊，讓使用者可以變更連結的物件。

##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail

透過常駐郵件主機（如果有的話）以附加檔的方式傳送訊息。

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>備註

`OnFileSendMail`呼叫`OnSaveDocument`以將未命名和修改的檔序列化（儲存）到暫存檔，然後透過電子郵件傳送。 如果檔尚未修改，則不需要暫存檔案;會傳送原始的。 `OnFileSendMail`載入 MAPI32.DLL。DLL （如果尚未載入的話）。

不同`OnFileSendMail` 于`CDocument`的執行，此函式會正確處理複合檔案。

如需詳細資訊，請參閱 MFC 文章中的[Mapi 主題](../../mfc/mapi.md)和[mapi 支援](../../mfc/mapi-support-in-mfc.md)。

##  <a name="onshowviews"></a>COleDocument：： OnShowViews

架構會在檔的可見度狀態變更後呼叫此函式。

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>參數

*bVisible*<br/>
指出檔是否已成為可見或不可見。

### <a name="remarks"></a>備註

此函式的預設版本不會執行任何工作。 如果您的應用程式必須在檔的可見度變更時執行任何特殊處理，請覆寫它。

##  <a name="onupdateeditchangeicon"></a>COleDocument：： OnUpdateEditChangeIcon

由架構呼叫，以更新 [編輯] 功能表上的 [變更圖示] 命令。

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
`CCmdUI`結構的指標，表示產生 update 命令的功能表。 更新處理常式會透過`Enable` *pCmdUI*呼叫`CCmdUI`結構的成員函式，以更新使用者介面。

### <a name="remarks"></a>備註

`OnUpdateEditChangeIcon`根據檔中是否有有效的圖示，更新命令的使用者介面。 覆寫此函式以變更行為。

##  <a name="onupdateeditlinksmenu"></a>COleDocument：： OnUpdateEditLinksMenu

由架構呼叫以更新 [編輯] 功能表上的 [連結] 命令。

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
`CCmdUI`結構的指標，表示產生 update 命令的功能表。 更新處理常式會透過`Enable` *pCmdUI*呼叫`CCmdUI`結構的成員函式，以更新使用者介面。

### <a name="remarks"></a>備註

從檔中的第一個 OLE 專案開始， `OnUpdateEditLinksMenu`會存取每個專案、測試專案是否為連結，如果它是連結，則會啟用 Links 命令。 覆寫此函式以變更行為。

##  <a name="onupdateobjectverbmenu"></a>COleDocument：： OnUpdateObjectVerbMenu

由架構呼叫以更新 [編輯] 功能表上的 [ *objectname* ] 命令，以及從*ObjectName*命令存取的 [動詞] 子功能表，其中*objectname*是內嵌在檔中的 OLE 物件的名稱。

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
`CCmdUI`結構的指標，表示產生 update 命令的功能表。 更新處理常式會透過`Enable` *pCmdUI*呼叫`CCmdUI`結構的成員函式，以更新使用者介面。

### <a name="remarks"></a>備註

`OnUpdateObjectVerbMenu`根據檔中是否有有效的物件，更新*ObjectName*命令的使用者介面。 如果物件存在，則會啟用 [編輯] 功能表上的 [ *ObjectName* ] 命令。 選取此功能表命令時，會顯示 [動詞] 子功能表。 [動詞] 子功能表包含物件可用的所有動詞命令，例如 [編輯]、[屬性] 等等。 覆寫此函式以變更行為。

##  <a name="onupdatepastelinkmenu"></a>COleDocument：： OnUpdatePasteLinkMenu

由架構呼叫，以判斷是否可以從剪貼簿貼入連結的 OLE 專案。

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
`CCmdUI`結構的指標，表示產生 update 命令的功能表。 更新處理常式會透過`Enable` *pCmdUI*呼叫`CCmdUI`結構的成員函式，以更新使用者介面。

### <a name="remarks"></a>備註

[貼入特殊功能表] 命令會根據專案是否可以貼入檔而啟用或停用。

##  <a name="onupdatepastemenu"></a>COleDocument：： OnUpdatePasteMenu

由架構呼叫，以判斷是否可以從剪貼簿貼上內嵌的 OLE 專案。

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
`CCmdUI`結構的指標，表示產生 update 命令的功能表。 更新處理常式會透過`Enable` *pCmdUI*呼叫`CCmdUI`結構的成員函式，以更新使用者介面。

### <a name="remarks"></a>備註

[貼上] 功能表命令和按鈕已啟用或停用，視專案是否可以貼入檔而定。

##  <a name="removeitem"></a>COleDocument：： RemoveItem

呼叫此函式可從檔中移除專案。

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
要移除之檔專案的指標。

### <a name="remarks"></a>備註

您通常不需要明確呼叫此函式;它是由`COleClientItem`和`COleServerItem`的析構函數所呼叫。

##  <a name="updatemodifiedflag"></a>COleDocument：： UpdateModifiedFlag

呼叫此函式可在已修改任何包含的 OLE 專案時，將檔標記為已修改。

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>備註

這可讓架構在關閉之前提示使用者儲存檔，即使檔中的原生資料尚未修改也一樣。

## <a name="see-also"></a>另請參閱

[MFC 範例容器](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
