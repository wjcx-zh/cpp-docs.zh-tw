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
ms.openlocfilehash: fcfb521e309463da81d0064451297b3b73610d2f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505324"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton 類別

按一下時其行為像一般按鈕的工具列按鈕類型。 不過, 如果使用者按下並按住工具列按鈕, 就會開啟下拉式工具列 ( [CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md))。

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

|名稱|說明|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|將另一個工具列按鈕的屬性複製到目前的按鈕。 (覆寫[CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|
|`CMFCDropDownToolbarButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|開啟下拉式工具列。|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|將文字從工具列按鈕複製到功能表。 (覆寫[CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)。)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|抓取與按鈕相關聯的下拉式工具列。|
|`CMFCDropDownToolbarButton::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|判斷下拉式工具列目前是否開啟。|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|決定是否可以使用延伸框線來顯示按鈕。 (覆寫[CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|由架構呼叫, 以計算指定裝置內容和停駐狀態的按鈕大小。 (覆寫[CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|
|`CMFCDropDownToolbarButton::OnCancelMode`|由架構呼叫以處理[WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode)訊息。 (覆寫 `CMCToolBarButton::OnCancelMode`。)|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|當按鈕插入新工具列時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|當使用者按一下滑鼠按鍵時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick))。|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|當使用者放開滑鼠按鍵時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)。)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|當父工具列處理 WM_HELPHITTEST 訊息時, 由架構呼叫。 (覆寫[CMFCToolBarButton:: OnCoNtextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)。)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|當應用程式在父工具列上顯示快捷方式功能表時, 修改提供的功能表。 (覆寫[CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)。)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|由架構呼叫, 使用指定的樣式和選項繪製按鈕。 (覆寫[CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|由架構呼叫, 以在 [**自訂**] 對話方塊的 [**命令**] 窗格中繪製按鈕。 (覆寫[CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|從封存讀取此物件, 或將它寫入封存。 (覆寫[CMFCToolBarButton:: 序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|設定當使用者按一下按鈕時, 架構所使用的預設命令。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|指定在下拉式工具列出現之前, 使用者必須按住滑鼠按鍵的時間長度。|

## <a name="remarks"></a>備註

與`CMFCDropDownToolBarButton`一般按鈕不同的是, 它在按鈕的右下角有一個小箭號。 當使用者從下拉式工具列選取按鈕之後, 架構會在最上層工具列按鈕 (右下角的小箭號按鈕) 中顯示其圖示。

如需如何執行下拉式工具列的詳細資訊, 請參閱[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)。

物件可以匯出至[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)物件, 並顯示為具有快顯功能表的功能表按鈕。 `CMFCDropDownToolBarButton`

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom

將另一個工具列按鈕的屬性複製到目前的按鈕。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]要從中複製來源按鈕參考。

### <a name="remarks"></a>備註

呼叫這個方法, 將另一個工具列按鈕複製到這個工具列按鈕。 *src*的類型`CMFCDropDownToolbarButton`必須是。

##  <a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

建構 `CMFCDropDownToolbarButton` 物件。

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
在按鈕的預設文字。

*pToolBar*<br/>
在當使用者按下`CMFCDropDownToolBar`按鈕時所顯示之物件的指標。

### <a name="remarks"></a>備註

此函式的第二個多載會從*pToolBar*指定的工具列, 將第一個按鈕複製到下拉式按鈕。

通常, 下拉式工具列按鈕會使用*pToolBar*指定之工具列中最近使用的按鈕所提供的文字。 當按鈕轉換成功能表按鈕, 或在 [**自訂**] 對話方塊的 [**命令**] 索引標籤中顯示時, 它會使用*lpszName*所指定的文字。 如需 [**自訂**] 對話方塊的詳細資訊, 請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

### <a name="example"></a>範例

下列範例示範如何建立`CMFCDropDownToolbarButton`類別的物件。 此程式碼片段是[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar

開啟下拉式工具列。

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
在下拉式框架的父視窗, 或 Null 表示使用下拉式工具列按鈕的父視窗。

### <a name="return-value"></a>傳回值

如果方法成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

當使用者按下並按住工具列按鈕時, [CMFCDropDownToolbarButton:: OnClick](#onclick)方法會呼叫這個方法來開啟下拉式工具列。

這個方法會使用[CMFCDropDownFrame:: Create](../../mfc/reference/cmfcdropdownframe-class.md#create)方法來建立下拉式工具列。 如果父工具列是以垂直方式停駐, 這個方法會將下拉式工具列放在父工具列的左側或右側, 視 [調整] 而定。 否則, 這個方法會將下拉式工具列置於父工具列下方。

如果*pWnd*為 Null, 而且下拉式工具列按鈕沒有父視窗, 這個方法就會失敗。

##  <a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

將文字從工具列按鈕複製到功能表。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*menuButton*<br/>
在[目標] 功能表按鈕的參考。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零，否則為零。

### <a name="remarks"></a>備註

這個方法會呼叫基類實 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)), 然後附加至 [目標] 功能表按鈕, 此快顯功能表包含此按鈕中的每個工具列功能表項目。 這個方法不會將子功能表附加至快顯功能表。

如果父工具列、、為 Null, `m_pToolBar`或基類實傳回 FALSE, 這個方法就會失敗。

##  <a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

抓取與按鈕相關聯的下拉式工具列。

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>傳回值

與按鈕相關聯的下拉式工具列。

### <a name="remarks"></a>備註

這個方法`m_pToolBar`會傳回資料成員。

##  <a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown

判斷下拉式工具列目前是否開啟。

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>傳回值

如果下拉式工具列目前為開啟, 則為非零;否則為0。

### <a name="remarks"></a>備註

此架構會使用[CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar)方法來開啟下拉式工具列。 當使用者在下拉式工具列的非工作區中按下滑鼠左鍵時, 此架構會關閉下拉式工具列。

##  <a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

決定是否可以使用延伸框線來顯示按鈕。

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>傳回值

如果工具列按鈕可以使用延伸框線來顯示, 則為非零。否則為0。

### <a name="remarks"></a>備註

如需延伸框線的詳細資訊, 請參閱[CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。

##  <a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

指定在下拉式工具列出現之前, 使用者必須按住滑鼠按鍵的時間長度。

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>備註

延遲時間以毫秒為單位。 預設值為 500。 您可以藉由變更此共用資料成員的值來設定另一個延遲。

##  <a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

由架構呼叫, 以計算指定裝置內容和停駐狀態的按鈕大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在顯示按鈕的裝置內容。

*sizeDefault*<br/>
在按鈕的預設大小。

*bHorz*<br/>
在父工具列的停駐狀態。 如果工具列是以水準方式停駐或浮動, 則此參數為 TRUE, 如果工具列已垂直停駐, 則為 FALSE。

### <a name="return-value"></a>傳回值

包含按鈕維度的結構(以圖元為單位)。`SIZE`

### <a name="remarks"></a>備註

這個方法會將下拉式箭號的寬度加入按鈕大小的水準維度, 以擴充基類實 ( [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize))。

##  <a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

當按鈕插入新工具列時由架構呼叫。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在新的父視窗。

### <a name="remarks"></a>備註

這個方法會藉由清除文字標籤 ( [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) 並設定[CMFCToolBarButton:: m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext)和 CMFCToolBarButton, 來覆寫基類實 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) [:: m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton)資料成員設為 FALSE。

##  <a name="onclick"></a>CMFCDropDownToolbarButton:: OnClick

當使用者按一下滑鼠按鍵時由架構呼叫。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
在工具列按鈕的父視窗。

*bDelay*<br/>
在如果應該使用延遲來處理訊息, 則為 TRUE。

### <a name="return-value"></a>傳回值

如果按鈕處理按一下訊息, 則為非零值;否則為0。

### <a name="remarks"></a>備註

這個方法會藉由更新下拉式工具列的狀態, 來擴充基類的實[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。

當使用者按一下工具列按鈕時, 這個方法會建立計時器, 等候[CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay)資料成員所指定的時間長度, 然後使用 CMFCDropDownToolbarButton 開啟下拉式工具列。 [::D ropDownToolbar](#dropdowntoolbar)方法。 這個方法會在使用者第二次按下工具列按鈕時關閉下拉式工具列。

##  <a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

當使用者放開滑鼠按鍵時由架構呼叫。

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>傳回值

如果按鈕處理按一下訊息, 則為非零值;否則為0。

### <a name="remarks"></a>備註

這個方法會藉由更新下拉式工具列的狀態, 來擴充基類的實[CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)。

這個方法會在使用中時停止下拉工具列計時器。 如果下拉式工具列已開啟, 則會將它關閉。

如需下拉式工具列和下拉式工具列計時器的詳細資訊, 請參閱[CMFCDropDownToolbarButton:: OnClick](#onclick)。

##  <a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnCoNtextHelp

當父工具列處理 WM_HELPHITTEST 訊息時, 由架構呼叫。

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
在工具列按鈕的父視窗。

### <a name="return-value"></a>傳回值

如果按鈕處理說明訊息, 則為非零值。否則為0。

### <a name="remarks"></a>備註

這個方法會藉由呼叫[CMFCDropDownToolbarButton:: OnClick](#onclick)方法, 並將*BDELAY*設定為 FALSE, 來擴充基類實值 ( [CMFCToolBarButton:: OnCoNtextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp))。 這個方法會傳回[CMFCDropDownToolbarButton:: OnClick](#onclick)所傳回的值。

如需 WM_HELPHITTEST 訊息的詳細資訊, 請[參閱 TN028:即時線上說明支援](../../mfc/tn028-context-sensitive-help-support.md)。

##  <a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu

當應用程式在父工具列上顯示快捷方式功能表時, 修改提供的功能表。

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>參數

*pMenu*<br/>
在要自訂的功能表。

### <a name="return-value"></a>傳回值

這個方法會傳回 TRUE。

### <a name="remarks"></a>備註

這個方法會藉由停用下列功能表項目來擴充基類實 ( [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)):

- **複製按鈕影像**

- **按鈕外觀**

- **影像**

- **Text**

- **影像和文字**

覆寫這個方法, 以修改架構在自訂模式中顯示的快捷方式功能表。

##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw

由架構呼叫, 使用指定的樣式和選項繪製按鈕。

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
在顯示按鈕的裝置內容。

*rect*<br/>
在按鈕的周框。

*pImages*<br/>
在與按鈕相關聯的工具列影像集合。

*bHorz*<br/>
在父工具列的停駐狀態。 當按鈕已水準停駐時, 此參數為 TRUE, 而當按鈕固定時則為 FALSE。

*bCustomizeMode*<br/>
在指定工具列是否處於自訂模式。 當工具列處於自訂模式時, 此參數為 TRUE, 而當工具列不是自訂模式時, 則為 FALSE。

*bHighlight*<br/>
在指定是否反白顯示按鈕。 當按鈕反白顯示時, 此參數為 TRUE, 而未反白顯示按鈕時則為 FALSE。

*bDrawBorder*<br/>
在指定按鈕是否應顯示其框線。 當按鈕應該顯示其框線時, 此參數為 TRUE, 而當按鈕不應顯示其框線時, 則為 FALSE。

*bGrayDisabledButtons*<br/>
在指定是否要為停用的按鈕加上網底, 或使用已停用的影像集合。 當停用的按鈕應該加上陰影時, 此參數為 TRUE, 而此方法應使用已停用的影像集合時則為 FALSE。

### <a name="remarks"></a>備註

覆寫此方法以自訂工具列按鈕繪製。

##  <a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

由架構呼叫, 以在 [**自訂**] 對話方塊的 [**命令**] 窗格中繪製按鈕。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在顯示按鈕的裝置內容。

*rect*<br/>
在按鈕的周框。

*bSelected*<br/>
[in]是否已選取按鈕。 如果此參數為 TRUE, 則會選取按鈕。 如果此參數為 FALSE, 則不會選取此按鈕。

### <a name="return-value"></a>傳回值

指定裝置內容上按鈕的寬度 (以圖元為單位)。

### <a name="remarks"></a>備註

當按鈕需要在 [主控描繪] 清單方塊上顯示時, [自訂] 對話方塊 ([**命令**] 索引標籤) 會呼叫這個方法。

這個方法會藉由將按鈕的文字標籤變更為按鈕的名稱 (也就是您傳遞給此函式的*lpszName*參數值), 來擴充基類實 ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist))。).

##  <a name="serialize"></a>CMFCDropDownToolbarButton:: 序列化

從封存讀取此物件, 或將它寫入封存。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
在要從中序列化或的物件。`CArchive`

### <a name="remarks"></a>備註

這個方法會藉由序列化父工具列的資源識別碼, 來擴充基類實 ( [CMFCToolBarButton:: 序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize))。 當封存載入時 ( [CArchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading)傳回非零值), 這個方法會將`m_pToolBar`資料成員設定為包含序列化資源識別碼的工具列。

##  <a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

設定當使用者按一下按鈕時, 架構所使用的預設命令。

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在預設命令的識別碼。

### <a name="remarks"></a>備註

呼叫這個方法, 以指定當使用者按一下按鈕時, 架構所執行的預設命令。 具有*uiCmd*所指定命令識別碼的專案, 必須位於父系下拉式工具列中。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton 類別](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
