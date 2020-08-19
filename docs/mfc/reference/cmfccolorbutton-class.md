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
ms.openlocfilehash: 7abe37969799d7fcd78d525a5ec1c6faa9d876ee
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560994"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 類別

`CMFCColorButton`和[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)類別會一起用來執行色彩選擇器控制項。

## <a name="syntax"></a>語法

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|建構新的 `CMFCColorButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|啟用並停用位於一般色彩按鈕上方的 [自動] 按鈕。  (標準系統自動按鈕會標示為 [ **自動**]。 ) |
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|啟用並停用位於一般色彩按鈕下方的 [其他] 按鈕。  (標準系統的 [其他] 按鈕標示為 [ **更多色彩**]。 ) |
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|抓取目前的自動色彩。|
|[CMFCColorButton::GetColor](#getcolor)|抓取按鈕的色彩。|
|[CMFCColorButton：： SetColor](#setcolor)|設定按鈕的色彩。|
|[CMFCColorButton::SetColorName](#setcolorname)|設定色彩名稱。|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|設定 [色彩選擇器] 對話方塊上的資料行數目。|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|指定要顯示在 [色彩選擇器] 對話方塊上的檔特定色彩清單。|
|[CMFCColorButton::SetPalette](#setpalette)|指定標準顯示色彩的調色板。|
|[CMFCColorButton：： System.windows.window.sizetocontent](#sizetocontent)|變更按鈕控制項的大小，視其文字和影像大小而定。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|指出目前的色彩按鈕是否以 Windows XP 的視覺化樣式顯示。|
|[CMFCColorButton：： OnDraw](#ondraw)|由架構呼叫以顯示按鈕的影像。|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|由架構呼叫以顯示按鈕的框線。|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|由架構呼叫，以在按鈕具有焦點時顯示焦點矩形。|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|在 [色彩選擇器] 對話方塊即將顯示時由架構呼叫。|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|將 `m_pPalette` 受保護的資料成員初始化為指定的調色板或預設的系統調色板。|
|[CMFCColorButton::UpdateColor](#updatecolor)|當使用者從 [色彩選擇器] 對話方塊的 [調色板] 選取色彩時，由架構呼叫。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|`m_bAltColorDlg`|布林值。 若為 TRUE，則當按一下 [*其他*] 按鈕時，架構會顯示 [ [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)色彩] 對話方塊，若為 FALSE，則會顯示 [系統色彩] 對話方塊。 預設值為 TRUE。 如需詳細資訊，請參閱 [CMFCColorButton：： EnableOtherButton](#enableotherbutton)。|
|`m_bAutoSetFocus`|布林值。 若為 TRUE，當顯示功能表時，架構會將焦點設定在 [色彩] 功能表上，如果為 FALSE，則不會變更焦點。 預設值為 TRUE。|
|[CMFCColorButton：： m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指出是否啟用 [色彩] 按鈕的自訂模式。|
|`m_Color`|[COLORREF](/windows/win32/gdi/colorref)值。 包含目前選取的色彩。|
|`m_ColorAutomatic`|[COLORREF](/windows/win32/gdi/colorref)值。 包含目前選取的預設色彩。|
|`m_Colors`|[COLORREF](/windows/win32/gdi/colorref)值的[CArray](../../mfc/reference/carray-class.md) 。 包含目前可用的色彩。|
|`m_lstDocColors`|[COLORREF](/windows/win32/gdi/colorref)值的[CList](../../mfc/reference/clist-class.md) 。 包含目前的檔色彩。|
|`m_nColumns`|整數。 包含要在色彩選取功能表中的色彩格線中顯示的資料行數目。|
|`m_pPalette`|指向 [CPalette](../../mfc/reference/cpalette-class.md)的指標。 包含目前色彩選取功能表中可用的色彩。|
|`m_pPopup`|[CMFCColorPopupMenu 類別](../../mfc/reference/cmfccolorpopupmenu-class.md)物件的指標。 當您按一下 [色彩] 按鈕時所顯示的色彩選取功能表。|
|`m_strAutoColorText`|字串。 色彩選取功能表中的 [自動] 按鈕標籤。|
|`m_strDocColorsText`|字串。 色彩選取功能表中顯示檔色彩的按鈕標籤。|
|`m_strOtherText`|字串。 色彩選取功能表中的 [其他] 按鈕標籤。|

## <a name="remarks"></a>備註

根據預設， `CMFCColorButton` 類別會以開啟 [色彩選擇器] 對話方塊的 [推送] 按鈕的方式運作。 [色彩選擇器] 對話方塊包含一個小顏色按鈕的陣列，以及一個顯示自訂色彩選擇器的 [其他] 按鈕。  (標準系統的 [其他] 按鈕標示為 [ **更多色彩**]。 ) 當使用者選取新的色彩時， `CMFCColorButton` 物件會反映變更並顯示選取的色彩。

您可以直接在程式碼中建立色彩按鈕控制項，也可以使用 **ClassWizard** 工具和對話方塊範本來建立。 如果您直接建立色彩按鈕控制項，請將 `CMFCColorButton` 變數新增至您的應用程式，然後呼叫物件的函式和 `Create` 方法 `CMFCColorButton` 。 如果您使用 **ClassWizard**，請將 `CButton` 變數新增至您的應用程式，然後將變數的類型從變更 `CButton` 為 `CMFCColorButton` 。

當架構呼叫事件處理常式時， [CMFCColorButton：： OnShowColorPopup](#onshowcolorpopup)方法會顯示 [色彩選擇器] 對話方塊 ( [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)) `OnLButtonDown` 。 您可以覆寫 [CMFCColorButton：： OnShowColorPopup](#onshowcolorpopup) 方法，以支援自訂色彩選取。

`CMFCColorButton`物件會藉由將 WM_COMMAND 傳送給其父系，來通知其父控制項的色彩變更 |BN_CLICKED 通知。 父系會使用 [CMFCColorButton：： GetColor](#getcolor) 方法來取得目前的色彩。

## <a name="example"></a>範例

下列範例示範如何使用類別中的各種方法來設定色彩按鈕 `CMFCColorButton` 。 這些方法會設定色彩按鈕的色彩和其資料行的數目，並啟用 [自動] 和 [其他] 按鈕。 此範例是 [狀態列示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>規格需求

**標頭：** afxcolorbutton。h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a> CMFCColorButton::CMFCColorButton

建構新的 `CMFCColorButton` 物件。

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a> CMFCColorButton::EnableAutomaticButton

啟用或停用色彩選擇器控制項的 [自動] 按鈕，並將 [自動 (預設) 色彩]。

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
在指定自動按鈕的文字。

*colorAutomatic*<br/>
在指定自動按鈕預設色彩的 RGB 值。

*bEnable*<br/>
在指定是否啟用或停用 [自動] 按鈕。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a> CMFCColorButton::EnableOtherButton

啟用或停用 [其他] 按鈕，此按鈕會出現在 [一般色彩] 按鈕下方。

```cpp
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

