---
title: CMFCDropDownToolbarButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: d62d5ecb0962f74a5dac1658c207cfb08cf12588
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367614"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 類別

按一下時其行為像一般按鈕的工具列按鈕類型。 但是,如果使用者按下並按下工具列按鈕,它將打開下拉工具列[(CMFCDropDownToolBar 類](../../mfc/reference/cmfcdropdowntoolbar-class.md))。

## <a name="syntax"></a>語法

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC向下工具列按鈕::CMFC向下工具列按鈕](#cmfcdropdowntoolbarbutton)|建構 `CMFCDropDownToolbarButton` 物件。|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC向下拖拉工具列按鈕::從複製](#copyfrom)|將另一個工具列按鈕的屬性複製到當前按鈕。 (覆寫[CMFCToolBar 按鈕::從](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)複製。)|
|`CMFCDropDownToolbarButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFC下線工具列按鈕::DropDown工具列](#dropdowntoolbar)|打開下拉工具列。|
|[CMFC向下工具列按鈕::匯出到選單按鈕](#exporttomenubutton)|將工具列按鈕中的文本複製到菜單。 (覆寫[CMFC 工具列按鈕::匯出到選單按鈕](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFC向下拖下工具列按鈕::取得向下拖拉工具列](#getdropdowntoolbar)|檢索與按鈕關聯的下拉工具列。|
|`CMFCDropDownToolbarButton::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC向下拖下工具列按鈕::是向下](#isdropdown)|確定下拉工具列當前是否打開。|
|[CMFC向下工具列按鈕::是超尺寸](#isextrasize)|確定按鈕是否可以使用擴展邊框顯示。 (覆寫[CMFCToolBar 按鈕:是超大型](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFC向下拖拉工具列按鈕::在計算大小](#oncalculatesize)|由框架呼叫,以計算指定設備上下文和停靠狀態的按鈕大小。 (覆寫[CMFC 工具列按鈕:「正在計算大小](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)」)|
|`CMFCDropDownToolbarButton::OnCancelMode`|由框架調用以處理[WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode)消息。 (覆寫 `CMCToolBarButton::OnCancelMode`。)|
|[CMFC下拉工具列按鈕::打開更改家長](#onchangeparentwnd)|將按鈕插入到新工具列時由框架調用。 (覆寫[CMFC 工具列按鈕:開啟變更父項目](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFC向下工具列按鈕::點擊](#onclick)|當用戶按下滑鼠按鈕時由框架調用。 (覆寫[CMFC 工具列按鈕::按下](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFC下拉工具列按鈕::點擊向上](#onclickup)|當用戶釋放滑鼠按鈕時由框架調用。 (覆寫[CMFC 工具列按鈕::按下 .)](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)|
|[CMFC向下工具列按鈕::在上下文説明](#oncontexthelp)|當父工具列處理WM_HELPHITTEST消息時,由框架調用。 (覆寫[CMFC 工具列按鈕:開啟上下文説明](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFC向下工具列按鈕::在自定義功能表上](#oncustomizemenu)|當應用程式在父工具列上顯示快捷方式功能表時,修改提供的功能表。 ( 覆寫[CMFC 工具列按鈕::在自訂選單](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)上 。|
|[CMFC向下工具列按鈕::開拉](#ondraw)|框架呼叫使用指定的樣式和選項繪製按鈕。 (覆寫[CMFC 工具列按鈕::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFC向下拖拉工具列按鈕::在繪製上自定義清單](#ondrawoncustomizelist)|由框架呼叫以在 **「自訂」** 對話框的 **「命令」** 窗格中繪製按鈕。 (覆寫[CMFC 工具列按鈕:在「繪製」自訂清單](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFC下拉工具列按鈕:序列化](#serialize)|從存檔中讀取此物件或將其寫入存檔。 (覆寫[CMFCToolBarButton:序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFC下拉下工具列按鈕::設定預設命令](#setdefaultcommand)|設置框架在用戶按下按鈕時使用的預設命令。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC下拉工具列按鈕::m_uiShowBarDelay](#m_uishowbardelay)|指定用戶必須在下拉工具列出現之前按住滑鼠按鈕的時間長度。|

## <a name="remarks"></a>備註

A`CMFCDropDownToolBarButton`與普通按鈕不同,因為它在按鈕的右下角有一個小箭頭。 使用者從下拉工具列中選擇一個按鈕后,框架會在頂部工具列按鈕上顯示其圖示(右下角有小箭頭的按鈕)。

有關如何實現下拉工具列的資訊,請參閱[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)。

該`CMFCDropDownToolBarButton`物件可以匯出到[CMFCToolBarMenuButton 類](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件,並顯示為帶有彈出功能表的功能表按鈕。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarbuttoncopyfrom"></a><a name="copyfrom"></a>CMFC向下拖拉工具列按鈕::從複製

將另一個工具列按鈕的屬性複製到當前按鈕。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[在]對要從中複製的源按鈕的引用。

### <a name="remarks"></a>備註

呼叫此方法以將另一個工具列按鈕複製到此工具列按鈕。 *src*必須是型`CMFCDropDownToolbarButton`態的 。

## <a name="cmfcdropdowntoolbarbuttoncmfcdropdowntoolbarbutton"></a><a name="cmfcdropdowntoolbarbutton"></a>CMFC向下工具列按鈕::CMFC向下工具列按鈕

建構 `CMFCDropDownToolbarButton` 物件。

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
[在]按鈕的預設文本。

*pToolBar*<br/>
[在]指向`CMFCDropDownToolBar`使用者按下按鈕時顯示的物件的指標。

### <a name="remarks"></a>備註

建構函數的第二個重載將*pToolBar*指定的工具列中的第一個按鈕複製到下拉按鈕。

通常,下拉工具列按鈕使用*pToolBar*指定的工具列中最近使用的按鈕中的文本。 當按鈕轉換為選單按鈕或顯示在 **「自訂**」對話框的 **「命令」** 選項卡中時,它使用*lpszName*指定的文字。 關於 **「自訂」** 對話框的詳細資訊,請參閱[CMFCToolBars 自訂對話方塊類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCDropDownToolbarButton`類的物件。 此代碼段是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

## <a name="cmfcdropdowntoolbarbuttondropdowntoolbar"></a><a name="dropdowntoolbar"></a>CMFC下線工具列按鈕::DropDown工具列

打開下拉工具列。

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
[在]下拉框架的父視窗,或「NULL」使用下拉工具列按鈕的父視窗。

### <a name="return-value"></a>傳回值

如果方法成功,則非零;否則 0。

### <a name="remarks"></a>備註

[CMFCDrop下拉工具列按鈕:OnClick](#onclick)方法調用此方法,當使用者按下並按下工具列按鈕時打開下拉工具列。

此方法使用[CMFCDrop 下線:創建](../../mfc/reference/cmfcdropdownframe-class.md#create)方法創建下拉工具列。 如果父工具列垂直停靠,則此方法會將下拉工具列定位到父工具列的左側或右側,具體取決於擬合。 否則,此方法將下拉工具列定位在父工具列下方。

如果*pWnd*為 NULL 並且下拉工具列按鈕沒有父視窗,則此方法將失敗。

## <a name="cmfcdropdowntoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFC向下工具列按鈕::匯出到選單按鈕

將工具列按鈕中的文本複製到菜單。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*選單按鈕*<br/>
[在]對目標功能表按鈕的引用。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零，否則為零。

### <a name="remarks"></a>備註

此方法呼叫基類別的執行 ( [CMFCToolBarButton::exportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), 然後將包含此按鈕中的每個工具列選單項的彈出選單追加到目標選單按鈕。 此方法不會將子功能表追加到彈出式功能表。

如果父工具列 為 NULL 或`m_pToolBar`基類實現返回 FALSE,則此方法將失敗。

## <a name="cmfcdropdowntoolbarbuttongetdropdowntoolbar"></a><a name="getdropdowntoolbar"></a>CMFC向下拖下工具列按鈕::取得向下拖拉工具列

檢索與按鈕關聯的下拉工具列。

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>傳回值

與按鈕關聯的下拉工具列。

### <a name="remarks"></a>備註

此方法返回`m_pToolBar`數據成員。

## <a name="cmfcdropdowntoolbarbuttonisdropdown"></a><a name="isdropdown"></a>CMFC向下拖下工具列按鈕::是向下

確定下拉工具列當前是否打開。

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>傳回值

如果下拉工具列當前處於打開狀態,則非零;否則 0。

### <a name="remarks"></a>備註

框架使用[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)方法打開下拉工具列。 當使用者按下下拉工具列的非工作區中的左滑鼠按鈕時,框架將關閉下拉工具列。

## <a name="cmfcdropdowntoolbarbuttonisextrasize"></a><a name="isextrasize"></a>CMFC向下工具列按鈕::是超尺寸

確定按鈕是否可以使用擴展邊框顯示。

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>傳回值

如果工具列按鈕可以顯示擴展邊框,則非零;否則 0。

### <a name="remarks"></a>備註

有關擴展邊框的詳細資訊,請參閱[CMFCToolBarButton::是超大型](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。

## <a name="cmfcdropdowntoolbarbuttonm_uishowbardelay"></a><a name="m_uishowbardelay"></a>CMFC下拉工具列按鈕::m_uiShowBarDelay

指定用戶必須在下拉工具列出現之前按住滑鼠按鈕的時間長度。

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>備註

延遲時間以毫秒為單位。 預設值為 500。 您可以通過更改此共享數據成員的值來設置另一個延遲。

## <a name="cmfcdropdowntoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFC向下拖拉工具列按鈕::在計算大小

由框架呼叫,以計算指定設備上下文和停靠狀態的按鈕大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]顯示按鈕的設備上下文。

*預設*<br/>
[在]按鈕的預設大小。

*布霍茲*<br/>
[在]父工具列的停靠狀態。 如果工具列水準停靠或浮動,則此參數為 TRUE;如果工具列垂直停靠,則 FALSE 為 TRUE。

### <a name="return-value"></a>傳回值

包含`SIZE`按鈕尺寸(以像素為單位)的結構。

### <a name="remarks"></a>備註

此方法通過將下拉箭頭的寬度添加到按鈕大小的水準尺寸來擴展基類實現 ( [CMFCToolBarButton::onCalculateSize)。](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)

## <a name="cmfcdropdowntoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFC下拉工具列按鈕::打開更改家長

將按鈕插入到新工具列時由框架調用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]新的父視窗。

### <a name="remarks"></a>備註

此方法通過清除文本標籤[(CMFCToolBarButton::m_strText)](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)並設置[CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext)和[CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton)數據成員到 FALSE 來覆蓋基類實現 ( [CMFCToolBarButton::onChangeParentwnd)。](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)

## <a name="cmfcdropdowntoolbarbuttononclick"></a><a name="onclick"></a>CMFC向下工具列按鈕::點擊

當用戶按下滑鼠按鈕時由框架調用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
[在]工具列按鈕的父視窗。

*bDelay*<br/>
[在]如果消息應延遲處理,則為 TRUE。

### <a name="return-value"></a>傳回值

如果按鈕處理按一下消息,則非零;否則 0。

### <a name="remarks"></a>備註

此方法通過更新下拉工具列的狀態擴展基類實現[CMFCToolBarButton::onClick。](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)

當使用者按一下工具列按鈕時,此方法將創建一個計時器,等待[CMFCDropDownToolbarBarButton:m_uiShowBarDelay](#m_uishowbardelay)資料成員指定的時間長度,然後使用[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)方法打開下拉工具列。 此方法在使用者第二次按一下工具列按鈕時關閉下拉工具列。

## <a name="cmfcdropdowntoolbarbuttononclickup"></a><a name="onclickup"></a>CMFC下拉工具列按鈕::點擊向上

當用戶釋放滑鼠按鈕時由框架調用。

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>傳回值

如果按鈕處理按一下消息,則非零;否則 0。

### <a name="remarks"></a>備註

此方法通過更新下拉工具列的狀態擴展基類實現[CMFCToolBarButton::onClickUp。](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)

此方法將停止下拉工具列計時器(如果處於活動狀態)。 如果工具列處於打開狀態,則關閉下拉工具列。

有關下拉工具列和下拉工具列計時器的詳細資訊,請參閱[CMFCDrop 下拉工具列按鈕::按下](#onclick)。

## <a name="cmfcdropdowntoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a>CMFC向下工具列按鈕::在上下文説明

當父工具列處理WM_HELPHITTEST消息時,由框架調用。

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
[在]工具列按鈕的父視窗。

### <a name="return-value"></a>傳回值

如果按鈕處理説明消息,則非零;否則 0。

### <a name="remarks"></a>備註

此方法通過調用[CMFCDropDown 下工具列按鈕::按一下](#onclick)方法 *(bDelay*設置為 FALSE)來擴展基類實現[(CMFCToolBarButton::onContextHelp)。](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp) 此方法傳回[由 CMFCDropDown 下工具列按鈕傳回的值::按一下](#onclick)。

有關WM_HELPHITTEST消息的詳細資訊,請參閱[TN028:上下文相關幫助支援](../../mfc/tn028-context-sensitive-help-support.md)。

## <a name="cmfcdropdowntoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a>CMFC向下工具列按鈕::在自定義功能表上

當應用程式在父工具列上顯示快捷方式功能表時,修改提供的功能表。

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>參數

*pMenu*<br/>
[在]要自定義的功能表。

### <a name="return-value"></a>傳回值

此方法返回 TRUE。

### <a name="remarks"></a>備註

此方法通過關閉以下選單項目來擴充基類別( [CMFCToolBarButton::on自訂選單](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)):

- **複製按鈕影像**

- **按鈕外觀**

- **影像**

- **Text**

- **影像與文字**

重寫此方法以修改框架在自定義模式下顯示的快捷功能表。

## <a name="cmfcdropdowntoolbarbuttonondraw"></a><a name="ondraw"></a>CMFC向下工具列按鈕::開拉

框架呼叫使用指定的樣式和選項繪製按鈕。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]顯示按鈕的設備上下文。

*矩形*<br/>
[在]按鈕的邊界矩形。

*pImage*<br/>
[在]與按鈕關聯的工具列圖像的集合。

*布霍茲*<br/>
[在]父工具列的停靠狀態。 當按鈕水準停靠時,此參數為 TRUE;當按鈕垂直停靠時,則 FALSE 為 TRUE。

*b 客製模式*<br/>
[在]指定工具列是否處於自定義模式。 當工具列處於自訂模式時,此參數為 TRUE;當工具列未處於自定義模式時,則 FALSE 為 TRUE。

*b 高光*<br/>
[在]指定按鈕是否突出顯示。 當按鈕高亮顯示時,此參數為 TRUE,在按鈕未突出顯示時為 FALSE。

*bDraw邊框*<br/>
[在]指定按鈕是否應顯示其邊框。 當按鈕不應顯示其邊框時,此參數為 TRUE,當按鈕不應顯示其邊框時,則 FALSE。

*b 格雷關閉按鈕*<br/>
[在]指定是為禁用按鈕著色還是使用禁用的圖像集合。 當禁用的按鈕應進行掃描時,此參數為 TRUE,當此方法應使用禁用的圖像集合時,則 FALSE 為 TRUE。

### <a name="remarks"></a>備註

重寫此方法以自定義工具列按鈕繪圖。

## <a name="cmfcdropdowntoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFC向下拖拉工具列按鈕::在繪製上自定義清單

由框架呼叫以在 **「自訂」** 對話框的 **「命令」** 窗格中繪製按鈕。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]顯示按鈕的設備上下文。

*矩形*<br/>
[在]按鈕的邊界矩形。

*b選定*<br/>
[在]是否選擇了按鈕。 如果此參數為 TRUE,則選擇該按鈕。 如果此參數為 FALSE,則未選擇該按鈕。

### <a name="return-value"></a>傳回值

指定設備上下文中按鈕的寬度(以像素為單位)。

### <a name="remarks"></a>備註

當需要按鈕在擁有者繪製列表框中顯示自身時,自定義對話框(**命令**選項卡)調用此方法。

此方法透過按鈕的文字標籤更改為按鈕的名稱(即,將傳遞給建構函數的*lpszName*參數的值)來擴展基類實現[(CMFCToolBarButton::onDrawOn自定義清單](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist))。

## <a name="cmfcdropdowntoolbarbuttonserialize"></a><a name="serialize"></a>CMFC下拉工具列按鈕:序列化

從存檔中讀取此物件或將其寫入存檔。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
[在]要`CArchive`從其序列化的物件。

### <a name="remarks"></a>備註

此方法通過序列化父工具列的資源 ID 來擴展基類實現 ( [CMFCToolBarButton::序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize))。 當存檔正在載入時[(CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)傳回非零值),此方法`m_pToolBar`將 資料成員設置到包含序列化資源 ID 的工具列。

## <a name="cmfcdropdowntoolbarbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a>CMFC下拉下工具列按鈕::設定預設命令

設置框架在用戶按下按鈕時使用的預設命令。

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]默認命令的識別碼。

### <a name="remarks"></a>備註

呼叫此方法以指定框架在使用者按下按鈕時執行的預設命令。 具有*uiCmd*指定的命令 ID 的項必須位於父下拉工具列中。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
