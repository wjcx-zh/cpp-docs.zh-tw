---
title: CMFCToolBarEditBoxButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
ms.openlocfilehash: 52989f7b523bf0ba9a00da350242a968ca0db153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360475"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton 類別

包含編輯控制檔( [CEdit 類別](../../mfc/reference/cedit-class.md)) 的工具列按鈕 。

## <a name="syntax"></a>語法

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolbar編輯盒按鈕:CMFC工具列編輯箱按鈕](#cmfctoolbareditboxbutton)|建構 `CMFCToolBarEditBoxButton` 物件。|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolbar編輯盒按鈕::可以拉伸](#canbestretched)|指定使用者是否可以在自定義期間拉伸按鈕。 (覆蓋[CMFC 工具列按鈕::可以拉伸](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolbar編輯盒按鈕::抄襲](#copyfrom)|將另一個工具列按鈕的屬性複製到當前按鈕。 (覆寫[CMFCToolBar 按鈕::從](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)複製。)|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar編輯盒按鈕::建立編輯](#createedit)|在按鈕中創建新的編輯控制項。|
|`CMFCToolBarEditBoxButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCToolbar編輯盒按鈕::獲取](#getbycmd)|檢索應用程式中具有指定`CMFCToolBarEditBoxButton`命令 ID 的第一個物件。|
|[CMFCToolbar編輯盒按鈕::獲取內容所有](#getcontentsall)|檢索具有指定命令 ID 的第一個編輯框工具列控制項的文字。|
|[CMFCToolbar編輯盒按鈕::取得上下文選單ID](#getcontextmenuid)|檢索與按鈕關聯的快捷功能表的資源 ID。|
|[CMFCToolbar編輯盒按鈕::取得編輯邊框](#geteditborder)|檢索編輯框按鈕編輯部分的邊界矩形。|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar編輯盒按鈕::取得編輯框](#geteditbox)|返回指向嵌入在按鈕中的編輯控制項的指標。|
|[CMFCToolBar編輯盒按鈕::獲取Hwnd](#gethwnd)|檢索與工具列按鈕關聯的視窗句柄。 (覆蓋[CMFCToolBarButton:取得 Hwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolbar編輯盒按鈕::獲得驗證](#getinvalidaterect)|檢索必須重繪的按鈕的工作區區域。 ( 覆[寫 CMFCToolBar 按鈕:取得驗證重新](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)完成 。|
|`CMFCToolBarEditBoxButton::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCToolbar編輯盒按鈕::有熱邊框](#havehotborder)|確定當使用者按下這個按鈕時是否顯示按鈕的邊框。 (覆蓋[CMFCToolBar 按鈕::有 Hot 邊框](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolbar編輯盒按鈕::是平模式](#isflatmode)|確定編輯框按鈕是否具有平面樣式。|
|[CMFCToolbar編輯盒按鈕::通知命令](#notifycommand)|指定按鈕是否處理[WM_COMMAND](/windows/win32/menurc/wm-command)訊息。 (覆寫[CMFCToolBar 按鈕:通知命令](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolbar編輯盒按鈕::在「添加」上自訂頁面](#onaddtocustomizepage)|將按鈕添加到 **「自訂」** 對話框時由框架調用。 (覆寫[CMFC 工具列按鈕::在 Addto 自訂頁](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|由框架呼叫,以計算指定設備上下文和停靠狀態的按鈕大小。 (覆寫[CMFC 工具列按鈕:「正在計算大小](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)」)|
|[CMFCToolbar編輯盒按鈕::打開更改家長](#onchangeparentwnd)|將按鈕插入到新工具列時由框架調用。 (覆寫[CMFC 工具列按鈕:開啟變更父項目](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolbar編輯盒按鈕::點擊](#onclick)|當用戶按下滑鼠按鈕時由框架調用。 (覆寫[CMFC 工具列按鈕::按下](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolbar編輯盒按鈕::在CtlColor上](#onctlcolor)|當父工具列處理WM_CTLCOLOR消息時,框架調用。 (覆寫[CMFCToolBar 按鈕:OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|框架呼叫使用指定的樣式和選項繪製按鈕。 (覆寫[CMFC 工具列按鈕::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|由框架呼叫以在 **「自訂」** 對話框的 **「命令」** 窗格中繪製按鈕。 (覆寫[CMFC 工具列按鈕:在「繪製」自訂清單](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolbar編輯盒按鈕::在全域字型上更改](#onglobalfontschanged)|當全域字體已更改時由框架調用。 (覆寫[CMFC 工具列按鈕::在全域字型變更](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolbar編輯盒按鈕::移動](#onmove)|當父工具欄移動時由框架調用。 (覆寫[CMFC 工具列按鈕::開啟](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)移動 .)|
|[CMFCToolbar編輯盒按鈕::上展](#onshow)|當按鈕變得可見或不可見時,由框架調用。 (覆寫[CMFCToolBar 按鈕::在顯示](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolbar編輯盒按鈕::打開尺寸](#onsize)|當父工具列更改其大小或位置且此更改導致按鈕更改大小時,框架調用該按鈕。 (覆寫[CMFC 工具列按鈕::開啟大小](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolbar編輯盒按鈕::更新工具提示](#onupdatetooltip)|當父工具列更新其工具提示文本時,由框架調用。 (覆寫[CMFC 工具列按鈕:開啟更新工具提示](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|從存檔中讀取此物件或將其寫入存檔。 (覆寫[CMFCToolBarButton:序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|使用工具列按鈕中的`CAccessibilityData`輔助功能數據填充提供的物件。 (覆寫[CMFC 工具列按鈕:設定ACC資料](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar編輯盒按鈕::設定內容](#setcontents)|在按鈕的編輯控制項中設定文本。|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar編輯盒按鈕::設定內容所有](#setcontentsall)|尋找具有指定命令 ID 的編輯控制項按鈕,並在該按鈕的編輯控制項中設定文本。|
|[CMFCToolbar編輯盒按鈕::設定上下文選單ID](#setcontextmenuid)|指定與按鈕關聯的快捷功能表的資源 ID。|
|[CMFCToolbar編輯盒按鈕::設定平壓模式](#setflatmode)|指定應用程式中編輯框按鈕的平面樣式外觀。|
|`CMFCToolBarEditBoxButton::`[CMFCToolbar編輯盒按鈕::設定樣式](#setstyle)|指定按鈕的樣式。 (覆寫[CMFC 工具列按鈕::設定樣式](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>備註

要向工具列加入編輯框按鈕,請按照以下步驟操作:

1. 為父工具列資源的按鈕保留假的資源 ID。

2. 構造`CMFCToolBarEditBoxButton`物件。

3. 在處理AFX_WM_RESETTOOLBAR消息的消息處理程式中,使用[CMFCToolBar:::替換Button,](../../mfc/reference/cmfctoolbar-class.md#replacebutton)將虛擬按鈕替換為新的組合框按鈕。

有關詳細資訊,請參閱[演練:將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarEditBoxButton` 類別中使用各種方法。 該範例展示如何指定使用者可以在自訂期間拉伸按鈕,指定在使用者按下按鈕時顯示按鈕的邊框,在文字框控制件中設定文本,指定應用程式中編輯框按鈕的平面樣式外觀,以及指定工具列編輯框控制件的樣式。

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>需求

**標題:** afxtoolbar編輯盒按鈕.h

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolbar編輯盒按鈕::可以拉伸

指定使用者是否可以在自定義期間拉伸按鈕。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>傳回值

此方法返回 TRUE。

### <a name="remarks"></a>備註

默認情況下,框架不允許使用者在自定義期間拉伸工具列按鈕。 此方法通過允許使用者在自定義期間拉伸編輯框工具列按鈕來擴展基類實現[(CMFCToolBarButton::CanBe拉伸](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))。

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a>CMFCToolbar編輯盒按鈕:CMFC工具列編輯箱按鈕

建構[CMFCToolBar 編輯BoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)物件。

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]指定控制項識別碼。

*i 影像*<br/>
[在]指定工具列圖像的零基索引。 圖像位於[CMFCToolBar 類](../../mfc/reference/cmfctoolbar-class.md)維護的[CMFCToolBar 圖像類](../../mfc/reference/cmfctoolbarimages-class.md)物件中。

*dwStyle*<br/>
[在]指定編輯控制項樣式。

*iWidth*<br/>
[在]指定編輯控制項的寬度(以像素為單位)。

### <a name="remarks"></a>備註

預設建構函數將編輯控制項樣式設定為以下組合:

WS_CHILD |WS_VISIBLE |ES_AUTOHSCROLL

控制項預設寬度為 150 像素。

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolbar編輯盒按鈕::抄襲

將另一個工具列按鈕的屬性複製到當前按鈕。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[在]對要從中複製的源按鈕的引用。

### <a name="remarks"></a>備註

呼叫此方法以將另一個工具列按鈕複製到此工具列按鈕。 *src*必須是型`CMFCToolBarEditBoxButton`態的 。

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolbar編輯盒按鈕::建立編輯

在按鈕中創建新的編輯控制項。

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指定編輯控制項的父視窗。 它不得為 NULL。

*矩形*<br/>
[在]指定編輯控制項大小和位置。

### <a name="return-value"></a>傳回值

指向新創建的編輯控制件的指標;如果控制項的建立和附件失敗,則為 NULL。

### <a name="remarks"></a>備註

分兩步`CMFCToolBarEditBoxButton`構造物件。 首先調用建構函數,然後調用`CreateEdit`,這將創建 Windows 編輯控件並將`CMFCToolBarEditBoxButton`其附加到 物件。

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolbar編輯盒按鈕::獲取

檢索應用程式中具有指定`CMFCToolBarEditBoxButton`命令 ID 的第一個物件。

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]要檢索的按鈕的命令 ID。

### <a name="return-value"></a>傳回值

應用程式中的第`CMFCToolBarEditBoxButton`一個物件具有指定的命令 ID,如果不存在此類物件,則為 NULL。

### <a name="remarks"></a>備註

此共享實用程式方法由以下方法使用,例如[CMFCToolBarEditBoxButton:SetContentsAll](#setcontentsall)和[CMFCToolBarEditBoxButton:獲取內容所有](#getcontentsall)來設置或獲取具有指定命令 ID 的第一個編輯框工具列控件的文本。

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a>CMFCToolbar編輯盒按鈕::獲取內容所有

檢索具有指定命令 ID 的第一個編輯框工具列控制項的文字。

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]要從中檢索內容的按鈕的命令 ID。

### <a name="return-value"></a>傳回值

包含`CString`指定指令 ID 的第一個編輯框工具列控制的文字的物件。

### <a name="remarks"></a>備註

如果沒有`CMFCToolBarEditBoxButton`物件具有指定的命令 ID,此方法將返回空字串。

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolbar編輯盒按鈕::取得上下文選單ID

檢索與按鈕關聯的快捷功能表的資源 ID。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>傳回值

與按鈕關聯的快捷功能表的資源 ID;如果按鈕沒有關聯的快捷功能表,則為 0。

### <a name="remarks"></a>備註

當使用者右鍵按下按鈕時,框架使用資源 ID 創建快捷功能表。

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a>CMFCToolbar編輯盒按鈕::取得編輯邊框

檢索編輯框按鈕編輯部分的邊界矩形。

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>參數

*rectBorder*<br/>
[出]對接收邊界矩形`CRect`的物件的引用。

### <a name="remarks"></a>備註

此方法檢索客戶端座標中編輯控制件的邊界矩形。 它將每個方向上的矩形大小擴展一個圖元。

`CMFCToolBarEditBoxButton` [CMFCVisualManager:在繪製物件周圍的邊框時,OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder)方法調用此方法。

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a>CMFCToolbar編輯盒按鈕::取得編輯框

返回指向嵌入在按鈕中的[CEdit 類](../../mfc/reference/cedit-class.md)控件的指標。

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>傳回值

指向按鈕包含[的CEdit類](../../mfc/reference/cedit-class.md)控制項的指標。 如果尚未建立控制項,`CEdit`則為 NULL。

### <a name="remarks"></a>備註

您可以透過呼`CEdit`叫[CMFCToolBar 編輯BoxButton來建立控制項:建立編輯](#createedit)。

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBar編輯盒按鈕::獲取Hwnd

檢索與工具列按鈕關聯的視窗句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>傳回值

與按鈕關聯的視窗句柄。

### <a name="remarks"></a>備註

此方法通過返回編輯框按鈕的編輯控件部分的視窗句柄來覆蓋[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a>CMFCToolbar編輯盒按鈕::獲得驗證

檢索必須重繪的按鈕的工作區區域。

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>傳回值

指定`CRect`必須重繪的區域的物件。

### <a name="remarks"></a>備註

此方法通過在區域中包括文本標籤的區域來擴展基類實現[CMFCToolBarButton::獲取驗證Rect。](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a>CMFCToolbar編輯盒按鈕::有熱邊框

確定當使用者按下這個按鈕時是否顯示按鈕的邊框。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>傳回值

如果按鈕在選定時顯示其邊框,則非零;否則 0。

### <a name="remarks"></a>備註

此方法通過在控制項可見時返回非零值來擴展基類實現[CMFCToolBarButton::HaveHotBorder。](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolbar編輯盒按鈕::是平模式

確定編輯框按鈕是否具有平面樣式。

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>傳回值

如果按鈕具有平面樣式,則非零;否則,0。

### <a name="remarks"></a>備註

默認情況下,編輯框按鈕具有平面樣式。 使用[CMFCToolBar 編輯BoxButton:SetFlatMode](#setflatmode)方法來更改應用程式的平面樣式外觀。

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolbar編輯盒按鈕::通知命令

指定按鈕是否處理[WM_COMMAND](/windows/win32/menurc/wm-command)訊息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>參數

*iNotify代碼*<br/>
[在]與命令關聯的通知消息。

### <a name="return-value"></a>傳回值

如果按鈕處理WM_COMMAND消息,則為 TRUE,或 FALSE 指示該消息必須由父工具列處理。

### <a name="remarks"></a>備註

當此方法要向父視窗發送[WM_COMMAND](/windows/win32/menurc/wm-command)訊息時,框架將調用此方法。

此方法通過處理[EN_UPDATE](/windows/win32/Controls/en-update)通知來擴展基類實現 ( [CMFCToolBarButton::通知命令](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))。 對於每個具有相同物件命令 ID 的編輯框,它將其文本標籤設置為此物件的文本標籤。

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolbar編輯盒按鈕::在「添加」上自訂頁面

將按鈕添加到 **「自訂」** 對話框時由框架調用。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>備註

此方法通過從具有與此物件具有相同命令 ID 的任何工具列中的編輯框控制項中的屬性複製來擴展基類實現 ( [CMFCToolBarButton::onAddTo 自訂頁](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage))。 如果沒有工具列具有與此物件具有相同命令 ID 的編輯框控制件,則此方法不執行任何操作。

關於 **「自訂」** 對話框的詳細資訊,請參閱[CMFCToolBars 自訂對話方塊類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolbar編輯盒按鈕::打開更改家長

將按鈕插入到新工具列時由框架調用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向新父視窗的指標。

### <a name="remarks"></a>備註

此方法通過重新創建內部`CEdit`物件來重寫基類實現 ( [CMFCToolBarButton::onChangeParentwnd)。](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a>CMFCToolbar編輯盒按鈕::點擊

當用戶按下滑鼠按鈕時由框架調用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
[在]閑置。

*bDelay*<br/>
[在]閑置。

### <a name="return-value"></a>傳回值

如果按鈕處理按一下消息,則非零;否則 0。

### <a name="remarks"></a>備註

此方法通過在內部`CEdit`物件可見時返回非零值來覆蓋基類實現[(CMFCToolBarButton::OnClick)。](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolbar編輯盒按鈕::在CtlColor上

當父工具列處理WM_CTLCOLOR消息時,框架調用。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]顯示按鈕的設備上下文。

*nCtlColor*<br/>
[在]閑置。

### <a name="return-value"></a>傳回值

全域視窗畫筆的句柄。

### <a name="remarks"></a>備註

此方法通過分別將所提供的設備上下文的文本和背景顏色分別設置為全域文本和背景顏色來覆蓋基類實現[(CMFCToolBarButton::onCtlColor)。](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)

有關應用程式可用的全域選項的詳細資訊,請參閱[AFX_GLOBAL_DATA結構](../../mfc/reference/afx-global-data-structure.md)。

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolbar編輯盒按鈕::在全域字型上更改

當全域字體已更改時由框架調用。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>備註

此方法通過將控制項的字型更改為全域字型來擴展基類實現 ( [CMFCToolBarButton::onGlobalFonts 已更改](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))。

有關應用程式可用的全域選項的詳細資訊,請參閱[AFX_GLOBAL_DATA結構](../../mfc/reference/afx-global-data-structure.md)。

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a>CMFCToolbar編輯盒按鈕::移動

當父工具欄移動時由框架調用。

```
virtual void OnMove();
```

### <a name="remarks"></a>備註

此方法透過更新內部`CEdit`物件的位置來覆寫預設類別 ( [CMFCToolBarButton::onMove)](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a>CMFCToolbar編輯盒按鈕::上展

當按鈕變得可見或不可見時,由框架調用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
[在]指定按鈕是否可見。 如果此參數為 TRUE,則按鈕為可見。 否則,該按鈕不可見。

### <a name="remarks"></a>備註

此方法通過顯示按鈕(如果*bShow*為 TRUE)來擴展基類實現 ( [CMFCToolBarButton::onShow)。](../../mfc/reference/cmfctoolbarbutton-class.md#onshow) 否則,此方法將隱藏該按鈕。

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a>CMFCToolbar編輯盒按鈕::打開尺寸

當父工具列更改其大小或位置且此更改導致按鈕更改大小時,框架調用該按鈕。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>參數

*iSize*<br/>
[在]按鈕的新寬度(以像素為單位)。

### <a name="remarks"></a>備註

此方法通過更新內部`CEdit`物件的大小和位置來覆蓋預設類實現[CMFCToolBarButton::onSize。](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolbar編輯盒按鈕::更新工具提示

當父工具列更新其工具提示文本時,由框架調用。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]閑置。

*iButtonIndex*<br/>
[在]閑置。

*wndToolTip*<br/>
[在]顯示工具提示文字的控制項。

*Str*<br/>
[出]接收`CString`更新的工具提示文字的物件。

### <a name="return-value"></a>傳回值

如果方法更新工具提示文本,則非零;否則 0。

### <a name="remarks"></a>備註

此方法通過顯示與按鈕的編輯部分關聯的工具提示文本來擴展基類實現[(CMFCToolBarButton::onUpdateToolTip)。](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip) 如果內部`CEdit`物件為 NULL 或`CEdit`物件的視窗句柄未標識現有視窗,則此方法不執行任何操作並返回 FALSE。

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a>CMFCToolbar編輯盒按鈕::設定內容

設定文字框控制的文字。

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>參數

*內容*<br/>
[在]指定要設置的新文本。

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a>CMFCToolbar編輯盒按鈕::設定內容所有

尋找具有指定命令 ID 並在其文字框中設置指定文本的[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)物件。

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]指定要為其更改文本的控制項的命令 ID。

*斯特裡特*<br/>
[在]指定要設置的新文本。

### <a name="return-value"></a>傳回值

設置文本時非零;如果具有指定`CMFCToolBarEditBoxButton`命令ID的控制項不存在,則為 0。

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolbar編輯盒按鈕::設定上下文選單ID

指定與按鈕關聯的快捷功能表的資源 ID。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]快捷功能表的資源 ID。

### <a name="remarks"></a>備註

當用戶右鍵按一下工具列按鈕時,框架使用資源 ID 創建快捷功能表。

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolbar編輯盒按鈕::設定平壓模式

指定應用程式中編輯框按鈕的平面樣式外觀。

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>參數

*bFlat*<br/>
[在]編輯框按鈕的平面樣式。 如果此參數為 TRUE,則啟用平面樣式外觀;如果此參數為 TRUE,則啟用平面樣式外觀。否則,平面樣式外觀將禁用。

### <a name="remarks"></a>備註

編輯框按鈕的預設平面樣式為 TRUE。 使用[CMFCToolBar 編輯BoxButton:isFlatMode](#isflatmode)方法檢索應用程式的平面樣式外觀。

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolbar編輯盒按鈕::設定樣式

指定工具列編輯框控制件的樣式。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
[在]要設置的新樣式。

### <a name="remarks"></a>備註

此方法將[CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)設置為*nStyle*當應用程式處於自定義模式時,它還禁用文本框,並在應用程式未處於自定義模式時啟用它(請參閱[CMFCToolBar:set自定義模式](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode)和[CMFCToolBar::是自定義模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))。 有關有效樣式旗標的清單,請參考[工具列控制元件樣式](../../mfc/reference/toolbar-control-styles.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CMFC工具列:更換按鈕](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
