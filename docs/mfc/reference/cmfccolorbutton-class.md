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
ms.openlocfilehash: 21d05fd8e805467f1a7a77d20c81d5ba0401455e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367726"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton 類別

和`CMFCColorButton` [CMFCColorBar 類](../../mfc/reference/cmfccolorbar-class.md)一起使用以實現顏色選取器控制項。

## <a name="syntax"></a>語法

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC顏色按鈕:CMFC顏色按鈕](#cmfccolorbutton)|建構新的 `CMFCColorButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 顏色按鈕::開啟自動按鈕](#enableautomaticbutton)|啟用並關閉位於常規顏色按鈕上方的自動按鈕。 ( 標準系統自動按鈕標記為**自動**.)|
|[CMFC 顏色按鈕:啟用其他按鈕](#enableotherbutton)|啟用並禁用位於常規顏色按鈕下方的"其他"按鈕。 ( 標準系統' 其他按鈕標記為**更多顏色**。|
|[CMFC 顏色按鈕:取得自動顏色](#getautomaticcolor)|檢索目前自動顏色。|
|[CMFC 顏色按鈕:取得顏色](#getcolor)|檢索按鈕的顏色。|
|[CMFC顏色按鈕::設定顏色](#setcolor)|設置按鈕的顏色。|
|[CMFC 顏色按鈕::設定顏色名稱](#setcolorname)|設置顏色名稱。|
|[CMFC顏色按鈕::設定欄數](#setcolumnsnumber)|設定顏色選取器對話方塊上的欄數。|
|[CMFC 顏色按鈕::設定文件顏色](#setdocumentcolors)|指定顏色選取器對話框中顯示的特定於文件的顏色的清單。|
|[CMFC顏色按鈕::設定調色板](#setpalette)|指定標準顯示顏色的調色板。|
|[CMFC 顏色按鈕::大小到內容](#sizetocontent)|更改按鈕控制項大小,具體取決於其文字和圖像大小。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC顏色按鈕::是DrawXP主題](#isdrawxptheme)|指示當前顏色按鈕是否以 Windows XP 的可視樣式顯示。|
|[CMFC顏色按鈕:在畫上](#ondraw)|由框架調用以顯示按鈕的圖像。|
|[CMFC顏色按鈕::在繪製邊框](#ondrawborder)|框架調用以顯示按鈕的邊框。|
|[CMFC顏色按鈕::在DrawFocusrect上](#ondrawfocusrect)|當按鈕具有焦點時,框架調用以顯示焦點矩形。|
|[CMFC顏色按鈕::在顯示顏色彈出](#onshowcolorpopup)|當顏色選取器對話框即將顯示時,由框架調用。|
|[CMFC顏色按鈕::重建調色板](#rebuildpalette)|將`m_pPalette`受保護的數據成員初始化到指定的調色板或預設系統調色板。|
|[CMFCColorButton::UpdateColor](#updatecolor)|當使用者從顏色選取器對話框的調色板中選擇顏色時,由框架調用。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|`m_bAltColorDlg`|布林值。 如果為 TRUE,則當按下*另一個*按鈕或「FALSE」系統顏色對話框時,框架將顯示[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)顏色對話框。 預設值為 TRUE。 有關詳細資訊,請參閱[CMFCColorButton::啟用其他按鈕](#enableotherbutton)。|
|`m_bAutoSetFocus`|布林值。 如果為 TRUE,則框架在顯示菜單時將焦點設置在顏色功能表上,或者如果 FALSE 不會更改焦點。 預設值為 TRUE。|
|[CMFC顏色按鈕::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|指示顏色按鈕是否已啟用自定義模式。|
|`m_Color`|[顏色值](/windows/win32/gdi/colorref)。 包含當前選擇的顏色。|
|`m_ColorAutomatic`|[顏色值](/windows/win32/gdi/colorref)。 包含目前選擇預設顏色。|
|`m_Colors`|[COLORREF](/windows/win32/gdi/colorref)值的[CArray。](../../mfc/reference/carray-class.md) 包含當前可用的顏色。|
|`m_lstDocColors`|[COLORREF](/windows/win32/gdi/colorref)值的[CList。](../../mfc/reference/clist-class.md) 包含當前文件顏色。|
|`m_nColumns`|整數。 包含在顏色選擇選單中的顏色格線中顯示的欄數。|
|`m_pPalette`|指向[CPalette](../../mfc/reference/cpalette-class.md)的指標。 包含目前顏色選擇選單中可用的顏色。|
|`m_pPopup`|指向[CMFCColorPopupMenu 類](../../mfc/reference/cmfccolorpopupmenu-class.md)物件的指標。 按下顏色按鈕時顯示的顏色選擇功能表。|
|`m_strAutoColorText`|字串。 顏色選擇選單中"自動"按鈕的標籤。|
|`m_strDocColorsText`|字串。 顯示文件顏色的顏色選擇功能表中按鈕的標籤。|
|`m_strOtherText`|字串。 顏色選擇功能表中「其他」按鈕的標籤。|

## <a name="remarks"></a>備註

預設情況下,`CMFCColorButton`類充當按鈕,打開顏色選取器對話方塊。 顏色選擇器對話框包含一系列小顏色按鈕和顯示自訂顏色選取器的「其他」 按鈕。 ( 標準系統' 其他按鈕標記為**更多顏色**。當使用者選擇新顏色時,`CMFCColorButton`物件將反映更改並顯示所選顏色。

直接在代碼中創建顏色按鈕控制項,或者使用**ClassWizard**工具和對話方塊樣本。 如果直接創建顏色按鈕控件,請向應用程式添加`CMFCColorButton`變數,然後調用`Create``CMFCColorButton`物件的構造函數和方法。 如果使用**ClassWizard,** 請加入`CButton`應用程式新增變數,然後會變數的類型從`CButton`變更為`CMFCColorButton`。

顏色選取器對話框( [CMFCColorBar 類](../../mfc/reference/cmfccolorbar-class.md)) 由[CMFCColorButton::在](#onshowcolorpopup)框架呼叫`OnLButtonDown`事件處理程式時顯示ColorPopup 方法顯示。 [CMFCColorButton:可以重寫顯示顏色彈出](#onshowcolorpopup)方法以支援自定義顏色選擇。

對`CMFCColorButton`象 通過向其發送WM_COMMAND來通知其父物件顏色正在更改 |BN_CLICKED通知。 父級使用[CMFCColorButton:getColor](#getcolor)方法檢索當前顏色。

## <a name="example"></a>範例

下面的範例展示如何使用`CMFCColorButton`類中的各種方法配置顏色按鈕。 這些方法設置顏色按鈕的顏色及其列數,並啟用自動按鈕和其他按鈕。 此示例是[狀態列演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>需求

**標題:** afxcolor 按鈕.h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a>CMFC顏色按鈕:CMFC顏色按鈕

建構新的 `CMFCColorButton` 物件。

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFC 顏色按鈕::開啟自動按鈕

啟用或禁用顏色選取器控制項的"自動"按鈕,並設置自動(預設)顏色。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]指定自動按鈕的文字。

*顏色 自動*<br/>
[在]指定自動按鈕預設顏色的 RGB 值。

*b 啟用*<br/>
[在]指定自動按鈕是啟用還是禁用。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFC 顏色按鈕:啟用其他按鈕

啟用或禁用"其他"按鈕,該按鈕顯示在常規顏色按鈕下方。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]指定按鈕的文字。

*巴爾特·博拉爾德格*<br/>
[在]指定在使用者按下這個按鈕時是否打開[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)對話框或系統顏色對話框。

*b 啟用*<br/>
[在]指定「其他」按鈕是啟用還是禁用。

### <a name="remarks"></a>備註

按下「其他」按鈕可顯示顏色對話框。 如果*bAltColorDlg*參數為 TRUE,則顯示 CMFCColorDialog 類;如果 bAltColorDlg 參數為 TRUE,則顯示[CMFCColorDialog 類](../../mfc/reference/cmfccolordialog-class.md);否則,將顯示系統顏色對話方塊。

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFC 顏色按鈕:取得自動顏色

檢索目前自動(預設)顏色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>傳回值

表示目前自動顏色的 RGB 值。

### <a name="remarks"></a>備註

目前自動顏色由[CMFCColorButton 設定:啟用自動按鈕](#enableautomaticbutton)方法。

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a>CMFC 顏色按鈕:取得顏色

檢索當前選擇的顏色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

RGB 值。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a>CMFC顏色按鈕::是DrawXP主題

指示當前顏色按鈕是否以 Windows XP 的可視樣式顯示。

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>傳回值

如果支援視覺樣式,並且當前顏色按鈕以 Windows XP 的視覺樣式顯示,則為 TRUE;否則,FALSE。

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a>CMFC顏色按鈕::m_bEnabledInCustomizeMode

將顏色按鈕設置為自定義模式。

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>備註

如果需要向自定義對話框的頁面添加顏色按鈕(或允許使用者在自定義期間進行其他顏色選擇),請通過將`m_bEnabledInCustomizeMode`成員設置為 TRUE 來啟用該按鈕。 默認情況下,此成員設置為 FALSE。

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a>CMFC顏色按鈕:在畫上

由框架調用以呈現按鈕的圖像。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向用於渲染按鈕圖像的設備上下文。

*矩形*<br/>
[在]綁定按鈕的矩形。

*uiState*<br/>
[在]指定按鈕的可視狀態。

### <a name="remarks"></a>備註

重寫此方法以自定義呈現過程。

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a>CMFC顏色按鈕::在繪製邊框

框架調用以顯示按鈕的邊框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向用於繪製邊框的設備上下文。

*rectClient*<br/>
[在]由*pDC*參數指定的裝置上下文中的矩形,用於定義要繪製的按鈕的邊界。

*uiState*<br/>
[在]指定按鈕的可視狀態。

### <a name="remarks"></a>備註

重寫此函數以自定義顏色按鈕的邊框外觀。

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFC顏色按鈕::在DrawFocusrect上

當按鈕具有焦點時,框架調用以顯示焦點矩形。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向用於繪製焦點矩形的設備上下文。

*rectClient*<br/>
[在]由*pDC*參數指定的裝置上下文中的矩形,用於定義按鈕的邊界。

### <a name="remarks"></a>備註

重寫此方法以自定義焦點矩形的外觀。

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a>CMFC顏色按鈕::在顯示顏色彈出

在顯示彈出顏色列之前調用。

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a>CMFC顏色按鈕::重建調色板

將`m_pPalette`受保護的數據成員初始化到指定的調色板或預設系統調色板。

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pPal*|[在]指向邏輯調色板或 NULL 的指標。 如果為 NULL,則使用預設系統調色板。|

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a>CMFC顏色按鈕::設定顏色

指定按鈕的顏色。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]RGB 值。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFC 顏色按鈕::設定顏色名稱

指定顏色的名稱。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]顏色的 RGB 值。

*strName*<br/>
[在]顏色的名稱。

### <a name="remarks"></a>備註

顏色名稱清單是每個應用程式的全域名稱。 因此,此方法將其參數傳輸到[CMFCColorBar::setColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)。

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFC顏色按鈕::設定欄數

定義在使用者顏色選擇過程中向使用者顯示的顏色表中顯示的列數。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>參數

*nColumns*<br/>
[在]指定列數。

### <a name="remarks"></a>備註

用戶可以從顯示預定義顏色表的彈出顏色列中選擇顏色。 使用此方法定義表中的列數。

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFC 顏色按鈕::設定文件顏色

指定一組顏色和集的名稱。 使用[CMFCColorBar 類](../../mfc/reference/cmfccolorbar-class.md)物件顯示顏色集。

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]指定要使用文件顏色集顯示的標籤。

*lstColors*<br/>
[在]對 RGB 值清單的引用。

### <a name="remarks"></a>備註

物件`CMFCColorButton`維護傳輸到[CMFCColorBar 類](../../mfc/reference/cmfccolorbar-class.md)物件的 RGB 值的清單。 顯示顏色列時,這些顏色將顯示在由*lpszLabel*參數指定的標籤的特殊部分中。

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a>CMFC顏色按鈕::設定調色板

指定要在彈出顏色列上顯示的標準顏色。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>參數

*pPalette*<br/>
[在]指向調色板的指標。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFC 顏色按鈕::大小到內容

調整按鈕控制項大小以適合其文本和圖像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
[在]如果為非零,則計算按鈕控制件的新大小,但不會更改實際大小。

### <a name="return-value"></a>傳回值

指定`CSize`新按鈕控制大小的物件。

### <a name="remarks"></a>備註

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFC顏色按鈕::更新顏色

當使用者從使用者按下顏色按鈕時顯示的顏色列中選擇顏色時,由框架調用。

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]使用者選擇的顏色。

### <a name="remarks"></a>備註

該`UpdateColor`函數更改當前選定的按鈕的顏色,並通過發送帶有BN_CLICKED標準通知的WM_COMMAND消息通知其父按鈕。 使用[CMFCColorButton:getColor](#getcolor)方法檢索所選顏色。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFC顏色按鈕::在顯示顏色彈出](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette 類別](../../mfc/reference/cpalette-class.md)<br/>
[CArray 類別](../../mfc/reference/carray-class.md)<br/>
[CList 類別](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
