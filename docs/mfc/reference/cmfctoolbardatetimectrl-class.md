---
title: CMFCToolBarDateTimeCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2ef8bddd43b8a6102a39dfa20787a627c21bb6a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073028"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl 類別

包含的日期和時間選擇器控制項的工具列按鈕。

## <a name="syntax"></a>語法

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|建構 `CMFCToolBarDateTimeCtrl` 物件。|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|指定使用者是否可以在自訂期間延伸按鈕。 (覆寫[CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|另一個工具列按鈕的屬性複製到目前的按鈕。 (覆寫[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|保留供未來使用。|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|複製文字從工具列按鈕的功能表。|
|`CMFCToolBarDateTimeCtrl::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|擷取第一個`CMFCToolBarDateTimeCtrl`中具有指定之命令識別碼的應用程式物件|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|傳回日期和時間選擇器控制項的指標。|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|擷取工具列按鈕與相關聯的視窗控制代碼。 (覆寫[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|取得選取的時間，從日期和時間選擇器控制項，並將它放在指定的[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構。|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|傳回在選取的時間，從時間選擇器控制項按鈕具有指定的命令 id。|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|決定當使用者選取按鈕時，是否要顯示按鈕的框線。 (覆寫[CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|指定是否要處理按鈕[WM_COMMAND](/windows/desktop/menurc/wm-command)訊息。 (覆寫[CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|加入按鈕時由架構呼叫**自訂** 對話方塊。 (覆寫[CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|由架構呼叫以計算的銜接狀態與指定的裝置內容的按鈕大小。 (覆寫[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|插入新的工具列按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|當使用者按一下控制項時，由架構呼叫。 (覆寫[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|為父工具列處理 WM_CTLCOLOR 訊息時由架構呼叫。 (覆寫[CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|由架構呼叫以繪製按鈕，使用指定的樣式和選項。 (覆寫[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|由架構呼叫以繪製按鈕**命令**窗格**自訂** 對話方塊。 (覆寫[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|當全域的字型變更時由架構呼叫。 (覆寫[CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|為父工具列移動時，由架構呼叫。 (覆寫[CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|由架構呼叫時按鈕會變成可見或不可見。 (覆寫[CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|
|`CMFCToolBarDateTimeCtrl::OnSize`|為父工具列變更它的大小或位置和這項變更會使按鈕將大小變更時由架構呼叫。 (覆寫[CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|為父工具列更新其工具提示文字時，由架構呼叫。 (覆寫[CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|
|`CMFCToolBarDateTimeCtrl::Serialize`|從封存讀取這個物件，或將它寫入封存，(會覆寫[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|將工具列按鈕的樣式設定。 (覆寫[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|設定的時間和日期時間選擇器控制項中。|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|設定具有指定的命令識別碼。 時間選擇器控制項的所有執行個體中的日期和時間|

## <a name="remarks"></a>備註

如需如何使用日期和時間選擇器控制項的範例，請參閱 ToolbarDateTimePicker 範例專案。 如需如何將控制項的按鈕加入至工具列，請參閱[逐步解說： 將工具列控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>需求

**標頭：** afxtoolbardatetimectrl.h

##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched

指定使用者是否可以在自訂期間延伸按鈕。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>傳回值

這個方法會傳回 TRUE。

### <a name="remarks"></a>備註

根據預設，架構不允許使用者在自訂期間延展的工具列按鈕。 此方法擴充的基底類別實作 ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) 藉由讓使用者能夠延展進行自訂時的日期和時間的工具列按鈕。

##  <a name="cmfctoolbardatetimectrl"></a>  CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

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
[in]控制項 id。

*iImage*<br/>
[in]在工具列上的影像索引`CMFCToolBarImages`物件。

*cheaderctrl:: Create*<br/>
[in]樣式`CMFCToolBarDateTimeCtrlImpl`使用者按一下按鈕時所建立的視窗。

*iWidth*<br/>
[in]控制項，單位為像素的寬度。

### <a name="remarks"></a>備註

此物件會初始化為系統日期和時間。 內部的視窗樣式`CMFCToolBarDateTimeCtrlImpl`物件包含*cheaderctrl:: Create*參數和 WS_CHILD 和 WS_VISIBLE 樣式。 您無法使用，以變更這些樣式`CMFCToolBarDateTimeCtrl::SetStyle`。 使用`SetStyle`若要變更的樣式`CMFCToolBarDateTimeCtrl`控制項。

### <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCToolBarDateTimeCtrl`類別。 此程式碼片段是一部分[工具列的日期時間選擇器範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom

另一個工具列按鈕的屬性複製到目前的按鈕。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>參數

*src*<br/>
[in]要從中複製來源按鈕參考。

### <a name="remarks"></a>備註

呼叫這個方法，以將另一個工具列按鈕複製到此工具列按鈕。 *src*必須是型別`CMFCToolBarDateTimeCtrl`。

##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton

複製文字從工具列按鈕的功能表。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>參數

*MenuButton*<br/>
[in][目標] 功能表按鈕的參考。

### <a name="return-value"></a>傳回值

這個方法會傳回 TRUE。

### <a name="remarks"></a>備註

這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) 載入控制項的命令識別碼相關聯的字串資源。 如需有關字串資源的詳細資訊，請參閱[CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)。

##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd

擷取第一個`CMFCToolBarDateTimeCtrl`中具有指定之命令識別碼的應用程式物件

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]要擷取按鈕的命令識別碼。

### <a name="return-value"></a>傳回值

第一個`CMFCToolBarDateTimeCtrl`具有指定的命令 ID，則為 NULL，如果沒有任何應用程式中的物件`CMFCToolBarDateTimeCtrl`物件具有指定的命令識別碼。

### <a name="remarks"></a>備註

這個共用公用程式方法由方法這類[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)並[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)來設定或取得的所有執行個體時的日期和時間選擇器控制項，具有指定的命令識別碼。

##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

傳回日期和時間選擇器控制項的指標。

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>傳回值

日期和時間選擇器控制項; 指標或者，如果控制項不存在，則為 NULL。

### <a name="remarks"></a>備註

`CMFCToolBarDateTimeCtrl`類別初始化`m_pWndDateTime`當您插入的資料成員`CMFCToolBarDateTimeCtrl`工具列物件。

##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd

擷取工具列按鈕與相關聯的視窗控制代碼。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>傳回值

視窗控制代碼所關聯的日期和時間 工具列按鈕。

### <a name="remarks"></a>備註

這個方法會覆寫[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。

##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime

取得選取的時間，從相關聯的日期和時間選擇器控制項，並將它放在指定的[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>參數

*timeDest*<br/>
[out]在第一個多載中， [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)會收到系統時間資訊的物件。 在第二個多載中， [CTime](../../atl-mfc-shared/reference/ctime-class.md)會收到系統時間資訊的物件。

*pTimeDest*<br/>
[out]指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)接收系統時間資訊的結構。 必須不是 NULL。

### <a name="return-value"></a>傳回值

在第一個多載中，如果成功寫入時為非零[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件; 否則為 0。 在第二個和第三個多載中，傳回的值會等於 dwFlag 成員中所設定的 DWORD [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)結構。

### <a name="remarks"></a>備註

方法會設定[NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)結構將 dwFlags 成員表示的日期和時間選擇器是否設定為日期和時間。 如果值等於 GDT_NONE，控制項就會設定為`no date`狀態，並使用 DTS_SHOWNONE 樣式。 如果傳回的值等於 GDT_VALID，系統時間已成功儲存中的目的地位置。

##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll

傳回具有指定的命令識別碼。 時間選擇器控制項按鈕從使用者所選取的時間

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
[in]指定工具列按鈕的命令識別碼。

*timeDest*<br/>
[out]在第一個多載中， [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)會收到系統時間資訊的物件。 在第二個多載中， [CTime](../../atl-mfc-shared/reference/ctime-class.md)會收到系統時間資訊的物件。

*pTimeDest*<br/>
[out]指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)接收系統時間資訊的結構。 必須不是 NULL。

### <a name="return-value"></a>傳回值

如果架構找不到工具列按鈕與命令識別碼相符*uiCmd*，傳回的值是零，在第一個多載中和在其他多載 GDT_NONE。 如果找到工具列按鈕，則傳回值是從呼叫傳回的值相同[CMFCToolBarDateTimeCtrl::GetTime](#gettime)該按鈕。 傳回值為零或 GDT_NONE 可能是按鈕找到時，表示呼叫`GetTime`未傳回有效的日期，某些其他原因。

### <a name="remarks"></a>備註

這個方法會尋找具有指定的命令 ID 及呼叫的工具列按鈕[CMFCToolBarDateTimeCtrl::GetTime](#gettime)該按鈕上的方法。

##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder

決定當使用者選取按鈕時，是否要顯示按鈕的框線。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>傳回值

如果按鈕會顯示其框線選取; 時，非零值。否則為 0。

### <a name="remarks"></a>備註

如果控制項為可見，這個方法會傳回非零值。

##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand

指定是否要處理按鈕[WM_COMMAND](/windows/desktop/menurc/wm-command)訊息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>參數

*iNotifyCode*<br/>
[in]與命令相關聯的通知訊息。

### <a name="return-value"></a>傳回值

如果按鈕處理來指示訊息應該由父工具列的 WM_COMMAND 訊息或 FALSE，則為 TRUE。

### <a name="remarks"></a>備註

要傳送時，架構會呼叫這個方法[WM_COMMAND](/windows/desktop/menurc/wm-command)父視窗的訊息。

此方法擴充的基底類別實作 ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) 處理[DTN_DATETIMECHANGE](/windows/desktop/Controls/dtn-datetimechange)通知。 它會更新的內部時間狀態並更新所有的時間屬性`CMFCToolBarDateTimeCtrl`物件具有相同命令 id。

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

加入按鈕時由架構呼叫**自訂** 對話方塊。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>備註

此方法擴充的基底類別實作中， [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)，藉由屬性複製第一個日期和時間任何具有相同的命令 ID，與此物件的工具列中的控制項。 如果沒有工具列有具有相同的命令識別碼，與此物件的日期和時間控制項，這個方法任何作用。

如需詳細資訊**自訂** 對話方塊中，請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。

##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd

插入新的工具列按鈕時由架構呼叫。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]新的父視窗。

### <a name="remarks"></a>備註

這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 重新建立內部`CMFCToolBarDateTimeCtrlImpl`物件。

##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick

當使用者按一下控制項時，由架構呼叫。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
[in]未使用。

*bDelay*<br/>
[in]未使用。

### <a name="return-value"></a>傳回值

非零值，如果按鈕處理按一下訊息;否則為 0。

### <a name="remarks"></a>備註

這個方法會覆寫基底類別實作中， [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)，藉由傳回非零值，如果內部`CMFCToolBarDateTimeCtrlImpl`物件為可見。

##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor

為父工具列處理 WM_CTLCOLOR 訊息時由架構呼叫。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容，顯示的按鈕。

*nCtlColor*<br/>
[in]未使用。

### <a name="return-value"></a>傳回值

通用架構用來繪製按鈕背景的筆刷控制代碼。

### <a name="remarks"></a>備註

這個方法會覆寫基底類別實作中， [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)，藉由設定文字和背景分別提供的裝置內容全域文字的色彩和背景色彩。

如需可供您的應用程式的全域選項的詳細資訊，請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

當全域的字型變更時由架構呼叫。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>備註

此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) 的全域的字型變更控制項的字型。

如需可供您的應用程式的全域選項的詳細資訊，請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。

##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove

為父工具列移動時，由架構呼叫。

```
virtual void OnMove();
```

### <a name="remarks"></a>備註

這個方法會覆寫預設類別實作 ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) 藉由更新的內部位置`CMFCToolBarDateTimeCtrlImpl`物件。

##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow

由架構呼叫時按鈕會變成可見或不可見。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>參數

*bShow*<br/>
[in]指定按鈕是否可見。 如果此參數為 TRUE，則按鈕會顯示。 否則，按鈕看不到。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) 所顯示的按鈕，如果*bShow*為 TRUE。 否則，這個方法會隱藏按鈕。

##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize

為父工具列變更它的大小或位置和這項變更會使按鈕將大小變更時由架構呼叫。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>參數

*iSize*<br/>
[in]按鈕，像素為單位的新寬度。

### <a name="remarks"></a>備註

這個方法會覆寫預設類別實作 ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) 藉由更新的大小和位置的內部`CMFCToolBarDateTimeCtrlImpl`物件。

