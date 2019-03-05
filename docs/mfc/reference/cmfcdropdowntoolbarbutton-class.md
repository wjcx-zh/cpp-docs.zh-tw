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
ms.openlocfilehash: b33e50328fd3c8997774515f248780edda6bcc75
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275489"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 類別

按一下時其行為像一般按鈕的工具列按鈕類型。 不過，它會開啟下拉式工具列 ( [CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)使用者是否按下並按住工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|建構 `CMFCDropDownToolbarButton` 物件。|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|另一個工具列按鈕的屬性複製到目前的按鈕。 (覆寫[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|
|`CMFCDropDownToolbarButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|會開啟下拉式工具列。|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|複製文字從工具列按鈕的功能表。 (覆寫[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)。)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|擷取與按鈕相關聯的下拉式清單 工具列。|
|`CMFCDropDownToolbarButton::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|判斷是否為目前開啟的下拉工具列。|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|判斷是否可以使用擴充的框線中顯示按鈕。 (覆寫[CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|由架構呼叫以計算的銜接狀態與指定的裝置內容的按鈕大小。 (覆寫[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|
|`CMFCDropDownToolbarButton::OnCancelMode`|由架構呼叫以處理[WM_CANCELMODE](/windows/desktop/winmsg/wm-cancelmode)訊息。 (覆寫 `CMCToolBarButton::OnCancelMode`。)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|插入新的工具列按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|使用者按下滑鼠按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|當使用者放開滑鼠按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)。)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|為父工具列處理 WM_HELPHITTEST 訊息時由架構呼叫。 (覆寫[CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)。)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|當應用程式為父工具列上顯示捷徑功能表，請修改提供的功能表。 (覆寫[CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)。)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|由架構呼叫以繪製按鈕，使用指定的樣式和選項。 (覆寫[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由架構呼叫以繪製按鈕**命令**窗格**自訂** 對話方塊。 (覆寫[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|從封存讀取這個物件，或將其寫入至封存。 (覆寫[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|設定當使用者按一下按鈕時，架構會使用預設命令。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|指定使用者必須按住滑鼠按鈕才會出現下拉式工具列的時間的長度。|

## <a name="remarks"></a>備註

A`CMFCDropDownToolBarButton`不同於一般的按鈕，因為它有一個小箭號按鈕右下角。 使用者從下拉式清單 工具列中選取按鈕之後，架構會顯示其圖示，在最上層工具列按鈕 （在右下角的小箭號按鈕）。

如需如何實作下拉式工具列的資訊，請參閱[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)。

`CMFCDropDownToolBarButton`物件可以匯出至[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件，並顯示為快顯功能表的功能表按鈕。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom

另一個工具列按鈕的屬性複製到目前的按鈕。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]要從中複製來源按鈕參考。

### <a name="remarks"></a>備註

呼叫這個方法，以將另一個工具列按鈕複製到此工具列按鈕。 *src*必須是型別`CMFCDropDownToolbarButton`。

##  <a name="cmfcdropdowntoolbarbutton"></a>  CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

建構 `CMFCDropDownToolbarButton` 物件。

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
[in]預設按鈕的文字。

*pToolBar*<br/>
[in]指標`CMFCDropDownToolBar`使用者按下按鈕時顯示的物件。

### <a name="remarks"></a>備註

第二個多載的建構函式會將複製到下拉式按鈕的第一個按鈕從工具列的*pToolBar*指定。

一般而言，下拉式工具列按鈕會從最近使用的按鈕文字使用工具列中， *pToolBar*指定。 它會使用所指定的文字*lpszName*  按鈕時轉換成功能表按鈕或顯示在**命令**索引標籤**自訂** 對話方塊。 如需詳細資訊**自訂** 對話方塊中，請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

### <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCDropDownToolbarButton`類別。 此程式碼片段是一部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar

會開啟下拉式工具列。

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
[in]下拉式清單的範圍內，則為 NULL，若要使用的下拉工具列按鈕的父視窗的父視窗。

### <a name="return-value"></a>傳回值

如果方法成功則為非零否則為 0。

### <a name="remarks"></a>備註

[CMFCDropDownToolbarButton::OnClick](#onclick)方法會呼叫這個方法，以開啟下拉式工具列，當使用者按下並按住工具列按鈕。

此方法使用，建立下拉式工具列[CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create)方法。 如果為父工具列停駐垂直，這個方法會將下拉式工具列為父工具列的 調整依據的左側或右側端。 否則，這個方法會將為父工具列下方的下拉工具列。

如果這個方法會失敗*pWnd*是 NULL，且下拉式工具列按鈕並沒有父視窗。

##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton

複製文字從工具列按鈕的功能表。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*menuButton*<br/>
[in][目標] 功能表按鈕的參考。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零，否則為零。

### <a name="remarks"></a>備註

這個方法會呼叫基底類別實作 ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton))，然後附加到 [目標] 功能表按鈕，其中包含每個工具列功能表項目，這個按鈕，在快顯功能表。 這個方法不會將子功能表附加至快顯功能表。

這個方法會失敗，如果父工具列`m_pToolBar`、 為 NULL 或基底類別實作會傳回 FALSE。

##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar

擷取與按鈕相關聯的下拉式清單 工具列。

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>傳回值

下拉式工具列按鈕與相關聯。

### <a name="remarks"></a>備註

這個方法會傳回`m_pToolBar`資料成員。

##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown

判斷是否為目前開啟的下拉工具列。

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>傳回值

目前開啟下拉式工具列時，非零值。否則為 0。

### <a name="remarks"></a>備註

此架構使用開啟下拉式工具列[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)方法。 當使用者按下左滑鼠按鈕的下拉工具列非工作區中，架構就會關閉下拉式工具列。

##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize

判斷是否可以使用擴充的框線中顯示按鈕。

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>傳回值

如果工具列按鈕可以使用擴充的框線; 來顯示，非零值。否則為 0。

### <a name="remarks"></a>備註

如需有關擴充框線的詳細資訊，請參閱[CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。

##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay

指定使用者必須按住滑鼠按鈕才會出現下拉式工具列的時間的長度。

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>備註

延遲時間的測量以毫秒為單位。 預設值為 500。 您可以藉由變更這個共用的資料成員的值來設定另一個的延遲。

##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize

由架構呼叫以計算的銜接狀態與指定的裝置內容的按鈕大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容，顯示的按鈕。

*sizeDefault*<br/>
[in]按鈕的預設大小。

*bHorz*<br/>
[in]為父工具列停駐狀態。 如果工具列停駐垂直，這個參數會是如果工具列會以水平方式停駐或浮動，則為 TRUE 或 FALSE。

### <a name="return-value"></a>傳回值

A`SIZE`結構，其中包含按鈕，像素為單位的大小。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) 藉由將按鈕的大小的水平維度中的下拉箭號的寬度。

##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd

插入新的工具列按鈕時由架構呼叫。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]新的父視窗。

### <a name="remarks"></a>備註

這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 藉由清除文字標籤 ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) 並設定[CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext)並[CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton)資料成員設為 FALSE。

##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick

使用者按下滑鼠按鈕時由架構呼叫。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
[in]工具列按鈕的父視窗。

*bDelay*<br/>
[in]如果應該處理訊息，且延遲時間，則為 TRUE。

### <a name="return-value"></a>傳回值

非零值，如果按鈕處理按一下訊息;否則為 0。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作中， [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)，藉由更新狀態的下拉工具列。

當使用者按一下工具列按鈕時，這個方法會建立一個計時器，會等候指定的時間長度[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)資料成員，然後使用開啟下拉式工具列[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)方法。 這個方法會關閉下拉式工具列第二次使用者按一下工具列按鈕。

##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp

當使用者放開滑鼠按鈕時由架構呼叫。

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>傳回值

非零值，如果按鈕處理按一下訊息;否則為 0。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作中， [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)，藉由更新狀態的下拉工具列。

如果是作用中，此方法就會停止下拉式工具列計時器。 如果已開啟，它就會關閉下拉式工具列。

如需有關的下拉工具列和下拉式工具列計時器的詳細資訊，請參閱[CMFCDropDownToolbarButton::OnClick](#onclick)。

##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp

為父工具列處理 WM_HELPHITTEST 訊息時由架構呼叫。

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
[in]工具列按鈕的父視窗。

### <a name="return-value"></a>傳回值

非零值，如果按鈕處理說明訊息;否則為 0。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) 藉由呼叫[CMFCDropDownToolbarButton::OnClick](#onclick)方法*bDelay*設為 FALSE。 這個方法會傳回所傳回的值[CMFCDropDownToolbarButton::OnClick](#onclick)。

如需有關 WM_HELPHITTEST 訊息的詳細資訊，請參閱[TN028:即時線上說明支援](../../mfc/tn028-context-sensitive-help-support.md)。

##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu

當應用程式為父工具列上顯示捷徑功能表，請修改提供的功能表。

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>參數

*pMenu*<br/>
[in]若要自訂功能表。

### <a name="return-value"></a>傳回值

這個方法會傳回 TRUE。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) 停用下列功能表項目：

- **複製按鈕影像**

- **按鈕的外觀**

- **影像**

- **Text**

- **影像和文字**

覆寫此方法來修改架構會顯示在自訂模式中的捷徑功能表。

##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw

由架構呼叫以繪製按鈕，使用指定的樣式和選項。

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
[in]裝置內容，顯示的按鈕。

*rect*<br/>
[in]按鈕的週框。

*pImages*<br/>
[in]與按鈕關聯的工具列影像集合。

*bHorz*<br/>
[in]為父工具列停駐狀態。 [] 按鈕停駐時以水平和 FALSE 以垂直方式停駐按鈕時，此參數為 TRUE。

*bCustomizeMode*<br/>
[in]指定工具列是否為自訂模式。 當工具列在自訂模式和 FALSE 無法自訂模式工具列時，此參數為 TRUE。

*bHighlight*<br/>
[in]指定按鈕會反白顯示。 這個參數時，按鈕會反白顯示時的 TRUE 和 FALSE 按鈕不反白顯示。

*bDrawBorder*<br/>
[in]指定按鈕是否應該顯示框線。 此參數為 TRUE，當按鈕應該顯示其框線和 FALSE，當按鈕應該不會顯示其框線時。

*bGrayDisabledButtons*<br/>
[in]指定是否要加上陰影停用的按鈕，或使用已停用的映像集合。 此參數為 TRUE，當停用的按鈕應該是陰影則為 FALSE，當這個方法應該使用已停用的映像集合。

### <a name="remarks"></a>備註

覆寫這個方法以自訂工具列按鈕繪製。

##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList

由架構呼叫以繪製按鈕**命令**窗格**自訂** 對話方塊。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容，顯示的按鈕。

*rect*<br/>
[in]按鈕的週框。

*bSelected*<br/>
[in]是否已選取 按鈕。 如果此參數為 TRUE 時，會選取 [] 按鈕。 如果此參數為 FALSE，未選取 按鈕。

### <a name="return-value"></a>傳回值

寬度，單位為像素上指定的裝置內容的按鈕。

### <a name="remarks"></a>備註

自訂 對話方塊中會呼叫此方法 (**命令** 索引標籤) 按鈕時所需使其顯示在主控描繪清單方塊。

此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) 按鈕的名稱變更 按鈕的文字標籤 (也就是值*lpszName*參數傳遞至建構函式）。

##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize

從封存讀取這個物件，或將其寫入至封存。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
[in]`CArchive`從中或要序列化的物件。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作 ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) 透過序列化為父工具列的資源識別碼。 載入封存檔時 ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)傳回非零值)，這個方法會設定`m_pToolBar`資料成員，至工具列，其中包含序列化的資源識別碼。

##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand

設定當使用者按一下按鈕時，架構會使用預設命令。

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]預設命令的識別碼。

### <a name="remarks"></a>備註

呼叫這個方法，指定架構就會執行使用者按一下按鈕時的預設命令。 具有所指定的命令 ID 的項目*uiCmd*必須位在父下拉式工具列。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[逐步解說：將放在工具列上的控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)
