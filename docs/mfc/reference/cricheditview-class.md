---
title: CRichEditView 類別
ms.date: 11/04/2016
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
ms.openlocfilehash: 9cedcfbfb662d7d4d635a02b82ea45828c54b958
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259512"
---
# <a name="cricheditview-class"></a>CRichEditView 類別

具有[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)並[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供 rich edit 控制項的 MFC 的文件檢視架構內容中的功能。

## <a name="syntax"></a>語法

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|建構 `CRichEditView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|移動的對話方塊，使它不會擋在目前選取範圍。|
|[CRichEditView::CanPaste](#canpaste)|告知剪貼簿是否包含可以貼入 rich edit 檢視表的資料。|
|[CRichEditView::DoPaste](#dopaste)|將 OLE 項目貼到此 rich edit 檢視表中。|
|[CRichEditView::FindText](#findtext)|尋找指定的文字，叫用將等待游標。|
|[CRichEditView::FindTextSimple](#findtextsimple)|尋找指定的文字。|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|擷取的字元格式化目前選取範圍的屬性。|
|[CRichEditView::GetDocument](#getdocument)|擷取相關的指標[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)。|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|擷取目前就地啟用作用中豐富的編輯檢視中的 OLE 項目。|
|[CRichEditView::GetMargins](#getmargins)|擷取此 rich edit 檢視表的邊界。|
|[CRichEditView::GetPageRect](#getpagerect)|擷取此 rich edit 檢視表的頁框。|
|[CRichEditView::GetPaperSize](#getpapersize)|擷取此 rich edit 檢視表的紙張大小。|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|擷取段落格式化目前選取範圍的屬性。|
|[CRichEditView::GetPrintRect](#getprintrect)|擷取此 rich edit 檢視表的列印矩形。|
|[CRichEditView::GetPrintWidth](#getprintwidth)|擷取此 rich edit 檢視表的列印寬度。|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|擷取的 rich edit 控制項。|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Rich edit 檢視表中擷取選取的項目。|
|[CRichEditView::GetTextLength](#gettextlength)|擷取 rich edit 檢視表中的文字的長度。|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|擷取字元或在 rich edit 檢視表中的位元組的數目。 方法來決定長度的展開旗標清單。|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|插入檔案做為 OLE 項目。|
|[CRichEditView::InsertItem](#insertitem)|插入新項目做為 OLE 項目。|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|告知剪貼簿是否包含在 rich edit 或文字格式的資料。|
|[CRichEditView::OnCharEffect](#onchareffect)|切換目前選取範圍格式的字元。|
|[CRichEditView::OnParaAlign](#onparaalign)|變更段落對齊的方式。|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|更新命令 UI 字元 public 成員函式。|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|更新命令 UI 段落公用成員函式。|
|[CRichEditView::PrintInsideRect](#printinsiderect)|格式化給定矩形內指定的文字。|
|[CRichEditView::PrintPage](#printpage)|格式化指定的文字內指定的頁面。|
|[CRichEditView::SetCharFormat](#setcharformat)|設定字元，格式化目前選取範圍的屬性。|
|[CRichEditView::SetMargins](#setmargins)|設定此豐富的邊界編輯檢視。|
|[CRichEditView::SetPaperSize](#setpapersize)|設定此 rich edit 檢視表的紙張大小。|
|[CRichEditView::SetParaFormat](#setparaformat)|設定的段落格式化目前選取範圍的屬性。|
|[CRichEditView::TextNotFound](#textnotfound)|重設內部搜尋控制項的狀態。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|擷取此 rich edit 檢視中某個範圍的剪貼簿物件。|
|[CRichEditView::GetContextMenu](#getcontextmenu)|擷取操作功能表，使用滑鼠右鍵下。|
|[CRichEditView::IsSelected](#isselected)|表示與否，是否已選取指定的 OLE 項目。|
|[CRichEditView::OnFindNext](#onfindnext)|尋找子字串的下一個項目。|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|重新整理檢視時第一次附加至文件。|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|從 OLE 項目擷取原生的資料。|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|將列印特性設定指定的裝置。|
|[CRichEditView::OnReplaceAll](#onreplaceall)|新字串取代所有出現的指定字串。|
|[CRichEditView::OnReplaceSel](#onreplacesel)|取代目前的選取範圍。|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|找不到要求的文字的控制代碼使用者通知。|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|若要查看有關之資料的查詢`IDataObject`。|
|[CRichEditView::WrapChanged](#wrapchanged)|針對此豐富編輯的值為基礎的檢視會調整的目標輸出裝置`m_nWordWrap`。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|表示項目符號清單的縮排的量。|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|表示文字換行條件約束。|

## <a name="remarks"></a>備註

「 Rich edit 控制項 」 是一個視窗，讓使用者輸入及編輯文字。 文字字元和段落格式，可指派，而且可以包含內嵌的 OLE 物件。 Rich edit 控制項的格式化文字，提供程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。

`CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc` 會維護檢視中的 OLE 用戶端項目清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。

這個 Windows 通用控制項 (因而[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類別) 僅適用於 Windows 95/98 和 Windows NT 的版本 3.51 下執行的程式和更新版本。

在 MFC 應用程式中使用 rich edit 檢視表的範例，請參閱[WORDPAD](../../visual-cpp-samples.md)範例應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>需求

**標頭：** afxrich.h

##  <a name="adjustdialogposition"></a>  CRichEditView::AdjustDialogPosition

呼叫此函式來移動指定的對話方塊，讓它不會不會遮住目前的選取範圍。

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>參數

*pDlg*<br/>
指向 `CDialog` 物件的指標。

##  <a name="canpaste"></a>  CRichEditView::CanPaste

呼叫此函式來判斷 [剪貼簿] 是否包含可以貼到此 rich edit 檢視表的資訊。

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>傳回值

如果剪貼簿包含可接受此 rich edit 檢視; 格式的資料，非零值。否則就是 0。

##  <a name="cricheditview"></a>  CRichEditView::CRichEditView

呼叫此函式可建立`CRichEditView`物件。

```
CRichEditView();
```

##  <a name="dopaste"></a>  CRichEditView::DoPaste

呼叫此函式可貼上中的 OLE 項目*dataobj*到這個豐富的編輯文件/檢視。

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>參數

*dataobj*<br/>
[COleDataObject](../../mfc/reference/coledataobject-class.md)包含貼上資料。

*cf*<br/>
所需的剪貼簿格式。

*hMetaPict*<br/>
表示要貼上項目之中繼檔。

### <a name="remarks"></a>備註

架構會呼叫此函式的預設實作的一部分[QueryAcceptData](#queryacceptdata)。

此函式會判斷結果為基礎的處理常式的選擇性貼上的貼上的型別。 如果*cf*為 0 時，新的項目會使用目前的圖示表示。 如果*cf*為非零值並*hMetaPict*不是 NULL，新的項目會使用*hMetaPict*其表示法。

##  <a name="findtext"></a>  CRichEditView::FindText

呼叫此函式以尋找指定的文字，並將它設為目前的選取範圍。

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
包含要搜尋的字串。

*bCase*<br/>
指出搜尋是否區分大小寫。

*bWord*<br/>
表示是否搜尋應符合完整單字，不是文字的一部份。

*bNext*<br/>
表示搜尋方向。 如果為 TRUE，搜尋方向是往緩衝區的結尾。 如果為 FALSE，搜尋方向是朝緩衝區的開頭。

### <a name="return-value"></a>傳回值

非零*lpszFind*找到文字; 否則為 0。

### <a name="remarks"></a>備註

此函式會尋找作業期間顯示等待游標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>  CRichEditView::FindTextSimple

呼叫此函式以尋找指定的文字，並將它設為目前的選取範圍。

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
包含要搜尋的字串。

*bCase*<br/>
指出搜尋是否區分大小寫。

*bWord*<br/>
表示是否搜尋應符合完整單字，不是文字的一部份。

*bNext*<br/>
表示搜尋方向。 如果為 TRUE，搜尋方向是往緩衝區的結尾。 如果為 FALSE，搜尋方向是朝緩衝區的開頭。

### <a name="return-value"></a>傳回值

非零*lpszFind*找到文字; 否則為 0。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::FindText](#findtext)。

##  <a name="getcharformatselection"></a>  CRichEditView::GetCharFormatSelection

呼叫此函式可取得的字元格式的目前選取範圍的屬性。

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>傳回值

A [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a)結構，其中包含的字元格式的目前選取範圍的屬性。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [EM_GETCHARFORMAT](/windows/desktop/Controls/em-getcharformat)訊息並[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) Windows SDK 中的結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>  CRichEditView::GetClipboardData

架構會呼叫此函式的處理過程[IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata)。

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>參數

*lpchrg*<br/>
指標[CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange)結構，指定的字元範圍 （OLE 項目） 複製到所指定的資料物件*lplpdataobj*。

*dwReco*<br/>
剪貼簿作業旗標。 可以是下列值之一。

- RECO_COPY 複製到剪貼簿。

- RECO_CUT 剪下到剪貼簿。

- RECO_DRAG 拖曳作業 （拖曳和卸除）。

- RECO_DROP 卸除作業 （拖曳和卸除）。

- 從剪貼簿 RECO_PASTE 貼。

*lpRichDataObj*<br/>
指標[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)物件，其中包含剪貼簿的資料來自 rich edit 控制項 ( [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata))。

*lplpdataobj*<br/>
收到的位址指標變數的指標`IDataObject`物件，表示在指定的範圍*lpchrg*參數。 值*lplpdataobj*如果會傳回錯誤，則會忽略。

### <a name="return-value"></a>傳回值

報告作業的成功 HRESULT 值。 如需有關 HRESULT 的詳細資訊，請參閱 <<c0> [ 錯誤碼的結構 COM](/windows/desktop/com/structure-of-com-error-codes) Windows SDK 中。

### <a name="remarks"></a>備註

如果傳回值，表示成功時，`IRichEditOleCallback::GetClipboardData`會傳回`IDataObject`存取*lplpdataobj*; 否則它會傳回所存取的一個*lpRichDataObj*。 覆寫此函式可提供您自己的剪貼簿資料。 此函式的預設實作會傳回 E_NOTIMPL。

這是一種進階可覆寫。

如需詳細資訊，請參閱 < [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata)， [IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata)，並[CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange)在 Windows SDK，請參閱[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) Windows SDK 中。

##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu

架構會呼叫此函式的處理過程[IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu)。

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>參數

*seltyp*<br/>
選取項目型別。 選取項目類型值詳述於 < 備註 > 一節。

*lpoleobj*<br/>
指標`OLEOBJECT`結構，指定第一個選取的 OLE 物件，如果選取項目包含一或多個 OLE 項目。 如果選取項目不包含任何項目*lpoleobj*是 NULL。 `OLEOBJECT`結構存放一個 OLE 物件的 v-資料表的指標。

*lpchrg*<br/>
指標[CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange)結構，包含目前的選取範圍。

### <a name="return-value"></a>傳回值

操作功能表的控制代碼。

### <a name="remarks"></a>備註

此函式是常見的一部分處理下的右滑鼠按鈕。

選取項目類型可以是下列旗標的任意組合：

- SEL_EMPTY 表示沒有目前的選取項目。

- SEL_TEXT 表示目前的選取範圍包含文字。

- SEL_OBJECT 表示目前的選取範圍包含至少一個 OLE 項目。

- SEL_MULTICHAR 表示目前的選取範圍包含多個文字字元。

- SEL_MULTIOBJECT 表示目前的選取範圍包含多個 OLE 物件。

預設實作會傳回 NULL。 這是一種進階可覆寫。

如需詳細資訊，請參閱 < [IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu)並[CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) Windows SDK 中。

##  <a name="getdocument"></a>  CRichEditView::GetDocument

呼叫此函式可取得的指標`CRichEditDoc`這份檢視相關聯。

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>傳回值

指標[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)相關聯的物件您`CRichEditView`物件。

##  <a name="getinplaceactiveitem"></a>  CRichEditView::GetInPlaceActiveItem

呼叫此函式可取得 OLE 項目，目前會啟動在這個就地`CRichEditView`物件。

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>傳回值

單一的就地使用中的指標[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)此 rich edit 檢視表中; 中的物件如果沒有 OLE 項目目前處於就地使用中狀態，則為 NULL。

##  <a name="getmargins"></a>  CRichEditView::GetMargins

呼叫此函式可擷取目前用於列印的邊界。

```
CRect GetMargins() const;
```

### <a name="return-value"></a>傳回值

用於列印的邊界以 MM_TWIPS。

##  <a name="getpagerect"></a>  CRichEditView::GetPageRect

呼叫此函式可取得用於列印頁面的尺寸。

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>傳回值

用於列印的頁面範圍以 MM_TWIPS。

### <a name="remarks"></a>備註

這個值會根據紙張大小。

##  <a name="getpapersize"></a>  CRichEditView::GetPaperSize

呼叫此函式可擷取目前的紙張大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>傳回值

用於列印在紙張的大小以 MM_TWIPS 單位。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>  CRichEditView::GetParaFormatSelection

呼叫此函式可取得的段落格式化目前選取範圍的屬性。

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>傳回值

A [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2)結構所在的段落格式化目前選取範圍的屬性。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [EM_GETPARAFORMAT](/windows/desktop/Controls/em-getparaformat)訊息並[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) Windows SDK 中的結構。

##  <a name="getprintrect"></a>  CRichEditView::GetPrintRect

呼叫此函式可擷取頁面矩形內的列印區域的界限。

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>傳回值

用於列印的影像區域的界限被以 MM_TWIPS。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>  CRichEditView::GetPrintWidth

呼叫此函式來決定所要的列印區域的寬度。

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>傳回值

列印的區域中，以 MM_TWIPS 寬度。

##  <a name="getricheditctrl"></a>  CRichEditView::GetRichEditCtrl

呼叫此函式來擷取[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)相關聯的物件`CRichEditView`物件。

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>傳回值

`CRichEditCtrl`此檢視的物件。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::FindText](#findtext)。

##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem

呼叫此函式以擷取 OLE 項目 (`CRichEditCntrItem`物件) 目前未在此選取`CRichEditView`物件。

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>傳回值

指標[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)中所選取物件`CRichEditView`物件;如果在此檢視中不選取任何項目，則為 NULL。

##  <a name="gettextlength"></a>  CRichEditView::GetTextLength

呼叫此函式，以取得此文字的長度`CRichEditView`物件。

```
long GetTextLength() const;
```

### <a name="return-value"></a>傳回值

在這個文字的長度`CRichEditView`物件。

##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx

呼叫此成員函式，來計算此文字的長度`CRichEditView`物件。

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
值，指定要用來判斷文字長度的方法。 這個成員可以是其中一個或多個值的旗標成員中所列[GETTEXTLENGTHEX](/windows/desktop/api/richedit/ns-richedit-_gettextlengthex) Windows SDK 中所述。

*uCodePage*<br/>
翻譯 （ANSI 字碼頁，Unicode 的 1200 cp_acp） 解譯的字碼頁。

### <a name="return-value"></a>傳回值

字元或編輯控制項中的位元組數目。 如果在已設定不相容的旗標*dwFlags*，此成員函式會傳回 E_INVALIDARG。

### <a name="remarks"></a>備註

`GetTextLengthEx` 提供其他方法可決定文字的長度。 它支援的 Rich Edit 2.0 功能。 如需詳細資訊，請參閱 <<c0> [ 關於 Rich Edit 控制項](/windows/desktop/Controls/about-rich-edit-controls)Windows SDK 中。

##  <a name="insertfileasobject"></a>  CRichEditView::InsertFileAsObject

呼叫此函式來插入指定的檔案 (做為[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件) 至豐富的編輯檢視。

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
包含要插入的檔案名稱的字串。

##  <a name="insertitem"></a>  CRichEditView::InsertItem

呼叫此函式插入[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)至 rich edit 檢視表的物件。

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
要插入之項目的指標。

### <a name="return-value"></a>傳回值

HRESULT 值，指出成功的插入。

### <a name="remarks"></a>備註

如需有關 HRESULT 的詳細資訊，請參閱 <<c0> [ 錯誤碼的結構 COM](/windows/desktop/com/structure-of-com-error-codes) Windows SDK 中。

##  <a name="isricheditformat"></a>  CRichEditView::IsRichEditFormat

呼叫此函式，以判斷是否*cf*是剪貼簿格式，也就是文字、 豐富的文字或 rtf 文字與 OLE 項目。

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
感興趣的剪貼簿格式。

### <a name="return-value"></a>傳回值

非零*cf*是豐富的編輯或文字剪貼簿格式。

##  <a name="isselected"></a>  CRichEditView::IsSelected

呼叫此函式可判斷指定的 OLE 項目目前在此檢視中選取。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>參數

*pDocItem*<br/>
在檢視中物件的指標。

### <a name="return-value"></a>傳回值

非零值，如果有選取的物件;否則為 0。

### <a name="remarks"></a>備註

如果您的衍生的檢視類別具有不同的方法來處理 OLE 項目的選取範圍，請覆寫這個函式。

##  <a name="m_nbulletindent"></a>  CRichEditView::m_nBulletIndent

清單中; 中的項目符號項目縮排根據預設，720 單位，也就是 1/2 英吋。

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap

指出此 rich edit 檢視表的自動換行的類型。

```
int m_nWordWrap;
```

### <a name="remarks"></a>備註

下列其中一個值：

- `WrapNone` 表示不會自動文字換行。

- `WrapToWindow` 表示視窗的寬度為基礎的自動換行。

- `WrapToTargetDevice` 指出目標裝置的特性為基礎的自動換行。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::WrapChanged](#wrapchanged)。

##  <a name="onchareffect"></a>  CRichEditView::OnCharEffect

呼叫此函式可切換的字元格式化目前選取範圍的效果。

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>參數

*dwMask*<br/>
字元，格式化目前選取範圍中修改的效果。

*dwEffect*<br/>
字元格式可切換的效果所需的清單。

### <a name="remarks"></a>備註

每個呼叫此函式會切換目前選取範圍指定的格式化效果。

如需詳細資訊*dwMask*並*dwEffect*參數和其可能的值，請參閱對應的資料成員[CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>  CRichEditView::OnFindNext

處理從 [尋找/取代] 對話方塊中的命令時，由架構呼叫。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要尋找的字串。

*bNext*<br/>
要搜尋的方向：TRUE 表示關閉;為 FALSE，最多。

*bCase*<br/>
指出搜尋是否區分大小寫。

*bWord*<br/>
指出搜尋是否只能比對完整字詞。

### <a name="remarks"></a>備註

呼叫此函式來尋找文字內`CRichEditView`。 覆寫這個函式來改變搜尋您的衍生的檢視類別的特性。

##  <a name="oninitialupdate"></a>  CRichEditView::OnInitialUpdate

檢視第一次附加至文件之後，但一開始顯示檢視之前，由架構呼叫。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>備註

此函式的預設實作會呼叫[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)成員函式，而不提示的資訊 (也就使用預設值為 0，表示*lHint*參數，則為NULL*pHint*參數)。 覆寫這個函式來執行任何需要的文件的相關資訊的單次初始化。 比方說，如果您的應用程式有固定大小的文件，您可以使用此函式來初始化檢視的捲動文件大小為基礎的限制。 如果您的應用程式支援可變大小的文件，使用`OnUpdate`更新捲動會限制每次文件變更。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::m_nWordWrap](#m_nwordwrap)。

##  <a name="onpastenativeobject"></a>  CRichEditView::OnPasteNativeObject

您可以使用此函式，從內嵌項目載入原生資料。

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>參數

*lpStg*<br/>
指標[IStorage](/windows/desktop/api/objidl/nn-objidl-istorage)物件。

### <a name="return-value"></a>傳回值

如果成功則為非零否則，便是 0;

### <a name="remarks"></a>備註

一般而言，您可以這樣藉由建立[COleStreamFile](../../mfc/reference/colestreamfile-class.md)周圍`IStorage`。 `COleStreamFile`可以附加至封存並[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)呼叫以將資料載入。

這是一種進階可覆寫。

如需詳細資訊，請參閱 < [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) Windows SDK 中。

##  <a name="onparaalign"></a>  CRichEditView::OnParaAlign

呼叫此函式來變更選取的段落的段落對齊方式。

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>參數

*wAlign*<br/>
所需的段落對齊方式。 下列其中一個值：

- PFA_LEFT 對齊左邊界的段落。

- PFA_RIGHT 對齊右邊界的段落。

- PFA_CENTER 中心之間的邊界的段落。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>  CRichEditView::OnPrinterChanged

覆寫這個函式來變更此 rich edit 檢視表的特性，印表機變更時。

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>參數

*dcPrinter*<br/>
A [CDC](../../mfc/reference/cdc-class.md)新印表機的物件。

### <a name="remarks"></a>備註

預設實作會設定紙張大小的實體的高度和寬度的輸出裝置 （印表機）。 如果沒有任何裝置內容會與相關聯*dcPrinter*的預設實作會將紙張大小設定為 8.5 11 英吋。

##  <a name="onreplaceall"></a>  CRichEditView::OnReplaceAll

處理從 取代 對話方塊中的全部取代 命令時，由架構呼叫。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要被取代的文字。

*lpszReplace*<br/>
取代的文字。

*bCase*<br/>
指出搜尋是否區分大小寫。

*bWord*<br/>
表示搜尋是否必須選取整個單字。

### <a name="remarks"></a>備註

呼叫此函式可使用另一個字串取代所有出現的某些指定的文字。 覆寫這個函式來改變此檢視的搜尋服務特性。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::FindText](#findtext)。

##  <a name="onreplacesel"></a>  CRichEditView::OnReplaceSel

處理從 [取代] 對話方塊中的 Replace 命令時，由架構呼叫。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要被取代的文字。

*bNext*<br/>
表示搜尋方向：關閉，則為 TRUE為 FALSE，最多。

*bCase*<br/>
指出搜尋是否區分大小寫。

*bWord*<br/>
表示搜尋是否必須選取整個單字。

*lpszReplace*<br/>
取代的文字。

### <a name="remarks"></a>備註

呼叫此函式可一次的某些指定的文字取代為另一個字串。 覆寫這個函式來改變此檢視的搜尋服務特性。

##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound

每當搜尋失敗時由架構呼叫。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
找不到文字。

### <a name="remarks"></a>備註

若要變更來自輸出通知此函式會覆寫[MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep)。

如需詳細資訊，請參閱 < [MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>  CRichEditView::OnUpdateCharEffect

架構會呼叫此函式來更新命令 UI 字元效果命令。

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指標[CCmdUI](../../mfc/reference/ccmdui-class.md)物件。

*dwMask*<br/>
表示格式化的遮罩字元。

*dwEffect*<br/>
表示的字元格式的效果。

### <a name="remarks"></a>備註

遮罩*dwMask*指定的字元格式化屬性來檢查。 旗標*dwEffect*清單之字元格式集/清除的屬性。

如需詳細資訊*dwMask*並*dwEffect*參數和其可能的值，請參閱對應的資料成員[CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>  CRichEditView::OnUpdateParaAlign

架構會呼叫此函式來更新命令 UI 段落效果命令。

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指標[CCmdUI](../../mfc/reference/ccmdui-class.md)物件。

*wAlign*<br/>
若要檢查的段落對齊方式。 下列其中一個值：

- PFA_LEFT 對齊左邊界的段落。

- PFA_RIGHT 對齊右邊界的段落。

- PFA_CENTER 中心之間的邊界的段落。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>  CRichEditView::PrintInsideRect

呼叫此函式可設定範圍，以便容納 rich edit 控制項中文字的格式*rectLayout*所指定的裝置*pDC*。

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>參數

*pDC*<br/>
輸出區域的裝置內容指標。

*rectLayout*<br/>
[RECT](/windows/desktop/api/windef/ns-windef-tagrect)或是[CRect](../../atl-mfc-shared/reference/crect-class.md)定義輸出區域。

*nIndexStart*<br/>
要格式化的第一個字元的以零為起始索引。

*nIndexStop*<br/>
要格式化的最後一個字元的以零為起始索引。

*bOutput*<br/>
指出是否應該轉譯的文字。 如果為 FALSE，是只測量的文字。

### <a name="return-value"></a>傳回值

符合輸出區域加一的最後一個字元索引。

### <a name="remarks"></a>備註

一般而言，這個呼叫後面接著呼叫[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)以產生輸出。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::GetPaperSize](#getpapersize)。

##  <a name="printpage"></a>  CRichEditView::PrintPage

呼叫此函式來設定所指定的輸出裝置的 rich edit 控制項中的文字範圍的格式*pDC*。

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>參數

*pDC*<br/>
網頁輸出的裝置內容指標。

*nIndexStart*<br/>
要格式化的第一個字元的以零為起始索引。

*nIndexStop*<br/>
要格式化的最後一個字元的以零為起始索引。

### <a name="return-value"></a>傳回值

在頁面加一的最後一個字元索引。

### <a name="remarks"></a>備註

每個頁面的配置會受到[GetPageRect](#getpagerect)並[GetPrintRect](#getprintrect)。 一般而言，這個呼叫後面接著呼叫[CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)以產生輸出。

請注意，是相對於實體的頁面，而不是邏輯頁面的邊界。 因此，為零的邊界會將通常會裁剪文字，因為許多印表機無法列印頁面上的區域。 若要避免裁剪文字，您應該呼叫[SetMargins](#setmargins)並設定列印前先合理的邊界。

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

由架構呼叫以將物件貼到豐富的編輯。

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>參數

*lpdataobj*<br/>
指標[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)查詢。

*lpcfFormat*<br/>
可接受的資料格式的指標。

*dwReco*<br/>
未使用。

*bReally*<br/>
表示是否貼上作業應該繼續進行。

*hMetaFile*<br/>
用於繪製的項目圖示的中繼檔控制代碼。

### <a name="return-value"></a>傳回值

報告作業的成功 HRESULT 值。

### <a name="remarks"></a>備註

覆寫這個函式以處理不同的組織，COM 中的項目衍生的文件類別。 這是一種進階可覆寫。

如需有關 HRESULT 和`IDataObject`，請參閱[錯誤碼的結構 COM](/windows/desktop/com/structure-of-com-error-codes)並[IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject)，分別 Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>  CRichEditView::SetCharFormat

呼叫此函式可設定的字元格式屬性在這個新的文字`CRichEditView`物件。

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a)結構，其中包含新的預設字元格式的屬性。

### <a name="remarks"></a>備註

指定的屬性`dwMask`隸屬*cf*由此函式會變更。

如需詳細資訊，請參閱 < [EM_SETCHARFORMAT](/windows/desktop/Controls/em-setcharformat)訊息並[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) Windows SDK 中的結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>  CRichEditView::SetMargins

呼叫此函式來設定此 rich edit 檢視表的列印邊界。

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>參數

*rectMargin*<br/>
新的邊界值，用於列印，以 MM_TWIPS。

### <a name="remarks"></a>備註

如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，您應該呼叫[WrapChanged](#wrapchanged)之後使用此函式調整列印的特性。

請注意，所使用的邊界[PrintPage](#printpage)相對於實體頁面上，而不是邏輯頁面。 因此，為零的邊界會將通常會裁剪文字，因為許多印表機無法列印頁面上的區域。 若要避免裁剪文字，您應該呼叫使用`SetMargins`設定合理的印表機在列印之前的邊界。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::GetPaperSize](#getpapersize)。

##  <a name="setpapersize"></a>  CRichEditView::SetPaperSize

呼叫此函式以設定紙張大小來列印此 rich edit 檢視。

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>參數

*sizePaper*<br/>
新的紙張大小值，用於列印，以 MM_TWIPS 測量。

### <a name="remarks"></a>備註

如果[m_nWordWrap](#m_nwordwrap)是`WrapToTargetDevice`，您應該呼叫[WrapChanged](#wrapchanged)之後使用此函式調整列印的特性。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>  CRichEditView::SetParaFormat

呼叫此函式可設定的段落格式屬性目前的選取範圍，在此`CRichEditView`物件。

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>參數

*pf*<br/>
[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2)結構，其中包含新的預設段落格式屬性。

### <a name="return-value"></a>傳回值

如果成功則為非零否則就是 0。

### <a name="remarks"></a>備註

指定的屬性`dwMask`隸屬*pf*由此函式會變更。

如需詳細資訊，請參閱 < [EM_SETPARAFORMAT](/windows/desktop/Controls/em-setparaformat)訊息並[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) Windows SDK 中的結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>  CRichEditView::TextNotFound

呼叫此函式來重設的內部搜尋狀態[CRichEditView](../../mfc/reference/cricheditview-class.md)呼叫失敗後的控制項[FindText](#findtext)。

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
包含找不到文字字串。

### <a name="remarks"></a>備註

我們建議您呼叫這個方法時，會呼叫失敗後立即[FindText](#findtext)使控制項的內部搜尋狀態正確重設。

*LpszFind*參數應該包含相同的內容，做為字串提供給[FindText](#findtext)。 之後重設內部搜尋狀態，此方法會呼叫[OnTextNotFound](#ontextnotfound)提供的搜尋字串的方法。

### <a name="example"></a>範例

  範例，請參閱[CRichEditView::FindText](#findtext)。

##  <a name="wrapchanged"></a>  CRichEditView::WrapChanged

列印特性已變更時呼叫此函式 ( [SetMargins](#setmargins)或是[SetPaperSize](#setpapersize))。

```
virtual void WrapChanged();
```

### <a name="remarks"></a>備註

此函式可修改的 rich edit 檢視的方式回應中的變更覆寫[m_nWordWrap](#m_nwordwrap)或列印的特性 ( [OnPrinterChanged](#onprinterchanged))。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 WORDPAD](../../visual-cpp-samples.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 類別](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem 類別](../../mfc/reference/cricheditcntritem-class.md)
