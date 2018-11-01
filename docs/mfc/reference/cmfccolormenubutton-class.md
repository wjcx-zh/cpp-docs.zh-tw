---
title: CMFCColorMenuButton 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f307a5c0d1c1666c4d8a016496d9a6bf717c6d48
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083007"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton 類別

`CMFCColorMenuButton`類別支援功能表命令或工具列按鈕，啟動色彩選擇器對話方塊。

## <a name="syntax"></a>語法

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|建構 `CMFCColorMenuButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|啟用和停用位於標準色彩按鈕上方的 「 自動 」 按鈕。 (標準系統自動按鈕會標示**自動**。)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|允許特定文件而不是系統色彩的色彩的顯示。|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|啟用和停用 「 其他 」 位於標準色彩按鈕下方的按鈕。 (標準的系統標示為 「 其他 」 按鈕**更多色彩**。)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|可讓您分離出來的色彩窗格。|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|擷取目前的自動色彩。|
|[CMFCColorMenuButton::GetColor](#getcolor)|擷取目前按鈕的色彩。|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|擷取色彩對應到指定的命令識別碼。|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|父視窗變更時由架構呼叫。|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|會開啟色彩選取對話方塊。|
|[CMFCColorMenuButton::SetColor](#setcolor)|設定目前的 [色彩] 按鈕的色彩。|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|設定指定的色彩功能表按鈕的色彩。|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|設定指定的色彩的新名稱。|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|設定所顯示的資料行數目`CMFCColorBar`物件。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|將另一個工具列按鈕複製 [目前] 按鈕。|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|建立色彩選擇器對話方塊。|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|指出是否支援空的功能表。|
|[CMFCColorMenuButton::OnDraw](#ondraw)|由架構呼叫以在按鈕上顯示影像。|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由架構之前呼叫`CMFCColorMenuButton`工具列自訂對話方塊的清單中顯示物件。|

## <a name="remarks"></a>備註

若要取代的原始功能表命令或工具列按鈕`CMFCColorMenuButton`物件，建立`CMFCColorMenuButton`設定任何適當的物件[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)樣式，然後再呼叫`ReplaceButton`方法[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別。 如果您自訂工具列時，呼叫[CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)方法。

色彩選擇器對話方塊建立的過程[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)事件處理常式。 事件處理常式會告知父框架的 WM_COMMAND 訊息。 `CMFCColorMenuButton`物件傳送指派給原始的功能表命令或工具列按鈕的控制項 ID。

## <a name="example"></a>範例

下列範例示範如何建立和使用中的各種方法來設定色彩功能表按鈕`CMFCColorMenuButton`類別。 在範例中，`CPalette`物件是第一次建立，然後用來建構的物件`CMFCColorMenuButton`類別。 `CMFCColorMenuButton`藉由啟用其自動和其他按鈕，並設定其色彩和資料行數目，然後設定物件。 此程式碼屬於[Wordpad 範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxcolormenubutton.h

##  <a name="cmfccolormenubutton"></a>  CMFCColorMenuButton::CMFCColorMenuButton

建構 `CMFCColorMenuButton` 物件。

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>參數

*uiCmdID*<br/>
[in]按鈕命令識別碼。

*lpszText*<br/>
[in]按鈕的文字。

*pPalette*<br/>
[in]按鈕的色彩調色盤指標。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

第一個建構函式是預設建構函式。 物件的目前色彩和自動色彩會初始化為黑色 (RGB （0，0，0）)。

第二個建構函式初始化對應至指定的命令識別碼的色彩按鈕

##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom

複製其中一個[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)-到另一個衍生物件。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]若要複製的 [來源] 按鈕。

### <a name="remarks"></a>備註

覆寫這個方法，以複製物件衍生自`CMFCColorMenuButton`物件。

##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu

建立色彩選擇器對話方塊。

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>傳回值

物件，表示色彩選擇器對話方塊。

### <a name="remarks"></a>備註

當使用者按下色彩功能表按鈕時，這個方法是由架構呼叫。

##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton

啟用和停用位於標準色彩按鈕上方的 「 自動 」 按鈕。 (標準系統自動按鈕會標示**自動**。)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in]指定自動按鈕時顯示的按鈕文字。

*colorAutomatic*<br/>
[in]指定新的自動色彩。

*bEnable*<br/>
[in]指定按鈕是否為自動。

### <a name="remarks"></a>備註

自動按鈕適用於目前的預設色彩。

##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors

允許特定文件而不是系統色彩的色彩的顯示。

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in]指定按鈕的文字。

*bEnable*<br/>
[in]若要顯示特定文件的色彩或為 FALSE，則會顯示系統色彩則為 TRUE。

### <a name="remarks"></a>備註

使用此方法來顯示目前的文件色彩或系統調色盤色彩，當使用者按一下色彩功能表按鈕。

##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton

啟用和停用 「 其他 」 位於標準色彩按鈕下方的按鈕。 (標準的系統標示為 「 其他 」 按鈕**更多色彩**。)

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
[in]指定 TRUE，即可顯示`CMFCColorDialog`] 對話方塊中或 FALSE 表示顯示標準系統的 [色彩] 對話方塊。

*bEnable*<br/>
[in]指定 TRUE，以顯示 [其他] 按鈕，否則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff

可讓您分離出來的色彩窗格。

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[in]指定 [分割] 窗格中的識別碼。

*nVertDockColumns*<br/>
[in]在分割狀態的垂直停駐的色彩窗格中指定資料行的數目。

*nHorzDockRows*<br/>
[in]指定在分割狀態的水平停駐的色彩窗格的資料列數目。

### <a name="remarks"></a>備註

呼叫這個方法來啟用 「 分割 」 功能，以便出現時所使用的色彩窗格`CMFCColorMenuButton`按下按鈕時。

##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor

擷取目前的自動色彩。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>傳回值

表示目前的自動色彩的 RGB 色彩值。

### <a name="remarks"></a>備註

呼叫這個方法來取得設定自動色彩[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)。

##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor

擷取目前按鈕的色彩。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

按鈕的色彩。

### <a name="remarks"></a>備註

##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID

擷取色彩對應到指定的命令識別碼。

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>參數

*uiCmdID*<br/>
[in]命令識別碼。

### <a name="return-value"></a>傳回值

色彩對應於指定的命令識別碼。

### <a name="remarks"></a>備註

當您的應用程式中有數個色彩按鈕時，請使用這個方法。 當使用者按一下色彩按鈕時，按鈕會將其命令識別碼 WM_COMMAND 訊息中傳送至其父代中。 `GetColorByCmdID`方法使用命令識別碼來擷取對應的色彩。

##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed

指出是否支援空的功能表。

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>傳回值

如果允許空白的功能表;，非零值。否則為零。

### <a name="remarks"></a>備註

預設會支援空的功能表。 覆寫這個方法，以變更此行為衍生類別中。

##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd

父視窗變更時由架構呼叫。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]新的父視窗的指標。

### <a name="remarks"></a>備註

##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw

由架構呼叫以在按鈕上顯示影像。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz=TRUE,
    BOOL bCustomizeMode=FALSE,
    BOOL bHighlight=FALSE,
    BOOL bDrawBorder=TRUE,
    BOOL bGrayDisabledButtons=TRUE);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rect*<br/>
[in]之界限重新繪製區域的矩形。

*pImages*<br/>
[in]指向清單中工具列影像。

*bHorz*<br/>
[in]若要指定工具列為水平的停駐狀態;，則為 TRUE否則為 FALSE。 預設值為 TRUE。

*bCustomizeMode*<br/>
[in]若要指定應用程式為自訂模式，則為 TRUE否則為 FALSE。 預設值為 FALSE。

*bHighlight*<br/>
[in]TRUE 表示指定按鈕會反白顯示;否則為 FALSE。 預設值為 FALSE。

*bDrawBorder*<br/>
[in]TRUE 會指定，則會顯示按鈕的框線;否則為 FALSE。 預設值為 TRUE。

*bGrayDisabledButtons*<br/>
[in]TRUE 表示指定 out; 的 [停用的按鈕會呈現灰色 (dimmed)否則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList

由架構之前呼叫`CMFCColorMenuButton`工具列自訂對話方塊的清單中顯示物件。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rect*<br/>
[in]之界限的按鈕要繪製的矩形。

*bSelected*<br/>
[in]TRUE 會指定按鈕處於選取狀態;否則為 FALSE。

### <a name="return-value"></a>傳回值

按鈕的寬度。

### <a name="remarks"></a>備註

由架構呼叫這個方法時`CMFCColorMenuButton`物件工具列自訂程序期間，會顯示在清單方塊中。

##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog

會開啟色彩選取對話方塊。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>參數

*colorDefault*<br/>
[in]在 [色彩] 對話方塊中選取的預設色彩。

*colorRes*<br/>
[out]傳回使用者從 [色彩] 對話方塊中選取的色彩。

### <a name="return-value"></a>傳回值

非零值，如果使用者選取新的色彩;否則為零。

### <a name="remarks"></a>備註

按一下 [功能表] 按鈕時，呼叫這個方法，以開啟 [色彩] 對話方塊。 傳回值為非零值，如果使用者選取的色彩會儲存在*colorRes*參數。 使用[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)方法，以切換 [標準色彩] 對話方塊中， [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md) 對話方塊。

##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor

設定目前的 [色彩] 按鈕的色彩。

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>參數

*clr*<br/>
[in]RGB 色彩值。

*bNotify*<br/>
[in]True 表示套用*clr*參數色彩的任何相關聯的功能表按鈕或工具列按鈕，否則為 FALSE。

### <a name="remarks"></a>備註

呼叫這個方法來變更目前的 [色彩] 按鈕的色彩。 如果*bNotify*參數為非零值，對應上的任何相關聯的快顯功能表或工具列按鈕的色彩變更為所指定的色彩*clr*參數。

##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID

設定指定的色彩功能表按鈕的色彩。

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>參數

*uiCmdID*<br/>
[in]色彩功能表按鈕的資源識別碼。

*色彩*<br/>
[in]RGB 色彩值。

##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName

設定指定的色彩的新名稱。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*色彩*<br/>
[in]其名稱會變更色彩的 RGB 值。

*strName*<br/>
[in]新色彩的名稱。

### <a name="remarks"></a>備註

##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber

設定色彩選取範圍控制項中顯示的資料行數目 ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)物件)。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>參數

*nColumns*<br/>
[in]若要顯示的資料行數目。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)