##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip

為父工具列更新其工具提示文字時，由架構呼叫。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]父視窗。

*iButtonIndex*<br/>
[in]父代按鈕集合中的按鈕之以零起始的索引。

*wndToolTip*<br/>
[in]顯示工具提示文字的控制項。

*str*<br/>
[out]A`CString`接收更新的工具提示文字的物件。

### <a name="return-value"></a>傳回值

方法會更新的工具提示文字; 如果為非零否則為 0。

### <a name="remarks"></a>備註

此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) 藉由顯示與按鈕相關聯的工具提示文字。 如果未以水平方式停駐按鈕，這個方法不做任何動作，且會傳回 FALSE。

##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime

設定的時間和日期時間選擇器控制項中。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>參數

*timeNew*<br/>
[in]在第一個版本中，參考[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件，包含控制項設定的時間。 在第二個版本中，指標[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，包含控制項設定的時間。

*pTimeNew*<br/>
[in]指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，包含控制項設定的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

日期和時間選擇器控制項中設定的時間，藉由呼叫[CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime)。

##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll

設定具有指定的命令識別碼。 時間選擇器控制項的所有執行個體中的日期和時間

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
[in]指定工具列按鈕的命令識別碼。

*timeNew*<br/>
[in]在第一個版本中， [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件，包含控制項設定的時間。 在第二個版本中，指標[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，包含控制項設定的時間。

*pTimeNew*<br/>
[in]指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，包含控制項設定的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

尋找具有指定的命令 ID 的工具列按鈕，並設定日期和時間選擇器控制項中的時間，藉由呼叫[CMFCToolBarDateTimeCtrl::SetTime](#settime)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)

