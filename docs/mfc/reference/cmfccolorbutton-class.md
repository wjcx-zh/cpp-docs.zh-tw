---
title: CMFCColorButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: ac49957f075f8798607535286d6c4518c0eeeeae
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505367"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 類別

和 [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)會一起用來執行色彩選擇器控制項。`CMFCColorButton`

## <a name="syntax"></a>語法

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|建立新`CMFCColorButton`的物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|啟用和停用位於一般色彩按鈕上方的 [自動] 按鈕。 （標準系統 [自動] 按鈕會標示為 [**自動**]）。|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|啟用和停用位於一般色彩按鈕底下的 [其他] 按鈕。 （標準系統的 [其他] 按鈕會標示為 [**更多色彩**]）。|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|抓取目前的自動色彩。|
|[CMFCColorButton::GetColor](#getcolor)|抓取按鈕的色彩。|
|[CMFCColorButton::SetColor](#setcolor)|設定按鈕的色彩。|
|[CMFCColorButton::SetColorName](#setcolorname)|設定色彩名稱。|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|設定 [色彩選擇器] 對話方塊上的資料行數目。|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|指定顯示在 [色彩選擇器] 對話方塊上的檔特定色彩清單。|
|[CMFCColorButton::SetPalette](#setpalette)|指定標準顯示色彩的調色板。|
|[CMFCColorButton::SizeToContent](#sizetocontent)|變更按鈕控制項的大小，視其文字和影像大小而定。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|指出目前的色彩按鈕是否會以 Windows XP 的視覺化樣式顯示。|
|[CMFCColorButton::OnDraw](#ondraw)|由架構呼叫以顯示按鈕的影像。|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|由架構呼叫以顯示按鈕的框線。|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|由架構呼叫，以在按鈕具有焦點時顯示焦點矩形。|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|當 [色彩選擇器] 對話方塊即將顯示時由架構呼叫。|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|將受`m_pPalette`保護的資料成員初始化為指定的調色板或預設的系統調色板。|
|[CMFCColorButton::UpdateColor](#updatecolor)|當使用者從 [色彩選擇器] 對話方塊的 [調色板] 選取色彩時，由架構呼叫。|

### <a name="data-members"></a>資料成員

|名稱|說明|
|----------|-----------------|
|`m_bAltColorDlg`|布林值。 若為 TRUE，則當您按一下 [*其他*] 按鈕時，架構會顯示 [ [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)色彩] 對話方塊，如果 [系統色彩] 對話方塊為 FALSE，則為 FALSE。 預設值為 TRUE。 如需詳細資訊，請參閱[CMFCColorButton：： EnableOtherButton](#enableotherbutton)。|
|`m_bAutoSetFocus`|布林值。 若為 TRUE，則當顯示功能表時，架構會將焦點設定在 [色彩] 功能表上，如果為 [FALSE]，則不會變更焦點。 預設值為 TRUE。|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指出是否已啟用色彩按鈕的自訂模式。|
|`m_Color`|[COLORREF](/windows/win32/gdi/colorref)值。 包含目前選取的色彩。|
|`m_ColorAutomatic`|[COLORREF](/windows/win32/gdi/colorref)值。 包含目前選取的預設色彩。|
|`m_Colors`|[COLORREF](/windows/win32/gdi/colorref)值的[CArray](../../mfc/reference/carray-class.md) 。 包含目前可用的色彩。|
|`m_lstDocColors`|[COLORREF](/windows/win32/gdi/colorref)值的[CList](../../mfc/reference/clist-class.md) 。 包含目前的檔色彩。|
|`m_nColumns`|整數。 包含要在色彩選擇功能表的色彩方格中顯示的資料行數目。|
|`m_pPalette`|指向[CPalette](../../mfc/reference/cpalette-class.md)的指標。 包含 [目前色彩選擇] 功能表中可用的色彩。|
|`m_pPopup`|[CMFCColorPopupMenu 類別](../../mfc/reference/cmfccolorpopupmenu-class.md)物件的指標。 當您按一下 [色彩] 按鈕時，所顯示的色彩選擇功能表。|
|`m_strAutoColorText`|字串。 色彩選取功能表中 [自動] 按鈕的標籤。|
|`m_strDocColorsText`|字串。 色彩選取功能表中顯示檔色彩的按鈕標籤。|
|`m_strOtherText`|字串。 色彩選取功能表中 [其他] 按鈕的標籤。|

## <a name="remarks"></a>備註

根據預設， `CMFCColorButton`類別的行為會是開啟 [色彩選擇器] 對話方塊的 [按下] 按鈕。 [色彩選擇器] 對話方塊包含一個小色彩按鈕的陣列，以及一個顯示自訂色彩選擇器的 [其他] 按鈕。 （標準系統的 [其他] 按鈕會標示為 [**更多色彩**]）。當使用者選取新的色彩時， `CMFCColorButton`物件會反映該變更，並顯示選取的色彩。

直接在您的程式碼中建立色彩按鈕控制項，或使用**ClassWizard**工具和對話方塊範本。 如果您直接建立色彩按鈕控制項，請將`CMFCColorButton`變數加入至您的應用程式，然後呼叫`CMFCColorButton`物件的`Create`函式和方法。 如果您使用**ClassWizard**，請將`CButton`變數新增至您的應用程式，然後將變數的類型從`CButton`變更為`CMFCColorButton`。

當`OnLButtonDown`架構呼叫事件處理常式時， [CMFCColorButton：： OnShowColorPopup](#onshowcolorpopup)方法會顯示 [色彩選擇器] 對話方塊（ [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)）。 您可以覆寫[CMFCColorButton：： OnShowColorPopup](#onshowcolorpopup)方法，以支援自訂色彩選取專案。

`CMFCColorButton`物件會藉由傳送 WM_COMMAND 來通知其父系，其色彩會變更 |BN_CLICKED 通知。 父系使用[CMFCColorButton：： GetColor](#getcolor)方法來取得目前的色彩。

## <a name="example"></a>範例

下列範例示範如何使用`CMFCColorButton`類別中的各種方法來設定色彩按鈕。 方法會設定色彩按鈕和其資料行數目的色彩，並啟用 [自動] 和 [其他] 按鈕。 這個範例是[狀態列示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>需求

**標頭：** afxcolorbutton。h

##  <a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton

建立新`CMFCColorButton`的物件。

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton

啟用或停用色彩選擇器控制項的 [自動] 按鈕，並設定自動（預設）色彩。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
在指定自動按鈕的文字。

*colorAutomatic*<br/>
在RGB 值，指定自動按鈕的預設色彩。

*bEnable*<br/>
在指定是否要啟用或停用 [自動] 按鈕。

### <a name="remarks"></a>備註

##  <a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton

啟用或停用 [其他] 按鈕，這會出現在一般色彩按鈕底下。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
在指定按鈕的文字。

*bAltColorDlg*<br/>
在指定當使用者按一下按鈕時，是否要開啟 [ [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ] 對話方塊或 [系統色彩] 對話方塊。

*bEnable*<br/>
在指定是否啟用或停用 [其他] 按鈕。

### <a name="remarks"></a>備註

按一下 [其他] 按鈕以顯示 [色彩] 對話方塊。 如果*bAltColorDlg*參數為 TRUE，則會顯示[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md);否則，會顯示 [系統色彩] 對話方塊。

##  <a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor

抓取目前的自動（預設）色彩。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>傳回值

代表目前自動色彩的 RGB 值。

### <a name="remarks"></a>備註

目前的自動色彩是由[CMFCColorButton：： EnableAutomaticButton](#enableautomaticbutton)方法所設定。

##  <a name="getcolor"></a>CMFCColorButton：： GetColor

抓取目前選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

RGB 值。

### <a name="remarks"></a>備註

##  <a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme

指出目前的色彩按鈕是否會以 Windows XP 的視覺化樣式顯示。

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>傳回值

如果支援視覺化樣式，而且目前的色彩按鈕是以 Windows XP 的視覺化樣式顯示，則為 TRUE;否則為 FALSE。

##  <a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode

將色彩按鈕設定為自訂模式。

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>備註

如果您需要將色彩按鈕加入至自訂對話方塊的頁面（或允許使用者在自訂期間選取另一個色彩），請將`m_bEnabledInCustomizeMode`成員設定為 TRUE 來啟用按鈕。 根據預設，這個成員會設定為 FALSE。

##  <a name="ondraw"></a>CMFCColorButton：： OnDraw

由架構呼叫以呈現按鈕的影像。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在指向用來呈現按鈕影像的裝置內容。

*rect*<br/>
在矩形，其為按鈕的界限。

*uiState*<br/>
在指定按鈕的視覺狀態。

### <a name="remarks"></a>備註

覆寫這個方法以自訂轉譯進程。

##  <a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder

由架構呼叫以顯示按鈕的框線。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在指向用來繪製框線的裝置內容。

*rectClient*<br/>
在裝置內容中的矩形，由*pDC*參數所指定，可定義要繪製之按鈕的界限。

*uiState*<br/>
在指定按鈕的視覺狀態。

### <a name="remarks"></a>備註

覆寫此函式以自訂色彩按鈕的框線外觀。

##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect

由架構呼叫，以在按鈕具有焦點時顯示焦點矩形。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在指向用來繪製焦點矩形的裝置內容。

*rectClient*<br/>
在*PDC*參數所指定之裝置內容中的矩形，可定義按鈕的界限。

### <a name="remarks"></a>備註

覆寫這個方法，以自訂焦點矩形的外觀。

##  <a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup

在快顯視窗色軸顯示之前呼叫。

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>備註

##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette

將受`m_pPalette`保護的資料成員初始化為指定的調色板或預設的系統調色板。

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pPal*|在邏輯調色板的指標或 Null。 如果是 Null，則會使用預設的系統調色板。|

##  <a name="setcolor"></a>CMFCColorButton：： SetColor

指定按鈕的色彩。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
在RGB 值。

### <a name="remarks"></a>備註

##  <a name="setcolorname"></a>CMFCColorButton::SetColorName

指定色彩的名稱。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*color*<br/>
在色彩的 RGB 值。

*strName*<br/>
在色彩的名稱。

### <a name="remarks"></a>備註

每個應用程式的色彩名稱清單是全域的。 因此，此方法會將其參數傳送至[CMFCColorBar：： SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。

##  <a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber

定義在使用者的色彩選擇程式期間，顯示于使用者的色彩表中的資料行數目。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>參數

*nColumns*<br/>
在指定資料行的數目。

### <a name="remarks"></a>備註

使用者可以從顯示預先定義色彩資料表的快顯色軸中選取色彩。 使用這個方法可定義資料表中的資料行數目。

##  <a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors

指定一組色彩和集合的名稱。 色彩集合會使用[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件來顯示。

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
在指定要與檔色彩集一起顯示的標籤。

*lstColors*<br/>
在RGB 值清單的參考。

### <a name="remarks"></a>備註

物件會維護傳送至[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件的 RGB 值清單。 `CMFCColorButton` 當色軸顯示時，這些色彩會顯示在*lpszLabel*參數指定其標籤的特殊區段中。

##  <a name="setpalette"></a>CMFCColorButton::SetPalette

指定要在快顯視窗色軸上顯示的標準色彩。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>參數

*pPalette*<br/>
在色板的指標。

### <a name="remarks"></a>備註

##  <a name="sizetocontent"></a>CMFCColorButton：： System.windows.window.sizetocontent

調整按鈕控制項的大小，以符合其文字和影像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
在如果是非零值，則會計算按鈕控制項的新大小，但不會變更實際大小。

### <a name="return-value"></a>傳回值

指定新按鈕控制項大小的物件。`CSize`

### <a name="remarks"></a>備註

##  <a name="updatecolor"></a>CMFCColorButton::UpdateColor

當使用者在使用者按一下色彩按鈕時，從顯示的色軸選取色彩時，由架構呼叫。

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
在使用者選取的色彩。

### <a name="remarks"></a>備註

`UpdateColor`函式會變更目前選取的按鈕色彩，並傳送具有 BN_CLICKED 標準通知的 WM_COMMAND 訊息來通知其父系。 使用[CMFCColorButton：： GetColor](#getcolor)方法來取出選取的色彩。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette 類別](../../mfc/reference/cpalette-class.md)<br/>
[CArray 類別](../../mfc/reference/carray-class.md)<br/>
[CList 類別](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
