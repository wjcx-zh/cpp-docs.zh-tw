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
ms.openlocfilehash: 9aebd55f19a6687554d8d8378ef84ed5932025a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372181"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl 類別

包含日期和時間選取器控制項的工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarDatetimeCtrl::CMFCToolBarDatetimeCtrl](#cmfctoolbardatetimectrl)|建構 `CMFCToolBarDateTimeCtrl` 物件。|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarDatetimeCtrl::可以拉伸](#canbestretched)|指定使用者是否可以在自定義期間拉伸按鈕。 (覆蓋[CMFC 工具列按鈕::可以拉伸](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDatetimectrl::從](#copyfrom)|將另一個工具列按鈕的屬性複製到當前按鈕。 (覆寫[CMFCToolBar 按鈕::從](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)複製。)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|保留供未來使用。|
|[CMFC工具列按鈕::匯出到選單按鈕](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|將工具列按鈕中的文本複製到菜單。|
|`CMFCToolBarDateTimeCtrl::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCToolBarDatetimectrl::GetByCmd](#getbycmd)|檢索應用程式中具有指定`CMFCToolBarDateTimeCtrl`命令 ID 的第一個物件。|
|[CMFCToolBarDatetimeCtrl::取得DatetimeCtrl](#getdatetimectrl)|返回指向日期和時間選取器控制件的指標。|
|[CMFCToolBarDatetimeCtrl::GetHwnd](#gethwnd)|檢索與工具列按鈕關聯的視窗句柄。 (覆蓋[CMFCToolBarButton:取得 Hwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCToolBarDatetimeCtrl::取得時間](#gettime)|從日期和時間選取器控制項獲取所選時間,並將其放入指定的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構中。|
|[CMFCToolBarDatetimeCtrl:取得時間所有](#gettimeall)|從具有指定命令 ID 的時間選取器控制按鈕返回所選時間。|
|[CMFCToolBarDatetimeCtrl::有熱邊界](#havehotborder)|確定當用戶選擇該按鈕時是否顯示按鈕的邊框。 (覆蓋[CMFCToolBar 按鈕::有 Hot 邊框](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDatetimeCtrl::通知命令](#notifycommand)|指定按鈕是否處理[WM_COMMAND](/windows/win32/menurc/wm-command)訊息。 (覆寫[CMFCToolBar 按鈕:通知命令](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolbardatetimectrl::在Addto自定義頁面上](#onaddtocustomizepage)|將按鈕添加到 **「自訂」** 對話框時由框架調用。 (覆寫[CMFC 工具列按鈕::在 Addto 自訂頁](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|由框架呼叫,以計算指定設備上下文和停靠狀態的按鈕大小。 (覆寫[CMFC 工具列按鈕:「正在計算大小](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)」)|
|[CMFCToolBarDatetimectrl::在更改家長](#onchangeparentwnd)|將按鈕插入到新工具列時由框架調用。 (覆寫[CMFC 工具列按鈕:開啟變更父項目](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDatetimectrl::點擊](#onclick)|當用戶單擊控件時由框架調用。 (覆寫[CMFC 工具列按鈕::按下](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDatetimectrl:onCtlColor](#onctlcolor)|當父工具列處理WM_CTLCOLOR消息時,框架調用。 (覆寫[CMFCToolBar 按鈕:OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|框架呼叫使用指定的樣式和選項繪製按鈕。 (覆寫[CMFC 工具列按鈕::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|由框架呼叫以在 **「自訂」** 對話框的 **「命令」** 窗格中繪製按鈕。 (覆寫[CMFC 工具列按鈕:在「繪製」自訂清單](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDatetimectrl::在全域字體上更改](#onglobalfontschanged)|當全域字體已更改時由框架調用。 (覆寫[CMFC 工具列按鈕::在全域字型變更](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDatetimectrl::移動](#onmove)|當父工具欄移動時由框架調用。 (覆寫[CMFC 工具列按鈕::開啟](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)移動 .)|
|[CMFCToolBarDatetimectrl::上展](#onshow)|當按鈕變得可見或不可見時,由框架調用。 (覆寫[CMFCToolBar 按鈕::在顯示](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|當父工具列更改其大小或位置且此更改導致按鈕更改大小時,框架調用該按鈕。 (覆寫[CMFC 工具列按鈕::開啟大小](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDatetimectrl::打開更新工具提示](#onupdatetooltip)|當父工具列更新其工具提示文本時,由框架調用。 (覆寫[CMFC 工具列按鈕:開啟更新工具提示](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|從封存中讀取此物件或寫入檔(覆寫[CMFCToolBarButton::序列化](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。|
|`CMFCToolBarDateTimeCtrl::SetStyle`|設置工具列按鈕的樣式。 (覆寫[CMFC 工具列按鈕::設定樣式](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDatetimeCtrl::設定時間](#settime)|設置時間選取器控制項中的時間和日期。|
|[CMFCToolBarDatetimeCtrl::設定時間所有](#settimeall)|設置具有指定命令 ID 的時間選取器控制件的所有實例中的時間和日期。|

## <a name="remarks"></a>備註

有關如何使用日期和時間選取器控制項的範例,請參閱工具列DateTimePicker範例專案。 有關如何向工具列添加控制按鈕的資訊,請參閱[演練:將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDatetimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxtoolbardatetimectrl.h

## <a name="cmfctoolbardatetimectrlcanbestretched"></a><a name="canbestretched"></a>CMFCToolBarDatetimeCtrl::可以拉伸

指定使用者是否可以在自定義期間拉伸按鈕。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>傳回值

此方法返回 TRUE。

### <a name="remarks"></a>備註

默認情況下,框架不允許使用者在自定義期間拉伸工具列按鈕。 此方法通過允許使用者在自定義期間拉伸日期和時間工具列按鈕來擴展基類實現[(CMFCToolBarButton::CanBe拉伸](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))。

## <a name="cmfctoolbardatetimectrlcmfctoolbardatetimectrl"></a><a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDatetimeCtrl::CMFCToolBarDatetimeCtrl

創建並初始化[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)物件。

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]控件識別碼。

*i 影像*<br/>
[在]工具列物件中圖像的`CMFCToolBarImages`索引。

*dwStyle*<br/>
[在]當用戶按下按鈕時`CMFCToolBarDateTimeCtrlImpl`創建的視窗樣式。

*iWidth*<br/>
[在]控件的寬度(以像素為單位)。

### <a name="remarks"></a>備註

此物件將初始化到系統日期和時間。 內部`CMFCToolBarDateTimeCtrlImpl`物件的視窗樣式包括*dwStyle*參數以及WS_CHILD和WS_VISIBLE樣式。 不能通過使用`CMFCToolBarDateTimeCtrl::SetStyle`來更改這些樣式。 用於`SetStyle`更改控制項的`CMFCToolBarDateTimeCtrl`樣式。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCToolBarDateTimeCtrl`類的物件。 此程式碼段是[工具列日期時間選取器範例的一](../../overview/visual-cpp-samples.md)部分。

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

## <a name="cmfctoolbardatetimectrlcopyfrom"></a><a name="copyfrom"></a>CMFCToolBarDatetimectrl::從

將另一個工具列按鈕的屬性複製到當前按鈕。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[在]對要從中複製的源按鈕的引用。

### <a name="remarks"></a>備註

呼叫此方法以將另一個工具列按鈕複製到此工具列按鈕。 *src*必須是型`CMFCToolBarDateTimeCtrl`態的 。

## <a name="cmfctoolbardatetimectrlexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolbardatetimectrl::匯出到菜單按鈕

將工具列按鈕中的文本複製到菜單。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*選單按鈕*<br/>
[在]對目標功能表按鈕的引用。

### <a name="return-value"></a>傳回值

此方法返回 TRUE。

### <a name="remarks"></a>備註

此方法通過載入與控制項的命令 ID 關聯的字串資源來覆寫基類實現[(CMFCToolBarButton::exportToMenuButton)。](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton) 有關字串資源的詳細資訊,請參閱[CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)。

## <a name="cmfctoolbardatetimectrlgetbycmd"></a><a name="getbycmd"></a>CMFCToolBarDatetimectrl::GetByCmd

檢索應用程式中具有指定`CMFCToolBarDateTimeCtrl`命令 ID 的第一個物件。

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]要檢索的按鈕的命令 ID。

### <a name="return-value"></a>傳回值

應用程式中具有`CMFCToolBarDateTimeCtrl`指定命令 ID 的第一個`CMFCToolBarDateTimeCtrl`物件,如果沒有 物件具有指定的命令 ID,則為 NULL。

### <a name="remarks"></a>備註

此共享實用程式方法由以下方法使用,例如[CMFCToolBarDateTimeCtrl:SetTimeAll](#settimeall)和[CMFCToolBarDateTimeCtrl:GetTimeAll](#gettimeall)用於設定或獲取具有指定命令 ID 的時間選取器控制件的所有實例的時間和日期。

## <a name="cmfctoolbardatetimectrlgetdatetimectrl"></a><a name="getdatetimectrl"></a>CMFCToolBarDatetimeCtrl::取得DatetimeCtrl

返回指向日期和時間選取器控制件的指標。

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>傳回值

指向日期和時間選取器控制件的指標;或 NULL,如果控制項不存在。

### <a name="remarks"></a>備註

當您`CMFCToolBarDateTimeCtrl`將物件插入工具列`m_pWndDateTime`時`CMFCToolBarDateTimeCtrl`, 類別將初始化資料成員。

## <a name="cmfctoolbardatetimectrlgethwnd"></a><a name="gethwnd"></a>CMFCToolBarDatetimeCtrl::GetHwnd

檢索與工具列按鈕關聯的視窗句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>傳回值

與日期和時間工具列按鈕關聯的視窗句柄。

### <a name="remarks"></a>備註

此方法重寫[CMFCToolBarButton:getHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

## <a name="cmfctoolbardatetimectrlgettime"></a><a name="gettime"></a>CMFCToolBarDatetimeCtrl::取得時間

從關聯的日期和時間選取器控制項取得選取時間,並將其置於指定的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構中

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>參數

*時間時間*<br/>
[出]在第一個重載中,將接收系統時間資訊的[COleDateTime 類](../../atl-mfc-shared/reference/coledatetime-class.md)物件。 在第二個重載中,將收到系統時間資訊的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。

*pTimeD*<br/>
[出]指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,用於接收系統時間資訊。 不能為 NULL。

### <a name="return-value"></a>傳回值

在第一個重載中,如果時間成功寫入[COleDateTime 類](../../atl-mfc-shared/reference/coledatetime-class.md)物件,則非零;否則 0。 在第二個和第三個重載中,返回值是 DWORD,它等於[在 NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)結構中設置的 dwFlag 成員。

### <a name="remarks"></a>備註

該方法設定[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)結構成員 dwFlags 以指示日期和時間選取器是否設置為日期和時間。 如果值等於GDT_NONE,則控件將設置為`no date`狀態,並使用DTS_SHOWNONE樣式。 如果返回的值等於GDT_VALID,則系統時間將成功存儲在目標位置。

## <a name="cmfctoolbardatetimectrlgettimeall"></a><a name="gettimeall"></a>CMFCToolBarDatetimeCtrl:取得時間所有

從具有指定命令 ID 的時間選取器控制程式按鈕傳回使用者選擇的時間。

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

*烏伊Cmd*<br/>
[在]指定工具列按鈕的命令 ID。

*時間時間*<br/>
[出]在第一個重載中,將接收系統時間資訊的[COleDateTime 類](../../atl-mfc-shared/reference/coledatetime-class.md)物件。 在第二個重載中,將收到系統時間資訊的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。

*pTimeD*<br/>
[出]指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,用於接收系統時間資訊。 不能為 NULL。

### <a name="return-value"></a>傳回值

如果框架找不到與命令 ID *uiCmd*匹配的工具列按鈕,則返回值在第一次重載中為零,並在其他重載中GDT_NONE。 如果找到工具列按鈕,則返回值與從調用[CMFCToolBarDateTimeCtrl](#gettime)返回值相同:獲取該按鈕上的返回時間。 找到按鈕時,可能會出現零或GDT_NONE的返回值,該按鈕指示對的`GetTime`調用由於某種其他原因未返回有效日期。

### <a name="remarks"></a>備註

此方法查找具有指定命令 ID 並調用該按鈕上的[CMFCToolBarDateTimeCtrl:getTime](#gettime)方法的工具列按鈕。

## <a name="cmfctoolbardatetimectrlhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarDatetimeCtrl::有熱邊界

確定當用戶選擇該按鈕時是否顯示按鈕的邊框。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>傳回值

如果按鈕在選定時顯示其邊框,則非零;否則 0。

### <a name="remarks"></a>備註

如果控件可見,此方法將返回非零值。

## <a name="cmfctoolbardatetimectrlnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarDatetimeCtrl::通知命令

指定按鈕是否處理[WM_COMMAND](/windows/win32/menurc/wm-command)訊息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>參數

*iNotify代碼*<br/>
[在]與命令關聯的通知消息。

### <a name="return-value"></a>傳回值

如果按鈕處理WM_COMMAND消息,則為 TRUE,或 FALSE 指示該消息應由父工具列處理。

### <a name="remarks"></a>備註

當此方法要向父視窗發送[WM_COMMAND](/windows/win32/menurc/wm-command)訊息時,框架將調用此方法。

此方法通過處理[DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange)通知擴展基類實現 ( [CMFCToolBarButton::通知命令](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))。 它更新內部時間狀態,並更新具有相同命令`CMFCToolBarDateTimeCtrl`ID 的所有物件的時間屬性。

## <a name="cmfctoolbardatetimectrlonaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolbardatetimectrl::在Addto自定義頁面上

將按鈕添加到 **「自訂」** 對話框時由框架調用。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>備註

這個方法以複製有相同物件的指令 ID 的任何工具列中的第一個日期和時間控制項的屬性來延伸基項實現[CMFCToolBarButton::onAddTo自訂頁](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。 如果沒有工具列具有與此物件具有相同命令 ID 的日期和時間控制項,則此方法不執行任何操作。

關於 **「自訂」** 對話框的詳細資訊,請參閱[CMFCToolBars 自訂對話方塊類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

## <a name="cmfctoolbardatetimectrlonchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarDatetimectrl::在更改家長

將按鈕插入到新工具列時由框架調用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]新的父視窗。

### <a name="remarks"></a>備註

此方法通過重新創建內部`CMFCToolBarDateTimeCtrlImpl`物件來重寫基類實現 ( [CMFCToolBarButton::onChangeParentwnd)。](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)

## <a name="cmfctoolbardatetimectrlonclick"></a><a name="onclick"></a>CMFCToolBarDatetimectrl::點擊

當用戶單擊控件時由框架調用。

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

此方法重寫基類實現[CMFCToolBarButton::onClick,](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)通過`CMFCToolBarDateTimeCtrlImpl`在內部 物件可見時返回非零值。

## <a name="cmfctoolbardatetimectrlonctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarDatetimectrl:onCtlColor

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

框架用於繪製按鈕背景的全域畫筆的句柄。

### <a name="remarks"></a>備註

此方法通過分別將所提供的設備上下文的文本和背景顏色分別設置為全域文本和背景顏色來覆蓋基類實現[CMFCToolBarButton:onCtlColor。](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)

有關應用程式可用的全域選項的詳細資訊,請參閱[AFX_GLOBAL_DATA結構](../../mfc/reference/afx-global-data-structure.md)。

## <a name="cmfctoolbardatetimectrlonglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarDatetimectrl::在全域字體上更改

當全域字體已更改時由框架調用。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>備註

此方法通過將控制項的字型更改為全域字型來擴展基類實現 ( [CMFCToolBarButton::onGlobalFonts 已更改](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))。

有關應用程式可用的全域選項的詳細資訊,請參閱[AFX_GLOBAL_DATA結構](../../mfc/reference/afx-global-data-structure.md)。

## <a name="cmfctoolbardatetimectrlonmove"></a><a name="onmove"></a>CMFCToolBarDatetimectrl::移動

當父工具欄移動時由框架調用。

```
virtual void OnMove();
```

### <a name="remarks"></a>備註

此方法通過更新內部`CMFCToolBarDateTimeCtrlImpl`物件的位置來重寫預設類實現 ( [CMFCToolBarButton::onMove)。](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)

## <a name="cmfctoolbardatetimectrlonshow"></a><a name="onshow"></a>CMFCToolBarDatetimectrl::上展

當按鈕變得可見或不可見時,由框架調用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
[在]指定按鈕是否可見。 如果此參數為 TRUE,則按鈕為可見。 否則,該按鈕不可見。

### <a name="remarks"></a>備註

此方法通過顯示按鈕(如果*bShow*為 TRUE)來擴展基類實現 ( [CMFCToolBarButton::onShow)。](../../mfc/reference/cmfctoolbarbutton-class.md#onshow) 否則,此方法將隱藏該按鈕。

## <a name="cmfctoolbardatetimectrlonsize"></a><a name="onsize"></a>CMFCToolBarDatetimectrl::打開尺寸

當父工具列更改其大小或位置且此更改導致按鈕更改大小時,框架調用該按鈕。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>參數

*iSize*<br/>
[在]按鈕的新寬度(以像素為單位)。

### <a name="remarks"></a>備註

此方法通過更新內部`CMFCToolBarDateTimeCtrlImpl`物件的大小和位置來覆蓋預設類實現 ( [CMFCToolBarButton::onSize)。](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)

## <a name="cmfctoolbardatetimectrlonupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarDatetimectrl::打開更新工具提示

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
[在]父視窗。

*iButtonIndex*<br/>
[在]父按鈕集合中按鈕的零基索引。

*wndToolTip*<br/>
[在]顯示工具提示文字的控制項。

*Str*<br/>
[出]接收`CString`更新的工具提示文字的物件。

### <a name="return-value"></a>傳回值

如果方法更新工具提示文本,則非零;否則 0。

### <a name="remarks"></a>備註

此方法通過顯示與按鈕關聯的工具提示文本來擴展基類實現[(CMFCToolBarButton::onUpdateToolTip)。](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip) 如果按鈕未水準停靠,則此方法不執行任何操作並返回 FALSE。

## <a name="cmfctoolbardatetimectrlsettime"></a><a name="settime"></a>CMFCToolBarDatetimeCtrl::設定時間

設置時間選取器控制項中的時間和日期。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>參數

*時間新*<br/>
[在]在第一個版本中,對包含將控制項設置為的時間的[COleDateTime 類](../../atl-mfc-shared/reference/coledatetime-class.md)物件的引用。 在第二個版本中,指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的指標,該物件包含將控制項設定為的時間。

*pTimeNew*<br/>
[在]指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含將控制項設置為的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

通過調用[CDateTimeCtrl::setTime,](../../mfc/reference/cdatetimectrl-class.md#settime)設定日期和時間選取器控制項中的時間。

## <a name="cmfctoolbardatetimectrlsettimeall"></a><a name="settimeall"></a>CMFCToolBarDatetimeCtrl::設定時間所有

設置具有指定命令 ID 的時間選取器控制件的所有實例中的時間和日期。

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

*烏伊Cmd*<br/>
[在]指定工具列按鈕的命令 ID。

*時間新*<br/>
[在]在第一版本中,包含將控制項設置為的時間的[COleDateTime 類](../../atl-mfc-shared/reference/coledatetime-class.md)物件。 在第二個版本中,指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的指標,該物件包含將控制項設定為的時間。

*pTimeNew*<br/>
[在]指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含將控制項設置為的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

尋找具有指定命令 ID 的工具列按鈕,並透過除錯[CMFCToolBarDateTimeCtrl::SetTime](#settime)來設定日期和時間選取器控制項中的時間。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
