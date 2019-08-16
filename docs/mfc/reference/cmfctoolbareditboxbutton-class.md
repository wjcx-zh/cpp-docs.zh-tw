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
ms.openlocfilehash: 3e988d789ca6a038ce41bca829850f6509fd9df1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504721"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton 類別

包含編輯控制項 ( [CEdit 類別](../../mfc/reference/cedit-class.md)) 的工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|建構 `CMFCToolBarEditBoxButton` 物件。|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|指定使用者是否可以在自訂期間延展按鈕。 (覆寫[CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|將另一個工具列按鈕的屬性複製到目前的按鈕。 (覆寫[CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: CreateEdit](#createedit)|在按鈕中建立新的編輯控制項。|
|`CMFCToolBarEditBoxButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|抓取應用程式`CMFCToolBarEditBoxButton`中具有指定命令識別碼的第一個物件。|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|抓取具有指定命令識別碼之第一個編輯方塊工具列控制項的文字。|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|抓取與按鈕相關聯之快捷方式功能表的資源識別碼。|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|抓取編輯方塊按鈕編輯部分的周框。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: GetEditBox](#geteditbox)|傳回按鈕中內嵌之編輯控制項的指標。|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|抓取與工具列按鈕相關聯的視窗控制碼。 (覆寫[CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|抓取必須重新繪製之按鈕工作區的區域。 (覆寫[CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)。)|
|`CMFCToolBarEditBoxButton::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|決定當使用者按一下按鈕時, 是否要顯示按鈕的框線。 (覆寫[CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|決定編輯方塊按鈕是否具有平面樣式。|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|指定按鈕是否處理[WM_COMMAND](/windows/win32/menurc/wm-command)訊息。 (覆寫[CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|當按鈕加入**自訂**對話方塊時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|由架構呼叫, 以計算指定裝置內容和停駐狀態的按鈕大小。 (覆寫[CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|當按鈕插入新工具列時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|當使用者按一下滑鼠按鍵時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick))。|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|當父工具列處理 WM_CTLCOLOR 訊息時, 由架構呼叫。 (覆寫[CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|
|`CMFCToolBarEditBoxButton::OnDraw`|由架構呼叫, 使用指定的樣式和選項繪製按鈕。 (覆寫[CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|由架構呼叫, 以在 [**自訂**] 對話方塊的 [**命令**] 窗格中繪製按鈕。 (覆寫[CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|全域字型已變更時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|當父工具列移動時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|當按鈕變成可見或不可見時, 由架構呼叫。 (覆寫[CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|由架構在父工具列變更其大小或位置時呼叫, 而這項變更會導致按鈕變更大小。 (覆寫[CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|當父工具列更新其工具提示文字時, 由架構呼叫。 (覆寫[CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|
|`CMFCToolBarEditBoxButton::Serialize`|從封存讀取此物件, 或將它寫入封存。 (覆寫[CMFCToolBarButton:: 序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|
|`CMFCToolBarEditBoxButton::SetACCData`|使用工具列按鈕`CAccessibilityData`的協助工具資料填入提供的物件。 (覆寫[CMFCToolBarButton:: SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)。)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetContents](#setcontents)|設定按鈕的編輯控制項中的文字。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall)|尋找具有指定命令識別碼的編輯控制項按鈕, 並在該按鈕的編輯控制項中設定文字。|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|指定與按鈕相關聯之快捷方式功能表的資源識別碼。|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|指定應用程式中編輯方塊按鈕的平面樣式外觀。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetStyle](#setstyle)|指定按鈕的樣式。 (覆寫[CMFCToolBarButton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|

## <a name="remarks"></a>備註

若要將編輯方塊按鈕新增至工具列, 請依照下列步驟執行:

1. 為父工具列資源的按鈕保留假的資源 ID。

2. `CMFCToolBarEditBoxButton`建立物件。

3. 在處理 AFX_WM_RESETTOOLBAR 訊息的訊息處理常式中, 使用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton), 將虛擬按鈕取代為新的下拉式方塊按鈕。

如需詳細資訊，請參閱[逐步解說：將控制項放在](../../mfc/walkthrough-putting-controls-on-toolbars.md)工具列上。

## <a name="example"></a>範例

下例示範如何在 `CMFCToolBarEditBoxButton` 類別中使用各種方法。 此範例示範如何指定使用者可以在自訂期間延展按鈕, 指定當使用者按一下按鈕、設定文字方塊控制項中的文字、在 & 中指定編輯方塊按鈕的平面樣式外觀時, 會顯示按鈕的框線。程式, 並指定工具列編輯方塊控制項的樣式。

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>需求

**標頭:** afxtoolbareditboxbutton。h

##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBeStretched

指定使用者是否可以在自訂期間延展按鈕。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>傳回值

這個方法會傳回 TRUE。

### <a name="remarks"></a>備註

根據預設, 架構不允許使用者在自訂期間延展工具列按鈕。 這個方法會在自訂期間允許使用者延展編輯方塊工具列按鈕, 以擴充基類實 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))。

##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

結構[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)物件。

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>參數

*uiID*<br/>
在指定控制項識別碼。

*iImage*<br/>
在指定工具列影像之以零為起始的索引。 影像位於[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)類別所維護的[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件中。

*dwStyle*<br/>
在指定編輯控制項樣式。

*iWidth*<br/>
在指定編輯控制項的寬度 (以圖元為單位)。

### <a name="remarks"></a>備註

預設的函式會將編輯控制項樣式設定為下列組合:

WS_CHILD |WS_VISIBLE |ES_AUTOHSCROLL

控制項的預設寬度為150圖元。

##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton:: CopyFrom

將另一個工具列按鈕的屬性複製到目前的按鈕。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]要從中複製來源按鈕參考。

### <a name="remarks"></a>備註

呼叫這個方法, 將另一個工具列按鈕複製到這個工具列按鈕。 *src*的類型`CMFCToolBarEditBoxButton`必須是。

##  <a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit

在按鈕中建立新的編輯控制項。

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在指定編輯控制項的父視窗。 不得為 Null。

*rect*<br/>
在指定編輯控制項的大小和位置。

### <a name="return-value"></a>傳回值

新建立之編輯控制項的指標;如果控制項的建立和附件失敗, 則為 Null。

### <a name="remarks"></a>備註

您可以使用`CMFCToolBarEditBoxButton`兩個步驟來建立物件。 首先呼叫此函式, 然後呼叫`CreateEdit`, 它會建立 Windows 編輯控制項並將其附加`CMFCToolBarEditBoxButton`至物件。

##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

抓取應用程式`CMFCToolBarEditBoxButton`中具有指定命令識別碼的第一個物件。

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在要取出之按鈕的命令 ID。

### <a name="return-value"></a>傳回值

應用程式`CMFCToolBarEditBoxButton`中具有指定命令識別碼的第一個物件, 如果沒有這類物件存在, 則為 Null。

### <a name="remarks"></a>備註

這個共用公用程式方法是由[CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall)和[CMFCToolBarEditBoxButton:: GetContentsAll](#getcontentsall)之類的方法所使用, 以設定或取得具有指定命令識別碼之第一個編輯方塊工具列控制項的文字。

##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

抓取具有指定命令識別碼之第一個編輯方塊工具列控制項的文字。

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在要從其中抓取內容之按鈕的命令 ID。

### <a name="return-value"></a>傳回值

`CString`物件, 包含具有指定命令識別碼之第一個編輯方塊工具列控制項的文字。

### <a name="remarks"></a>備註

如果沒有任何`CMFCToolBarEditBoxButton`物件具有指定的命令識別碼, 這個方法會傳回空字串。

##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetCoNtextMenuID

抓取與按鈕相關聯之快捷方式功能表的資源識別碼。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>傳回值

與按鈕相關聯之快捷方式功能表的資源識別碼, 如果按鈕沒有相關聯的快捷方式功能表, 則為0。

### <a name="remarks"></a>備註

當使用者以滑鼠右鍵按一下按鈕時, 此架構會使用資源識別碼來建立快捷方式功能表。

##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

抓取編輯方塊按鈕編輯部分的周框。

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>參數

*rectBorder*<br/>
脫銷接收周框之`CRect`物件的參考。

### <a name="remarks"></a>備註

這個方法會在用戶端座標中抓取編輯控制項的周框。 它會將每個方向的矩形大小展開一個圖元。

當[CMFCVisualManager:: OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder)方法繪製`CMFCToolBarEditBoxButton`物件周圍的框線時, 會呼叫這個方法。

##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

傳回內嵌在按鈕中的[CEdit 類別](../../mfc/reference/cedit-class.md)控制項的指標。

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>傳回值

按鈕包含之[CEdit 類別](../../mfc/reference/cedit-class.md)控制項的指標。 如果尚未建立`CEdit`控制項, 則為 Null。

### <a name="remarks"></a>備註

您可以藉`CEdit`由呼叫[CMFCToolBarEditBoxButton:: CreateEdit](#createedit)來建立控制項。

##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd

抓取與工具列按鈕相關聯的視窗控制碼。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>傳回值

與按鈕相關聯的視窗控制碼。

### <a name="remarks"></a>備註

這個方法會藉由傳回編輯方塊按鈕的編輯控制項部分的視窗控制碼, 覆寫[CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

抓取必須重新繪製之按鈕工作區的區域。

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>傳回值

`CRect`物件, 指定必須重新繪製的區域。

### <a name="remarks"></a>備註

這個方法會在文字標籤的區域中包含, 藉以擴充基類實[CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)。

##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

決定當使用者按一下按鈕時, 是否要顯示按鈕的框線。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>傳回值

如果按鈕在選取時顯示其框線, 則為非零值;否則為0。

### <a name="remarks"></a>備註

這個方法會在控制項為可見時傳回非零值, 藉以擴充基類實[CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。

##  <a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode

決定編輯方塊按鈕是否具有平面樣式。

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>傳回值

如果按鈕具有平面樣式, 則為非零。否則為0。

### <a name="remarks"></a>備註

根據預設, 編輯方塊按鈕具有平面樣式。 請使用[CMFCToolBarEditBoxButton:: SetFlatMode](#setflatmode)方法來變更應用程式的平面樣式外觀。

##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

指定按鈕是否處理[WM_COMMAND](/windows/win32/menurc/wm-command)訊息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>參數

*iNotifyCode*<br/>
在與命令相關聯的通知訊息。

### <a name="return-value"></a>傳回值

如果按鈕會處理 WM_COMMAND 訊息, 則為 TRUE, 否則為 FALSE, 表示訊息必須由父工具列處理。

### <a name="remarks"></a>備註

當架構即將傳送[WM_COMMAND](/windows/win32/menurc/wm-command)訊息至父視窗時, 會呼叫這個方法。

這個方法會藉由處理[EN_UPDATE](/windows/win32/Controls/en-update)通知來擴充基類實 ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))。 針對與此物件具有相同命令識別碼的每個編輯方塊, 它會將其文字標籤設定為此物件的文字標籤。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage

當按鈕加入**自訂**對話方塊時由架構呼叫。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>備註

這個方法會在與這個物件具有相同命令識別碼的任何工具列中, 從編輯方塊控制項複製屬性, 藉以擴充基類實 ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage))。 如果沒有任何工具列具有與此物件具有相同命令識別碼的編輯方塊控制項, 這個方法就不會執行任何操作。

如需 [**自訂**] 對話方塊的詳細資訊, 請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

當按鈕插入新工具列時由架構呼叫。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在新父視窗的指標。

### <a name="remarks"></a>備註

這個方法會藉由重新建立內部`CEdit`物件來覆寫基類實 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd))。

##  <a name="onclick"></a>CMFCToolBarEditBoxButton:: OnClick

當使用者按一下滑鼠按鍵時由架構呼叫。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
在未使用.

*bDelay*<br/>
在未使用.

### <a name="return-value"></a>傳回值

如果按鈕處理按一下訊息, 則為非零值;否則為0。

### <a name="remarks"></a>備註

這個方法會在內部`CEdit`物件為可見時傳回非零值, 藉此覆寫基類實 ( [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick))。

##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor

當父工具列處理 WM_CTLCOLOR 訊息時, 由架構呼叫。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在顯示按鈕的裝置內容。

*nCtlColor*<br/>
在未使用.

### <a name="return-value"></a>傳回值

全域視窗筆刷的控制碼。

### <a name="remarks"></a>備註

這個方法會將提供之裝置內容的文字和背景色彩分別設定為全域文字和背景色彩, 藉此覆寫基類實 ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor))。

如需應用程式可用之全域選項的詳細資訊, 請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged

全域字型已變更時由架構呼叫。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>備註

這個方法會將控制項的字型變更為全域字型的字型, 藉以擴充基類實 ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))。

如需應用程式可用之全域選項的詳細資訊, 請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove

當父工具列移動時由架構呼叫。

```
virtual void OnMove();
```

### <a name="remarks"></a>備註

這個方法會藉由更新內部`CEdit`物件的位置, 來覆寫預設的類別實 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove))

##  <a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow

當按鈕變成可見或不可見時, 由架構呼叫。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
在指定按鈕是否可見。 如果此參數為 TRUE, 則會顯示此按鈕。 否則, 就不會顯示此按鈕。

### <a name="remarks"></a>備註

如果*bShow*為 TRUE, 則此方法會藉由顯示按鈕來擴充基類實值 ( [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow))。 否則, 這個方法會隱藏按鈕。

##  <a name="onsize"></a>CMFCToolBarEditBoxButton:: OnSize

由架構在父工具列變更其大小或位置時呼叫, 而這項變更會導致按鈕變更大小。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>參數

*iSize*<br/>
在按鈕的新寬度 (以圖元為單位)。

### <a name="remarks"></a>備註

這個方法會藉由更新內部`CEdit`物件的大小和位置, 來覆寫預設的類別實[CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。

##  <a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip

當父工具列更新其工具提示文字時, 由架構呼叫。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在未使用.

*iButtonIndex*<br/>
在未使用.

*wndToolTip*<br/>
在顯示工具提示文字的控制項。

*str*<br/>
脫銷`CString`物件, 接收已更新的工具提示文字。

### <a name="return-value"></a>傳回值

如果方法更新工具提示文字, 則為非零。否則為0。

### <a name="remarks"></a>備註

這個方法會藉由顯示與按鈕的編輯部分相關聯的工具提示文字, 來擴充基類實 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip))。 如果內部`CEdit`物件為 Null, 或`CEdit`物件的視窗控制碼未識別現有的視窗, 則這個方法不會執行任何操作, 而且會傳回 FALSE。

##  <a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents

設定文字方塊控制項中的文字。

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>參數

*sContents*<br/>
在指定要設定的新文字。

##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

尋找具有指定命令識別碼的[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)物件, 並在其文字方塊內設定指定的文字。

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在指定將變更文字之控制項的命令識別碼。

*strContents*<br/>
在指定要設定的新文字。

### <a name="return-value"></a>傳回值

如果已設定文字, 則為非零值;如果具有指定`CMFCToolBarEditBoxButton`命令識別碼的控制項不存在, 則為0。

##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetCoNtextMenuID

指定與按鈕相關聯之快捷方式功能表的資源識別碼。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在快捷方式功能表的資源識別碼。

### <a name="remarks"></a>備註

當使用者以滑鼠右鍵按一下工具列按鈕時, 此架構會使用資源識別碼來建立快捷方式功能表。

##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

指定應用程式中編輯方塊按鈕的平面樣式外觀。

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>參數

*bFlat*<br/>
在編輯方塊按鈕的平面樣式。 如果此參數為 TRUE, 則會啟用平面樣式外觀;否則, 就會停用平面樣式外觀。

### <a name="remarks"></a>備註

編輯方塊按鈕的預設平面樣式為 TRUE。 使用[CMFCToolBarEditBoxButton:: IsFlatMode](#isflatmode)方法來抓取應用程式的平面樣式外觀。

##  <a name="setstyle"></a>CMFCToolBarEditBoxButton:: SetStyle

指定工具列編輯方塊控制項的樣式。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
在要設定的新樣式。

### <a name="remarks"></a>備註

這個方法會將[CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)設定為*nStyle*它也會在應用程式處於自訂模式時停用文字方塊, 並在應用程式不在自訂模式時加以啟用 (請參閱[CMFCToolBar:: SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode)和[CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))。 如需有效樣式旗標的清單, 請參閱[工具列控制項樣式](../../mfc/reference/toolbar-control-styles.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
