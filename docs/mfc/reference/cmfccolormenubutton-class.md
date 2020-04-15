---
title: CMFCColorMenuButton 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 22208aec505033d372f5a80ba2a9641b1bd15874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367709"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton 類別

該`CMFCColorMenuButton`類支援功能表命令或啟動顏色選取器對話方塊的工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 顏色選單按鈕::CMFCColor功能表按鈕](#cmfccolormenubutton)|建構 `CMFCColorMenuButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 顏色選單按鈕::開啟自動按鈕](#enableautomaticbutton)|啟用並關閉位於常規顏色按鈕上方的自動按鈕。 ( 標準系統自動按鈕標記為**自動**.)|
|[CMFC 顏色選單按鈕::啟用文件顏色](#enabledocumentcolors)|啟用顯示文件特定顏色而不是系統顏色。|
|[CMFC 顏色選單按鈕::啟用其他按鈕](#enableotherbutton)|啟用並禁用位於常規顏色按鈕下方的"其他"按鈕。 ( 標準系統' 其他按鈕標記為**更多顏色**。|
|[CMFCColor功能表按鈕::啟用"關閉"](#enabletearoff)|能夠撕下顏色窗格。|
|[CMFCColor選單按鈕:取得自動顏色](#getautomaticcolor)|檢索目前自動顏色。|
|[CMFCColor選單按鈕:取得顏色](#getcolor)|檢索當前按鈕的顏色。|
|[CMFCColor選單按鈕:取得顏色乘 CmdID](#getcolorbycmdid)|檢索對應於指定命令 ID 的顏色。|
|[CMFCColor功能表按鈕::打開更改家長](#onchangeparentwnd)|父視窗更改時由框架調用。|
|[CMFC 顏色選單按鈕::打開顏色對話](#opencolordialog)|打開顏色選擇對話方塊。|
|[CMFCColor選單按鈕::設定顏色](#setcolor)|設置當前顏色按鈕的顏色。|
|[CMFC 顏色選單按鈕::設定顏色乘CmdID](#setcolorbycmdid)|設定指定顏色功能表按鈕的顏色。|
|[CMFC 顏色選單按鈕::設定顏色名稱](#setcolorname)|為指定顏色設置新名稱。|
|[CMFCColor選單按鈕::設定欄數](#setcolumnsnumber)|設置`CMFCColorBar`物件顯示的列數。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCColor功能表按鈕::抄襲](#copyfrom)|將另一個工具列按鈕複製到當前按鈕。|
|[CMFC 顏色選單按鈕:: 建立彈出選單](#createpopupmenu)|建立顏色選取器對話方塊。|
|[CMFCColor選單按鈕::空選單允許](#isemptymenuallowed)|指示是否支援空功能表。|
|[CMFCColor功能表按鈕::開拉](#ondraw)|框架調用以在按鈕上顯示圖像。|
|[CMFCColor功能表按鈕::在畫上定製清單](#ondrawoncustomizelist)|在`CMFCColorMenuButton`工具列自定義對話框清單中顯示物件之前由框架調用。|

## <a name="remarks"></a>備註

要將原始選單命令或工具列按鈕替換為`CMFCColorMenuButton`物件,請`CMFCColorMenuButton`建立 物件,設置任何適當的[CMFCColorBar 類](../../mfc/reference/cmfccolorbar-class.md)樣`ReplaceButton`式,然後調用[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)的方法。 如果自定義工具列,請調用[CMFCToolBars 自定義對話框::替換按鈕](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)方法。

顏色選取器對話框是在處理[CMFCColorMenuButton::創建PopupMenu](#createpopupmenu)事件處理程式期間創建的。 事件處理程式使用WM_COMMAND消息通知父幀。 物件`CMFCColorMenuButton`將分配給原始功能表命令或工具列按鈕的控制 ID 發送。

## <a name="example"></a>範例

下面的範例展示如何使用`CMFCColorMenuButton`類中的各種方法創建和配置顏色功能表按鈕。 在此示例中,首先創建物件`CPalette`,然後用於構`CMFCColorMenuButton`造 類的物件。 然後`CMFCColorMenuButton`,通過啟用其自動和其他按鈕,並設置其顏色和列數來配置物件。 此代碼是 Word [Pad 示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxcolormenu按鈕.h

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a>CMFC 顏色選單按鈕::CMFCColor功能表按鈕

建構 `CMFCColorMenuButton` 物件。

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>參數

*烏伊CmdID*<br/>
[在]按鈕命令識別碼。

*lpszText*<br/>
[在]按鈕文字。

*pPalette*<br/>
[在]指向按鈕調色板的指標。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

第一個構造函數是預設構造函數。 物件的當前顏色和自動顏色被初始化為黑色(RGB(0,0,0)。

第二個建構函數將按鈕初始化到對應於指定命令 ID 的顏色。

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCColor功能表按鈕::抄襲

將一個[CMFCToolBarMenuButton 類](../../mfc/reference/cmfctoolbarmenubutton-class.md)派生物件複製到另一個物件。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[在]要複製的源按鈕。

### <a name="remarks"></a>備註

重寫此方法以複製從`CMFCColorMenuButton`物件派生的物件。

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFC 顏色選單按鈕:: 建立彈出選單

建立顏色選取器對話方塊。

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>傳回值

表示顏色選取器對話方塊的物件。

### <a name="remarks"></a>備註

當使用者按下顏色功能表按鈕時,框架將調用此方法。

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFC 顏色選單按鈕::開啟自動按鈕

啟用並關閉位於常規顏色按鈕上方的自動按鈕。 ( 標準系統自動按鈕標記為**自動**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]指定按鈕變為自動時顯示的按鈕文字。

*顏色 自動*<br/>
[在]指定新的自動顏色。

*b 啟用*<br/>
[在]指定按鈕是否自動。

### <a name="remarks"></a>備註

自動按鈕應用目前預設顏色。

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a>CMFC 顏色選單按鈕::啟用文件顏色

啟用顯示文件特定顏色而不是系統顏色。

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]指定按鈕文字。

*b 啟用*<br/>
[在]TRUE 顯示特定於文件的顏色,或顯示系統顏色的 FALSE。

### <a name="remarks"></a>備註

當使用者按下顏色選單按鈕時,使用此方法顯示當前文件顏色或系統調色板顏色。

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFC 顏色選單按鈕::啟用其他按鈕

啟用並禁用位於常規顏色按鈕下方的"其他"按鈕。 ( 標準系統' 其他按鈕標記為**更多顏色**。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[在]指定按鈕文字。

*巴爾特·博拉爾德格*<br/>
[在]指定 TRUE`CMFCColorDialog`以 顯示對話框,或指定 FALSE 以顯示標準系統顏色對話框。

*b 啟用*<br/>
[在]指定 TRUE 以顯示「其他」按鈕;否則,FALSE。 預設值是 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a>CMFCColor功能表按鈕::啟用"關閉"

能夠撕下顏色窗格。

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]指定拆解窗格的識別碼。

*nVertDock 柱子*<br/>
[在]指定垂直停靠顏色窗格中處於撕扯狀態的列數。

*n霍茲多克羅茨*<br/>
[在]指定處於撕下狀態時水準停靠顏色窗格的行數。

### <a name="remarks"></a>備註

呼叫此方法,為按下`CMFCColorMenuButton`按鈕時彈出的顏色窗格啟用"撕掉"功能。

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColor選單按鈕:取得自動顏色

檢索目前自動顏色。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>傳回值

表示目前自動顏色的 RGB 顏色值。

### <a name="remarks"></a>備註

呼叫此方法以取得[由 CMFCColorMenuButton](#enableautomaticbutton)設定的自動顏色:啟用自動按鈕 。

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a>CMFCColor選單按鈕:取得顏色

檢索當前按鈕的顏色。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>傳回值

按鈕的顏色。

### <a name="remarks"></a>備註

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a>CMFCColor選單按鈕:取得顏色乘 CmdID

檢索對應於指定命令 ID 的顏色。

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>參數

*烏伊CmdID*<br/>
[在]命令識別碼。

### <a name="return-value"></a>傳回值

對應於指定命令 ID 的顏色。

### <a name="remarks"></a>備註

當應用程式中有多個顏色按鈕時,請使用此方法。 當用戶按下顏色按鈕時,該按鈕將WM_COMMAND消息中的命令 ID 發送到其父級。 該方法`GetColorByCmdID`使用命令 ID 檢索相應的顏色。

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCColor選單按鈕::空選單允許

指示是否支援空功能表。

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>傳回值

允許空菜單時非零;否則,零。

### <a name="remarks"></a>備註

默認情況下支援空功能表。 重寫此方法以更改派生類中的此行為。

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCColor功能表按鈕::打開更改家長

父視窗更改時由框架調用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向新父視窗的指標。

### <a name="remarks"></a>備註

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a>CMFCColor功能表按鈕::開拉

框架調用以在按鈕上顯示圖像。

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
[在]指向設備上下文的指標。

*矩形*<br/>
[在]綁定要重繪的區域的矩形。

*pImage*<br/>
[在]指向工具列圖像清單。

*布霍茲*<br/>
[在]TRUE 指定工具列處於水準停靠狀態;否則,FALSE。 預設值是 TRUE。

*b 客製模式*<br/>
[在]TRUE 指定應用程序處於自定義模式;否則,FALSE。 預設值為 FALSE。

*b 高光*<br/>
[在]TRUE 以指定按鈕突出顯示;否則,FALSE。 預設值為 FALSE。

*bDraw邊框*<br/>
[在]TRUE 以指定顯示按鈕的邊框;否則,FALSE。 預設值是 TRUE。

*b 格雷關閉按鈕*<br/>
[在]TRUE 指定禁用的按鈕為灰色(變暗)出;否則,FALSE。 預設值是 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCColor功能表按鈕::在畫上定製清單

在`CMFCColorMenuButton`工具列自定義對話框清單中顯示物件之前由框架調用。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]綁定要繪製的按鈕的矩形。

*b選定*<br/>
[在]TRUE 指定按鈕處於所選狀態;因此,該按鈕將處於所選狀態。否則,FALSE。

### <a name="return-value"></a>傳回值

按鈕的寬度。

### <a name="remarks"></a>備註

當`CMFCColorMenuButton`物件在工具列自定義過程中顯示在列表框中時,框架將調用此方法。

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a>CMFC 顏色選單按鈕::打開顏色對話

打開顏色選擇對話方塊。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>參數

*顏色 預設*<br/>
[在]在顏色對話框中選擇的預設顏色。

*顏色 Res*<br/>
[出]返回使用者從顏色對話方塊中選擇的顏色。

### <a name="return-value"></a>傳回值

如果用戶選擇新顏色,則非零;否則,零。

### <a name="remarks"></a>備註

按下選單按鈕時,調用此方法以打開顏色對話方塊。 如果返回值為非零,則用戶選擇的顏色存儲在*顏色 Res*參數中。 使用[CMFCColorMenuButton:啟用其他按鈕](#enableotherbutton)方法在標準顏色對話方塊和[CMFCColorDialog 類](../../mfc/reference/cmfccolordialog-class.md)對話框之間切換。

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a>CMFCColor選單按鈕::設定顏色

設置當前顏色按鈕的顏色。

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>參數

*Clr*<br/>
[在]RGB 顏色值。

*b 通知*<br/>
[在]TRUE 將*clr*參數顏色應用於任何關聯的功能表按鈕或工具列按鈕;否則,FALSE。

### <a name="remarks"></a>備註

呼叫此方法以更改當前顏色按鈕的顏色。 如果*bNotify*參數為非零,則任何關聯的彈出式功能表或工具列上的相應按鈕的顏色將更改為*clr*參數指定的顏色。

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a>CMFC 顏色選單按鈕::設定顏色乘CmdID

設定指定顏色功能表按鈕的顏色。

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>參數

*烏伊CmdID*<br/>
[在]顏色選單按鈕的資源 ID。

*顏色*<br/>
[在]RGB 顏色值。

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a>CMFC 顏色選單按鈕::設定顏色名稱

為指定顏色設置新名稱。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>參數

*顏色*<br/>
[在]名稱更改的顏色的 RGB 值。

*strName*<br/>
[在]顏色的新名稱。

### <a name="remarks"></a>備註

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColor選單按鈕::設定欄數

設定要在顏色選擇控制項[(CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)物件)中顯示的欄數。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>參數

*nColumns*<br/>
[在]要顯示的列數。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)
