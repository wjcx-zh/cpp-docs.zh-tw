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
ms.openlocfilehash: c8eba16779b837b33912006a2ff3b7cdfa73f1e6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502636"
---
# <a name="cricheditview-class"></a>CRichEditView 類別

使用[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)和[CRICHEDITCNTRITEM](../../mfc/reference/cricheditcntritem-class.md), 在 MFC 的檔視圖架構內容中提供 rich edit 控制項的功能。

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
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|移動對話方塊, 使其不會遮蔽目前的選取範圍。|
|[CRichEditView::CanPaste](#canpaste)|指出剪貼簿是否包含可以貼入 rich edit 視圖中的資料。|
|[CRichEditView::DoPaste](#dopaste)|將 OLE 專案貼入這個 rich edit 視圖中。|
|[CRichEditView::FindText](#findtext)|尋找指定的文字, 叫用等待游標。|
|[CRichEditView::FindTextSimple](#findtextsimple)|尋找指定的文字。|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|抓取目前選取範圍的字元格式屬性。|
|[CRichEditView::GetDocument](#getdocument)|抓取相關[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的指標。|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|在 rich edit 視圖中, 抓取目前就地作用中的 OLE 專案。|
|[CRichEditView::GetMargins](#getmargins)|抓取此 rich edit 視圖的邊界。|
|[CRichEditView::GetPageRect](#getpagerect)|抓取此 rich edit 視圖的頁面矩形。|
|[CRichEditView::GetPaperSize](#getpapersize)|抓取此 rich edit 視圖的紙張大小。|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|抓取目前選取範圍的段落格式屬性。|
|[CRichEditView::GetPrintRect](#getprintrect)|抓取此 rich edit 視圖的列印矩形。|
|[CRichEditView::GetPrintWidth](#getprintwidth)|抓取此 rich edit 視圖的列印寬度。|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|抓取 rich edit 控制項。|
|[CRichEditView::GetSelectedItem](#getselecteditem)|從 rich edit 視圖中抓取選取的專案。|
|[CRichEditView::GetTextLength](#gettextlength)|抓取 rich edit 視圖中文字的長度。|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|抓取 rich edit 視圖中的字元數或位元組數。 用於決定長度之方法的展開旗標清單。|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|插入檔案做為 OLE 專案。|
|[CRichEditView::InsertItem](#insertitem)|將新專案插入做為 OLE 專案。|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|指出剪貼簿是否包含豐富的編輯或文字格式的資料。|
|[CRichEditView::OnCharEffect](#onchareffect)|切換目前選取範圍的字元格式。|
|[CRichEditView::OnParaAlign](#onparaalign)|變更段落的對齊方式。|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|更新字元公用成員函式的命令 UI。|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|更新段落公用成員函式的命令 UI。|
|[CRichEditView::PrintInsideRect](#printinsiderect)|格式化給定矩形內的指定文字。|
|[CRichEditView::PrintPage](#printpage)|格式化給定頁面中指定的文字。|
|[CRichEditView::SetCharFormat](#setcharformat)|設定目前選取範圍的字元格式屬性。|
|[CRichEditView::SetMargins](#setmargins)|設定此 rich edit 視圖的邊界。|
|[CRichEditView::SetPaperSize](#setpapersize)|設定此 rich edit 視圖的紙張大小。|
|[CRichEditView::SetParaFormat](#setparaformat)|設定目前選取範圍的段落格式屬性。|
|[CRichEditView::TextNotFound](#textnotfound)|重設控制項的內部搜尋狀態。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|在此 rich edit 視圖中, 抓取範圍的剪貼簿物件。|
|[CRichEditView::GetContextMenu](#getcontextmenu)|抓取以滑鼠右鍵向下鍵使用的內容功能表。|
|[CRichEditView::IsSelected](#isselected)|指出是否已選取指定的 OLE 專案。|
|[CRichEditView::OnFindNext](#onfindnext)|尋找子字串的下一個出現專案。|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|第一次附加至檔時, 會重新整理視圖。|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|從 OLE 專案抓取原生資料。|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|將列印特性設定為指定的裝置。|
|[CRichEditView::OnReplaceAll](#onreplaceall)|以新字串取代所有出現的指定字串。|
|[CRichEditView::OnReplaceSel](#onreplacesel)|取代目前的選取範圍。|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|處理找不到要求之文字的使用者通知。|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|查詢, 以查看上`IDataObject`的資料。|
|[CRichEditView::WrapChanged](#wrapchanged)|根據的值`m_nWordWrap`, 調整這個 rich edit 視圖的目標輸出裝置。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|表示專案符號清單的縮排數量。|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|表示文字換行條件約束。|

## <a name="remarks"></a>備註

「Rich edit 控制項」是一種視窗, 使用者可以在其中輸入和編輯文字。 文字可以被指派字元和段落格式, 而且可以包含內嵌的 OLE 物件。 Rich edit 控制項會提供用來格式化文字的程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。

`CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`維護在此視圖中的 OLE 用戶端專案清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。

這個 Windows 通用控制項 (因此也就是[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類別) 僅適用于在 windows 95/98 和 windows NT 3.51 版和更新版本下執行的程式。

如需在 MFC 應用程式中使用 rich edit 視圖的範例, 請參閱[WORDPAD](../../overview/visual-cpp-samples.md)範例應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>需求

**標頭:** afxrich。h

##  <a name="adjustdialogposition"></a>CRichEditView:: AdjustDialogPosition

呼叫此函式以移動指定的對話方塊, 使其不會遮蔽目前的選取範圍。

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>參數

*pDlg*<br/>
指向 `CDialog` 物件的指標。

##  <a name="canpaste"></a>CRichEditView:: CanPaste

呼叫此函式可判斷剪貼簿是否包含可以貼入這個 rich edit 視圖中的資訊。

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>傳回值

如果剪貼簿包含的資料格式可供此 rich edit view 接受, 則為非零值;否則為0。

##  <a name="cricheditview"></a>CRichEditView:: CRichEditView

呼叫此函式以建立`CRichEditView`物件。

```
CRichEditView();
```

##  <a name="dopaste"></a>CRichEditView::D oPaste

呼叫此函式, 將*dataobj*中的 OLE 專案貼入此 rich edit 檔/視圖中。

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>參數

*dataobj*<br/>
包含要貼上之資料的[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*cf*<br/>
所需的剪貼簿格式。

*hMetaPict*<br/>
中繼檔, 代表要貼入的專案。

### <a name="remarks"></a>備註

架構會在[QueryAcceptData](#queryacceptdata)的預設執行過程中呼叫此函式。

此函式會根據處理常式的結果來決定貼上特殊的類型。 如果*cf*為 0, 則新專案會使用目前的 iconic 標記法。 如果*cf*為非零值, 而*hMetaPict*不是 Null, 則新專案會使用*hMetaPict*來表示其呈現方式。

##  <a name="findtext"></a>CRichEditView:: FindText

呼叫此函式以尋找指定的文字, 並將它設定為目前的選取範圍。

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
指出搜尋是否應僅符合全字, 而不是單字的一部分。

*bNext*<br/>
表示搜尋的方向。 如果為 TRUE, 則表示搜尋方向朝向緩衝區結尾。 如果為 FALSE, 則表示搜尋方向朝向緩衝區的開頭。

### <a name="return-value"></a>傳回值

如果找到*lpszFind*文字, 則為非零值;否則為0。

### <a name="remarks"></a>備註

此函式會在尋找作業期間顯示等待游標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>CRichEditView:: FindTextSimple

呼叫此函式以尋找指定的文字, 並將它設定為目前的選取範圍。

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
指出搜尋是否應僅符合全字, 而不是單字的一部分。

*bNext*<br/>
表示搜尋的方向。 如果為 TRUE, 則表示搜尋方向朝向緩衝區結尾。 如果為 FALSE, 則表示搜尋方向朝向緩衝區的開頭。

### <a name="return-value"></a>傳回值

如果找到*lpszFind*文字, 則為非零值;否則為0。

### <a name="example"></a>範例

  請參閱[CRichEditView:: FindText](#findtext)的範例。

##  <a name="getcharformatselection"></a>CRichEditView:: GetCharFormatSelection

呼叫此函式可取得目前選取範圍的字元格式屬性。

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>傳回值

[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)結構, 其中包含目前選取範圍的字元格式屬性。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱[EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat)訊息和 Windows SDK 中的[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>CRichEditView:: GetClipboardData

在處理[IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)的過程中, 架構會呼叫此函式。

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>參數

*lpchrg*<br/>
[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)結構的指標, 指定要複製到*lplpdataobj*所指定之資料物件的字元範圍 (和 OLE 專案)。

*dwReco*<br/>
剪貼簿作業旗標。 可以是下列其中一個值。

- 將 RECO_COPY 複製到剪貼簿。

- RECO_CUT 剪下至剪貼簿。

- RECO_DRAG 拖曳作業 (拖放)。

- RECO_DROP Drop operation (拖放)。

- 從剪貼簿 RECO_PASTE 貼上。

*lpRichDataObj*<br/>
[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)物件的指標, 其中包含來自 rich edit 控制項 ( [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)) 的剪貼簿資料。

*lplpdataobj*<br/>
指標變數的指標, 其接收`IDataObject`物件的位址, 代表*lpchrg*參數中指定的範圍。 如果傳回錯誤, 則會忽略*lplpdataobj*的值。

### <a name="return-value"></a>傳回值

報告作業成功的 HRESULT 值。 如需 HRESULT 的詳細資訊, 請參閱 Windows SDK 中[COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="remarks"></a>備註

如果傳回值表示成功, `IRichEditOleCallback::GetClipboardData`會傳回*lplpdataobj*所存取的`IDataObject` , 否則會傳回*lpRichDataObj*所存取的一個。 覆寫此函式以提供您自己的剪貼簿資料。 此函式的預設實作用會傳回 E_NOTIMPL。

這是一個先進的可覆寫。

如需詳細資訊, 請參閱 Windows SDK 中的[IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)、 [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)和[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) , 並參閱 Windows SDK 中的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 。

##  <a name="getcontextmenu"></a>CRichEditView:: GetCoNtextMenu

在處理[IRichEditOleCallback:: GetCoNtextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)的過程中, 架構會呼叫此函式。

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>參數

*seltyp*<br/>
選取類型。 [備註] 區段中會描述選取類型的值。

*lpoleobj*<br/>
`OLEOBJECT`結構的指標, 如果選取範圍包含一個或多個 ole 專案, 則指定第一個選取的 ole 物件。 如果選取範圍未包含任何專案, 則*lpoleobj*為 Null。 `OLEOBJECT`結構會保存 OLE 物件 v 資料表的指標。

*lpchrg*<br/>
包含目前選取範圍之[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)結構的指標。

### <a name="return-value"></a>傳回值

內容功能表的控制碼。

### <a name="remarks"></a>備註

此函式是滑鼠右鍵處理的一般部分。

選取類型可以是下列旗標的任意組合:

- SEL_EMPTY 表示沒有目前的選取專案。

- SEL_TEXT 表示目前的選取範圍包含文字。

- SEL_OBJECT 表示目前的選取範圍至少包含一個 OLE 專案。

- SEL_MULTICHAR 表示目前的選取範圍包含一個以上的文字字元。

- SEL_MULTIOBJECT 表示目前的選取範圍包含一個以上的 OLE 物件。

預設的實值會傳回 Null。 這是一個先進的可覆寫。

如需詳細資訊, 請參閱 Windows SDK 中的[IRichEditOleCallback:: GetCoNtextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)和[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) 。

##  <a name="getdocument"></a>CRichEditView:: GetDocument

呼叫此函式可取得與此視圖`CRichEditDoc`相關聯之的指標。

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>傳回值

與`CRichEditView`物件相關聯之[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)物件的指標。

##  <a name="getinplaceactiveitem"></a>CRichEditView:: GetInPlaceActiveItem

呼叫此函式, 以取得目前在此`CRichEditView`物件中已啟用的 OLE 專案。

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>傳回值

這個 rich edit 視圖中單一就地作用中[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件的指標;如果目前沒有任何 OLE 專案處於就地作用中狀態, 則為 Null。

##  <a name="getmargins"></a>CRichEditView:: GetMargins

呼叫此函式可抓取目前用於列印的邊界。

```
CRect GetMargins() const;
```

### <a name="return-value"></a>傳回值

用於列印的邊界, 以 MM_TWIPS 為單位。

##  <a name="getpagerect"></a>CRichEditView:: GetPageRect

呼叫此函式可取得用於列印的頁面尺寸。

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>傳回值

用於列印的頁面範圍, 以 MM_TWIPS 為單位。

### <a name="remarks"></a>備註

這個值是根據紙張大小而定。

##  <a name="getpapersize"></a>CRichEditView:: GetPaperSize

呼叫此函式可取得目前的紙張大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>傳回值

用於列印的紙張大小 (以 MM_TWIPS 為單位)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>CRichEditView:: GetParaFormatSelection

呼叫此函式可取得目前選取範圍的段落格式屬性。

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>傳回值

[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)結構, 其中包含目前選取範圍的段落格式屬性。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat)訊息和[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)結構。

##  <a name="getprintrect"></a>CRichEditView:: GetPrintRect

呼叫此函式可抓取頁面矩形內列印範圍的範圍。

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>傳回值

用於列印的影像區域範圍, 以 MM_TWIPS 為單位。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>CRichEditView:: GetPrintWidth

呼叫此函式可判斷列印範圍的寬度。

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>傳回值

列印範圍的寬度 (以 MM_TWIPS 為單位)。

##  <a name="getricheditctrl"></a>  CRichEditView::GetRichEditCtrl

呼叫此函式可抓取與`CRichEditView`物件相關聯的[ CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 物件。

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>傳回值

這個`CRichEditCtrl`視圖的物件。

### <a name="example"></a>範例

  請參閱[CRichEditView:: FindText](#findtext)的範例。

##  <a name="getselecteditem"></a>CRichEditView:: GetSelectedItem

呼叫此函式可抓取目前在此`CRichEditCntrItem` `CRichEditView`物件中選取的 OLE 專案 (物件)。

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>傳回值

在`CRichEditView`物件中選取之[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件的指標;如果未在此視圖中選取任何專案, 則為 Null。

##  <a name="gettextlength"></a>CRichEditView:: GetTextLength

呼叫此函式可取得此`CRichEditView`物件中的文字長度。

```
long GetTextLength() const;
```

### <a name="return-value"></a>傳回值

這個`CRichEditView`物件中的文字長度。

##  <a name="gettextlengthex"></a>CRichEditView:: GetTextLengthEx

呼叫這個成員函式以計算此`CRichEditView`物件中的文字長度。

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
值, 指定要用來決定文字長度的方法。 這個成員可以是 Windows SDK 中所述[GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex)旗標成員中所列的一或多個值。

*uCodePage*<br/>
翻譯的字碼頁 (ANSI 字碼頁為 CP_ACP, Unicode 為 1200)。

### <a name="return-value"></a>傳回值

編輯控制項中的字元數或位元組數。 如果在*dwFlags*中設定了不相容的旗標, 此成員函式會傳回 E_INVALIDARG。

### <a name="remarks"></a>備註

`GetTextLengthEx`提供其他方式來決定文字的長度。 它支援豐富的編輯2.0 功能。 如需詳細資訊, 請參閱關於 Windows SDK 中的[Rich Edit 控制項](/windows/win32/Controls/about-rich-edit-controls)。

##  <a name="insertfileasobject"></a>CRichEditView:: InsertFileAsObject

呼叫此函式可將指定的檔案 (做為[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件) 插入 rich edit 視圖中。

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
包含要插入之檔案名的字串。

##  <a name="insertitem"></a>CRichEditView:: InsertItem

呼叫此函式可將[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)物件插入 rich edit 視圖中。

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
要插入之專案的指標。

### <a name="return-value"></a>傳回值

HRESULT 值, 表示插入成功。

### <a name="remarks"></a>備註

如需 HRESULT 的詳細資訊, 請參閱 Windows SDK 中[COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes)。

##  <a name="isricheditformat"></a>CRichEditView:: IsRichEditFormat

呼叫此函式可判斷*cf*是否為文字、rtf 文字或具有 OLE 專案之 Rtf 的剪貼簿格式。

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
感對的剪貼簿格式。

### <a name="return-value"></a>傳回值

如果*cf*是 rich edit 或 text 剪貼簿格式, 則為非零值。

##  <a name="isselected"></a>CRichEditView:: IsSelected

呼叫此函式, 以判斷目前是否已在此視圖中選取指定的 OLE 專案。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>參數

*pDocItem*<br/>
視圖中物件的指標。

### <a name="return-value"></a>傳回值

如果已選取物件, 則為非零。否則為0。

### <a name="remarks"></a>備註

如果您的衍生視圖類別有不同的方法來處理 OLE 專案的選取, 請覆寫這個函式。

##  <a name="m_nbulletindent"></a>CRichEditView:: m_nBulletIndent

清單中的專案符號專案縮排。預設為720單位, 也就是1/2 英寸。

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>CRichEditView:: m_nWordWrap

表示此 rich edit 視圖的自動換行類型。

```
int m_nWordWrap;
```

### <a name="remarks"></a>備註

下列其中一個值：

- `WrapNone`表示不自動換行。

- `WrapToWindow`表示根據視窗寬度的自動換行。

- `WrapToTargetDevice`表示根據目標裝置的特性換行。

### <a name="example"></a>範例

  請參閱[CRichEditView:: WrapChanged](#wrapchanged)的範例。

##  <a name="onchareffect"></a>CRichEditView:: OnCharEffect

呼叫此函式可切換目前選取範圍的字元格式效果。

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>參數

*dwMask*<br/>
要在目前選取範圍中修改的字元格式效果。

*dwEffect*<br/>
要切換的所需字元格式效果清單。

### <a name="remarks"></a>備註

此函式的每個呼叫都會針對目前的選取範圍, 切換指定的格式設定效果。

如需*dwMask*和*dwEffect*參數及其潛在值的詳細資訊, 請參閱 Windows SDK 中的對應資料成員[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-_charformat) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>CRichEditView:: OnFindNext

從 [尋找/取代] 對話方塊處理命令時, 由架構呼叫。

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
要搜尋的方向:TRUE 表示關閉;FALSE、up。

*bCase*<br/>
指出搜尋是否區分大小寫。

*bWord*<br/>
指出搜尋是否只符合整個單字。

### <a name="remarks"></a>備註

呼叫此函式可在中`CRichEditView`尋找文字。 覆寫此函式, 以改變衍生視圖類別的搜尋特性。

##  <a name="oninitialupdate"></a>CRichEditView:: OnInitialUpdate

在第一次將視圖附加至檔, 但在一開始顯示視圖之前, 由架構呼叫。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>備註

此函式的預設執行會呼叫不含提示資訊的[CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate)成員函式 (亦即, 針對*lHint*參數使用預設值 0, 而*pHint*參數為 Null)。 覆寫這個函式, 以執行需要檔相關資訊的任何一次性初始化。 例如, 如果您的應用程式具有固定大小的檔, 您可以使用此函式, 根據檔案大小來初始化視圖的滾動限制。 如果您的應用程式支援可變大小的檔`OnUpdate` , 請在每次檔變更時使用來更新捲軸限制。

### <a name="example"></a>範例

  請參閱[CRichEditView:: m_nWordWrap](#m_nwordwrap)的範例。

##  <a name="onpastenativeobject"></a>CRichEditView:: OnPasteNativeObject

使用此函式可從內嵌專案載入原生資料。

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>參數

*lpStg*<br/>
[IStorage](/windows/win32/api/objidl/nn-objidl-istorage)物件的指標。

### <a name="return-value"></a>傳回值

如果成功, 則為非零;否則為 0;

### <a name="remarks"></a>備註

一般來說, 您可以藉由建立周圍`IStorage`的[COleStreamFile](../../mfc/reference/colestreamfile-class.md)來執行這項操作。 可以附加至封存和[CObject:: 序列化](../../mfc/reference/cobject-class.md#serialize)呼叫來載入資料。 `COleStreamFile`

這是一個先進的可覆寫。

如需詳細資訊, 請參閱 Windows SDK 中的[IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 。

##  <a name="onparaalign"></a>CRichEditView:: OnParaAlign

呼叫此函式可變更所選段落的段落對齊。

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>參數

*wAlign*<br/>
所需的段落對齊。 下列其中一個值：

- PFA_LEFT 對齊段落與左邊界。

- PFA_RIGHT 會將段落對齊右邊界。

- PFA_CENTER 置中邊界之間的段落。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>CRichEditView:: OnPrinterChanged

覆寫此函式, 以在印表機變更時變更此 rich edit 視圖的特性。

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>參數

*dcPrinter*<br/>
新印表機的[CDC](../../mfc/reference/cdc-class.md)物件。

### <a name="remarks"></a>備註

預設的執行會將紙張大小設定為輸出裝置 (印表機) 的實體高度和寬度。 如果沒有與*dcPrinter*相關聯的裝置內容, 則預設的執行會將紙張大小設定為 8.5 x 11 英寸。

##  <a name="onreplaceall"></a>CRichEditView:: OnReplaceAll

當處理取代對話方塊中的所有命令時, 由架構呼叫。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要取代的文字。

*lpszReplace*<br/>
取代文字。

*bCase*<br/>
指出搜尋是否區分大小寫。

*bWord*<br/>
指出搜尋是否必須選取整個單字。

### <a name="remarks"></a>備註

呼叫此函式可將某些指定文字的所有出現專案取代為另一個字串。 覆寫此函式以改變此視圖的搜尋特性。

### <a name="example"></a>範例

  請參閱[CRichEditView:: FindText](#findtext)的範例。

##  <a name="onreplacesel"></a>CRichEditView:: OnReplaceSel

由架構在處理 [取代] 對話方塊中的 [取代] 命令時呼叫。

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
要取代的文字。

*bNext*<br/>
表示搜尋的方向:TRUE 已關閉;FALSE、up。

*bCase*<br/>
指出搜尋是否區分大小寫。

*bWord*<br/>
指出搜尋是否必須選取整個單字。

*lpszReplace*<br/>
取代文字。

### <a name="remarks"></a>備註

呼叫此函式可使用另一個字串來取代某些指定文字的一次出現。 覆寫此函式以改變此視圖的搜尋特性。

##  <a name="ontextnotfound"></a>CRichEditView:: OnTextNotFound

每次搜尋失敗時由架構呼叫。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
找不到的文字。

### <a name="remarks"></a>備註

覆寫此函式, 以變更[若要 messagebeep](/windows/win32/api/winuser/nf-winuser-messagebeep)的輸出通知。

如需詳細資訊, 請參閱 Windows SDK 中的[若要 messagebeep](/windows/win32/api/winuser/nf-winuser-messagebeep) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>CRichEditView:: OnUpdateCharEffect

架構會呼叫這個函式來更新字元效果命令的命令 UI。

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標。

*dwMask*<br/>
表示字元格式遮罩。

*dwEffect*<br/>
表示字元格式設定效果。

### <a name="remarks"></a>備註

Mask *dwMask*會指定要檢查的字元格式化屬性。 旗標*dwEffect*會列出要設定/清除的字元格式屬性。

如需*dwMask*和*dwEffect*參數及其潛在值的詳細資訊, 請參閱 Windows SDK 中的對應資料成員[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-_charformat) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>CRichEditView:: OnUpdateParaAlign

架構會呼叫這個函式來更新段落效果命令的命令 UI。

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標。

*wAlign*<br/>
要檢查的段落對齊方式。 下列其中一個值：

- PFA_LEFT 對齊段落與左邊界。

- PFA_RIGHT 會將段落對齊右邊界。

- PFA_CENTER 置中邊界之間的段落。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>CRichEditView::P rintInsideRect

呼叫此函式可將 rich edit 控制項中的文字範圍格式化, 以符合*pDC*所指定裝置的*rectLayout* 。

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
輸出區域之裝置內容的指標。

*rectLayout*<br/>
定義輸出區域的[矩形](/windows/win32/api/windef/ns-windef-rect)或[CRect](../../atl-mfc-shared/reference/crect-class.md) 。

*nIndexStart*<br/>
要格式化的第一個字元之以零為基底的索引。

*nIndexStop*<br/>
要格式化之最後一個字元的以零為基底的索引。

*bOutput*<br/>
指出是否應該呈現文字。 如果為 FALSE, 則只會測量文字。

### <a name="return-value"></a>傳回值

符合輸出區域加一的最後一個字元的索引。

### <a name="remarks"></a>備註

一般來說, 此呼叫會接著呼叫[CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) , 這會產生輸出。

### <a name="example"></a>範例

  請參閱[CRichEditView:: GetPaperSize](#getpapersize)的範例。

##  <a name="printpage"></a>CRichEditView::P rintPage

呼叫此函式可針對*pDC*所指定的輸出裝置, 格式化 rich edit 控制項中的文字範圍。

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>參數

*pDC*<br/>
頁面輸出之裝置內容的指標。

*nIndexStart*<br/>
要格式化的第一個字元之以零為基底的索引。

*nIndexStop*<br/>
要格式化之最後一個字元的以零為基底的索引。

### <a name="return-value"></a>傳回值

放在頁面上的最後一個字元的索引加一。

### <a name="remarks"></a>備註

每個頁面的版面配置都是由[GetPageRect](#getpagerect)和[GetPrintRect](#getprintrect)所控制。 一般來說, 此呼叫會接著呼叫[CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) , 這會產生輸出。

請注意, 邊界是相對於實體頁面, 而不是邏輯頁面。 因此, 零的邊界通常會裁剪文字, 因為許多印表機在頁面上都有無法列印的區域。 若要避免裁剪您的文字, 您應該先呼叫[SetMargins](#setmargins)並設定合理的邊界, 再列印。

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

由架構呼叫, 以將物件貼入 rich edit。

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
要查詢之[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)的指標。

*lpcfFormat*<br/>
可接受之資料格式的指標。

*dwReco*<br/>
未使用。

*bReally*<br/>
指出貼上作業是否應該繼續。

*hMetaFile*<br/>
用來繪製專案圖示之中繼檔的控制碼。

### <a name="return-value"></a>傳回值

報告作業成功的 HRESULT 值。

### <a name="remarks"></a>備註

覆寫此函式, 以處理衍生檔類別中 COM 專案的不同組織。 這是一個先進的可覆寫。

如需有關 HRESULT 和`IDataObject`的詳細資訊, 請分別參閱 Windows SDK 中的[COM 錯誤碼](/windows/win32/com/structure-of-com-error-codes)和[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>CRichEditView:: SetCharFormat

呼叫此函式可為這個`CRichEditView`物件中的新文字設定字元格式屬性。

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
包含新的預設字元格式屬性的[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)結構。

### <a name="remarks"></a>備註

此函式只會變更`dwMask` *cf*的成員所指定的屬性。

如需詳細資訊, 請參閱 Windows SDK 中的[EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat)訊息和[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>CRichEditView:: SetMargins

呼叫此函式可設定此 rich edit 視圖的列印邊界。

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>參數

*rectMargin*<br/>
用於列印的新邊界值 (以 MM_TWIPS 為單位)。

### <a name="remarks"></a>備註

如果[m_nWordWrap](#m_nwordwrap)為`WrapToTargetDevice`, 則在使用此函式來調整列印特性之後, 您應該呼叫[WrapChanged](#wrapchanged) 。

請注意, [system.drawing.printing.printdocument.printpage>](#printpage)使用的邊界是相對於實體頁面, 而不是邏輯頁面。 因此, 零的邊界通常會裁剪文字, 因為許多印表機在頁面上都有無法列印的區域。 若要避免裁剪您的文字, 您應該`SetMargins`在列印前呼叫使用來設定合理的印表機邊界。

### <a name="example"></a>範例

  請參閱[CRichEditView:: GetPaperSize](#getpapersize)的範例。

##  <a name="setpapersize"></a>CRichEditView:: SetPaperSize

呼叫此函式可設定列印此 rich edit 視圖的紙張大小。

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>參數

*sizePaper*<br/>
列印的新紙張大小值, 以 MM_TWIPS 為單位。

### <a name="remarks"></a>備註

如果[m_nWordWrap](#m_nwordwrap)為`WrapToTargetDevice`, 則在使用此函式來調整列印特性之後, 您應該呼叫[WrapChanged](#wrapchanged) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>CRichEditView:: SetParaFormat

呼叫此函式可設定此`CRichEditView`物件中目前選取範圍的段落格式屬性。

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>參數

*pf*<br/>
包含新的預設段落格式屬性的[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)結構。

### <a name="return-value"></a>傳回值

如果成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

此函式只會變更`dwMask` *pf*的成員所指定的屬性。

如需詳細資訊, 請參閱 Windows SDK 中的[EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat)訊息和[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>CRichEditView:: TextNotFound

呼叫此函式可在失敗的[FindText](#findtext)呼叫之後, 重設[CRichEditView](../../mfc/reference/cricheditview-class.md)控制項的內部搜尋狀態。

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
包含找不到的文字字串。

### <a name="remarks"></a>備註

建議您在呼叫[FindText](#findtext)失敗之後立即呼叫此方法, 讓控制項的內部搜尋狀態正確地重設。

*LpszFind*參數應該包含與提供給[FindText](#findtext)的字串相同的內容。 在重設內部搜尋狀態之後, 這個方法會使用提供的搜尋字串來呼叫[OnTextNotFound](#ontextnotfound)方法。

### <a name="example"></a>範例

  請參閱[CRichEditView:: FindText](#findtext)的範例。

##  <a name="wrapchanged"></a>CRichEditView:: WrapChanged

當列印特性變更時, 呼叫此函式 ( [SetMargins](#setmargins)或[SetPaperSize](#setpapersize))。

```
virtual void WrapChanged();
```

### <a name="remarks"></a>備註

覆寫此函式, 以修改 rich edit 視圖回應[m_nWordWrap](#m_nwordwrap)或列印特性 ( [OnPrinterChanged](#onprinterchanged)) 變更的方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 類別](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem 類別](../../mfc/reference/cricheditcntritem-class.md)
