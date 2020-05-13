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
ms.openlocfilehash: 1500035cb8be3036678090918154829aace48d2f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753869"
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
|[COle 文件:COleDocument](#coledocument)|建構 `COleDocument` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDocument::新增專案](#additem)|將項添加到文檔維護的項清單中。|
|[COle 文件::套用列印裝置](#applyprintdevice)|設置文檔中所有用戶端項的列印目標設備。|
|[COle 文件:開啟複合檔案](#enablecompoundfile)|使用 OLE 結構化儲存檔案格式儲存文件。|
|[COle 文件:抓取位置活動項目](#getinplaceactiveitem)|返回當前就地處於活動狀態的 OLE 項。|
|[COle 文件:取得下一個客戶端項目](#getnextclientitem)|獲取用於反覆運算的下一個用戶端項。|
|[COle 文件:抓取下一個項目](#getnextitem)|獲取下一個文檔項以進行反覆運算。|
|[COle 文件:取得下一個伺服器項目](#getnextserveritem)|獲取用於反覆運算的下一個伺服器項。|
|[COleDocument:取得主要選定項目](#getprimaryselecteditem)|返回文檔中主要選定的 OLE 項。|
|[COle 文件:抓取起始位置](#getstartposition)|獲取開始反覆運算的初始位置。|
|[COle 文件::有空白項目](#hasblankitems)|檢查文檔中的空白項。|
|[COle 文件::在顯示檢視](#onshowviews)|當文檔變得可見或不可見時調用。|
|[COle 文件:移除項目](#removeitem)|從文件維護的項清單中刪除項。|
|[COle 文件::更新已修改的標記](#updatemodifiedflag)|如果包含的任何 OLE 項已被修改,則將文檔標記為已修改。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COle 文件::編輯變更圖示](#oneditchangeicon)|在"更改圖示"功能表命令中處理事件。|
|[COle 文件:開啟轉換](#oneditconvert)|處理嵌入或連結物件從一種類型轉換為另一種類型。|
|[COleDocument::編輯連結](#oneditlinks)|在"編輯"選單上處理"連結"命令中的事件。|
|[COle 文件::在檔案傳送郵件](#onfilesendmail)|發送附有文件的郵件。|
|[COle 文件::更新編輯變更圖示](#onupdateeditchangeicon)|由框架呼叫以更新「編輯/更改圖示」功能表選項的命令 UI。|
|[COle 文件::更新連結選單](#onupdateeditlinksmenu)|由框架呼叫以更新「編輯/連結」功能表選項的命令 UI。|
|[COleDocument::更新物件Verbmenu](#onupdateobjectverbmenu)|由框架呼叫以更新"編輯/*物件名稱"* 選單選項的命令 UI,以及從"編輯/*物件名稱*"存取的 Verb 子選單。|
|[COle 文件::更新貼上連結選單](#onupdatepastelinkmenu)|由框架呼叫以更新「貼貼特殊」功能表選項的命令 UI。|
|[COle 文件::更新貼上選單](#onupdatepastemenu)|由框架呼叫以更新「貼貼」功能表選項的命令 UI。|

## <a name="remarks"></a>備註

`COleDocument`派生自`CDocument`,它允許 OLE 應用程式使用 Microsoft 基礎類庫提供的文檔/視圖體系結構。

`COleDocument`將文件視為處理 OLE 項的[CDocItem](../../mfc/reference/cdocitem-class.md)物件的集合。 容器和伺服器應用程式都需要這樣的體系結構,因為它們的文檔必須能夠包含OLE項。 [COleServerItem](../../mfc/reference/coleserveritem-class.md)和[COleClientItem](../../mfc/reference/coleclientitem-class.md)類`CDocItem`都派生 自 ,管理應用程式和 OLE 項之間的交互。

如果要編寫一個簡單的容器應用程式,請從`COleDocument`派生文檔類。 如果要編寫一個容器應用程式,該應用程式支援連結到其文檔中包含的嵌入項,請從[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)派生您的文檔類。 如果要編寫伺服器應用程式或組合容器/伺服器,請從[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)派生文檔類。 `COleLinkingDoc``COleServerDoc`派生`COleDocument`自 ,因此這些類`COleDocument``CDocument`繼承 和 中提供的所有服務。

要使用`COleDocument`派生類,並添加用於管理應用程式的非 OLE 資料以及嵌入或連結項的功能。 如果定義`CDocItem`派生類以儲存應用程式的本機數據,則可以使用`COleDocument`定義的 預設實現來存儲 OLE 和非 OLE 資料。 您還可以設計自己的資料結構,以便將非 OLE 數據與 OLE 項分開儲存。 有關詳細資訊,請參閱文章[容器:複合檔](../../mfc/containers-compound-files.md).

`CDocument`支援通過郵件支援 (MAPI) 傳送文件。 `COleDocument`已更新[OnFileSendMail](#onfilesendmail)以正確處理複合文檔。 有關詳細資訊,請參閱 MFC 中的[MAPI](../../mfc/mapi.md)與[MAPI 支援](../../mfc/mapi-support-in-mfc.md)文章 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`COleDocument`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coledocumentadditem"></a><a name="additem"></a>COleDocument::新增專案

呼叫此函數以向文件添加項。

```
virtual void AddItem(CDocItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要添加的文檔項的指標。

### <a name="remarks"></a>備註

當 接受指向文檔的指標`COleClientItem`的`COleServerItem`或建構函數調用此函數時,不需要顯式調用它。

## <a name="coledocumentapplyprintdevice"></a><a name="applyprintdevice"></a>COle 文件::套用列印裝置

呼叫此函數可更改應用程式容器文件中所有嵌入式[COleClientItem 專案的](../../mfc/reference/coleclientitem-class.md)列印目標設備。

```
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```

### <a name="parameters"></a>參數

*ptd*<br/>
指向數據結構`DVTARGETDEVICE`的指標,其中包含有關新列印目標設備的資訊。 可以是 NULL。

*Ppd*<br/>
指向數據結構`PRINTDLG`的指標,其中包含有關新列印目標設備的資訊。 可以是 NULL。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0。

### <a name="remarks"></a>備註

此函數更新所有專案的列印目標設備,但不會刷新這些專案的演示文稿緩存。 要更新專案的簡報簡報快取,請致電[COleClientItem::更新連結](../../mfc/reference/coleclientitem-class.md#updatelink)。

此函數的參數包含 OLE 用於標識目標設備的資訊。 [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)結構包含 Windows 用於初始化公共列印對話框的資訊。 使用者關閉對話方塊後,Windows 將返回有關使用者在此結構中選擇的資訊。 `m_pd` [CPrintDialog](../../mfc/reference/cprintdialog-class.md)物件的成員是一`PRINTDLG`個結構。

有關詳細資訊,請參閱 Windows SDK 中的[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)結構。

有關詳細資訊,請參閱 Windows SDK 中的[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)結構。

## <a name="coledocumentcoledocument"></a><a name="coledocument"></a>COle 文件:COleDocument

建構 `COleDocument` 物件。

```
COleDocument();
```

## <a name="coledocumentenablecompoundfile"></a><a name="enablecompoundfile"></a>COle 文件:開啟複合檔案

如果要使用複合檔案格式儲存文件,請呼叫此函數。

```cpp
void EnableCompoundFile(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
指定是啟用還是禁用複合檔案支援。

### <a name="remarks"></a>備註

這也稱為結構化存儲。 通常從`COleDocument`派生類的構造函數調用此函數。 有關複合文件的詳細資訊,請參閱文章[「容器:複合檔](../../mfc/containers-compound-files.md)」。

如果不呼叫此成員函數,文件將以非結構化("平面")檔案格式儲存。

為文件啟用或禁用複合文件支援後,不應在文檔的生存期內更改設置。

## <a name="coledocumentgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>COle 文件:抓取位置活動項目

調用此函數,獲取當前在包含*pWnd*標識的檢視的幀視窗中當前啟動的 OLE 項。

```
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向顯示容器文件的視窗的指標。

### <a name="return-value"></a>傳回值

指向單個、就地活動 OLE 項的指標;如果當前沒有 OLE 項處於"就地活動"狀態,則為 NULL。

## <a name="coledocumentgetnextclientitem"></a><a name="getnextclientitem"></a>COle 文件:取得下一個客戶端項目

重複呼叫此函數以造訪文件中的每個用戶端項。

```
COleClientItem* GetNextClientItem(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
對由上一個調用 為設置的`GetNextClientItem`定位 值的引用。成員函數返回`GetStartPosition`初始值。

### <a name="return-value"></a>傳回值

指向文檔中下一個用戶端項的指標,如果沒有更多的用戶端項,則指向 NULL。

### <a name="remarks"></a>備註

每次調用後,為文檔中的下一個項設置*pos*值,該項可能是用戶端項,也可能不是用戶端項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]

## <a name="coledocumentgetnextitem"></a><a name="getnextitem"></a>COle 文件:抓取下一個項目

重複調用此函數以訪問文檔中的每個專案。

```
virtual CDocItem* GetNextItem(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
對由上一個調用 為設置的`GetNextItem`定位 值的引用。成員函數返回`GetStartPosition`初始值。

### <a name="return-value"></a>傳回值

指向指定位置的文檔項的指標。

### <a name="remarks"></a>備註

每次呼叫後 *,pos*值將設定為文件中下一項的「位置」 值。 如果檢索到的元素是文檔中的最後一個元素,則*pos*的新值為NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]

## <a name="coledocumentgetnextserveritem"></a><a name="getnextserveritem"></a>COle 文件:取得下一個伺服器項目

重複呼叫此函數以造訪文件中的每個伺服器項。

```
COleServerItem* GetNextServerItem(POSITION& pos) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
對由上一個調用 為設置的`GetNextServerItem`定位 值的引用。成員函數返回`GetStartPosition`初始值。

### <a name="return-value"></a>傳回值

指向文檔中下一個伺服器項的指標,如果沒有更多的伺服器項,則指向 NULL。

### <a name="remarks"></a>備註

每次調用後,為文檔中的下一個項設置*pos*值,該項可能是伺服器項,也可能不是伺服器項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]

## <a name="coledocumentgetprimaryselecteditem"></a><a name="getprimaryselecteditem"></a>COleDocument:取得主要選定項目

由框架調用以檢索指定檢視中當前選定的 OLE 項。

```
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```

### <a name="parameters"></a>參數

*pView*<br/>
指向顯示文件的活動視圖物件的指標。

### <a name="return-value"></a>傳回值

指向單個所選 OLE 項的指標;如果未選擇 OLE 項或選擇多個 OLE 項,則為 NULL。

### <a name="remarks"></a>備註

預設實現搜索單個選定項包含的 OLE 項的清單,並返回指向它的指標。 如果沒有選擇任何項,或者有多個項目被選中,則函數將返回 NULL。 您必須重寫檢視類`CView::IsSelected`中的成員函數,才能工作。 如果您有自己的方法來存儲包含的 OLE 項,請重寫此函數。

## <a name="coledocumentgetstartposition"></a><a name="getstartposition"></a>COle 文件:抓取起始位置

呼叫此函數以獲取文檔中第一個專案的位置。

```
virtual POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

可用於開始遍曆文檔項的「位置」值;如果文件沒有項目,則為 NULL。

### <a name="remarks"></a>備註

將傳回的值傳`GetNextItem`送`GetNextClientItem`或`GetNextServerItem`。

## <a name="coledocumenthasblankitems"></a><a name="hasblankitems"></a>COle 文件::有空白項目

呼叫此函數以確定文件是否包含任何空白項。

```
BOOL HasBlankItems() const;
```

### <a name="return-value"></a>傳回值

如果文檔包含任何空白項,則非零;否則 0。

### <a name="remarks"></a>備註

空白項是其矩形為空的專案。

## <a name="coledocumentoneditchangeicon"></a><a name="oneditchangeicon"></a>COle 文件::編輯變更圖示

顯示 OLE 更改圖示對話方塊,並將表示當前選擇的 OLE 項的圖示更改為使用者在對話方塊中選擇的圖示。

```
afx_msg void OnEditChangeIcon();
```

### <a name="remarks"></a>備註

`OnEditChangeIcon`建立並啟動`COleChangeIconDialog`「更改圖示」對話框。

## <a name="coledocumentoneditconvert"></a><a name="oneditconvert"></a>COle 文件:開啟轉換

顯示 OLE 轉換對話方塊,並根據對話方塊中的使用者選擇轉換或啟動當前選取的 OLE 專案。

```
afx_msg void OnEditConvert();
```

### <a name="remarks"></a>備註

`OnEditConvert`建立並啟動`COleConvertDialog`『轉換』對話方塊。

轉換的一個範例是將Microsoft Word文檔轉換為WordPad文檔。

## <a name="coledocumentoneditlinks"></a><a name="oneditlinks"></a>COleDocument::編輯連結

顯示"OLE 編輯/連結"對話框。

```
afx_msg void OnEditLinks();
```

### <a name="remarks"></a>備註

`OnEditLinks`建立並啟動連結`COleLinksDialog`「對話框,該對話框允許使用者更改連結的物件。

## <a name="coledocumentonfilesendmail"></a><a name="onfilesendmail"></a>COle 文件::在檔案傳送郵件

通過駐留郵件主機(如果有)發送郵件,並將文檔作為附件。

```
afx_msg void OnFileSendMail();
```

### <a name="remarks"></a>備註

`OnFileSendMail`呼叫`OnSaveDocument`序列化(保存)無標題和修改的文件到暫存檔,然後透過電子郵件發送。 如果文檔尚未修改,則不需要臨時檔;因此,不需要臨時檔。原始檔已發送。 `OnFileSendMail`載入 MAPI32。尚未載入 DLL。

與`OnFileSendMail`的`CDocument`實現不同,此函數正確處理復合檔。

有關詳細資訊,請參閱 MFC 文章中的[MAPI 主題](../../mfc/mapi.md)與[MAPI 支援](../../mfc/mapi-support-in-mfc.md)。

## <a name="coledocumentonshowviews"></a><a name="onshowviews"></a>COle 文件::在顯示檢視

在文件的可見性狀態更改後,框架調用此函數。

```
virtual void OnShowViews(BOOL bVisible);
```

### <a name="parameters"></a>參數

*b 可見*<br/>
指示文檔是可見的還是不可見的。

### <a name="remarks"></a>備註

此函數的預設版本不執行任何操作。 如果應用程式必須在文檔的可見性更改時執行任何特殊處理,請覆蓋它。

## <a name="coledocumentonupdateeditchangeicon"></a><a name="onupdateeditchangeicon"></a>COle 文件::更新編輯變更圖示

由框架呼叫以更新"編輯"選單上的"更改圖示"命令。

```
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的功能表的結構的指標。 更新處理程式透過`Enable`*pCmdUI*`CCmdUI`呼叫結構的成員函數以更新用戶介面。

### <a name="remarks"></a>備註

`OnUpdateEditChangeIcon`更新命令的用戶介面,具體取決於文檔中是否存在有效的圖示。 重寫此函數以更改行為。

## <a name="coledocumentonupdateeditlinksmenu"></a><a name="onupdateeditlinksmenu"></a>COle 文件::更新連結選單

由框架呼叫以更新"編輯"選單上的"連結"命令。

```
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的功能表的結構的指標。 更新處理程式透過`Enable`*pCmdUI*`CCmdUI`呼叫結構的成員函數以更新用戶介面。

### <a name="remarks"></a>備註

從文檔中的第一個 OLE`OnUpdateEditLinksMenu`項開始 ,訪問每個項,測試該項是否為連結,如果是連結,則啟用 Links 命令。 重寫此函數以更改行為。

## <a name="coledocumentonupdateobjectverbmenu"></a><a name="onupdateobjectverbmenu"></a>COleDocument::更新物件Verbmenu

由框架呼叫以更新「編輯」選單上*的 ObjectName*命令,以及從*ObjectName*命令存取的 Verb 子選單,其中*ObjectName*是嵌入在文件中的 OLE 物件的名稱。

```
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的功能表的結構的指標。 更新處理程式透過`Enable`*pCmdUI*`CCmdUI`呼叫結構的成員函數以更新用戶介面。

### <a name="remarks"></a>備註

`OnUpdateObjectVerbMenu`更新*ObjectName*命令的使用者介面,具體取決於文檔中是否存在有效物件。 如果存在物件,則啟用"編輯"功能表上的*物件名稱*命令。 選擇此功能表命令時,將顯示「動詞子功能表」。 "動詞"子功能表包含可用於物件的所有謂詞命令,如"編輯"、"屬性"等。 重寫此函數以更改行為。

## <a name="coledocumentonupdatepastelinkmenu"></a><a name="onupdatepastelinkmenu"></a>COle 文件::更新貼上連結選單

由框架呼叫以確定是否可以從剪貼簿貼貼連結的 OLE 項。

```
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的功能表的結構的指標。 更新處理程式透過`Enable`*pCmdUI*`CCmdUI`呼叫結構的成員函數以更新用戶介面。

### <a name="remarks"></a>備註

根據專案是否可以貼上到文件中,啟用或禁用「貼貼特殊」選單命令。

## <a name="coledocumentonupdatepastemenu"></a><a name="onupdatepastemenu"></a>COle 文件::更新貼上選單

由框架呼叫以確定是否可以從剪貼簿貼貼嵌入的 OLE 項。

```
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向表示生成更新`CCmdUI`命令的功能表的結構的指標。 更新處理程式透過`Enable`*pCmdUI*`CCmdUI`呼叫結構的成員函數以更新用戶介面。

### <a name="remarks"></a>備註

"粘貼"功能表命令和按鈕已啟用或禁用,具體取決於專案是否可以粘貼到文檔中。

## <a name="coledocumentremoveitem"></a><a name="removeitem"></a>COle 文件:移除項目

呼叫此函數從文件中刪除專案。

```
virtual void RemoveItem(CDocItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要刪除的文檔項的指標。

### <a name="remarks"></a>備註

您通常不需要顯式調用此函數;因此,您不需要顯式調用此函數。它由`COleClientItem`和`COleServerItem`的析構函數調用。

## <a name="coledocumentupdatemodifiedflag"></a><a name="updatemodifiedflag"></a>COle 文件::更新已修改的標記

如果包含的任何 OLE 項已被修改,請呼叫此函數將文件標記為已修改。

```
virtual void UpdateModifiedFlag();
```

### <a name="remarks"></a>備註

這允許框架提示使用者在關閉之前保存文檔,即使文檔中的本機數據尚未修改也是如此。

## <a name="see-also"></a>另請參閱

[MFC 樣品容器](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
