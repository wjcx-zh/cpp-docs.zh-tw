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
ms.openlocfilehash: c0c9ad79342f2013aa071240c684fce168e55c9e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58779998"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 類別

`CMFCColorButton`並[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)類別會一起用來實作色彩選擇器控制項。

## <a name="syntax"></a>語法

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|建構新`CMFCColorButton`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|啟用和停用位於標準色彩按鈕上方的 「 自動 」 按鈕。 (標準系統自動按鈕會標示**自動**。)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|啟用和停用 「 其他 」 位於標準色彩按鈕下方的按鈕。 (標準的系統標示為 「 其他 」 按鈕**更多色彩**。)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|擷取目前的自動色彩。|
|[CMFCColorButton::GetColor](#getcolor)|擷取按鈕的色彩。|
|[CMFCColorButton::SetColor](#setcolor)|設定按鈕的色彩。|
|[CMFCColorButton::SetColorName](#setcolorname)|設定色彩的名稱。|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|在色彩選擇器對話方塊中設定資料行的數目。|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|指定會顯示在 [色彩選擇器] 對話方塊的特定文件色彩的清單。|
|[CMFCColorButton::SetPalette](#setpalette)|指定標準顯示色的調色盤。|
|[CMFCColorButton::SizeToContent](#sizetocontent)|變更大小的按鈕控制項，其文字和影像的大小而定。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|指出是否要將目前的 [色彩] 按鈕顯示在 Windows XP 視覺化樣式。|
|[CMFCColorButton::OnDraw](#ondraw)|由架構呼叫以顯示按鈕的影像。|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|由架構呼叫以顯示按鈕的框線。|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|由架構呼叫以顯示焦點矩形的按鈕具有焦點時。|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|顯示色彩選擇器對話方塊時，由架構呼叫。|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|初始化`m_pPalette`受保護的資料成員，才能指定的調色盤或預設系統調色盤。|
|[CMFCColorButton::UpdateColor](#updatecolor)|當使用者從色彩選擇器對話方塊中的調色盤選取色彩時由架構呼叫。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|`m_bAltColorDlg`|布林值。 如果為 TRUE，架構會顯示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)色彩對話方塊的 [當*其他*按一下按鈕時，或如果為 FALSE，系統色彩] 對話方塊。 預設值為 TRUE。 如需詳細資訊，請參閱 < [CMFCColorButton::EnableOtherButton](#enableotherbutton)。|
|`m_bAutoSetFocus`|布林值。 如果為 TRUE，framework 將焦點設定 [色彩] 功能表上的功能表顯示時，或如果為 FALSE，不會變更焦點時。 預設值為 TRUE。|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指出是否啟用 [色彩] 按鈕的自訂模式。|
|`m_Color`|A [COLORREF](/windows/desktop/gdi/colorref)值。 包含目前選取的色彩。|
|`m_ColorAutomatic`|A [COLORREF](/windows/desktop/gdi/colorref)值。 包含目前選取的預設色彩。|
|`m_Colors`|A [CArray](../../mfc/reference/carray-class.md)的[COLORREF](/windows/desktop/gdi/colorref)值。 包含目前可用的色彩。|
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md)的[COLORREF](/windows/desktop/gdi/colorref)值。 包含目前的文件色彩。|
|`m_nColumns`|整數。 包含資料行，顯示在方格中色彩選取範圍 功能表中的色彩數目。|
|`m_pPalette`|指標[CPalette](../../mfc/reference/cpalette-class.md)。 包含目前的色彩選取範圍 功能表中可用的色彩。|
|`m_pPopup`|指標[CMFCColorPopupMenu 類別](../../mfc/reference/cmfccolorpopupmenu-class.md)物件。 當您按一下色彩按鈕會顯示 [色彩選取範圍] 功能表。|
|`m_strAutoColorText`|字串。 「 自動 」 中色彩選取範圍 功能表按鈕的標籤。|
|`m_strDocColorsText`|字串。 中會顯示文件色彩的色彩選取範圍 功能表按鈕的標籤。|
|`m_strOtherText`|字串。 色彩選取範圍 功能表中的 「 其他 」 按鈕的標籤。|

## <a name="remarks"></a>備註

根據預設，`CMFCColorButton`類別的行為就像開啟色彩選擇器對話方塊按鈕。 [色彩選擇器] 對話方塊包含小型色彩按鈕和 「 其他 」 按鈕，以顯示自訂色彩選擇器的陣列。 (標準的系統標示為 「 其他 」 按鈕**更多色彩**。)當使用者選取新的色彩，`CMFCColorButton`物件會反映變更，並顯示所選取的色彩。

在您的程式碼中直接或透過建立色彩的按鈕控制項**ClassWizard**工具和對話方塊範本。 如果您直接建立色彩的按鈕控制項，將`CMFCColorButton`到您的應用程式，然後呼叫建構函式的變數和`Create`方法`CMFCColorButton`物件。 如果您使用**ClassWizard**，新增`CButton`變數設為您的應用程式，然後變更 來自變數的型別`CButton`到`CMFCColorButton`。

色彩選擇器對話方塊 ( [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)) 會顯示[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)方法時，架構會呼叫`OnLButtonDown`事件處理常式。 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)可以覆寫方法，以支援自訂色彩選取範圍。

`CMFCColorButton`物件通知其色彩會變更傳送 WM_COMMAND 的父代 |BN_CLICKED 通知。 父系會使用[CMFCColorButton::GetColor](#getcolor)方法來擷取目前的色彩。

## <a name="example"></a>範例

下列範例示範如何使用中的各種方法來設定色彩按鈕`CMFCColorButton`類別。 方法會設定色彩的色彩按鈕和資料行，其數目，並啟用自動 和 其他 按鈕。 此範例中是屬於[狀態列示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>需求

**標頭：** afxcolorbutton.h

##  <a name="cmfccolorbutton"></a>  CMFCColorButton::CMFCColorButton

建構新`CMFCColorButton`物件。

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton

啟用或停用 「 自動 」 按鈕的色彩選擇器控制項並設定自動 （預設） 色彩。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in]指定自動按鈕的文字。

*colorAutomatic*<br/>
[in]指定自動按鈕的預設色彩的 RGB 值。

*bEnable*<br/>
[in]指定自動按鈕是否要啟用或停用。

### <a name="remarks"></a>備註

##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton

啟用或停用 [其他] 按鈕時，即會出現標準色彩按鈕下方。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in]指定按鈕的文字。

*bAltColorDlg*<br/>
[in]指定是否[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)使用者按一下按鈕時，則會開啟對話方塊或系統的 [色彩] 對話方塊。

*bEnable*<br/>
[in]指定是否啟用或停用 「 其他 」 按鈕。

### <a name="remarks"></a>備註

按一下 [其他] 按鈕以顯示 [色彩] 對話方塊。 如果*bAltColorDlg*參數為 TRUE 時， [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)會顯示，否則會顯示系統的 [色彩] 對話方塊。

##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor

擷取目前的自動 （預設） 色彩。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>傳回值

表示目前的自動色彩的 RGB 值。

### <a name="remarks"></a>備註

設定目前的自動色彩[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)方法。

##  <a name="getcolor"></a>  CMFCColorButton::GetColor

擷取目前選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

RGB 值。

### <a name="remarks"></a>備註

##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme

指出是否要將目前的 [色彩] 按鈕顯示在 Windows XP 視覺化樣式。

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>傳回值

如果支援視覺化樣式，而目前的色彩按鈕會顯示在 Windows XP; 的視覺化樣式，則為 TRUE。否則為 FALSE。

##  <a name="m_benabledincustomizemode"></a>  CMFCColorButton::m_bEnabledInCustomizeMode

將色彩按鈕，設定自訂模式。

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>備註

如果您要將色彩按鈕新增至自訂對話方塊的頁面 （或允許使用者進行另一個色彩選取範圍，在自訂期間），藉由設定啟用按鈕`m_bEnabledInCustomizeMode`成員設為 TRUE。 根據預設，這個成員設定為 FALSE。

##  <a name="ondraw"></a>  CMFCColorButton::OnDraw

由架構呼叫以呈現按鈕的影像。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]用來呈現按鈕的影像之裝置內容的點。

*rect*<br/>
[in]之按鈕的界限的矩形。

*uiState*<br/>
[in]指定按鈕的可見狀態。

### <a name="remarks"></a>備註

覆寫這個方法來自訂轉譯程序。

##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder

由架構呼叫以顯示按鈕的框線。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]用來繪製框線的裝置內容指標。

*rectClient*<br/>
[in]在裝置內容所指定的矩形*pDC*參數，定義要繪製按鈕的界限。

*uiState*<br/>
[in]指定按鈕的可見狀態。

### <a name="remarks"></a>備註

覆寫此函式以自訂 [色彩] 按鈕的框線外觀。

##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect

由架構呼叫以顯示焦點矩形的按鈕具有焦點時。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]用來繪製焦點矩形的裝置內容指標。

*rectClient*<br/>
[in]所指定的裝置內容中的矩形*pDC*參數，定義按鈕的界限。

### <a name="remarks"></a>備註

覆寫這個方法以自訂的焦點矩形的外觀。

##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup

在快顯色彩列會顯示之前呼叫。

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>備註

##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette

初始化`m_pPalette`受保護的資料成員，才能指定的調色盤或預設系統調色盤。

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pPal*|[in]邏輯調色盤或 NULL 指標。 如果是 NULL，則會使用預設系統調色盤。|

##  <a name="setcolor"></a>  CMFCColorButton::SetColor

指定按鈕的色彩。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
[in]RGB 值。

### <a name="remarks"></a>備註

##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName

指定色彩的名稱。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*color*<br/>
[in]此色彩的 RGB 值。

*strName*<br/>
[in]色彩的名稱。

### <a name="remarks"></a>備註

色彩名稱清單為每個應用程式的全域項目。 因此，這個方法會傳送至其參數[CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。

##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber

定義會顯示使用者的色彩選取程序期間呈現給使用者的色彩表中的資料行數目。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>參數

*nColumns*<br/>
[in]指定資料行的數目。

### <a name="remarks"></a>備註

使用者可以從快顯色彩列，顯示預先定義之色彩的資料表中選取色彩。 您可以使用這個方法，在資料表中定義的資料行數目。

##  <a name="setdocumentcolors"></a>  CMFCColorButton::SetDocumentColors

指定一組色彩和集的名稱。 使用顯示色彩[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件。

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in]指定要使用的文件色彩來顯示標籤。

*lstColors*<br/>
[in]參考的 RGB 值清單。

### <a name="remarks"></a>備註

A`CMFCColorButton`物件會維護一份 RGB 值傳送至[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件。 這些色彩色軸顯示時，會顯示其標籤由所指定的特殊區段*lpszLabel*參數。

##  <a name="setpalette"></a>  CMFCColorButton::SetPalette

指定要顯示在快顯色彩列上的標準色彩。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>參數

*pPalette*<br/>
[in]色彩調色盤指標。

### <a name="remarks"></a>備註

##  <a name="sizetocontent"></a>  CMFCColorButton::SizeToContent

調整大小以符合其文字和影像的按鈕控制項。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
[in]如果是非零值，會計算新的按鈕控制項的大小，但不是會變更的實際大小。

### <a name="return-value"></a>傳回值

A`CSize`物件，指定新的按鈕控制項大小。

### <a name="remarks"></a>備註

##  <a name="updatecolor"></a>  CMFCColorButton::UpdateColor

當使用者從色彩列，其中顯示當使用者按一下色彩按鈕中選取某種顏色時，由架構呼叫。

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
[in]使用者所選取之色彩。

### <a name="remarks"></a>備註

`UpdateColor`函式會變更目前選取之按鈕的色彩，並傳送 WM_COMMAND 訊息 BN_CLICKED 標準通知會告知其父代。 使用[CMFCColorButton::GetColor](#getcolor)方法來擷取選取的色彩。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/desktop/gdi/colorref)<br/>
[CPalette 類別](../../mfc/reference/cpalette-class.md)<br/>
[CArray 類別](../../mfc/reference/carray-class.md)<br/>
[CList 類別](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