按一下 [其他] 按鈕以顯示 [色彩] 對話方塊。 如果 *bAltColorDlg* 參數為 TRUE，則會顯示 [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md) ;否則，就會顯示 [系統色彩] 對話方塊。

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a> CMFCColorButton::GetAutomaticColor

抓取目前的自動 (預設) 色彩。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>傳回值

表示目前自動色彩的 RGB 值。

### <a name="remarks"></a>備註

目前的自動色彩是由 [CMFCColorButton：： EnableAutomaticButton](#enableautomaticbutton) 方法所設定。

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a> CMFCColorButton::GetColor

抓取目前選取的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

RGB 值。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a> CMFCColorButton::IsDrawXPTheme

指出目前的色彩按鈕是否以 Windows XP 的視覺化樣式顯示。

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>傳回值

如果支援視覺化樣式，且目前的色彩按鈕以 Windows XP 的視覺化樣式顯示，則為 TRUE;否則為 FALSE。

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a> CMFCColorButton：： m_bEnabledInCustomizeMode

將 [色彩] 按鈕設定為自訂模式。

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>備註

如果您需要將 [色彩] 按鈕新增至自訂對話方塊的頁面 (或允許使用者在自訂) 期間選取另一個色彩，請將成員設為 TRUE，以啟用此按鈕 `m_bEnabledInCustomizeMode` 。 依預設，這個成員會設定為 FALSE。

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a> CMFCColorButton：： OnDraw

由架構呼叫以呈現按鈕的影像。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在指向用來呈現按鈕影像的裝置內容。

*矩形*<br/>
在用來包圍按鈕的矩形。

*uiState*<br/>
在指定按鈕的視覺狀態。

### <a name="remarks"></a>備註

覆寫這個方法以自訂轉譯流程。

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a> CMFCColorButton::OnDrawBorder

由架構呼叫以顯示按鈕的框線。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在指向用來繪製框線的裝置內容。

*rectClient*<br/>
在由 *pDC* 參數指定的裝置內容中的矩形，定義要繪製之按鈕的界限。

*uiState*<br/>
在指定按鈕的視覺狀態。

### <a name="remarks"></a>備註

覆寫此函式以自訂色彩按鈕的框線外觀。

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a> CMFCColorButton::OnDrawFocusRect

由架構呼叫，以在按鈕具有焦點時顯示焦點矩形。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在指向用來繪製焦點矩形的裝置內容。

*rectClient*<br/>
在由 *pDC* 參數指定的裝置內容中，定義按鈕界限的矩形。

### <a name="remarks"></a>備註

覆寫這個方法以自訂焦點矩形的外觀。

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a> CMFCColorButton::OnShowColorPopup

在顯示快捷方式色軸之前呼叫。

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a> CMFCColorButton::RebuildPalette

將 `m_pPalette` 受保護的資料成員初始化為指定的調色板或預設的系統調色板。

```cpp
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>參數

*pPal*\
在邏輯調色板的指標或 Null。 如果是 Null，則會使用預設的系統調色板。

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a> CMFCColorButton：： SetColor

指定按鈕的色彩。

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
在RGB 值。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a> CMFCColorButton::SetColorName

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

色彩名稱清單是每個應用程式的全域名稱。 因此，這個方法會將其參數傳輸至 [CMFCColorBar：： SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a> CMFCColorButton::SetColumnsNumber

定義在使用者的色彩選取程式期間，向使用者顯示的色彩表中顯示的資料行數目。

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>參數

*nColumns*<br/>
在指定資料行的數目。

### <a name="remarks"></a>備註

使用者可以從顯示預先定義色彩表的快顯視窗中選取色彩。 您可以使用這個方法來定義資料表中的資料行數目。

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a> CMFCColorButton::SetDocumentColors

指定一組色彩和集合的名稱。 這組色彩會使用 [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md) 物件來顯示。

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
在指定要與一組檔色彩一起顯示的標籤。

*lstColors*<br/>
在RGB 值清單的參考。

### <a name="remarks"></a>備註

`CMFCColorButton`物件會維護傳送至[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件的 RGB 值清單。 當色軸顯示時，這些色彩會顯示在 *lpszLabel* 參數指定其標籤的特殊區段中。

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a> CMFCColorButton::SetPalette

指定要顯示在快顯色軸上的標準色彩。

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>參數

*pPalette*<br/>
在色板的指標。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a> CMFCColorButton：： System.windows.window.sizetocontent

調整按鈕控制項的大小，使其符合其文字和影像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
在如果是非零值，則會計算按鈕控制項的新大小，但不會變更實際的大小。

### <a name="return-value"></a>傳回值

`CSize`指定新按鈕控制項大小的物件。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a> CMFCColorButton::UpdateColor

當使用者在按下 [色彩] 按鈕時所顯示的色軸中選取色彩時，由架構呼叫。

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>參數

*color*<br/>
在使用者選取的色彩。

### <a name="remarks"></a>備註

此函式會 `UpdateColor` 變更目前選取的按鈕色彩，並傳送具有 BN_CLICKED 標準通知的 WM_COMMAND 訊息來通知其父系。 使用 [CMFCColorButton：： GetColor](#getcolor) 方法來取出選取的色彩。

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
