---
title: CMFCToolBarDateTimeCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: 7ab6a240a403e70446ebc1860474f6cb9e1d71e3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504767"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl 類別

包含日期和時間選擇器控制項的工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|建構 `CMFCToolBarDateTimeCtrl` 物件。|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|指定使用者是否可以在自訂期間延展按鈕。 (覆寫[CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|將另一個工具列按鈕的屬性複製到目前的按鈕。 (覆寫[CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|保留供未來使用。|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|將文字從工具列按鈕複製到功能表。|
|`CMFCToolBarDateTimeCtrl::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|抓取應用程式`CMFCToolBarDateTimeCtrl`中具有指定命令識別碼的第一個物件。|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|傳回日期和時間選擇器控制項的指標。|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|抓取與工具列按鈕相關聯的視窗控制碼。 (覆寫[CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|從日期和時間選擇器控制項取得選取的時間, 並將它放在指定的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構中。|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|從具有指定命令識別碼的時間選擇器控制項按鈕傳回選取的時間。|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|決定當使用者選取按鈕時, 是否要顯示按鈕的框線。 (覆寫[CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|指定按鈕是否處理[WM_COMMAND](/windows/win32/menurc/wm-command)訊息。 (覆寫[CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|當按鈕加入**自訂**對話方塊時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|由架構呼叫, 以計算指定裝置內容和停駐狀態的按鈕大小。 (覆寫[CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|當按鈕插入新工具列時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|當使用者按一下控制項時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick))。|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|當父工具列處理 WM_CTLCOLOR 訊息時, 由架構呼叫。 (覆寫[CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|由架構呼叫, 使用指定的樣式和選項繪製按鈕。 (覆寫[CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|由架構呼叫, 以在 [**自訂**] 對話方塊的 [**命令**] 窗格中繪製按鈕。 (覆寫[CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|全域字型已變更時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|當父工具列移動時由架構呼叫。 (覆寫[CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|當按鈕變成可見或不可見時, 由架構呼叫。 (覆寫[CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|
|`CMFCToolBarDateTimeCtrl::OnSize`|由架構在父工具列變更其大小或位置時呼叫, 而這項變更會導致按鈕變更大小。 (覆寫[CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|當父工具列更新其工具提示文字時, 由架構呼叫。 (覆寫[CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|
|`CMFCToolBarDateTimeCtrl::Serialize`|從封存讀取此物件, 或將它寫入封存 (覆寫[CMFCToolBarButton:: 序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|設定工具列按鈕的樣式。 (覆寫[CMFCToolBarButton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|設定時間選擇器控制項中的時間和日期。|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|在時間選擇器控制項的所有實例中設定具有指定命令識別碼的時間和日期。|

## <a name="remarks"></a>備註

如需如何使用日期和時間選擇器控制項的範例, 請參閱 ToolbarDateTimePicker 範例專案。 如需如何將控制項按鈕新增至工具列的詳細資訊[, 請參閱逐步解說:將控制項放在](../../mfc/walkthrough-putting-controls-on-toolbars.md)工具列上。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>需求

**標頭:** afxtoolbardatetimectrl。h

##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched

指定使用者是否可以在自訂期間延展按鈕。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>傳回值

這個方法會傳回 TRUE。

### <a name="remarks"></a>備註

根據預設, 架構不允許使用者在自訂期間延展工具列按鈕。 這個方法會在自訂期間允許使用者延展 [日期和時間] 工具列按鈕, 以擴充基類實 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))。

##  <a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

建立並初始化[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)物件。

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>參數

*uiID*<br/>
在控制項識別碼。

*iImage*<br/>
在工具列`CMFCToolBarImages`物件中影像的索引。

*dwStyle*<br/>
在使用者按一下按鈕時`CMFCToolBarDateTimeCtrlImpl`所建立的視窗樣式。

*iWidth*<br/>
在控制項的寬度 (以圖元為單位)。

### <a name="remarks"></a>備註

這個物件會初始化為系統日期和時間。 內部`CMFCToolBarDateTimeCtrlImpl`物件的視窗樣式包括*dwStyle*參數和 WS_CHILD 和 WS_VISIBLE 樣式。 您無法使用`CMFCToolBarDateTimeCtrl::SetStyle`來變更這些樣式。 用`SetStyle`來變更`CMFCToolBarDateTimeCtrl`控制項的樣式。

### <a name="example"></a>範例

下列範例示範如何建立`CMFCToolBarDateTimeCtrl`類別的物件。 此程式碼片段是[工具列日期時間選擇器範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCToolBarDateTimeCtrl:: CopyFrom

將另一個工具列按鈕的屬性複製到目前的按鈕。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]要從中複製來源按鈕參考。

### <a name="remarks"></a>備註

呼叫這個方法, 將另一個工具列按鈕複製到這個工具列按鈕。 *src*的類型`CMFCToolBarDateTimeCtrl`必須是。

##  <a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton

將文字從工具列按鈕複製到功能表。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*menuButton*<br/>
在[目標] 功能表按鈕的參考。

### <a name="return-value"></a>傳回值

這個方法會傳回 TRUE。

### <a name="remarks"></a>備註

這個方法會載入與控制項的命令識別碼相關聯的字串資源, 以覆寫基類實 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton))。 如需有關字串資源的詳細資訊, 請參閱[CStringT:: loadstring 時](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)。

##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

抓取應用程式`CMFCToolBarDateTimeCtrl`中具有指定命令識別碼的第一個物件。

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在要取出之按鈕的命令 ID。

### <a name="return-value"></a>傳回值

應用程式`CMFCToolBarDateTimeCtrl`中具有指定命令識別碼的第一個物件, 如果沒有任何`CMFCToolBarDateTimeCtrl`物件具有指定的命令識別碼, 則為 Null。

### <a name="remarks"></a>備註

這個共用公用程式方法是由[CMFCToolBarDateTimeCtrl:: SetTimeAll](#settimeall)和[CMFCToolBarDateTimeCtrl:: GetTimeAll](#gettimeall)之類的方法所使用, 以設定或取得時間選擇器控制項中具有指定命令識別碼之所有實例的時間和日期。

##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

傳回日期和時間選擇器控制項的指標。

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>傳回值

日期和時間選擇器控制項的指標;如果控制項不存在, 則為 Null。

### <a name="remarks"></a>備註

當`CMFCToolBarDateTimeCtrl`您將`CMFCToolBarDateTimeCtrl`物件`m_pWndDateTime`插入工具列時, 類別會初始化資料成員。

##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd

抓取與工具列按鈕相關聯的視窗控制碼。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>傳回值

與 [日期和時間] 工具列按鈕相關聯的視窗控制碼。

### <a name="remarks"></a>備註

這個方法會覆寫[CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl:: GetTime

從相關聯的日期和時間選擇器控制項取得選取的時間, 並將它放在指定的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構中

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>參數

*timeDest*<br/>
脫銷在第一個多載中, 會接收系統時間資訊的[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件。 在第二個多載中, 會收到系統時間資訊的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。

*pTimeDest*<br/>
脫銷要接收系統時間資訊之[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標。 不得為 Null。

### <a name="return-value"></a>傳回值

在第一個多載中, 如果時間已成功寫入[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件, 則為非零。否則為0。 在第二個和第三個多載中, 傳回值是一個 DWORD, 它等於[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)結構中所設定的 dwFlag 成員。

### <a name="remarks"></a>備註

方法會設定[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)結構成員 dwFlags, 以指出日期和時間選擇器是否設定為日期和時間。 如果值等於 GDT_NONE, 則控制項會設定為`no date` status, 並使用 DTS_SHOWNONE 樣式。 如果傳回的值等於 GDT_VALID, 系統時間就會成功地儲存在目的地位置。

##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

從具有指定命令識別碼的時間選擇器控制項按鈕, 傳回使用者所選取的時間。

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在指定工具列按鈕的命令 ID。

*timeDest*<br/>
脫銷在第一個多載中, 會接收系統時間資訊的[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件。 在第二個多載中, 會收到系統時間資訊的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。

*pTimeDest*<br/>
脫銷要接收系統時間資訊之[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標。 不得為 Null。

### <a name="return-value"></a>傳回值

如果架構找不到符合命令 ID *uiCmd*的工具列按鈕, 則第一個多載中的傳回值會是零, 而在其他多載中則是 GDT_NONE。 如果找到工具列按鈕, 則傳回值與在該按鈕上呼叫[CMFCToolBarDateTimeCtrl:: GetTime](#gettime)的傳回值相同。 當找到按鈕時, 可能會傳回零或 GDT_NONE 的傳回值, 這表示呼叫`GetTime`並未因其他原因而傳回有效的日期。

### <a name="remarks"></a>備註

這個方法會尋找具有指定命令識別碼的工具列按鈕, 並在該按鈕上呼叫[CMFCToolBarDateTimeCtrl:: GetTime](#gettime)方法。

##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

決定當使用者選取按鈕時, 是否要顯示按鈕的框線。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>傳回值

如果按鈕在選取時顯示其框線, 則為非零值;否則為0。

### <a name="remarks"></a>備註

如果控制項為可見, 這個方法會傳回非零值。

##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

指定按鈕是否處理[WM_COMMAND](/windows/win32/menurc/wm-command)訊息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>參數

*iNotifyCode*<br/>
在與命令相關聯的通知訊息。

### <a name="return-value"></a>傳回值

如果按鈕會處理 WM_COMMAND 訊息, 則為 TRUE, 否則為 FALSE, 表示應該由父工具列來處理訊息。

### <a name="remarks"></a>備註

當架構即將傳送[WM_COMMAND](/windows/win32/menurc/wm-command)訊息至父視窗時, 會呼叫這個方法。

這個方法會藉由處理[DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange)通知來擴充基類實 ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))。 它會更新內部時間狀態, 並使用相同的命令識別碼`CMFCToolBarDateTimeCtrl`來更新所有物件的 time 屬性。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

當按鈕加入**自訂**對話方塊時由架構呼叫。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>備註

這個方法會從與這個物件具有相同命令識別碼的任何工具列中, 複製第一個日期和時間控制項的屬性, 以擴充基類的實[CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。 如果沒有任何工具列具有與這個物件具有相同命令識別碼的日期和時間控制項, 這個方法就不會執行任何操作。

如需 [**自訂**] 對話方塊的詳細資訊, 請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

當按鈕插入新工具列時由架構呼叫。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在新的父視窗。

### <a name="remarks"></a>備註

這個方法會藉由重新建立內部`CMFCToolBarDateTimeCtrlImpl`物件來覆寫基類實 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd))。

##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl:: OnClick

當使用者按一下控制項時由架構呼叫。

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

這個方法會藉由在內部`CMFCToolBarDateTimeCtrlImpl`物件為可見時傳回非零值, 來覆寫基類實[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。

##  <a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

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

架構用來繪製按鈕背景之全域筆刷的控制碼。

### <a name="remarks"></a>備註

這個方法會將提供之裝置內容的文字和背景色彩分別設定為全域文字和背景色彩, 藉此覆寫基類實[CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。

如需應用程式可用之全域選項的詳細資訊, 請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

全域字型已變更時由架構呼叫。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>備註

這個方法會將控制項的字型變更為全域字型的字型, 藉以擴充基類實 ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))。

如需應用程式可用之全域選項的詳細資訊, 請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove

當父工具列移動時由架構呼叫。

```
virtual void OnMove();
```

### <a name="remarks"></a>備註

這個方法會藉由更新內部`CMFCToolBarDateTimeCtrlImpl`物件的位置, 來覆寫預設的類別實 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove))。

##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow

當按鈕變成可見或不可見時, 由架構呼叫。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
在指定按鈕是否可見。 如果此參數為 TRUE, 則會顯示此按鈕。 否則, 就不會顯示此按鈕。

### <a name="remarks"></a>備註

如果*bShow*為 TRUE, 則此方法會藉由顯示按鈕來擴充基類實值 ( [CMFCToolBarButton:: OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow))。 否則, 這個方法會隱藏按鈕。

##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl:: OnSize

由架構在父工具列變更其大小或位置時呼叫, 而這項變更會導致按鈕變更大小。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>參數

*iSize*<br/>
在按鈕的新寬度 (以圖元為單位)。

### <a name="remarks"></a>備註

這個方法會藉由更新內部`CMFCToolBarDateTimeCtrlImpl`物件的大小和位置, 來覆寫預設的類別實 ( [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize))。

##  <a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip

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
在父視窗。

*iButtonIndex*<br/>
在父按鈕集合中按鈕之以零為起始的索引。

*wndToolTip*<br/>
在顯示工具提示文字的控制項。

*str*<br/>
脫銷`CString`物件, 接收已更新的工具提示文字。

### <a name="return-value"></a>傳回值

如果方法更新工具提示文字, 則為非零。否則為0。

### <a name="remarks"></a>備註

這個方法會藉由顯示與按鈕相關聯的工具提示文字, 來擴充基類實 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip))。 如果按鈕未水準停駐, 這個方法就不會執行任何操作, 而且會傳回 FALSE。

##  <a name="settime"></a>CMFCToolBarDateTimeCtrl:: SetTime

設定時間選擇器控制項中的時間和日期。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>參數

*timeNew*<br/>
在在第一個版本中, [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件的參考, 其中包含將設定控制項的時間。 在第二個版本中, 包含將設定控制項之時間的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件指標。

*pTimeNew*<br/>
在[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含將設定控制項的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

藉由呼叫[CDateTimeCtrl:: SetTime](../../mfc/reference/cdatetimectrl-class.md#settime), 設定日期和時間選擇器控制項中的時間。

##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll

在時間選擇器控制項的所有實例中設定具有指定命令識別碼的時間和日期。

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在指定工具列按鈕的命令 ID。

*timeNew*<br/>
在在第一個版本中, 包含將設定控制項之時間的[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件。 在第二個版本中, 包含將設定控制項之時間的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件指標。

*pTimeNew*<br/>
在[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含將設定控制項的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

尋找具有指定命令識別碼的工具列按鈕, 並藉由呼叫[CMFCToolBarDateTimeCtrl:: SetTime](#settime)來設定日期和時間選擇器控制項中的時間。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
