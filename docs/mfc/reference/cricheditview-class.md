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
ms.openlocfilehash: b72daac576411b45908d1e91bd86bbd9aeacf738
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754461"
---
# <a name="cricheditview-class"></a>CRichEditView 類別

通過[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)和[CRichEditCntrItem,](../../mfc/reference/cricheditcntritem-class.md)在 MFC 的文檔視圖體系結構上下文中提供了豐富的編輯控制項的功能。

## <a name="syntax"></a>語法

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[克里希編輯檢視:克里希編輯檢視](#cricheditview)|建構 `CRichEditView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[克里希編輯檢視::調整對話位置](#adjustdialogposition)|移動對話框,使其不會遮擋當前選擇。|
|[克里希編輯檢視::可以粘貼](#canpaste)|告知剪貼簿是否包含可粘貼到富編輯視圖中的數據。|
|[克里希編輯視圖::DoPaste](#dopaste)|將 OLE 項貼上到此豐富的編輯檢視中。|
|[克里希編輯檢視:尋找文字](#findtext)|尋找指定的文字,呼叫等待游標。|
|[克里希編輯檢視:尋找文字簡單](#findtextsimple)|尋找指定的文字。|
|[克里希編輯檢視:取得字元格式選擇](#getcharformatselection)|檢索當前選擇的字元格式屬性。|
|[克里希編輯檢視:取得文件](#getdocument)|檢索指向相關[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)的指標。|
|[克里希編輯檢視:抓取位置活動項目](#getinplaceactiveitem)|檢索目前在富編輯檢視中處於活動狀態的 OLE 項。|
|[克里希編輯檢視:抓取邊緣](#getmargins)|檢索此富編輯視圖的邊距。|
|[克里希編輯檢視:取得頁面Rect](#getpagerect)|檢索此富編輯視圖的頁面矩形。|
|[克里希編輯檢視:抓取紙張大小](#getpapersize)|檢索此富編輯視圖的紙張大小。|
|[克里希編輯檢視:取得帕拉格式選擇](#getparaformatselection)|檢索當前選擇的段落格式屬性。|
|[克里希編輯檢視:抓取列印重新](#getprintrect)|檢索此富編輯視圖的列印矩形。|
|[克里希編輯檢視:取得列印寬度](#getprintwidth)|檢索此富編輯視圖的列印寬度。|
|[克里希編輯檢視:取得里希編輯Ctrl](#getricheditctrl)|檢索豐富的編輯控制件。|
|[克里希編輯檢視:取得選取的項目](#getselecteditem)|從富編輯檢視中檢索所選專案。|
|[克里希編輯檢視:抓取文字長度](#gettextlength)|檢索富編輯視圖中的文本長度。|
|[克里希編輯檢視:取得文字長度Ex](#gettextlengthex)|檢索富編輯檢視中的字元或位元組數。 用於確定長度的方法的展開標誌清單。|
|[克里希編輯檢視::插入檔案物件](#insertfileasobject)|將檔案插入為 OLE 項。|
|[克里希編輯檢視:插入項目](#insertitem)|將新專案插入為 OLE 項。|
|[克里希編輯檢視::是裡希編輯格式](#isricheditformat)|告知剪貼簿是否包含豐富的編輯或文字格式的數據。|
|[克里希編輯檢視::在字元效果](#onchareffect)|切換目前選擇的字元格式。|
|[克里希編輯視圖:在帕拉維萊](#onparaalign)|更改段落的對齊方式。|
|[克里希編輯檢視:上更新字元效果](#onupdatechareffect)|更新字元公共成員函數的命令 UI。|
|[克里希編輯檢視:更新帕拉對齊](#onupdateparaalign)|更新段落公共成員函數的命令 UI。|
|[克里希編輯視圖::P林特內卡雷茨](#printinsiderect)|在給定矩形中設定指定文本的格式。|
|[克里希編輯檢視::PrintPage](#printpage)|在給定頁面中設定指定文本的格式。|
|[克里希編輯檢視:設定字元格式](#setcharformat)|設定當前選擇的字元格式屬性。|
|[克里希編輯檢視::設定邊距](#setmargins)|設置此富編輯視圖的邊距。|
|[克里希編輯檢視::設定紙張大小](#setpapersize)|設置此富編輯檢視的紙張大小。|
|[克里希編輯檢視::設定帕拉格式](#setparaformat)|設定當前選擇的段落格式屬性。|
|[克里希編輯檢視::未找到文字](#textnotfound)|重置控制件的內部搜索狀態。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[克里希編輯檢視:抓取剪貼簿資料](#getclipboarddata)|檢索此豐富編輯檢視中範圍的剪貼簿物件。|
|[克里希編輯檢視:抓取內容選單](#getcontextmenu)|檢索要在滑鼠右鍵下使用的上下文菜單。|
|[克里希編輯檢視:已選定](#isselected)|指示是否選擇了給定的 OLE 項。|
|[克里希編輯檢視::在查找下一個](#onfindnext)|尋找子字串的下一個符合項。|
|[克里希編輯檢視:初始更新](#oninitialupdate)|首次將檢視附加到文檔時刷新檢視。|
|[克里希編輯檢視::貼上本機物件](#onpastenativeobject)|從 OLE 項檢索本機數據。|
|[克里希編輯檢視:開啟印表機已變更](#onprinterchanged)|將列印特徵設置到給定設備。|
|[克里希編輯檢視::全部取代](#onreplaceall)|將給定字串的所有匹配項替換為新字串。|
|[克里希編輯檢視:開啟取代塞爾](#onreplacesel)|替換當前選擇。|
|[克里希編輯檢視::未找到文字](#ontextnotfound)|處理使用者通知,通知未找到請求的文本。|
|[克里希編輯檢視::查詢接受數據](#queryacceptdata)|查詢以檢視的資料`IDataObject`。|
|[克里希編輯檢視:包裝](#wrapchanged)|根據的值調整此富編輯檢視的目標輸出裝置`m_nWordWrap`。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[克里希編輯檢視:m_nBulletIndent](#m_nbulletindent)|指示項目符號清單的縮進量。|
|[克里希編輯檢視::m_nWordWrap](#m_nwordwrap)|指示換行約束。|

## <a name="remarks"></a>備註

"富編輯控制件"是使用者可以在其中輸入和編輯文本的視窗。 文本可以分配字元和段落格式,並可以包括嵌入的 OLE 物件。 豐富的編輯控制項為文字格式設定提供了程式設計介面。 然而，應用程式必須實作所有必要的使用者介面元件，讓使用者能夠執行格式化作業。

`CRichEditView` 會維護文字和文字的格式特性。 `CRichEditDoc`維護檢視中的 OLE 客戶端項的清單。 `CRichEditCntrItem` 提供 OLE 用戶端項目的存取權給容器端。

此 Windows 通用控件(因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相關類)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

有關在 MFC 應用程式中使用富編輯檢視的範例,請參閱[WORDPAD](../../overview/visual-cpp-samples.md)範例應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>需求

**標題:** afxrich.h

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a>克里希編輯檢視::調整對話位置

調用此函數以移動給定的對話框,以便它不會遮蓋當前選擇。

```cpp
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>參數

*pDlg*<br/>
指向 `CDialog` 物件的指標。

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a>克里希編輯檢視::可以粘貼

呼叫此函數以確定剪貼簿是否包含可貼上到此豐富編輯檢視中的資訊。

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>傳回值

如果剪貼板以此豐富的編輯檢視可以接受的格式包含數據,則非零;否則,0。

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a>克里希編輯檢視:克里希編輯檢視

呼叫此函式以建立物件`CRichEditView`。

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a>克里希編輯視圖::DoPaste

呼叫此函數以將*dataobj*中的 OLE 項貼上到此豐富的編輯文件/檢視中。

```cpp
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>參數

*達多布吉*<br/>
包含要貼上的[COleData 物件](../../mfc/reference/coledataobject-class.md)。

*cf*<br/>
所需的剪貼簿格式。

*哈梅塔皮克特*<br/>
表示要貼上的項的元檔。

### <a name="remarks"></a>備註

該框架調用此函數作為[查詢接受數據](#queryacceptdata)默認實現的一部分。

此函數根據粘貼特殊處理程序的結果確定粘貼類型。 如果*cf*是 0,則新專案使用當前標誌性表示形式。 如果*cf*是非零且*hMetaPict*不是 NULL,則新專案將使用*hMetaPict*進行表示。

## <a name="cricheditviewfindtext"></a><a name="findtext"></a>克里希編輯檢視:尋找文字

呼叫此函數以尋找指定的文本並將其設置為當前選擇。

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
指示搜索是否區分大小寫。

*bWord*<br/>
指示搜索是否應僅匹配整個單詞,而不是單詞的某些部分。

*b 下一個*<br/>
指示搜索的方向。 如果為 TRUE,則搜索方向朝向緩衝區的末尾。 如果 FALSE,則搜索方向朝向緩衝區的開頭。

### <a name="return-value"></a>傳回值

如果找到*lpsz 查找*文字,則非零;否則 0。

### <a name="remarks"></a>備註

此函數在查找操作期間顯示等待游標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a>克里希編輯檢視:尋找文字簡單

呼叫此函數以尋找指定的文本並將其設置為當前選擇。

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
指示搜索是否區分大小寫。

*bWord*<br/>
指示搜索是否應僅匹配整個單詞,而不是單詞的某些部分。

*b 下一個*<br/>
指示搜索的方向。 如果為 TRUE,則搜索方向朝向緩衝區的末尾。 如果 FALSE,則搜索方向朝向緩衝區的開頭。

### <a name="return-value"></a>傳回值

如果找到*lpsz 查找*文字,則非零;否則 0。

### <a name="example"></a>範例

  請參考[CRichEditView 的範例:尋找文字](#findtext)。

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a>克里希編輯檢視:取得字元格式選擇

呼叫此函數獲取當前選擇的字元格式屬性。

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>傳回值

包含當前選擇的字元格式屬性的[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)結構。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat)消息和[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a>克里希編輯檢視:抓取剪貼簿資料

該框架呼叫此函數作為[IRichEditOle 回檔處理的一部分:getClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)。

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>參數

*lpchrg*<br/>
指向[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)結構的指標,指定要複製到*lplpdataobj*指定的數據物件的字元範圍(和 OLE 項)。

*德德雷科*<br/>
剪貼簿操作標誌。 可以是這些值之一。

- RECO_COPY複製到剪貼板。

- RECO_CUT剪下剪貼簿。

- RECO_DRAG拖動操作(拖放)。

- RECO_DROP拖放操作(拖放)。

- RECO_PASTE從剪貼簿粘貼。

*lpRichDataObj*<br/>
指向包含來自豐富編輯控制項的剪貼簿資料的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)物件指標[(IRichEditOle::getClipboard資料](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata))。

*lpdataobj*<br/>
指向接收表示*lpchrg*參數中`IDataObject`指定範圍 的物件位址的指標變數。 如果返回錯誤,則忽略*lpdataobj*的值。

### <a name="return-value"></a>傳回值

報告操作成功的 HRESULT 值。 有關 HRESULT 的詳細資訊,請參閱 Windows SDK 中的[COM 錯誤代碼結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="remarks"></a>備註

如果傳回值指示成功,`IRichEditOleCallback::GetClipboardData`則`IDataObject`傳回*lplpdataobj*存取的 。否則,它傳回由*lpRichDataObj*存取的一個 。 重寫此函數以提供您自己的剪貼簿數據。 此函數的預設實現返回E_NOTIMPL。

這是一個高級的可重寫。

有關詳細資訊,請參閱[IRichEditOle::獲取剪貼簿數據](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)[、IRichEditOle 回撥::獲取剪輯板數據](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata),並在 Windows SDK 中查看[IDataObject。](/windows/win32/api/objidl/nn-objidl-idataobject) [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a>克里希編輯檢視:抓取內容選單

該框架呼叫此函數作為[IRichEditOleCallback](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)處理的一部份:取得ContextMenu 。

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>參數

*塞爾蒂普*<br/>
選擇類型。 選擇類型值在「備註」 部分中描述。

*利波洛比*<br/>
如果所選內容`OLEOBJECT`包含一個或多個 OLE 項,則指向指定第一個選定 OLE 物件的結構的指標。 如果選取的內容不包含任何專案,*則 lpoleobj*為 NULL。 結構`OLEOBJECT`包含指向 OLE 物件 v 表的指標。

*lpchrg*<br/>
指向包含當前選擇的[CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange)結構的指標。

### <a name="return-value"></a>傳回值

處理上下文菜單。

### <a name="remarks"></a>備註

此功能是滑鼠右下處理的典型部分。

選擇類型可以是以下旗標的任意組合:

- SEL_EMPTY 表示沒有當前選擇。

- SEL_TEXT 指示當前所選內容包含文本。

- SEL_OBJECT指示當前所選內容至少包含一個 OLE 項。

- SEL_MULTICHAR 指示當前所選內容包含多個文字字元。

- SEL_MULTIOBJECT指示當前選擇包含多個 OLE 物件。

預設實現返回 NULL。 這是一個高級的可重寫。

有關詳細資訊,請參閱[IRichEditOle 回撥::獲取 Windows](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) SDK 中的上下文菜單和[CHARRANGE。](/windows/win32/api/richedit/ns-richedit-charrange)

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a>克里希編輯檢視:取得文件

呼叫此函數以獲取指向與此檢視`CRichEditDoc`關聯的指標。

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>傳回值

指向與`CRichEditView`物件關聯的[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)物件。

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>克里希編輯檢視:抓取位置活動項目

呼叫此函數以取得當前在此`CRichEditView`物件中啟動的 OLE 項。

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>傳回值

指向此富編輯檢視中的單個、就地活動[CRichEdit CntrItem 物件的](../../mfc/reference/cricheditcntritem-class.md)指標;如果目前沒有 OLE 項處於就地活動狀態,則為 NULL。

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a>克里希編輯檢視:抓取邊緣

呼叫此函數以檢索列印中使用的當前邊距。

```
CRect GetMargins() const;
```

### <a name="return-value"></a>傳回值

列印中使用的邊距,以MM_TWIPS為單位。

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a>克里希編輯檢視:取得頁面Rect

呼叫此函數以獲取列印中使用的頁面的尺寸。

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>傳回值

列印中使用的頁面邊界,以MM_TWIPS為單位。

### <a name="remarks"></a>備註

此值基於紙張大小。

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a>克里希編輯檢視:抓取紙張大小

調用此函數以檢索當前紙張大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>傳回值

印刷用的紙張大小,以MM_TWIPS為單位。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a>克里希編輯檢視:取得帕拉格式選擇

呼叫此函數獲取當前選擇的段落格式屬性。

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>傳回值

包含當前選擇的段落格式屬性的[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)結構。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) Windows SDK 中的消息和[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)結構。

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a>克里希編輯檢視:抓取列印重新

調用此函數以檢索頁面矩形內列印區域的邊界。

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>傳回值

列印中使用的圖像區域的邊界,以MM_TWIPS為單位進行測量。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a>克里希編輯檢視:取得列印寬度

調用此函數以確定列印區域的寬度。

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>傳回值

列印區域的寬度,以MM_TWIPS為單位。

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a>克里希編輯檢視:取得里希編輯Ctrl

調用此函數以檢索與`CRichEditView`該物件關聯的[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)物件。

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>傳回值

此`CRichEditCtrl`視圖的物件。

### <a name="example"></a>範例

  請參考[CRichEditView 的範例:尋找文字](#findtext)。

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a>克里希編輯檢視:取得選取的項目

呼叫此函數以檢索當前在此`CRichEditCntrItem``CRichEditView`物件中選擇的 OLE 項(物件)。

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>傳回值

指向在物件中選擇的[CRichEdit CntrItem](../../mfc/reference/cricheditcntritem-class.md)`CRichEditView`物件;如果在此檢視中未選擇任何專案,則為 NULL。

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a>克里希編輯檢視:抓取文字長度

呼叫此函數以檢索此`CRichEditView`物件中文本的長度。

```
long GetTextLength() const;
```

### <a name="return-value"></a>傳回值

此`CRichEditView`物件中的文字長度。

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a>克里希編輯檢視:取得文字長度Ex

呼叫此成員函數以計算此`CRichEditView`物件中文本的長度。

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
指定用於確定文本長度的方法的值。 此成員可以是 Windows SDK 中描述的[GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex)標誌成員中列出的一個或多個值。

*u代碼頁*<br/>
用於轉換的代碼頁(CP_ACP用於 ANSI 代碼頁,Unicode 為 1200)。

### <a name="return-value"></a>傳回值

編輯控制項中的字元或位元組數。 如果在*dwFlags*中設置了不相容標誌,則此成員函數將返回E_INVALIDARG。

### <a name="remarks"></a>備註

`GetTextLengthEx`提供了確定文本長度的其他方法。 它支援富編輯 2.0 功能。 有關詳細資訊,請參閱有關 Windows SDK 中的[豐富編輯控制件](/windows/win32/Controls/about-rich-edit-controls)。

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a>克里希編輯檢視::插入檔案物件

呼叫此函數以將指定的檔(作為[CRichEditCntrItem 物件](../../mfc/reference/cricheditcntritem-class.md))插入到豐富的編輯檢視中。

```cpp
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>參數

*lpszFile 名稱*<br/>
包含要插入的檔案的名稱的字串。

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a>克里希編輯檢視:插入項目

呼叫此函數以將[CRichEditCntrItem 物件](../../mfc/reference/cricheditcntritem-class.md)插入到富編輯檢視中。

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>參數

*pItem*<br/>
指向要插入的項的指標。

### <a name="return-value"></a>傳回值

指示插入成功的 HRESULT 值。

### <a name="remarks"></a>備註

有關 HRESULT 的詳細資訊,請參閱 Windows SDK 中的[COM 錯誤代碼結構](/windows/win32/com/structure-of-com-error-codes)。

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a>克里希編輯檢視::是裡希編輯格式

呼叫此函數以確定*cf*是帶有 OLE 項的文本、富文本或富文本的剪貼簿格式。

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
感興趣的剪貼簿格式。

### <a name="return-value"></a>傳回值

如果*cf*是豐富的編輯或文字剪貼簿格式,則非零。

## <a name="cricheditviewisselected"></a><a name="isselected"></a>克里希編輯檢視:已選定

呼叫此函數以確定目前是否在此檢視中選擇了指定的 OLE 項。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>參數

*pDocItem*<br/>
指向視圖中的物件。

### <a name="return-value"></a>傳回值

如果選擇物件,則非零;否則 0。

### <a name="remarks"></a>備註

如果派生檢視類具有處理 OLE 項選擇的不同方法,請重寫此函數。

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a>克里希編輯檢視:m_nBulletIndent

清單中項目符號項的縮進;默認情況下,720 個單位,即 1/2 英寸。

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a>克里希編輯檢視::m_nWordWrap

指示此富編輯視圖的換行類型。

```
int m_nWordWrap;
```

### <a name="remarks"></a>備註

下列其中一個值：

- `WrapNone`指示沒有自動換字。

- `WrapToWindow`指示基於窗口寬度的換行符。

- `WrapToTargetDevice`指示基於目標設備特徵的換字。

### <a name="example"></a>範例

  請參考[CRichEditView 的範例::換行](#wrapchanged)。

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a>克里希編輯檢視::在字元效果

呼叫此函數以切換當前選擇的字元格式效果。

```cpp
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>參數

*dwMask*<br/>
要在當前選擇中修改的字元格式效果。

*dwEffect*<br/>
要切換的字元格式效果所需的清單。

### <a name="remarks"></a>備註

對此函數的每個調用都會切換當前選擇的指定格式效果。

有關*dwMask*和*dwEffect*參數及其潛在值的詳細資訊,請參閱 Windows SDK 中的[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)的相應資料成員。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a>克里希編輯檢視::在查找下一個

在處理「查找/替換」對話方塊中的命令時,框架調用。

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

*b 下一個*<br/>
搜索方向:TRUE 向下指示;FALSE,向上。

*bCase*<br/>
指示搜索是否區分大小寫。

*bWord*<br/>
指示搜索是否僅匹配整個單詞。

### <a name="remarks"></a>備註

呼叫此函式以尋找中`CRichEditView`的文字。 重寫此函數可更改派生檢視類的搜索特徵。

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a>克里希編輯檢視:初始更新

視圖首次附加到文檔後由框架調用,但在最初顯示視圖之前。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>備註

此函數的預設實現調用[CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)成員函數,沒有提示資訊(即,使用*lHint*參數的預設值 0,對於*pHint*參數使用 NULL)。 重寫此函數以執行任何需要有關文件資訊的一次性初始化。 例如,如果應用程式具有固定大小的文件,則可以使用此函數根據文檔大小初始化檢視的滾動限制。 如果應用程式支援可變大小的文件,請使用`OnUpdate`在每次文檔更改時更新滾動限制。

### <a name="example"></a>範例

  請參閱[CRichEditView 範例::m_nWordWrap](#m_nwordwrap)。

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a>克里希編輯檢視::貼上本機物件

使用此函數從嵌入項載入本機數據。

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>參數

*lpStg*<br/>
指向[IStorage](/windows/win32/api/objidl/nn-objidl-istorage)物件的指標。

### <a name="return-value"></a>傳回值

如果成功,則非零;否則,0;

### <a name="remarks"></a>備註

通常,您可以通過在中建立[COleStreamFile](../../mfc/reference/colestreamfile-class.md)來`IStorage`執行此動作 。 `COleStreamFile`可以附加到存檔和[CObject::序列化](../../mfc/reference/cobject-class.md#serialize)調用以載入資料。

這是一個高級的可重寫。

有關詳細資訊,請參閱 Windows SDK 中的[IStorage。](/windows/win32/api/objidl/nn-objidl-istorage)

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a>克里希編輯視圖:在帕拉維萊

調用此函數以更改所選段落的段落對齊方式。

```cpp
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>參數

*w對齊*<br/>
所需的段落對齊方式。 下列其中一個值：

- PFA_LEFT 將段落與左邊距對齊。

- PFA_RIGHT 將段落與右邊距對齊。

- PFA_CENTER 將段落居中邊緣。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a>克里希編輯檢視:開啟印表機已變更

覆蓋此功能以在印表機更改時更改此富編輯視圖的特徵。

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>參數

*直流印表機*<br/>
新印表機的[CDC](../../mfc/reference/cdc-class.md)物件。

### <a name="remarks"></a>備註

預設實現將紙張大小設置為輸出設備(印表機)的物理高度和寬度。 如果沒有與*dcPrinter*關聯的設備上下文,則默認實現將紙張大小設置為 8.5 x 11 英寸。

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a>克里希編輯檢視::全部取代

在處理「替換」對話框中替換所有命令時,框架調用該命令。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
要替換的文本。

*lpsz取代*<br/>
替換文字。

*bCase*<br/>
指示搜索是否區分大小寫。

*bWord*<br/>
指示搜索是否必須選擇整個單詞。

### <a name="remarks"></a>備註

呼叫此函數以將某些給定文本的所有匹配項替換為另一個字串。 重寫此函數以更改此檢視的搜索特徵。

### <a name="example"></a>範例

  請參考[CRichEditView 的範例:尋找文字](#findtext)。

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a>克里希編輯檢視:開啟取代塞爾

在處理「替換」對話方塊中的替換命令時,框架呼叫。

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
要替換的文本。

*b 下一個*<br/>
指示搜索的方向:TRUE 已關閉;FALSE,向上。

*bCase*<br/>
指示搜索是否區分大小寫。

*bWord*<br/>
指示搜索是否必須選擇整個單詞。

*lpsz取代*<br/>
替換文字。

### <a name="remarks"></a>備註

呼叫此函數以將某些給定文本的一個匹配項替換為另一個字串。 重寫此函數以更改此檢視的搜索特徵。

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a>克里希編輯檢視::未找到文字

每當搜索失敗時,由框架調用。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
找不到的文字。

### <a name="remarks"></a>備註

重寫此函數以更改[來自消息蜂比的](/windows/win32/api/winuser/nf-winuser-messagebeep)輸出通知。

有關詳細資訊,請參閱 Windows SDK 中的[MessageBeep。](/windows/win32/api/winuser/nf-winuser-messagebeep)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a>克里希編輯檢視:上更新字元效果

框架呼叫此函數以更新字元效果命令的命令 UI。

```cpp
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標。

*dwMask*<br/>
指示字元格式蒙版。

*dwEffect*<br/>
指示字元格式效果。

### <a name="remarks"></a>備註

遮*罩 dwMask*指定要檢查的字元格式屬性。 標誌*dwEffect*列出要設定/清除的字元格式屬性。

有關*dwMask*和*dwEffect*參數及其潛在值的詳細資訊,請參閱 Windows SDK 中的[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)的相應資料成員。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a>克里希編輯檢視:更新帕拉對齊

框架呼叫此函數以更新段落效果命令的命令 UI。

```cpp
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>參數

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)物件的指標。

*w對齊*<br/>
要檢查的段落對齊方式。 下列其中一個值：

- PFA_LEFT 將段落與左邊距對齊。

- PFA_RIGHT 將段落與右邊距對齊。

- PFA_CENTER 將段落居中邊緣。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a>克里希編輯視圖::P林特內卡雷茨

呼叫此函數以在豐富的編輯控制項中格式化文本範圍,以適應*pDC*指定的設備的*rectLayout。*

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
指向輸出區域的設備上下文。

*重新佈局*<br/>
定義輸出區域的[RECT](/windows/win32/api/windef/ns-windef-rect)或[CRect。](../../atl-mfc-shared/reference/crect-class.md)

*nIndex 開始*<br/>
要格式化的第一個字元的基於零的索引。

*nIndexStop*<br/>
要格式化的最後一個字元的零基索引。

*b輸出*<br/>
指示是否應呈現文本。 如果 FALSE,則僅測量文本。

### <a name="return-value"></a>傳回值

最後一個字元的索引,適合輸出區域加上1。

### <a name="remarks"></a>備註

通常,此調用之後是調用生成輸出的[CRichEditCtrl::DisplayBand。](../../mfc/reference/cricheditctrl-class.md#displayband)

### <a name="example"></a>範例

  請參考[CRichEditView 的範例:取得紙張大小](#getpapersize)。

## <a name="cricheditviewprintpage"></a><a name="printpage"></a>克里希編輯檢視::PrintPage

呼叫此函數,在*pDC*指定的輸出設備的富編輯控制件中格式化文本範圍。

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向設備上下文以進行頁面輸出。

*nIndex 開始*<br/>
要格式化的第一個字元的基於零的索引。

*nIndexStop*<br/>
要格式化的最後一個字元的零基索引。

### <a name="return-value"></a>傳回值

上一個字元的索引,位於頁面上,外加一個字元。

### <a name="remarks"></a>備註

每個頁面的佈局由[GetPageRect](#getpagerect)和[GetPrintRect](#getprintrect)控制。 通常,此調用之後是調用生成輸出的[CRichEditCtrl::DisplayBand。](../../mfc/reference/cricheditctrl-class.md#displayband)

請注意,邊距相對於物理頁,而不是邏輯頁。 因此,零邊距通常會剪輯文本,因為許多印表機在頁面上具有不可列印的區域。 為了避免剪切文本,應在列印之前調用[SetMargins](#setmargins)並設置合理的邊距。

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a>克里希編輯檢視::查詢接受數據

由框架調用,將物件粘貼到富編輯中。

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
指向要查詢的[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)的指標。

*lpcf格式*<br/>
指向可接受的數據格式的指標。

*德德雷科*<br/>
未使用。

*b真的*<br/>
指示粘貼操作是否應繼續。

*hMetaFile*<br/>
用於繪製專案圖示的元檔的句柄。

### <a name="return-value"></a>傳回值

報告操作成功的 HRESULT 值。

### <a name="remarks"></a>備註

重寫此函數以處理派生文檔類中不同的 COM 項組織。 這是一個高級的可重寫。

有關 HRESULT`IDataObject`和的詳細資訊,請參閱在 Windows SDK 中分別看到 COM[錯誤代碼](/windows/win32/com/structure-of-com-error-codes)和[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)的結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a>克里希編輯檢視:設定字元格式

呼叫此函數可為此`CRichEditView`物件中的新文字設置字元格式屬性。

```cpp
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>參數

*cf*<br/>
包含新的預設字元格式屬性的[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)結構。

### <a name="remarks"></a>備註

只有`dwMask`*cf*成員指定的屬性由此函數更改。

有關詳細資訊,請參閱[EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) Windows SDK 中的消息和[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a>克里希編輯檢視::設定邊距

呼叫此函數可設定此富編輯檢視的列印邊距。

```cpp
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>參數

*rectMargin*<br/>
列印的新邊距值,以MM_TWIPS為單位。

### <a name="remarks"></a>備註

如果[m_nWordWrap](#m_nwordwrap)m_nWordWrap`WrapToTargetDevice`為 ,則應在使用此函數調整列印特徵後調用[Wrap"更改](#wrapchanged)"。

請注意[,PrintPage](#printpage)使用的邊距與物理頁無關,而不是邏輯頁。 因此,零邊距通常會剪輯文本,因為許多印表機在頁面上具有不可列印的區域。 為了避免剪切文本,應在列印之前調用`SetMargins`使用 設置合理的印表機邊距。

### <a name="example"></a>範例

  請參考[CRichEditView 的範例:取得紙張大小](#getpapersize)。

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a>克里希編輯檢視::設定紙張大小

呼叫此函數以設置紙張大小以列印此豐富的編輯檢視。

```cpp
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>參數

*大小紙*<br/>
列印的新紙張大小值,以MM_TWIPS為單位。

### <a name="remarks"></a>備註

如果[m_nWordWrap](#m_nwordwrap)m_nWordWrap`WrapToTargetDevice`為 ,則應在使用此函數調整列印特徵後調用[Wrap"更改](#wrapchanged)"。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a>克里希編輯檢視::設定帕拉格式

呼叫此函數可為此`CRichEditView`物件中的當前選擇設置段落格式屬性。

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>參數

*普夫*<br/>
包含新的預設段落格式屬性的[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)結構。

### <a name="return-value"></a>傳回值

如果成功,則非零;否則,0。

### <a name="remarks"></a>備註

只有`dwMask`*pf*成員指定的屬性由此函數更改。

有關詳細資訊,請參閱[EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) Windows SDK 中的消息和[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)結構。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a>克里希編輯檢視::未找到文字

呼叫此函數以重置對[FindText](#findtext)的呼叫失敗後[CRichEditView](../../mfc/reference/cricheditview-class.md)控件的內部搜尋狀態。

```cpp
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>參數

*lpszFind*<br/>
包含未找到的文字字串。

### <a name="remarks"></a>備註

建議在調用[FindText](#findtext)失敗後立即調用此方法,以便正確重置控制件的內部搜尋狀態。

*lpszFind*參數應包含與提供給[FindText](#findtext)的字串相同的內容。 重置內部搜尋狀態後,此方法將使用提供的搜索字串調用[OnTextNotFound](#ontextnotfound)方法。

### <a name="example"></a>範例

  請參考[CRichEditView 的範例:尋找文字](#findtext)。

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a>克里希編輯檢視:包裝

當列印特徵發生更改時調用此功能([設定邊距](#setmargins)或[SetPaperSize)。](#setpapersize)

```
virtual void WrapChanged();
```

### <a name="remarks"></a>備註

重寫此函數以修改富編輯檢視回應[m_nWordWrap](#m_nwordwrap)或列印特徵[(OnPrinterEdit)](#onprinterchanged)更改的方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 類別](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem 類別](../../mfc/reference/cricheditcntritem-class.md)
