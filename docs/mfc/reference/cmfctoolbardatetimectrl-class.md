---
title: "CMFCToolBarDateTimeCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 60e9427b569c7f3e15b779b0764e0316945880b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl 類別
包含日期和時間選擇器控制項的工具列按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|建構 `CMFCToolBarDateTimeCtrl` 物件。|  
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|指定使用者是否可以在自訂期間延伸按鈕。 (覆寫[CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)。)|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|將另一個工具列按鈕的內容複製到目前的按鈕。 (覆寫[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)。)|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|保留供未來使用。|  
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|複製文字從工具列按鈕加入的功能表。|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|擷取第一個`CMFCToolBarDateTimeCtrl`中具有指定之命令識別碼的應用程式物件|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|傳回日期和時間選擇器控制項的指標。|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|擷取工具列按鈕與相關聯的視窗控制代碼。 (覆寫[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)。)|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|取得選取的時間從日期和時間選擇器控制項，並將它放在指定的[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構。|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|傳回選取的時間，在時間選擇器控制項的按鈕中具有指定的命令識別碼。|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|決定當使用者選擇按鈕時，是否要顯示按鈕的框線。 (覆寫[CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)。)|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|指定是否要處理按鈕[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息。 (覆寫[CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)。)|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|加入按鈕時由架構呼叫**自訂** 對話方塊。 (覆寫[CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)。)|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|由架構呼叫以計算指定之裝置內容和停駐狀態的按鈕的大小。 (覆寫[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)。)|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|插入新的工具列按鈕時由架構呼叫。 (覆寫[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)。)|  
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|當使用者按一下控制項時，由架構呼叫。 (覆寫[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)。)|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|為父工具列處理時，由架構呼叫`WM_CTLCOLOR`訊息。 (覆寫[CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)。)|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|由架構呼叫以繪製按鈕，使用指定的樣式和選項。 (覆寫[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)。)|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|由架構呼叫以繪製按鈕**命令**窗格**自訂** 對話方塊。 (覆寫[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。)|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|當全域字型變更時由架構呼叫。 (覆寫[CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)。)|  
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|為父工具列移動時由架構呼叫。 (覆寫[CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)。)|  
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|由架構呼叫時，按鈕會變成可見或不可見。 (覆寫[CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)。)|  
|`CMFCToolBarDateTimeCtrl::OnSize`|為父工具列變更它的大小或位置，這項變更會使按鈕將大小變更時由架構呼叫。 (覆寫[CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)。)|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|為父工具列更新其工具提示文字時，由架構呼叫。 (覆寫[CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)。)|  
|`CMFCToolBarDateTimeCtrl::Serialize`|從封存讀取此物件，或將它寫入至封存 (會覆寫[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)。)|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|工具列按鈕的樣式設定。 (覆寫[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。)|  
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|設定時間和日期時間選擇器控制項中。|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|設定的時間和日期時間選擇器控制項的所有具有指定的命令識別碼的執行個體|  
  
## <a name="remarks"></a>備註  
 如需如何使用日期和時間選擇器控制項的範例，請參閱 ToolbarDateTimePicker 範例專案。 如需如何將控制項的按鈕加入至工具列，請參閱[逐步解說： 將工具列控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtoolbardatetimectrl.h  
  
##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched  
 指定使用者是否可以在自訂期間延伸按鈕。  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此方法會傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 根據預設，架構不允許使用者在自訂期間 stretch 工具列按鈕。 此方法擴充的基底類別實作 ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) 允許使用者以延伸進行自訂時的日期和時間的工具列按鈕。  
  
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
 [in] `uiID`  
 控制項 id。  
  
 [in] `iImage`  
 在工具列上的映像的索引`CMFCToolBarImages`物件。  
  
 [in] `dwStyle`  
 樣式`CMFCToolBarDateTimeCtrlImpl`當使用者按一下按鈕時所建立的視窗。  
  
 [in] `iWidth`  
 控制項的寬度 (單位為像素)。  
  
### <a name="remarks"></a>備註  
 此物件會初始化為系統日期和時間。 內部的視窗樣式`CMFCToolBarDateTimeCtrlImpl`物件包含`dwStyle`參數和`WS_CHILD`和`WS_VISIBLE`樣式。 您無法使用，以變更這些樣式`CMFCToolBarDateTimeCtrl::SetStyle`。 使用`SetStyle`變更樣式`CMFCToolBarDateTimeCtrl`控制項。  
  
### <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCToolBarDateTimeCtrl`類別。 此程式碼片段是部分[工具列日期時間選擇器範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom  
 將另一個工具列按鈕的內容複製到目前的按鈕。  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
 要從中複製來源 按鈕參考。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，將另一個工具列按鈕複製到此工具列按鈕。 `src`必須是型別`CMFCToolBarDateTimeCtrl`。  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton  
 複製文字從工具列按鈕加入的功能表。  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `menuButton`  
 目標功能表按鈕的參考。  
  
### <a name="return-value"></a>傳回值  
 此方法會傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) 所載入之字串資源的相關聯控制項的命令識別碼。 如需字串資源的詳細資訊，請參閱[CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)。  
  
##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd  
 擷取第一個`CMFCToolBarDateTimeCtrl`中具有指定之命令識別碼的應用程式物件  
  
```  
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 要擷取按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 第一個`CMFCToolBarDateTimeCtrl`具有指定的命令 ID，在應用程式中的物件或`NULL`有`CMFCToolBarDateTimeCtrl`物件具有指定的命令識別碼。  
  
### <a name="remarks"></a>備註  
 這類的方法使用這個共用公用程式方法是[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)和[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)設定或取得的所有執行個體時的日期和時間選擇器控制項，具有指定的命令識別碼。  
  
##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl  
 傳回日期和時間選擇器控制項的指標。  
  
```  
CDateTimeCtrl* GetDateTimeCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 日期和時間選擇器控制項; 的指標或`NULL`如果控制項不存在。  
  
### <a name="remarks"></a>備註  
 `CMFCToolBarDateTimeCtrl`類別初始化`m_pWndDateTime`資料成員，當您插入`CMFCToolBarDateTimeCtrl`成為工具列物件。  
  
##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd  
 擷取工具列按鈕與相關聯的視窗控制代碼。  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>傳回值  
 視窗控制代碼 [日期和時間] 工具列按鈕與相關聯。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)方法。  
  
##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime  
 取得選取的時間從相關聯的日期和時間選擇器控制項，並將它放在指定的[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>參數  
 `[out] timeDest`  
 在第一個多載， [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)將會收到系統時間資訊的物件。 在第二個多載， [CTime](../../atl-mfc-shared/reference/ctime-class.md)將會收到系統時間資訊的物件。  
  
 `[out] pTimeDest`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)接收系統時間資訊的結構。 必須不是 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 在第一個多載中，如果已成功寫入時間則為非零[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件; 否則為 0。 在第二個和第三個多載，則傳回值是`DWORD`等於在已設定的 dwFlag 成員[NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730)結構。  
  
### <a name="remarks"></a>備註  
 方法會設定[NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730)結構成員將 dwFlags，表示是否要將日期和時間選擇器設定日期和時間。 如果值等於 GDT_NONE，控制設為 `no date`狀態，並使用 DTS_SHOWNONE 樣式。 如果傳回的值等於 GDT_VALID，系統時間已成功儲存在目的地位置。  
  
##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll  
 傳回具有指定之命令識別碼的時間選擇器控制項按鈕從使用者選取的時間  
  
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
 `[in] uiCmd`  
 指定工具列按鈕的命令識別碼。  
  
 `[out] timeDest`  
 在第一個多載， [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)將會收到系統時間資訊的物件。 在第二個多載， [CTime](../../atl-mfc-shared/reference/ctime-class.md)將會收到系統時間資訊的物件。  
  
 `[out] pTimeDest`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)接收系統時間資訊的結構。 必須不是 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 如果架構找不到符合的命令 ID 的工具列按鈕`uiCmd`，傳回的值為零，在第一個多載，GDT_NONE 中其他多載。 如果找到工具列按鈕，傳回值是從呼叫傳回的值相同[CMFCToolBarDateTimeCtrl::GetTime](#gettime)對該按鈕。 傳回值 0 或 GDT_NONE 按鈕找到時，這表示可能會發生在呼叫`GetTime`未傳回有效的日期，因其他原因。  
  
### <a name="remarks"></a>備註  
 這個方法會尋找具有指定的命令 ID 及呼叫工具列按鈕[CMFCToolBarDateTimeCtrl::GetTime](#gettime)該按鈕上的方法。  
  
##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder  
 決定當使用者選擇按鈕時，是否要顯示按鈕的框線。  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按鈕會顯示其框線時選取; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果控制項為可見，這個方法會傳回非零值。  
  
##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand  
 指定是否要處理按鈕[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息。  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>參數  
 [in] `iNotifyCode`  
 與命令相關聯的通知訊息。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕處理`WM_COMMAND`訊息，或`FALSE`來指示訊息應該由父工具列。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，當它是傳送[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)父視窗的訊息。  
  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) 藉由處理[DTN_DATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761737)通知。 它會更新內部時間狀態並更新所有的時間屬性`CMFCToolBarDateTimeCtrl`物件具有相同命令 id。  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage  
 加入按鈕時由架構呼叫**自訂** 對話方塊。  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作， [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)、 藉由複製屬性，從第一個日期和時間任何已經與此物件的相同命令 ID 的工具列中的控制項。 如果沒有工具列中的日期和時間的控制項具有相同的命令 ID，與此物件，這個方法任何作用。  
  
 如需有關**自訂**對話方塊中，請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd  
 插入新的工具列按鈕時由架構呼叫。  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 新的父視窗。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 重新建立內部`CMFCToolBarDateTimeCtrlImpl`物件。  
  
##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick  
 當使用者按一下控制項時，由架構呼叫。  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 未使用。  
  
 [in] `bDelay`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 如果按鈕處理按一下的訊息; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作中， [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)，藉由傳回非零值，如果內部`CMFCToolBarDateTimeCtrlImpl`物件為可見。  
  
##  <a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor  
 為父工具列處理時，由架構呼叫`WM_CTLCOLOR`訊息。  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容顯示的按鈕。  
  
 [in] `nCtlColor`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 通用架構會使用來繪製按鈕的背景的筆刷控制代碼。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作中， [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)、 藉由設定文字和背景分別提供的裝置內容，以全域文字的色彩和背景色彩。  
  
 如需全域選項，可用於您的應用程式的詳細資訊，請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged  
 當全域字型變更時由架構呼叫。  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) 的全域字型變更控制項的字型。  
  
 如需全域選項，可用於您的應用程式的詳細資訊，請參閱[AFX_GLOBAL_DATA 結構](../../mfc/reference/afx-global-data-structure.md)。  
  
##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove  
 為父工具列移動時由架構呼叫。  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫預設類別實作 ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) 藉由更新內部的位置`CMFCToolBarDateTimeCtrlImpl`物件。  
  
##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow  
 由架構呼叫時，按鈕會變成可見或不可見。  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShow`  
 指定按鈕是否可見。 如果這個參數是`TRUE`，按鈕會顯示。 否則，按鈕看不到。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) 來顯示按鈕`bShow`是`TRUE`。 否則，這個方法會隱藏按鈕。  
  
##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize  
 為父工具列變更它的大小或位置，這項變更會使按鈕將大小變更時由架構呼叫。  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>參數  
 [in] `iSize`  
 新按鈕，像素為單位的寬度。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫預設類別實作 ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) 藉由更新的大小和位置的內部`CMFCToolBarDateTimeCtrlImpl`物件。  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip  
 為父工具列更新其工具提示文字時，由架構呼叫。  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndParent`  
 父視窗。  
  
 [in] `iButtonIndex`  
 父代按鈕集合中的按鈕之以零為起始索引。  
  
 [in] `wndToolTip`  
 在顯示工具提示文字的控制項。  
  
 [輸出] `str`  
 A`CString`接收更新的工具提示文字的物件。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果此方法來更新的工具提示文字。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此方法擴充的基底類別實作 ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) 所顯示的工具提示文字與按鈕相關聯。 如果未以水平方式停駐 按鈕，這個方法不做任何動作，並傳回`FALSE`。  
  
##  <a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime  
 設定時間和日期時間選擇器控制項中。  
  
```  
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>參數  
 `[in] timeNew`  
 在第一個版本中，參考[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含要將設定控制項的時間。 在第二個版本中，指標[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含要將設定控制項的時間。  
  
 `[in] pTimeNew`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含要將設定控制項的時間。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 日期和時間選擇器控制項中設定的時間，藉由呼叫[CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime)。  
  
##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll  
 設定的時間和日期時間選擇器控制項的所有具有指定的命令識別碼的執行個體  
  
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
 `[in] uiCmd`  
 指定工具列按鈕的命令識別碼。  
  
 `[in] timeNew`  
 在第一個版本中， [COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含要將設定控制項的時間。 在第二個版本中，指標[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含要將設定控制項的時間。  
  
 `[in] pTimeNew`  
 指標[SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含要將設定控制項的時間。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 會尋找具有指定的命令 ID 的工具列按鈕，並設定日期和時間選擇器控制項中的時間，藉由呼叫[CMFCToolBarDateTimeCtrl::SetTime](#settime)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



