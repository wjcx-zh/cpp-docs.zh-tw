---
title: "CMFCToolBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBar class
ms.assetid: e7679c01-fb94-44c0-98c6-3af955292fb5
caps.latest.revision: 48
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a34997b4b68ddcc8f42869466f17d67f32141d7c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbar-class"></a>CMFCToolBar 類別
`CMFCToolBar`類別類似於[CToolBar 類別](../../mfc/reference/ctoolbar-class.md)，但是提供額外的使用者介面功能的支援。 這包括一般工具列、含作用中影像的工具列、大圖示、頁面巡覽區按鈕、鎖定工具列、Rebar 控制項、影像下方文字、背景影像和索引標籤式工具列。 `CMFCToolBar` 類別的內建支援也包括工具列和功能表的使用者自訂、工具列和功能表之間的拖放、下拉式方塊按鈕、編輯方塊按鈕、色彩選擇器和縮合按鈕。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBar : public CMFCBaseToolBar  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCToolBar::CMFCToolBar`|預設建構函式。|  
|`CMFCToolBar::~CMFCToolBar`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBar::AddBasicCommand](#addbasiccommand)|將功能表命令加入至一定會在使用者開啟功能表時所顯示的命令的清單。|  
|[CMFCToolBar::AddCommandUsage](#addcommandusage)|一個指定的命令相關聯的計數器遞增。|  
|[CMFCToolBar::AddToolBarForImageCollection](#addtoolbarforimagecollection)|將影像從使用者介面資源加入至應用程式中的映像的集合。|  
|[CMFCToolBar::AdjustLayout](#adjustlayout)|重新計算的大小和工具列的位置。 (覆寫[CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout))。|  
|[CMFCToolBar::AdjustSize](#adjustsize)|重新計算工具列的大小。|  
|[CMFCToolBar::AllowChangeTextLabels](#allowchangetextlabels)|指定是否可以顯示文字標籤影像的工具列按鈕下方。|  
|[CMFCToolBar::AreTextLabels](#aretextlabels)|指定影像下方文字標籤是否目前正在顯示的工具列按鈕。|  
|[CMFCToolBar::AutoGrayInactiveImages](#autograyinactiveimages)|啟用或停用自動產生的非作用中的按鈕影像。|  
|[CMFCToolBar::ButtonToIndex](#buttontoindex)|傳回指定之索引[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)這個工具列中的物件。|  
|[CMFCToolBar::CalcFixedLayout](#calcfixedlayout)|計算的水平大小的工具列。 (覆寫[CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|  
|[CMFCToolBar::CalcSize](#calcsize)|配置計算程序的一部分的架構所呼叫。 (覆寫[CPane::CalcSize](../../mfc/reference/cpane-class.md#calcsize)。)|  
|[CMFCToolBar::CanHandleSiblings](#canhandlesiblings)|決定是否工具列和其同層級位於相同的窗格上。|  
|[CMFCToolBar::CleanUpImages](#cleanupimages)|釋放系統資源配置給下工具列影像。|  
|[CMFCToolBar::CleanUpLockedImages](#cleanuplockedimages)|釋放系統資源配置的鎖定的工具列影像。|  
|[CMFCToolBar::CanBeClosed](#canbeclosed)|指定使用者是否可以關閉工具列。 (覆寫[CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)。)|  
|[CMFCToolBar::CanBeRestored](#canberestored)|決定是否系統可以工具列後還原到其原始狀態的自訂。|  
|[CMFCToolBar::CanFocus](#canfocus)|指定是否窗格可以接收焦點。 (覆寫[CBasePane::CanFocus](../../mfc/reference/cbasepane-class.md#canfocus)。)|  
|[CMFCToolBar::CanHandleSiblings](#canhandlesiblings)|決定是否工具列和其同層級位於相同的窗格上。|  
|[CMFCToolBar::CommandToIndex](#commandtoindex)|傳回在工具列中指定的命令 id 的按鈕索引|  
|[CMFCToolBar::Create](#create)|建立 `CMFCToolBar` 物件。|  
|[CMFCToolBar::CreateEx](#createex)|建立`CMFCToolBar`使用其他樣式選項時，例如大型圖示的物件。|  
|[CMFCToolBar::Deactivate](#deactivate)|停用工具列。|  
|[CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton)|啟用或停用**新增或移除按鈕**出現的工具列按鈕。|  
|[CMFCToolBar::EnableDocking](#enabledocking)|啟用停駐窗格的主框架。 (覆寫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。)|  
|[CMFCToolBar::EnableLargeIcons](#enablelargeicons)|啟用或停用工具列按鈕上的大型圖示。|  
|[CMFCToolBar::EnableQuickCustomization](#enablequickcustomization)|啟用或停用快速自訂的工具列，讓使用者可以按**Alt**鍵，然後將按鈕拖曳至新位置。|  
|[CMFCToolBar::EnableReflections](#enablereflections)|啟用或停用命令反映。|  
|[CMFCToolBar::EnableTextLabels](#enabletextlabels)|啟用或停用工具列按鈕影像下方文字標籤。|  
|[CMFCToolBar::FromHandlePermanent](#fromhandlepermanent)|擷取的指標`CMFCToolBar`物件，其中包含指定的視窗控制代碼。|  
|[CMFCToolBar::GetAllButtons](#getallbuttons)|傳回在工具列中的按鈕的唯讀清單。|  
|[CMFCToolBar::GetAllToolbars](#getalltoolbars)|在應用程式會傳回所有工具列唯讀清單。|  
|[CMFCToolBar::GetBasicCommands](#getbasiccommands)|傳回唯讀的應用程式中定義的基本命令清單。|  
|[CMFCToolBar::GetButton](#getbutton)|傳回的指標`CMFCToolBarButton`具有指定的工具列按鈕索引的物件。|  
|[CMFCToolBar::GetButtonInfo](#getbuttoninfo)|傳回命令 ID、 樣式和指定索引處的按鈕影像索引。|  
|[CMFCToolBar::GetButtonSize](#getbuttonsize)|在工具列上傳回每個按鈕的尺寸。|  
|[CMFCToolBar::GetButtonStyle](#getbuttonstyle)|傳回目前的工具列按鈕，指定索引處的樣式。|  
|[CMFCToolBar::GetButtonText](#getbuttontext)|傳回具有指定的索引的按鈕的文字標籤。|  
|[CMFCToolBar::GetColdImages](#getcoldimages)|在應用程式的冷的工具列按鈕影像的集合中傳回的指標。|  
|[CMFCToolBar::GetColumnWidth](#getcolumnwidth)|傳回的工具列按鈕的寬度。|  
|[CMFCToolBar::GetCommandButtons](#getcommandbuttons)|傳回一份應用程式中有指定的命令識別碼，從所有的工具列按鈕。|  
|[CMFCToolBar::GetCount](#getcount)|在工具列上傳回按鈕和分隔線的數目。|  
|[CMFCToolBar::GetCustomizeButton](#getcustomizebutton)|擷取的指標`CMFCCustomizeButton`與工具列相關聯的物件。|  
|[CMFCToolBar::GetDefaultImage](#getdefaultimage)|傳回具有指定的命令 ID 的工具列按鈕的預設影像的索引|  
|[CMFCToolBar::GetDisabledImages](#getdisabledimages)|用於應用程式中的已停用的工具列按鈕的影像集合中傳回的指標。|  
|[CMFCToolBar::GetDisabledMenuImages](#getdisabledmenuimages)|用於應用程式中已停用的功能表按鈕的影像集合中傳回的指標。|  
|[CMFCToolBar::GetDroppedDownMenu](#getdroppeddownmenu)|擷取目前正在顯示子功能表的功能表按鈕物件的指標。|  
|[CMFCToolBar::GetGrayDisabledButtons](#getgraydisabledbuttons)|指定已停用按鈕的影像是否要呈現暗灰色的版本一般按鈕的影像，或從已停用的按鈕影像的集合。|  
|[CMFCToolBar::GetHighlightedButton](#gethighlightedbutton)|讓指標回到目前反白顯示的工具列按鈕。|  
|[CMFCToolBar::GetHotBorder](#gethotborder)|決定工具列按鈕是否為熱追蹤。|  
|[CMFCToolBar::GetHotTextColor](#gethottextcolor)|傳回文字的色彩反白顯示的工具列按鈕。|  
|[CMFCToolBar::GetHwndLastFocus](#gethwndlastfocus)|傳回之前工具列未擁有輸入的焦點的視窗控制代碼。|  
|[CMFCToolBar::GetIgnoreSetText](#getignoresettext)|指定是否設定按鈕標籤的呼叫都會被忽略。|  
|[CMFCToolBar::GetImageSize](#getimagesize)|傳回目前的工具列按鈕影像的大小。|  
|[CMFCToolBar::GetImages](#getimages)|傳回的指標集合的預設按鈕影像應用程式中。|  
|[CMFCToolBar::GetImagesOffset](#getimagesoffset)|傳回用來尋找此工具列，工具列按鈕影像的全域清單中的工具列按鈕影像的索引位移。|  
|[CMFCToolBar::GetInvalidateItemRect](#getinvalidateitemrect)|擷取指定索引處的按鈕就必須重新繪製的工作區的區域。|  
|[CMFCToolBar::GetItemID](#getitemid)|傳回指定索引處的工具列按鈕的命令 ID。|  
|[CMFCToolBar::GetItemRect](#getitemrect)|傳回指定索引處的按鈕，這個周框。|  
|[CMFCToolBar::GetLargeColdImages](#getlargecoldimages)|應用程式中的大型冷的工具列按鈕影像的集合中傳回的指標。|  
|[CMFCToolBar::GetLargeDisabledImages](#getlargedisabledimages)|傳回集合的應用程式中的大型已停用的工具列按鈕影像的指標。|  
|[CMFCToolBar::GetLargeImages](#getlargeimages)|應用程式中的大型工具列按鈕影像的集合中傳回的指標。|  
|[CMFCToolBar::GetLockedColdImages](#getlockedcoldimages)|在工具列上的鎖定冷映像的集合中傳回的指標。|  
|[CMFCToolBar::GetLockedDisabledImages](#getlockeddisabledimages)|在工具列上的鎖定已停用映像的集合中傳回的指標。|  
|[CMFCToolBar::GetLockedImages](#getlockedimages)|在工具列上的鎖定的按鈕影像的集合中傳回的指標。|  
|[CMFCToolBar::GetLockedImageSize](#getlockedimagesize)|傳回已鎖定的工具列影像的預設大小。|  
|[CMFCToolBar::GetLockedMenuImages](#getlockedmenuimages)|傳回的指標集合的 [鎖定工具列] 功能表上的映像工具列中。|  
|[CMFCToolBar::GetMenuButtonSize](#getmenubuttonsize)|傳回應用程式功能表按鈕的大小。|  
|[CMFCToolBar::GetMenuImageSize](#getmenuimagesize)|傳回應用程式功能表按鈕影像的大小。|  
|[CMFCToolBar::GetMenuImages](#getmenuimages)|應用程式中的功能表按鈕影像的集合中傳回的指標。|  
|[CMFCToolBar::GetOrigButtons](#getorigbuttons)|擷取集合的非自訂按鈕的工具列。|  
|[CMFCToolBar::GetOrigResetButtons](#getorigresetbuttons)|擷取集合的非自訂的重設按鈕的工具列。|  
|[CMFCToolBar::GetResourceID](#getresourceid)|擷取工具列的資源識別碼。|  
|[CMFCToolBar::GetRouteCommandsViaFrame](#getroutecommandsviaframe)|決定哪些物件、 父框架或擁有者，將命令傳送至工具列。|  
|[CMFCToolBar::GetRowHeight](#getrowheight)|傳回工具列按鈕的高度。|  
|[CMFCToolBar::GetShowTooltips](#getshowtooltips)|指定的工具列按鈕是否會顯示工具提示。|  
|[CMFCToolBar::GetSiblingToolBar](#getsiblingtoolbar)|擷取工具列的同層級。|  
|[CMFCToolBar::GetUserImages](#getuserimages)|應用程式中的使用者定義工具列按鈕影像的集合中傳回的指標。|  
|[CMFCToolBar::HitTest](#hittest)|傳回位於指定位置處的工具列按鈕的索引。|  
|[CMFCToolBar::InsertButton](#insertbutton)|插入工具列按鈕。|  
|[CMFCToolBar::InsertSeparator](#insertseparator)|插入工具列中的分隔符號。|  
|[CMFCToolBar::InvalidateButton](#invalidatebutton)|失效的工具列按鈕，在提供的索引存在的工作區。|  
|[CMFCToolBar::IsAddRemoveQuickCustomize](#isaddremovequickcustomize)|決定使用者可以新增或移除工具列按鈕使用**自訂**功能表選項。|  
|[CMFCToolBar::IsAltCustomizeMode](#isaltcustomizemode)|指定是否*快速自訂*用來將按鈕拖曳。|  
|[CMFCToolBar::IsAutoGrayInactiveImages](#isautograyinactiveimages)|指定是否啟用自動產生的非作用中 （非反白顯示） 按鈕影像。|  
|[CMFCToolBar::IsBasicCommand](#isbasiccommand)|判斷命令是否在基本命令的清單。|  
|[CMFCToolBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|決定工具列是否會顯示擴充框線的按鈕。|  
|[CMFCToolBar::IsButtonHighlighted](#isbuttonhighlighted)|決定工具列上的按鈕會反白顯示。|  
|[CMFCToolBar::IsCommandPermitted](#iscommandpermitted)|決定是否要允許的命令。|  
|[CMFCToolBar::IsCommandRarelyUsed](#iscommandrarelyused)|決定是否很少使用的命令 (請參閱[CMFCToolBar::SetCommandUsageOptions](#setcommandusageoptions))。|  
|[CMFCToolBar::IsCustomizeMode](#iscustomizemode)|指定工具列 framework 是否為自訂模式。|  
|[CMFCToolBar::IsDragButton](#isdragbutton)|決定是否要拖曳的工具列按鈕。|  
|[CMFCToolBar::IsExistCustomizeButton](#isexistcustomizebutton)|判斷是否要包含工具列**自訂** 按鈕。|  
|[CMFCToolBar::IsFloating](#isfloating)|決定是否要浮動工具列。|  
|[CMFCToolBar::IsLargeIcons](#islargeicons)|指定是否在應用程式工具列目前顯示大圖示。|  
|[CMFCToolBar::IsLastCommandFromButton](#islastcommandfrombutton)|決定是否最近執行命令用來傳送指定的工具列按鈕。|  
|[CMFCToolBar::IsLocked](#islocked)|決定工具列是否已鎖定。|  
|[CMFCToolBar::IsOneRowWithSibling](#isonerowwithsibling)|判斷是否會將工具列和工具列，其同層級置於同一個資料列。|  
|[CMFCToolBar::IsUserDefined](#isuserdefined)|指定工具列是否為使用者定義。|  
|[CMFCToolBar::LoadBitmap](#loadbitmap)|從應用程式資源載入工具列影像。|  
|[CMFCToolBar::LoadBitmapEx](#loadbitmapex)|從應用程式資源載入工具列影像。 包含大量的影像。|  
|[CMFCToolBar::LoadParameters](#loadparameters)|從 Windows 登錄載入全域工具列選項。|  
|[CMFCToolBar::LoadState](#loadstate)|從 Windows 登錄載入工具列狀態資訊。 (覆寫[CPane::LoadState](../../mfc/reference/cpane-class.md#loadstate)。)|  
|[CMFCToolBar::LoadToolBar](#loadtoolbar)|從應用程式資源載入工具列。|  
|[CMFCToolBar::LoadToolBarEx](#loadtoolbarex)|從應用程式資源載入工具列使用`CMFCToolBarInfo`helper 類別，可讓應用程式使用大量的影像。|  
|[CMFCToolBar::OnChangeHot](#onchangehot)|當使用者選取工具列上的按鈕，由架構呼叫。|  
|[CMFCToolBar::OnFillBackground](#onfillbackground)|從架構呼叫[CBasePane::DoPaint](../../mfc/reference/cbasepane-class.md#dopaint)工具列背景填滿。|  
|[CMFCToolBar::OnReset](#onreset)|將工具列還原至其原始狀態。|  
|[CMFCToolBar::OnSetAccData](#onsetaccdata)|(覆寫[CBasePane::OnSetAccData](../../mfc/reference/cbasepane-class.md#onsetaccdata)。)|  
|[CMFCToolBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|工具列按鈕的文字會還原為其預設狀態。|  
|`CMFCToolBar::OnUpdateCmdUI`|在內部使用。|  
|[CMFCToolBar::RemoveAllButtons](#removeallbuttons)|從工具列中移除所有的按鈕。|  
|[CMFCToolBar::RemoveButton](#removebutton)|從工具列中移除具有指定之索引的按鈕。|  
|[CMFCToolBar::RemoveStateFromRegistry](#removestatefromregistry)|刪除 Windows 登錄中的工具列的狀態資訊。|  
|[CMFCToolBar::ReplaceButton](#replacebutton)|取代另一個工具列按鈕的工具列按鈕。|  
|[CMFCToolBar::ResetAll](#resetall)|將所有的工具列還原為原始狀態。|  
|[CMFCToolBar::ResetAllImages](#resetallimages)|清除所有應用程式中的工具列影像集合。|  
|[CMFCToolBar::RestoreOriginalState](#restoreoriginalstate)|還原工具列的原始狀態。|  
|[CMFCToolBar::SaveState](#savestate)|將工具列的狀態資訊儲存在 Windows 登錄。 (覆寫[CPane::SaveState](../../mfc/reference/cpane-class.md#savestate)。)|  
|`CMFCToolBar::Serialize`|(覆寫 `CBasePane::Serialize`。)|  
|[CMFCToolBar::SetBasicCommands](#setbasiccommands)|設定當使用者開啟功能表，一定會顯示的命令清單。|  
|[CMFCToolBar::SetButtonInfo](#setbuttoninfo)|設定命令 ID、 樣式和影像的工具列按鈕的 ID。|  
|[CMFCToolBar::SetButtonStyle](#setbuttonstyle)|設定指定索引處的工具列按鈕的樣式。|  
|[CMFCToolBar::SetButtonText](#setbuttontext)|設定的文字標籤的工具列按鈕。|  
|[CMFCToolBar::SetButtons](#setbuttons)|設定工具列按鈕。|  
|[CMFCToolBar::SetCommandUsageOptions](#setcommandusageoptions)|指定當很少使用的命令未出現在應用程式的功能表中。|  
|[CMFCToolBar::SetCustomizeMode](#setcustomizemode)|啟用或停用應用程式中的所有工具列的自訂模式。|  
|[CMFCToolBar::SetGrayDisabledButtons](#setgraydisabledbuttons)|指定的工具列上的已停用的按鈕會呈暗灰色，或如果已停用映像會使用已停用按鈕。|  
|[CMFCToolBar::SetHeight](#setheight)|設定工具列的高度。|  
|[CMFCToolBar::SetHotBorder](#sethotborder)|指定工具列按鈕是否熱追蹤。|  
|[CMFCToolBar::SetHotTextColor](#sethottextcolor)|設定作用的工具列按鈕的文字色彩。|  
|[CMFCToolBar::SetLargeIcons](#setlargeicons)|指定工具列按鈕是否顯示大圖示。|  
|[CMFCToolBar::SetLockedSizes](#setlockedsizes)|在工具列上設定鎖定的按鈕和鎖定的映像的大小。|  
|[CMFCToolBar::SetMenuSizes](#setmenusizes)|設定功能表的工具列按鈕和其影像的大小。|  
|[CMFCToolBar::SetNonPermittedCommands](#setnonpermittedcommands)|設定無法由使用者執行的命令清單。|  
|[CMFCToolBar::SetOneRowWithSibling](#setonerowwithsibling)|在工具列和其同層級置於相同的資料列。|  
|[CMFCToolBar::SetPermament](#setpermament)|指定使用者是否可以關閉工具列。|  
|[CMFCToolBar::SetRouteCommandsViaFrame](#setroutecommandsviaframe)|指定是否在父框架或擁有者將命令傳送至工具列。|  
|[CMFCToolBar::SetShowTooltips](#setshowtooltips)|指定是否，架構會顯示工具提示。|  
|[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)|指定工具列的同層級。|  
|[CMFCToolBar::SetSizes](#setsizes)|指定所有的工具列按鈕和影像的大小。|  
|[CMFCToolBar::SetToolBarBtnText](#settoolbarbtntext)|在工具列上，指定按鈕的屬性。|  
|[CMFCToolBar::SetTwoRowsWithSibling](#settworowswithsibling)|在工具列和其同層級置於個別的資料列。|  
|[CMFCToolBar::SetUserImages](#setuserimages)|應用程式中設定使用者定義的映像的集合。|  
|[CMFCToolBar::StretchPane](#stretchpane)|垂直或水平伸展工具列。 (覆寫[CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane)。)|  
|[CMFCToolBar::TranslateChar](#translatechar)|如果指定的按鍵碼對應至有效的鍵盤快速鍵，請執行按鈕命令。|  
|[CMFCToolBar::UpdateButton](#updatebutton)|更新指定的按鍵的狀態。|  
|[CMFCToolBar::WrapToolBar](#wraptoolbar)|重新放置在指定的維度內的工具列按鈕。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBar::AllowShowOnList](#allowshowonlist)|決定工具列是否會顯示在清單上**工具列**窗格**自訂**對話方塊。|  
|[CMFCToolBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|計算工具列中按鈕的最大高度。|  
|[CMFCToolBar::DoPaint](#dopaint)|工具列會重新繪製。|  
|[CMFCToolBar::DrawButton](#drawbutton)|工具列按鈕會重新繪製。|  
|[CMFCToolBar::DrawSeparator](#drawseparator)|在工具列上的分隔符號會重新繪製。|  
|[CMFCToolBar::OnUserToolTip](#onusertooltip)|顯示按鈕的工具提示時，由架構呼叫。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBar::m_bDontScaleImages](#m_bdontscaleimages)|高 DPI 模式中，指定是否要調整或不下工具列影像。|  
|[CMFCToolBar::m_dblLargeImageRatio](#m_dbllargeimageratio)|指定大量的影像維度 （高度或寬度） 與一般映像的維度之間的比率。|  
  
## <a name="remarks"></a>備註  
 若要納入`CMFCToolBar`物件插入您的應用程式，請依照下列步驟執行︰  
  
1.  新增`CMFCToolBar`到主框架視窗物件。  
  
2.  當您處理`WM_CREATE`主框架視窗的訊息，呼叫[CMFCToolBar::Create](#create)或[CMFCToolBar::CreateEx](#createex)建立的工具列，並指定其樣式。  
  
3.  呼叫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)指定的停駐樣式。  
  
 若要插入的特殊按鈕，例如下拉式方塊或下拉式工具列中，保留 dummy 按鈕在父資源中，並取代 dummy 按鈕，在執行階段使用[CMFCToolBar::ReplaceButton](#replacebutton)。 如需詳細資訊，請參閱[逐步解說︰ 將工具列控制項](../walkthrough-putting-controls-on-toolbars.md)。  
  
 `CMFCToolBar`MFC 程式庫類別的基底類別[CMFCMenuBar 類別](../../mfc/reference/cmfcmenubar-class.md)， [CMFCPopupMenuBar 類別](../../mfc/reference/cmfcpopupmenubar-class.md)，和[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCToolBar`類別。 此範例示範如何設定標籤文字的視窗的工具列上，設定的框線，設定樣式 窗格中，並啟用**新增或移除按鈕**出現的工具列按鈕。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&8;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbar.h  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 `CMFCToolBar`  
  
##  <a name="a-nameaddbasiccommanda--cmfctoolbaraddbasiccommand"></a><a name="addbasiccommand"></a>CMFCToolBar::AddBasicCommand  
 將功能表命令加入至一定會在使用者開啟功能表時所顯示的命令的清單。  
  
```  
static void __stdcall AddBasicCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 指定要新增的命令。  
  
### <a name="remarks"></a>備註  
 開啟功能表時，一律會顯示基本命令。 當使用者選擇要檢視最近使用的命令時，這個方法是有意義。  
  
 使用[CMFCToolBar::SetBasicCommands](#setbasiccommands)方法來設定一定會在使用者開啟功能表時所顯示的命令的清單。 使用[CMFCToolBar::GetBasicCommands](#getbasiccommands)方法來擷取基本命令，可由您的應用程式的清單。  
  
##  <a name="a-nameaddcommandusagea--cmfctoolbaraddcommandusage"></a><a name="addcommandusage"></a>CMFCToolBar::AddCommandUsage  
 一個指定的命令相關聯的計數器遞增。  
  
```  
static void __stdcall AddCommandUsage(UINT uiCommand);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCommand`  
 指定命令計數器遞增。  
  
### <a name="remarks"></a>備註  
 當使用者選取功能表項目時，架構會呼叫這個方法。  
  
 架構會使用命令的計數器，以顯示最近使用的功能表項目。  
  
 這個方法會使用命令計數器[CMFCCmdUsageCount::AddCmd](../../mfc/reference/cmfccmdusagecount-class.md#addcmd)方法。  
  
##  <a name="a-nameaddtoolbarforimagecollectiona--cmfctoolbaraddtoolbarforimagecollection"></a><a name="addtoolbarforimagecollection"></a>CMFCToolBar::AddToolBarForImageCollection  
 將影像從使用者介面資源加入至應用程式中的映像的集合。  
  
```  
static BOOL __stdcall AddToolBarForImageCollection(
    UINT uiResID,  
    UINT uiBmpResID=0,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiResID`  
 資源識別碼工具列與映像的載入。  
  
 [in] `uiBmpResID`  
 資源識別碼與工具列影像的點陣圖。  
  
 [in] `uiColdResID`  
 使用 「 冷 」 的工具列影像的點陣圖資源識別碼。  
  
 [in] `uiMenuResID`  
 使用功能表影像的點陣圖資源識別碼。  
  
 [in] `uiDisabledResID`  
 已停用的工具列影像的點陣圖資源識別碼。  
  
 [in] `uiMenuDisabledResID`  
 已停用的功能表影像的點陣圖資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功。`FALSE`如果`uiResID`或`uiBmpResID`未指定有效的資源，或發生其他錯誤。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法載入的工具列影像的點陣圖，並將其加入至工具列影像的集合。 這個方法會建立暫存的工具列物件並呼叫[CMFCToolBar::LoadToolBar](#loadtoolbar)。  
  
##  <a name="a-nameadjustlayouta--cmfctoolbaradjustlayout"></a><a name="adjustlayout"></a>CMFCToolBar::AdjustLayout  
 重新計算的大小和工具列的位置。  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>備註  
 建立工具列後重新計算的大小和位置，請呼叫這個方法。  
  
 架構會呼叫此方法每次時，必須變更工具列的版面配置。 例如，使用者將另一種控制列移動、 調整應用程式視窗，或自訂工具列時，必須變更版面配置。  
  
 覆寫這個方法以提供您自己衍生自的類別中的動態配置`CMFCToolbar`。  
  
##  <a name="a-nameadjustsizea--cmfctoolbaradjustsize"></a><a name="adjustsize"></a>CMFCToolBar::AdjustSize  
 重新計算工具列的大小。  
  
```  
void AdjustSize();
```  
  
### <a name="remarks"></a>備註  
 這個方法可確保工具列，以符合父框架的界限內。 如果工具列沒有父框架，這個方法作用。  
  
 [CMFCToolBar::AdjustLayout](#adjustlayout)方法會呼叫這個方法，以重新計算的大小，如果在工具列的父系不是`CMFCReBar`物件。  
  
##  <a name="a-nameallowchangetextlabelsa--cmfctoolbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCToolBar::AllowChangeTextLabels  
 指定是否可以顯示文字標籤影像的工具列按鈕下方。  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果允許顯示文字標籤下方的影像。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法稱為自訂對話方塊中，以判斷是否要啟用**顯示文字標籤**上的核取方塊**工具列**頁面選取的工具列。  
  
 預設實作會傳回 `TRUE`。  
  
 覆寫這個方法在一個物件衍生自`CMFCToolBar`，並傳回`FALSE`時不希望使用者可以決定是否會在影像下方的工具列按鈕上顯示文字標籤。  
  
##  <a name="a-nameallowshowonlista--cmfctoolbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCToolBar::AllowShowOnList  
 決定工具列是否會顯示在清單中的工具列上**工具列**窗格**自訂**對話方塊。  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列物件可以顯示在清單方塊中，在工具列的 [自訂] 頁面。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 若要判斷是否在工具列的 [自訂] 頁面的清單應該包含特定物件衍生自 framework 會呼叫這個方法`CMFCToolBar`。  
  
 預設實作一定會傳回`TRUE`。 當您不想要出現在自訂 對話方塊的 工具列 清單中的工具列，請覆寫這個方法。  
  
##  <a name="a-namearetextlabelsa--cmfctoolbararetextlabels"></a><a name="aretextlabels"></a>CMFCToolBar::AreTextLabels  
 指定影像下方文字標籤是否目前正在顯示的工具列按鈕。  
  
```  
BOOL AreTextLabels() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列按鈕顯示的影像，下方的文字標籤否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CMFCToolBar::EnableTextLabels](#enabletextlabels) ，指定是否要顯示文字。 預設值是 `FALSE`。 呼叫[CMFCToolBar::AllowChangeTextLabels](#allowchangetextlabels)來指定使用者是否可以變更此設定，在自訂 對話方塊。  
  
##  <a name="a-nameautograyinactiveimagesa--cmfctoolbarautograyinactiveimages"></a><a name="autograyinactiveimages"></a>CMFCToolBar::AutoGrayInactiveImages  
 啟用或停用自動產生的非作用中的按鈕影像。  
  
```  
static void AutoGrayInactiveImages(
    BOOL bEnable=TRUE,  
    int nGrayImagePercentage=0,  
    BOOL bRedrawAllToolbars=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值，指定是否要將非使用中的映像變暗。 如果這個參數是`TRUE`，會以灰色顯示非作用中的映像。 否則，非作用中的映像未呈現灰色。  
  
 [in] `nGrayImagePercentage`  
 指定非使用中的映像的亮度百分比。 如果`bEnable`是`FALSE`，這個值會被忽略。  
  
 [in] `bRedrawAllToolbars`  
 布林值，指定是否要重繪應用程式中的所有工具列。 如果這個參數是`TRUE`，這個方法會重新繪製所有的工具列。  
  
### <a name="remarks"></a>備註  
 如果`bEnable`是`TRUE`，架構會使用`nGrayImagePercentage`來產生與一般的映像的非作用中的影像。 否則，您必須提供一組非作用中的影像使用[CMFCToolBar::GetColdImages](#getcoldimages)方法。 根據預設，此選項已停用。  
  
 如需詳細資訊`nGrayImagePercentage`參數，請參閱[CMFCToolBarImages::GrayImages](../../mfc/reference/cmfctoolbarimages-class.md#grayimages)。  
  
##  <a name="a-namebuttontoindexa--cmfctoolbarbuttontoindex"></a><a name="buttontoindex"></a>CMFCToolBar::ButtonToIndex  
 傳回指定之索引[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)這個工具列中的物件。  
  
```  
int ButtonToIndex(const CMFCToolBarButton* pButton) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 工具列按鈕物件指標。  
  
### <a name="return-value"></a>傳回值  
 編製索引的`pButton`工具列按鈕，則為-1 指定的按鈕不在此工具列上的內部清單中。  
  
##  <a name="a-namecalcfixedlayouta--cmfctoolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCToolBar::CalcFixedLayout  
 計算的水平大小的工具列。  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `bStretch`  
 `TRUE`若要自動縮放工具列父框架的大小。  
  
 [in] `bHorz`  
 `TRUE`若要引導工具列水平空間。`FALSE`調整成垂直工具列。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，指定在工具列的大小。  
  
### <a name="remarks"></a>備註  
 這個方法會使用計算的工具列大小`CMFCToolBar::CalcLayout`方法。 它會傳遞`LM_STRETCH`設定旗標以`dwMode`參數如果`bStretch`是`TRUE`。 它會傳遞`LM_HORZ`旗標，如果`bHorz`是`TRUE`。  
  
 請參閱 VisualStudioDemo 範例，其中會使用這個方法的範例。  
  
##  <a name="a-namecalcmaxbuttonheighta--cmfctoolbarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFCToolBar::CalcMaxButtonHeight  
 計算工具列中按鈕的最大高度。  
  
```  
virtual int CalcMaxButtonHeight();
```  
  
### <a name="return-value"></a>傳回值  
 按鈕的最大高度。  
  
### <a name="remarks"></a>備註  
 這個方法會計算在工具列上的所有工具列按鈕之間的最大高度。 高度根據目前的工具列停駐狀態等因素而有所不同。  
  
 這個方法從衍生類別中的覆寫`CMFCToolBar`提供高度計算。  
  
##  <a name="a-namecalcsizea--cmfctoolbarcalcsize"></a><a name="calcsize"></a>CMFCToolBar::CalcSize  
 配置計算程序的一部分的架構所呼叫。  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>參數  
 [in] `bVertDock`  
 `TRUE`若要指定工具列會固定以垂直方式;`FALSE`指定工具列會固定以水平方式。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，指定在工具列上的按鈕的整體大小。  
  
### <a name="remarks"></a>備註  
 這個方法會視為會影響每個按鈕，例如文字標籤和框線大小的區域大小的屬性。  
  
 如果工具列會不包含任何按鈕，這個方法會傳回單一的按鈕保留的大小使用[CMFCToolBar::GetButtonSize](#getbuttonsize)方法。  
  
##  <a name="a-namecanbecloseda--cmfctoolbarcanbeclosed"></a><a name="canbeclosed"></a>CMFCToolBar::CanBeClosed  
 指定使用者是否可以關閉工具列。  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列可以關閉的使用者資訊。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法來判斷使用者是否可以關閉工具列。 如果此方法會傳回`TRUE`架構可讓 SC_CLOSE 命令，在工具列的 [系統] 功能表中，使用者可以使用 [自訂] 對話方塊中的工具列的清單中的核取方塊來關閉工具列。  
  
 預設實作會傳回 `TRUE`。 這個方法從衍生類別中的覆寫`CMFCToolBar`為了讓使用者無法關閉的工具列物件。  
  
##  <a name="a-namecanberestoreda--cmfctoolbarcanberestored"></a><a name="canberestored"></a>CMFCToolBar::CanBeRestored  
 決定是否系統可以工具列後還原到其原始狀態的自訂。  
  
```  
virtual BOOL CanBeRestored() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果您可以從應用程式資源; 還原工具列否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法來判斷是否工具列可以返回到其原始狀態自訂後。 從應用程式資源載入原始的狀態。  
  
 如果`CanBeRestored`傳回`TRUE`、**工具列**頁面的 [自訂] 對話方塊可讓**重設**選取的工具列按鈕。  
  
 預設實作會傳回`TRUE`如果工具列時載入它的原始的資源識別碼為非零。 通常，只有使用者定義的工具列無法還原。  
  
 您可以覆寫`CanBeRestored`方法，以自訂此行為在衍生類別。  
  
##  <a name="a-namecanfocusa--cmfctoolbarcanfocus"></a><a name="canfocus"></a>CMFCToolBar::CanFocus  
 指定是否窗格可以接收焦點。  
  
```  
virtual BOOL CanFocus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此方法會傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會覆寫基底類別實作時， [CBasePane::CanFocus](../../mfc/reference/cbasepane-class.md#canfocus)，因為工具列物件無法接收焦點。  
  
##  <a name="a-namecanhandlesiblingsa--cmfctoolbarcanhandlesiblings"></a><a name="canhandlesiblings"></a>CMFCToolBar::CanHandleSiblings  
 決定是否工具列和其同層級位於相同的窗格上。  
  
```  
BOOL CanHandleSiblings();
```  
  
### <a name="return-value"></a>傳回值  
 如果工具列有同層級而工具列和其同層級位於相同的窗格上則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 內部的 CMFCCustomizeButton::CreatePopupMenu 方法會呼叫這個方法，以決定如何顯示**自訂**快顯功能表。 如果這個方法會傳回`TRUE`，架構會顯示**按鈕顯示於資料列的資料上**或**按鈕顯示於兩個資料列上**按鈕。  
  
 您通常不需要使用這個方法。 若要啟用**自訂**按鈕出現在工具列上，呼叫[CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton)方法。 若要啟用**按鈕顯示於資料列的資料上**或**按鈕顯示於兩個資料列上**按鈕，呼叫[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)。  
  
##  <a name="a-namecleanupimagesa--cmfctoolbarcleanupimages"></a><a name="cleanupimages"></a>CMFCToolBar::CleanUpImages  
 釋放系統資源配置給下工具列影像。  
  
```  
static void CMFCToolBar::CleanUpImages();
```  
  
### <a name="remarks"></a>備註  
 應用程式關閉時，架構會呼叫這個方法。  
  
##  <a name="a-namecleanuplockedimagesa--cmfctoolbarcleanuplockedimages"></a><a name="cleanuplockedimages"></a>CMFCToolBar::CleanUpLockedImages  
 釋放系統資源配置的鎖定的工具列影像。  
  
```  
void CleanUpLockedImages();
```  
  
### <a name="remarks"></a>備註  
 您的應用程式的視覺化樣式變更時，請呼叫這個方法。 請參閱 VisualStudioDemo 範例，其中會使用這個方法的範例。  
  
##  <a name="a-namecommandtoindexa--cmfctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CMFCToolBar::CommandToIndex  
 傳回在工具列中指定的命令 id 的按鈕索引  
  
```  
int CommandToIndex(
    UINT nIDFind,  
    int iIndexFirst=0) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nIDFind`  
 指定命令識別碼。  
  
 [in] `iIndexFirst`  
 指定做為開頭的起始索引。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，工具列按鈕的以零起始的索引-1，如果沒有按鈕，並提供指定的識別碼。  
  
### <a name="remarks"></a>備註  
 A`CMFCToolBar`物件會維護內部清單工具列上的按鈕。 呼叫此函式可擷取索引指定按鈕的命令 ID 的清單中的按鈕。  
  
 如果`iIndex`大於 0，這個方法會忽略任何索引鍵的工具列上的按鈕少於`iIndex`。  
  
##  <a name="a-namecreatea--cmfctoolbarcreate"></a><a name="create"></a>CMFCToolBar::Create  
 建立 `CMFCToolBar` 物件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT nID=AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParentWnd`  
 工具列的父視窗的指標。  
  
 [in] `dwStyle`  
 工具列的樣式。 請參閱[工具列控制項和按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的樣式清單。  
  
 [in] `nID`  
 子視窗工具列的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會建立一種控制列，並將其附加至工具列。 它會建立與控制列`TBSTYLE_FLAT`樣式。 呼叫[CMFCToolBar::CreateEx](#createex)如果要使用不同的控制列樣式。  
  
##  <a name="a-namecreateexa--cmfctoolbarcreateex"></a><a name="createex"></a>CMFCToolBar::CreateEx  
 建立`CMFCToolBar`使用其他樣式選項時，例如大型圖示的物件。  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle=TBSTYLE_FLAT,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    CRect rcBorders=CRect(1,
    1,
    1,
    1),  
    UINT nID=AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParentWnd`  
 工具列的父視窗的指標。  
  
 [in] `dwCtrlStyle`  
 建立內嵌的控制列物件的其他樣式。  
  
 [in] `dwStyle`  
 工具列的樣式。 請參閱[工具列控制項和按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439)適當樣式的清單。  
  
 [in] `rcBorders`  
 A`CRect`物件，指定工具列視窗框線的寬度。  
  
 [in] `nID`  
 子視窗工具列的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會建立一種控制列，並將其附加至工具列。  
  
 呼叫這個方法，而不是[CMFCToolBar::Create](#create)當您想要提供特定的樣式。 例如，設定`dwCtrlStyle`至`TBSTYLE_FLAT | TBSTYLE_TRANSPARENT`來建立類似 Internet Explorer 4 所使用的工具列的工具列。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`CreateEx`方法`CMFCToolBar`類別。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&7;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_3.cpp)]  
  
##  <a name="a-namedeactivatea--cmfctoolbardeactivate"></a><a name="deactivate"></a>CMFCToolBar::Deactivate  
 停用工具列。  
  
```  
virtual void Deactivate();
```  
  
### <a name="remarks"></a>備註  
 這個方法會將焦點移除反白顯示的工具列按鈕，停用工具列。 工具列失去焦點，或已損毀時，架構會呼叫這個方法。  
  
##  <a name="a-namedopainta--cmfctoolbardopaint"></a><a name="dopaint"></a>CMFCToolBar::DoPaint  
 工具列會重新繪製。  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 必須重新繪製該工具列的一部分時，架構會呼叫這個方法。  
  
 覆寫這個方法來自訂物件衍生自外觀`CMFCToolBar`。  
  
##  <a name="a-namedrawbuttona--cmfctoolbardrawbutton"></a><a name="drawbutton"></a>CMFCToolBar::DrawButton  
 工具列按鈕會重新繪製。  
  
```  
virtual BOOL DrawButton(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CMFCToolBarImages* pImages,  
    BOOL bHighlighted,  
    BOOL bDrawDisabledImages);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `pButton`  
 若要繪製按鈕指標。  
  
 [in] `pImages`  
 指標，工具列影像。  
  
 [in] `bHighlighted`  
 `TRUE`如果按鈕會反白顯示。，否則`FALSE`。  
  
 [in] `bDrawDisabledImages`  
 `TRUE`如果已停用的按鈕會呈暗灰色。，否則`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕重新繪製。`FALSE`如果會隱藏按鈕。  
  
### <a name="remarks"></a>備註  
 [CMFCToolBar::DrawButton](#drawbutton)方法會呼叫這個方法時必須重新繪製該工具列按鈕。  
  
 如果您想要自訂的工具列上的按鈕外觀，請覆寫這個方法。  
  
##  <a name="a-namedrawseparatora--cmfctoolbardrawseparator"></a><a name="drawseparator"></a>CMFCToolBar::DrawSeparator  
 在工具列上的分隔符號會重新繪製。  
  
```  
virtual void DrawSeparator(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 繪製分隔符號的地方，可像素為單位的位置，這個周框。  
  
 [in] `bHorz`  
 `TRUE`如果分隔符號是水平、`FALSE`如果分隔符號是垂直。  
  
### <a name="remarks"></a>備註  
 [CMFCToolBar::DoPaint](#dopaint)呼叫這個方法，每個[CMFCToolBar::DrawSeparator](#drawseparator)物件具有`TBBS_SEPARATOR`樣式，而不是呼叫[CMFCToolBar::DrawButton](#drawbutton)這些按鈕。  
  
 這個方法從衍生類別中的覆寫[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)自訂分隔符號 工具列上的外觀。 預設實作會呼叫[CMFCVisualManager::OnDrawSeparator](../../mfc/reference/cmfcvisualmanager-class.md#ondrawseparator)繪製其外觀取決於目前的視覺管理員的分隔符號。  
  
##  <a name="a-nameenablecustomizebuttona--cmfctoolbarenablecustomizebutton"></a><a name="enablecustomizebutton"></a>CMFCToolBar::EnableCustomizeButton  
 啟用或停用會出現在工具列的 [自訂] 按鈕。  
  
```  
void EnableCustomizeButton(
    BOOL bEnable,  
    int iCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bQuickCustomize=TRUE);

 
void EnableCustomizeButton(
    BOOL bEnable,  
    int iCustomizeCmd,  
    UINT uiCustomizeTextResId,  
    BOOL bQuickCustomize=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 啟用或停用 [自訂] 按鈕。  
  
 [in] `iCustomizeCmd`  
 [自訂] 按鈕的命令 ID。  
  
 [in] `strCustomizeText`  
 [自訂] 按鈕的文字標籤。  
  
 [in] `uiCustomizeTextResId`  
 資源字串的自訂按鈕標籤識別碼。  
  
 [in] `bQuickCustomize`  
 啟用或停用**新增或移除按鈕**下拉按鈕功能表上的選項。  
  
### <a name="remarks"></a>備註  
 如果`iCustomizeCmd`為-1，則架構會顯示工具列區域中無法容納多個工具列按鈕時，[自訂] 按鈕。 按鈕會顯示雙重向左箭號或 > 形箭號，表示有更多的按鈕。  
  
 如果`iCustomizeCmd`指定有效的命令識別碼和`bEnable`是`TRUE`，一律會顯示 [自訂] 按鈕。 按鈕有少量向下箭號，並開啟一個包含命令功能表。 此命令會使用所指定的文字標籤`strCustomizeText`。 如果`bQuickCustomize`也`TRUE`，功能表就會顯示**新增或移除按鈕**選項。  
  
 架構以動態方式加入至功能表工具列區域之前所指定的項目不符合任何按鈕`iCustomizeCmd`。 向下箭號旁邊顯示的 > 形箭號。  
  
##  <a name="a-nameenabledockinga--cmfctoolbarenabledocking"></a><a name="enabledocking"></a>CMFCToolBar::EnableDocking  
 啟用停駐窗格的主框架。  
  
```  
virtual void EnableDocking(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwAlignment`  
 指定要啟用的停駐對齊。  
  
### <a name="remarks"></a>備註  
 此方法會擴充基底類別實作時， [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)，藉由設定`CBasePane::m_dwControlBarStyle`資料成員，才能`AFX_CBRS_FLOAT`。 這個方法接著會傳遞`dwAlignment`基底類別實作。  
  
##  <a name="a-nameenablelargeiconsa--cmfctoolbarenablelargeicons"></a><a name="enablelargeicons"></a>CMFCToolBar::EnableLargeIcons  
 啟用或停用工具列按鈕上的大型圖示。  
  
```  
void EnableLargeIcons(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用 大圖示、`FALSE`停用大圖示。  
  
### <a name="remarks"></a>備註  
 根據預設，會啟用 大圖示。  
  
##  <a name="a-nameenablequickcustomizationa--cmfctoolbarenablequickcustomization"></a><a name="enablequickcustomization"></a>CMFCToolBar::EnableQuickCustomization  
 啟用或停用快速自訂的工具列，讓使用者可以按**Alt**鍵，然後將按鈕拖曳至新位置。  
  
```  
static void EnableQuickCustomization(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用快速的自訂`FALSE`來停用快速自訂。  
  
##  <a name="a-nameenablereflectionsa--cmfctoolbarenablereflections"></a><a name="enablereflections"></a>CMFCToolBar::EnableReflections  
 啟用或停用命令反映。  
  
```  
void EnableReflections(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用命令反映。`FALSE`停用命令反映。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法讓包含內嵌的控制項，例如下拉式方塊的工具列按鈕的命令反映。  
  
 如需命令反映的詳細資訊，請參閱[TN062: Windows 控制項的訊息反映](../../mfc/tn062-message-reflection-for-windows-controls.md)。  
  
##  <a name="a-nameenabletextlabelsa--cmfctoolbarenabletextlabels"></a><a name="enabletextlabels"></a>CMFCToolBar::EnableTextLabels  
 啟用或停用工具列按鈕影像下方文字標籤。  
  
```  
void EnableTextLabels(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bEnable`  
 `TRUE`如果文字標籤出現在工具列按鈕影像。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果已啟用文字標籤，在工具列上的所有按鈕會都擴大來提供空間，讓影像下方顯示標籤。 自訂 對話方塊中有**顯示文字標籤**上的核取方塊**工具列**頁面。 當使用者選取一個工具列，並會檢查此選項時，架構會呼叫`EnableTextLabels`針對選取的工具列。 您可以停用核取方塊物件衍生自[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)藉由傳回`FALSE`從[CMFCToolBar::AllowChangeTextLabels](#allowchangetextlabels) 。  
  
##  <a name="a-namefromhandlepermanenta--cmfctoolbarfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CMFCToolBar::FromHandlePermanent  
 擷取的指標`CMFCToolBar`物件，其中包含指定的視窗控制代碼。  
  
```  
static CMFCToolBar* __stdcall FromHandlePermanent(HWND hwnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `hwnd`  
 若要尋找的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCToolBar`物件，其中包含指定的視窗控制代碼或`NULL`如果沒有對應`CMFCToolBar`物件存在。  
  
### <a name="remarks"></a>備註  
 此共用的方法會檢查每個工具列中的應用程式`CMFCToolBar`物件，其中包含指定的視窗控制代碼。  
  
##  <a name="a-namegetallbuttonsa--cmfctoolbargetallbuttons"></a><a name="getallbuttons"></a>CMFCToolBar::GetAllButtons  
 傳回在工具列中的按鈕的唯讀清單。  
  
```  
const CObList& GetAllButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
 常數參考[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中包含一系列[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)物件。  
  
##  <a name="a-namegetalltoolbarsa--cmfctoolbargetalltoolbars"></a><a name="getalltoolbars"></a>CMFCToolBar::GetAllToolbars  
 在應用程式會傳回所有工具列唯讀清單。  
  
```  
static const CObList& GetAllToolbars();
```  
  
### <a name="return-value"></a>傳回值  
 常數參考的[CObList 類別](../../mfc/reference/coblist-class.md)物件，其中包含一系列`CMFCToolBar`物件。  
  
##  <a name="a-namegetbasiccommandsa--cmfctoolbargetbasiccommands"></a><a name="getbasiccommands"></a>CMFCToolBar::GetBasicCommands  
 傳回唯讀的應用程式中定義的基本命令清單。  
  
```  
static const CList<UINT,UINT>& GetBasicCommands();
```  
  
### <a name="return-value"></a>傳回值  
 常數參考的[CList 類別](../../mfc/reference/clist-class.md)物件，其中包含的基本命令集合。  
  
### <a name="remarks"></a>備註  
 新增基本命令，藉由呼叫[CMFCToolBar::AddBasicCommand](#addbasiccommand)或[CMFCToolBar::SetBasicCommands](#setbasiccommands)。  
  
##  <a name="a-namegetbuttona--cmfctoolbargetbutton"></a><a name="getbutton"></a>CMFCToolBar::GetButton  
 傳回的指標[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)指定索引處的物件。  
  
```  
CMFCToolBarButton* GetButton(int iIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 指定要傳回的按鈕索引。  
  
### <a name="return-value"></a>傳回值  
 變數的指標，如果有的話，工具列按鈕或`NULL`如果沒有這類的按鈕。  
  
##  <a name="a-namegetbuttoninfoa--cmfctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CMFCToolBar::GetButtonInfo  
 傳回命令 ID、 樣式和指定索引處的按鈕影像索引。  
  
```  
void GetButtonInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& iImage) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 在工具列上的按鈕清單中指定的按鈕索引。  
  
 [輸出] `nID`  
 按鈕的命令 ID。  
  
 [輸出] `nStyle`  
 按鈕的樣式。  
  
 [輸出] `iImage`  
 按鈕影像的索引。  
  
### <a name="remarks"></a>備註  
 `GetButtonInfo`方法尋找指定之索引處的工具列按鈕，並擷取按鈕的命令 ID、 樣式和影像索引。  
  
 指定索引處的按鈕不存在，架構會將`nID`和`nStyle`為 0，和`iImage`方法傳回時為-1。  
  
##  <a name="a-namegetbuttonsizea--cmfctoolbargetbuttonsize"></a><a name="getbuttonsize"></a>CMFCToolBar::GetButtonSize  
 在工具列上傳回每個按鈕的尺寸。  
  
```  
CSize GetButtonSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CSize 類別](../../atl-mfc-shared/reference/csize-class.md)指定維度的每個按鈕的工具列的物件。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCToolBar::SetSizes](#setsizes)或[CMFCToolBar::SetLockedSizes](#setlockedsizes)設定工具列上的每個按鈕尺寸。  
  
##  <a name="a-namegetbuttonstylea--cmfctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CMFCToolBar::GetButtonStyle  
 傳回目前的工具列按鈕，指定索引處的樣式。  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定的工具列按鈕的索引。  
  
### <a name="return-value"></a>傳回值  
 值，指定的樣式的工具列按鈕。 。 請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)如需可能的樣式的清單。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCToolBar::SetButtonStyle](#setbuttonstyle)設定的樣式的工具列按鈕  
  
##  <a name="a-namegetbuttontexta--cmfctoolbargetbuttontext"></a><a name="getbuttontext"></a>CMFCToolBar::GetButtonText  
 傳回具有指定的索引的按鈕的文字標籤。  
  
```  
CString GetButtonText(int nIndex) const;  
  
void GetButtonText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 工具列按鈕的索引。  
  
 [輸出] `rString`  
 工具列按鈕的標籤文字。  
  
### <a name="return-value"></a>傳回值  
 工具列按鈕的標籤文字。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCToolBar::SetButtonText](#setbuttontext)或[CMFCToolBar::SetToolBarBtnText](#settoolbarbtntext)文字標籤設定。  
  
##  <a name="a-namegetcoldimagesa--cmfctoolbargetcoldimages"></a><a name="getcoldimages"></a>CMFCToolBar::GetColdImages  
 在應用程式的冷的工具列按鈕影像的集合中傳回的指標。  
  
```  
static CMFCToolBarImages* GetColdImages();
```  
  
### <a name="return-value"></a>傳回值  
 指標冷的工具列按鈕影像的集合。  
  
### <a name="remarks"></a>備註  
 冷映像是指在使用者不互動的工具列按鈕時所使用。 呼叫[CMFCToolBar::LoadBitmapEx](#loadbitmapex)或[CMFCToolBar::LoadBitmap](#loadbitmap)載入冷的影像。  
  
##  <a name="a-namegetcolumnwidtha--cmfctoolbargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFCToolBar::GetColumnWidth  
 傳回的工具列按鈕的寬度。  
  
```  
virtual int GetColumnWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指定的工具列按鈕的寬度的值。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以計算工具列版面配置。 若要指定不同的資料行寬度工具列在衍生類別中，這個方法會覆寫。  
  
##  <a name="a-namegetcommandbuttonsa--cmfctoolbargetcommandbuttons"></a><a name="getcommandbuttons"></a>CMFCToolBar::GetCommandButtons  
 傳回一份應用程式中有指定的命令識別碼，從所有的工具列按鈕。  
  
```  
static int GetCommandButtons(
    UINT uiCmd,  
    CObList& listButtons);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 按鈕的命令 ID。  
  
 [輸出] `listButtons`  
 參考[CObList 類別](../../mfc/reference/coblist-class.md)接收工具列按鈕的清單物件。  
  
### <a name="return-value"></a>傳回值  
 有指定的命令 ID 的按鈕數目  
  
##  <a name="a-namegetcounta--cmfctoolbargetcount"></a><a name="getcount"></a>CMFCToolBar::GetCount  
 在工具列上傳回按鈕和分隔線的數目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按鈕和工具列上的分隔線數目。  
  
##  <a name="a-namegetcustomizebuttona--cmfctoolbargetcustomizebutton"></a><a name="getcustomizebutton"></a>CMFCToolBar::GetCustomizeButton  
 擷取的指標`CMFCCustomizeButton`與工具列相關聯的物件。  
  
```  
CMFCCustomizeButton* GetCustomizeButton();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCCustomizeButton`與工具列相關聯的物件。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取**自訂**出現結尾的工具列按鈕。 使用[CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton)方法來加入**自訂**至工具列按鈕。  
  
 您可以呼叫[CMFCToolBar::IsExistCustomizeButton](#isexistcustomizebutton)方法，以判斷是否包含有效工具列`CMFCCustomizeButton`物件。  
  
##  <a name="a-namegetdefaultimagea--cmfctoolbargetdefaultimage"></a><a name="getdefaultimage"></a>CMFCToolBar::GetDefaultImage  
 傳回具有指定的命令 ID 的工具列按鈕的預設影像的索引  
  
```  
static int GetDefaultImage(UINT uiID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 指定按鈕的命令 ID。  
  
### <a name="return-value"></a>傳回值  
 共用的映像清單中的工具列影像的索引。  
  
### <a name="remarks"></a>備註  
 使用此共用的方法來擷取具有指定的命令 ID 的工具列按鈕的預設影像的索引 傳回值為共用集合的所有應用程式中的工具列的工具列按鈕影像的索引。 呼叫[CMFCToolBar::GetImages](#getimages)方法，以取得此集合的指標。  
  
##  <a name="a-namegetdisabledimagesa--cmfctoolbargetdisabledimages"></a><a name="getdisabledimages"></a>CMFCToolBar::GetDisabledImages  
 用於應用程式中的已停用的工具列按鈕的影像集合中傳回的指標。  
  
```  
static CMFCToolBarImages* __stdcall GetDisabledImages();
```  
  
### <a name="return-value"></a>傳回值  
 指標，已停用的工具列按鈕影像的集合。  
  
### <a name="remarks"></a>備註  
 使用載入已停用的工具列按鈕影像[CMFCToolBarEditBoxButton 類別](../../mfc/reference/cmfctoolbareditboxbutton-class.md)和[CMFCToolBar::LoadBitmap](#loadbitmap)方法。  
  
##  <a name="a-namegetdisabledmenuimagesa--cmfctoolbargetdisabledmenuimages"></a><a name="getdisabledmenuimages"></a>CMFCToolBar::GetDisabledMenuImages  
 用於應用程式中已停用的功能表按鈕的影像集合中傳回的指標。  
  
```  
static CMFCToolBarImages* __stdcall GetDisabledMenuImages();
```  
  
### <a name="return-value"></a>傳回值  
 已停用的功能表影像集合指標。  
  
### <a name="remarks"></a>備註  
 載入已停用的映像使用[CMFCToolBarEditBoxButton 類別](../../mfc/reference/cmfctoolbareditboxbutton-class.md)方法。  
  
##  <a name="a-namegetdroppeddownmenua--cmfctoolbargetdroppeddownmenu"></a><a name="getdroppeddownmenu"></a>CMFCToolBar::GetDroppedDownMenu  
 擷取目前正在顯示子功能表的功能表按鈕物件的指標。  
  
```  
CMFCToolBarMenuButton* GetDroppedDownMenu(int* pIndex = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `pIndex`  
 工具列按鈕的集合將會收到的按鈕索引。  
  
### <a name="return-value"></a>傳回值  
 顯示子功能表的功能表按鈕物件的指標或`NULL`如果功能表沒有顯示子功能表。  
  
### <a name="remarks"></a>備註  
 如果這個方法會傳回非`NULL`值和`pIndex`不`NULL`，所指值`pIndex`設為功能表按鈕的工具列按鈕集合中的索引。  
  
##  <a name="a-namegetgraydisabledbuttonsa--cmfctoolbargetgraydisabledbuttons"></a><a name="getgraydisabledbuttons"></a>CMFCToolBar::GetGrayDisabledButtons  
 指定已停用按鈕的影像是否要呈現暗灰色的版本一般按鈕的影像，或從已停用的按鈕影像的集合。  
  
```  
BOOL GetGrayDisabledButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`若要變暗的映像的已停用按鈕。`FALSE`取得集合中已停用映像的映像。  
  
### <a name="remarks"></a>備註  
 使用[CMFCToolBar::SetGrayDisabledButtons](#setgraydisabledbuttons)呈現暗灰色的映像和集合中已停用映像的映像之間切換。  
  
##  <a name="a-namegethighlightedbuttona--cmfctoolbargethighlightedbutton"></a><a name="gethighlightedbutton"></a>CMFCToolBar::GetHighlightedButton  
 讓指標回到目前反白顯示的工具列按鈕。  
  
```  
CMFCToolBarButton* GetHighlightedButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指向工具列按鈕物件。或`NULL`如果沒有按鈕會反白顯示。  
  
### <a name="remarks"></a>備註  
 如果它具有鍵盤焦點時，會反白顯示的工具列按鈕。 如果工具列按鈕的熱追蹤此應用程式中的工具列按鈕時也會反白顯示 (如需詳細資訊，請參閱[CMFCToolBar::GetHotBorder](#gethotborder)和[CMFCToolBar::SetHotBorder](#sethotborder)) 與滑鼠指向它時沒有工具列按鈕或功能表項目具有鍵盤焦點。  
  
##  <a name="a-namegethotbordera--cmfctoolbargethotborder"></a><a name="gethotborder"></a>CMFCToolBar::GetHotBorder  
 決定工具列按鈕是否*熱追蹤*。 如果按鈕是熱追蹤，其反白顯示，當滑鼠移過它。  
  
```  
BOOL GetHotBorder() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列按鈕的熱追蹤。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，工具列按鈕的熱追蹤。  
  
##  <a name="a-namegethottextcolora--cmfctoolbargethottextcolor"></a><a name="gethottextcolor"></a>CMFCToolBar::GetHotTextColor  
 傳回文字的色彩反白顯示的工具列按鈕。  
  
```  
static COLORREF GetHotTextColor();
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，代表目前的反白顯示的文字色彩。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCToolBar::SetHotTextColor](#sethottextcolor)設定新的文字色彩反白顯示的工具列按鈕。  
  
##  <a name="a-namegethwndlastfocusa--cmfctoolbargethwndlastfocus"></a><a name="gethwndlastfocus"></a>CMFCToolBar::GetHwndLastFocus  
 傳回之前工具列未擁有輸入的焦點的視窗控制代碼。  
  
```  
HWND GetHwndLastFocus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 不從衍生的視窗控制代碼[CMFCBaseToolBar 類別](../../mfc/reference/cmfcbasetoolbar-class.md)，其先前的輸入的焦點，或`NULL`如果沒有這類的時段。  
  
### <a name="remarks"></a>備註  
 當`CMFCToolBar`控制項收到輸入的焦點時，它就會將失去焦點，以便可以在稍後還原視窗的控制代碼。  
  
##  <a name="a-namegetignoresettexta--cmfctoolbargetignoresettext"></a><a name="getignoresettext"></a>CMFCToolBar::GetIgnoreSetText  
 指定是否設定按鈕標籤的呼叫都會被忽略。  
  
```  
BOOL GetIgnoreSetText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果設定按鈕標籤的呼叫都會被忽略。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetimagesa--cmfctoolbargetimages"></a><a name="getimages"></a>CMFCToolBar::GetImages  
 傳回的指標集合的預設按鈕影像應用程式中。  
  
```  
static CMFCToolBarImages* GetImages();
```  
  
### <a name="return-value"></a>傳回值  
 指標[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件，其中包含應用程式中的所有工具列的預設映像的集合。  
  
### <a name="remarks"></a>備註  
 此共用的方法提供應用程式的存取權的所有預設集合工具列影像。 呼叫[CMFCToolBar::LoadBitmap](#loadbitmap)方法，以將影像加入至集合。  
  
##  <a name="a-namegetimagesizea--cmfctoolbargetimagesize"></a><a name="getimagesize"></a>CMFCToolBar::GetImageSize  
 傳回目前的工具列按鈕影像的大小。  
  
```  
CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CSize 類別](../../atl-mfc-shared/reference/csize-class.md)物件，代表目前的工具列按鈕影像的大小。  
  
##  <a name="a-namegetimagesoffseta--cmfctoolbargetimagesoffset"></a><a name="getimagesoffset"></a>CMFCToolBar::GetImagesOffset  
 傳回用來尋找此工具列，工具列按鈕影像的全域清單中的工具列按鈕影像的索引位移。  
  
```  
int GetImagesOffset() const;  
```  
  
### <a name="return-value"></a>傳回值  
 工具列影像索引位移。  
  
### <a name="remarks"></a>備註  
 所有工具列預設影像會都儲存在全域[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)清單。 在工具列中的每個按鈕的映像會連續儲存在該清單。 若要計算之影像的索引，加入的按鈕索引工具列中的工具列按鈕的影像清單開頭的位移。  
  
 呼叫[CMFCToolBar::ButtonToIndex](#buttontoindex)取得指標給按鈕的工具列按鈕的索引。  
  
 呼叫[CMFCToolBar::GetImages](#getimages)取得變數的指標，工具列影像的集合。  
  
##  <a name="a-namegetinvalidateitemrecta--cmfctoolbargetinvalidateitemrect"></a><a name="getinvalidateitemrect"></a>CMFCToolBar::GetInvalidateItemRect  
 擷取指定索引處的按鈕就必須重新繪製的工作區的區域。  
  
```  
virtual void GetInvalidateItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 要擷取的工作區 按鈕的索引。  
  
 [輸出] `lpRect`  
 指標`RECT`物件，可接收用戶端區域的區域。  
  
### <a name="remarks"></a>備註  
 `lpRect`參數不得為`NULL`。 如果提供的索引，有沒有按鈕`lpRect`收到`RECT`會初始化為零的物件。  
  
##  <a name="a-namegetitemida--cmfctoolbargetitemid"></a><a name="getitemid"></a>CMFCToolBar::GetItemID  
 傳回指定索引處的工具列按鈕的命令 ID。  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定的工具列按鈕的索引。  
  
### <a name="return-value"></a>傳回值  
 命令 ID 的工具列按鈕。或如果不存在具有指定之索引的按鈕。  
  
##  <a name="a-namegetitemrecta--cmfctoolbargetitemrect"></a><a name="getitemrect"></a>CMFCToolBar::GetItemRect  
 傳回指定索引處的按鈕，這個周框。  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定的工具列按鈕的索引。  
  
 [輸出] `lpRect`  
 指標`CRect`接收影像的週框的座標的物件。  
  
### <a name="remarks"></a>備註  
 `CRect`物件`lpRect`點設定為 0，如果沒有指定索引處的按鈕。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`GetItemRect`方法`CMFCToolBar`類別。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&9;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_4.cpp)]  
  
##  <a name="a-namegetlargecoldimagesa--cmfctoolbargetlargecoldimages"></a><a name="getlargecoldimages"></a>CMFCToolBar::GetLargeColdImages  
 應用程式中的大型冷的工具列按鈕影像的集合中傳回的指標。  
  
```  
static CMFCToolBarImages* GetLargeColdImages();
```  
  
### <a name="return-value"></a>傳回值  
 指標的冷的大型影像集合。  
  
### <a name="remarks"></a>備註  
 冷映像是指在使用者不互動的工具列按鈕時所使用。 呼叫[CMFCToolBar::LoadBitmapEx](#loadbitmapex)載入大型冷映像。  
  
##  <a name="a-namegetlargedisabledimagesa--cmfctoolbargetlargedisabledimages"></a><a name="getlargedisabledimages"></a>CMFCToolBar::GetLargeDisabledImages  
 傳回集合的應用程式中的大型已停用的工具列按鈕影像的指標。  
  
```  
static CMFCToolBarImages* GetLargeDisabledImages();
```  
  
### <a name="return-value"></a>傳回值  
 指標的大型集合停用工具列按鈕影像。  
  
### <a name="remarks"></a>備註  
 大型影像是大型的標準工具列按鈕影像的版本。 呼叫[CMFCToolBar::LoadBitmapEx](#loadbitmapex)或[CMFCToolBar::LoadBitmap](#loadbitmap)載入大型影像。  
  
##  <a name="a-namegetlargeimagesa--cmfctoolbargetlargeimages"></a><a name="getlargeimages"></a>CMFCToolBar::GetLargeImages  
 應用程式中的大型工具列按鈕影像的集合中傳回的指標。  
  
```  
static CMFCToolBarImages* GetLargeImages();
```  
  
### <a name="return-value"></a>傳回值  
 指標的大型工具列按鈕影像集合。  
  
### <a name="remarks"></a>備註  
 大型影像是大型的標準工具列按鈕影像的版本。 呼叫[CMFCToolBar::LoadBitmapEx](#loadbitmapex)載入大型影像。  
  
##  <a name="a-namegetlockedcoldimagesa--cmfctoolbargetlockedcoldimages"></a><a name="getlockedcoldimages"></a>CMFCToolBar::GetLockedColdImages  
 在工具列上的鎖定冷映像的集合中傳回的指標。  
  
```  
CMFCToolBarImages* GetLockedColdImages();
```  
  
### <a name="return-value"></a>傳回值  
 鎖定冷的映像，集合的指標或`NULL`如果未鎖定工具列。  
  
### <a name="remarks"></a>備註  
 鎖定的影像是當使用者無法自訂工具列時，架構會使用標準工具列按鈕影像的版本。 冷映像是指在使用者不互動的工具列按鈕時所使用。  
  
 這個方法會傳回`NULL`如果未鎖定工具列。 這個方法也會會判斷提示失敗產生偵錯組建中，如果未鎖定工具列。 如需鎖定工具列的詳細資訊，請參閱[CMFCToolBar::IsLocked](#islocked)。  
  
 呼叫[CMFCToolBar::LoadBitmapEx](#loadbitmapex)方法，載入已鎖定的冷映像。  
  
##  <a name="a-namegetlockeddisabledimagesa--cmfctoolbargetlockeddisabledimages"></a><a name="getlockeddisabledimages"></a>CMFCToolBar::GetLockedDisabledImages  
 在工具列上的鎖定已停用映像的集合中傳回的指標。  
  
```  
CMFCToolBarImages* GetLockedDisabledImages();
```  
  
### <a name="return-value"></a>傳回值  
 鎖定已停用映像，集合的指標或`NULL`如果未鎖定工具列。  
  
### <a name="remarks"></a>備註  
 鎖定的影像是當使用者無法自訂工具列時，架構會使用標準工具列按鈕影像的版本。 已停用映像是指在架構時所使用的按鈕`TBBS_DISABLED`樣式。  
  
 這個方法會傳回`NULL`如果未鎖定工具列。 這個方法也會會判斷提示失敗產生偵錯組建中，如果未鎖定工具列。 如需鎖定工具列的詳細資訊，請參閱[CMFCToolBar::IsLocked](#islocked)。  
  
 呼叫[CMFCToolBar::LoadBitmapEx](#loadbitmapex)方法，載入已鎖定停用映像。  
  
##  <a name="a-namegetlockedimagesa--cmfctoolbargetlockedimages"></a><a name="getlockedimages"></a>CMFCToolBar::GetLockedImages  
 在工具列上的鎖定的按鈕影像的集合中傳回的指標。  
  
```  
CMFCToolBarImages* GetLockedImages();
```  
  
### <a name="return-value"></a>傳回值  
 鎖定的工具列按鈕的影像，集合的指標或`NULL`如果未鎖定工具列。  
  
### <a name="remarks"></a>備註  
 鎖定的影像是當使用者無法自訂工具列時，架構會使用標準工具列按鈕影像的版本。  
  
 這個方法會傳回`NULL`如果未鎖定工具列。 這個方法也會會判斷提示失敗產生偵錯組建中，如果未鎖定工具列。 如需鎖定工具列的詳細資訊，請參閱[CMFCToolBar::IsLocked](#islocked)。  
  
##  <a name="a-namegetlockedimagesizea--cmfctoolbargetlockedimagesize"></a><a name="getlockedimagesize"></a>CMFCToolBar::GetLockedImageSize  
 傳回已鎖定的工具列影像的預設大小。  
  
```  
CSize GetLockedImageSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`CSize`結構，指定鎖定的工具列影像或空白的大小`CSize`結構，如果未鎖定工具列。  
  
### <a name="remarks"></a>備註  
 鎖定的影像是當使用者無法自訂工具列時，架構會使用標準工具列按鈕影像的版本。  
  
 這個方法會傳回`CSize`結構和零的寬度和高度為零，如果未鎖定工具列。 這個方法也會會判斷提示失敗產生偵錯組建中，如果未鎖定工具列。 如需鎖定工具列的詳細資訊，請參閱[CMFCToolBar::IsLocked](#islocked)。  
  
 呼叫[CMFCToolBar::SetLockedSizes](#setlockedsizes)方法，以指定鎖定的映像大小。  
  
##  <a name="a-namegetlockedmenuimagesa--cmfctoolbargetlockedmenuimages"></a><a name="getlockedmenuimages"></a>CMFCToolBar::GetLockedMenuImages  
 傳回的指標集合的 [鎖定工具列] 功能表上的映像工具列中。  
  
```  
CMFCToolBarImages* GetLockedMenuImages();
```  
  
### <a name="return-value"></a>傳回值  
 鎖定的工具列 功能表上的影像，集合的指標或`NULL`如果未鎖定工具列。  
  
### <a name="remarks"></a>備註  
 鎖定映像是指版本的使用者無法自訂工具列時，架構會使用標準工具列功能表映像。  
  
 這個方法會傳回`NULL`如果未鎖定工具列。 這個方法也會會判斷提示失敗產生偵錯組建中，如果未鎖定工具列。 如需鎖定工具列的詳細資訊，請參閱[CMFCToolBar::IsLocked](#islocked)。  
  
 呼叫[CMFCToolBar::LoadBitmapEx](#loadbitmapex)方法來載入已鎖定的功能表影像。  
  
##  <a name="a-namegetmenubuttonsizea--cmfctoolbargetmenubuttonsize"></a><a name="getmenubuttonsize"></a>CMFCToolBar::GetMenuButtonSize  
 傳回應用程式功能表按鈕的大小。  
  
```  
static CSize GetMenuButtonSize();
```  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，表示功能表按鈕，單位為像素的大小。  
  
### <a name="remarks"></a>備註  
 在工具列上的功能表按鈕的大小保留為全域變數中，可以擷取這個靜態方法。  
  
 呼叫[CMFCToolBar::SetMenuSizes](#setmenusizes)設定這個全域變數。  
  
##  <a name="a-namegetmenuimagesa--cmfctoolbargetmenuimages"></a><a name="getmenuimages"></a>CMFCToolBar::GetMenuImages  
 應用程式中的功能表按鈕影像的集合中傳回的指標。  
  
```  
static CMFCToolBarImages* GetMenuImages();
```  
  
### <a name="return-value"></a>傳回值  
 指標的功能表影像集合。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCToolBar::LoadBitmapEx](#loadbitmapex)方法以載入功能表影像。  
  
 呼叫[CMFCToolBar::SetMenuSizes](#setmenusizes)方法來設定按鈕和其映像的大小。  
  
##  <a name="a-namegetmenuimagesizea--cmfctoolbargetmenuimagesize"></a><a name="getmenuimagesize"></a>CMFCToolBar::GetMenuImageSize  
 傳回應用程式功能表按鈕影像的大小。  
  
```  
static CSize GetMenuImageSize();
```  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，表示功能表影像的大小。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回影像的大小，維護與全域變數的工具列功能表按鈕上。 呼叫[CMFCToolBar::SetMenuSizes](#setmenusizes)設定這個全域變數。  
  
##  <a name="a-namegetorigbuttonsa--cmfctoolbargetorigbuttons"></a><a name="getorigbuttons"></a>CMFCToolBar::GetOrigButtons  
 擷取集合的非自訂按鈕的工具列。  
  
```  
const CObList& GetOrigButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非自訂按鈕的工具列的清單參考。  
  
### <a name="remarks"></a>備註  
 它們由使用者自訂之前，架構會建立工具列按鈕的複本。 [CMFCToolBar::SetButtons](#setbuttons)方法將每個按鈕的複本中所提供的陣列加入至原始按鈕的清單。 [CMFCToolBar::RestoreOriginalState](#restoreoriginalstate)方法會透過載入從資源檔來還原工具列的原始狀態。  
  
 若要設定的原始程式的工具列按鈕清單，請呼叫[CMFCToolBar::SetOrigButtons](#setorigbuttons)方法。  
  
##  <a name="a-namegetorigresetbuttonsa--cmfctoolbargetorigresetbuttons"></a><a name="getorigresetbuttons"></a>CMFCToolBar::GetOrigResetButtons  
 擷取集合的非自訂的重設按鈕的工具列。  
  
```  
const CObList& GetOrigResetButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
 參考的非自訂清單重設工具列的按鈕。  
  
### <a name="remarks"></a>備註  
 當使用者按一下**重設**按鈕在自訂模式下，架構會使用這個方法來還原已移除從工具列的按鈕。  
  
 [CMFCToolBar::SetButtons](#setbuttons)方法會將每個工具列按鈕的複本加入原始重設按鈕的清單之後，它會呼叫[CMFCToolBar::OnReset](#onreset)方法。 您可以覆寫[CMFCToolBar::OnReset](#onreset)方法，以自訂按鈕的外觀，使用者按下之後**重設** 按鈕。  
  
##  <a name="a-namegetresourceida--cmfctoolbargetresourceid"></a><a name="getresourceid"></a>CMFCToolBar::GetResourceID  
 擷取工具列的資源識別碼。  
  
```  
UINT GetResourceID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在工具列的資源識別碼。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCToolBar::LoadToolBarEx](#loadtoolbarex)方法來設定工具列的資源識別碼。  
  
##  <a name="a-namegetroutecommandsviaframea--cmfctoolbargetroutecommandsviaframe"></a><a name="getroutecommandsviaframe"></a>CMFCToolBar::GetRouteCommandsViaFrame  
 決定哪些物件、 父框架或擁有者，將命令傳送至工具列。  
  
```  
BOOL GetRouteCommandsViaFrame();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果父框架將命令傳送至工具列。0，表示擁有者會將命令傳送至工具列。  
  
### <a name="remarks"></a>備註  
 根據預設，父框架會將命令傳送至工具列。 呼叫[CMFCToolBar::SetRouteCommandsViaFrame](#setroutecommandsviaframe)來變更此行為。  
  
 如果這個方法會傳回非零值，您可以使用擷取父框架物件的指標`CMFCToolBar::GetCommandTarget`方法。 請參閱 VisualStudioDemo 範例，其中會使用這個方法的範例。  
  
##  <a name="a-namegetrowheighta--cmfctoolbargetrowheight"></a><a name="getrowheight"></a>CMFCToolBar::GetRowHeight  
 傳回工具列按鈕的高度。  
  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 工具列按鈕，單位為像素的高度。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以計算工具列版面配置。 在衍生類別來指定不同的高度，工具列中，這個方法會覆寫。  
  
##  <a name="a-namegetshowtooltipsa--cmfctoolbargetshowtooltips"></a><a name="getshowtooltips"></a>CMFCToolBar::GetShowTooltips  
 指定的工具列按鈕是否會顯示工具提示。  
  
```  
static BOOL GetShowTooltips();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具提示會顯示的工具列按鈕。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 依預設會顯示工具提示。 您可以變更這個靜態旗標呼叫[CMFCToolBar::SetShowTooltips](#setshowtooltips)。  
  
##  <a name="a-namegetsiblingtoolbara--cmfctoolbargetsiblingtoolbar"></a><a name="getsiblingtoolbar"></a>CMFCToolBar::GetSiblingToolBar  
 擷取工具列的同層級。  
  
```  
CMFCToolBar* GetSiblingToolBar();
```  
  
### <a name="return-value"></a>傳回值  
 同層級工具列指標。  
  
### <a name="remarks"></a>備註  
 如需有關如何啟用**按鈕顯示於資料列的資料上**和**按鈕顯示於兩個資料列上**按鈕，請參閱[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)。  
  
##  <a name="a-namegetuserimagesa--cmfctoolbargetuserimages"></a><a name="getuserimages"></a>CMFCToolBar::GetUserImages  
 應用程式中的使用者定義工具列按鈕影像的集合中傳回的指標。  
  
```  
static CMFCToolBarImages* GetUserImages();
```  
  
### <a name="return-value"></a>傳回值  
 指標的所有應用程式中的工具列的使用者定義工具列按鈕影像集合。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCToolBar::SetUserImages](#setuserimages)方法來設定應用程式中的使用者定義的影像集合。  
  
##  <a name="a-namehittesta--cmfctoolbarhittest"></a><a name="hittest"></a>CMFCToolBar::HitTest  
 傳回位於指定位置處的工具列按鈕的索引。  
  
```  
virtual int HitTest(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 要測試，在工作區座標的點。  
  
### <a name="return-value"></a>傳回值  
 位於指定的位置，則為-1 如果沒有這類的按鈕索引是按鈕的分隔符號。  
  
##  <a name="a-nameinsertbuttona--cmfctoolbarinsertbutton"></a><a name="insertbutton"></a>CMFCToolBar::InsertButton  
 插入工具列按鈕。  
  
```  
virtual int InsertButton(
    const CMFCToolBarButton& button,  
    INT_PTR iInsertAt=-1);

 
virtual int InsertButton(
    CMFCToolBarButton* pButton,  
    int iInsertAt=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `button`  
 指定要插入的按鈕。  
  
 [in] `iInsertAt`  
 指定要插入按鈕，以零為起始的位置。  
  
### <a name="return-value"></a>傳回值  
 位置的插入 按鈕，或-1 表示錯誤發生。  
  
### <a name="remarks"></a>備註  
 如果`iInsertAt`為-1，這個方法會將按鈕新增至工具列按鈕清單的結尾。  
  
 呼叫[CMFCToolBar::InsertSeparator](#insertseparator)方法來插入工具列中的分隔符號。  
  
##  <a name="a-nameinsertseparatora--cmfctoolbarinsertseparator"></a><a name="insertseparator"></a>CMFCToolBar::InsertSeparator  
 插入工具列中的分隔符號。  
  
```  
virtual int InsertSeparator(INT_PTR iInsertAt=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `iInsertAt`  
 指定要插入在分隔符號之以零為起始的位置。 這個參數必須是大於 0。  
  
### <a name="return-value"></a>傳回值  
 位置的分隔線已插入值或-1 表示錯誤發生。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以兩個現有的按鈕之間插入分隔符號。 如果`iInsertAt`為-1，此方法加入至工具列按鈕清單結尾分隔符號。  
  
 您無法使用這個方法，加入空白的工具列中的分隔符號。  
  
 呼叫[CMFCToolBar::InsertButton](#insertbutton)方法，以插入至工具列按鈕。  
  
##  <a name="a-nameinvalidatebuttona--cmfctoolbarinvalidatebutton"></a><a name="invalidatebutton"></a>CMFCToolBar::InvalidateButton  
 失效的工具列按鈕，在提供的索引存在的工作區。  
  
```  
CMFCToolBarButton* InvalidateButton(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 工具列中按鈕的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCToolBarButton`物件存在於提供的索引，或`NULL`如果物件不存在。  
  
### <a name="remarks"></a>備註  
 更新與工具列按鈕相關聯的工作區時，架構會呼叫這個方法。 它會呼叫[CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)方法的用戶端矩形`CMFCToolBarButton`存在所提供的索引處的物件。  
  
##  <a name="a-nameisaddremovequickcustomizea--cmfctoolbarisaddremovequickcustomize"></a><a name="isaddremovequickcustomize"></a>CMFCToolBar::IsAddRemoveQuickCustomize  
 決定使用者可以新增或移除工具列按鈕使用**自訂**功能表選項。  
  
```  
BOOL IsAddRemoveQuickCustomize();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果使用者可以使用**自訂**功能表選項，以修改工具列; 否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisaltcustomizemodea--cmfctoolbarisaltcustomizemode"></a><a name="isaltcustomizemode"></a>CMFCToolBar::IsAltCustomizeMode  
 指定是否*快速自訂*用來將按鈕拖曳。 啟用快速自訂時，使用者可以按下並按住 Alt 鍵，然後將按鈕拖曳至新位置。  
  
```  
static BOOL __stdcall IsAltCustomizeMode();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果正在使用快速自訂拖曳一個按鈕。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisautograyinactiveimagesa--cmfctoolbarisautograyinactiveimages"></a><a name="isautograyinactiveimages"></a>CMFCToolBar::IsAutoGrayInactiveImages  
 指定是否啟用自動產生的非作用中 （非反白顯示） 按鈕影像。  
  
```  
static BOOL IsAutoGrayInactiveImages();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用自動變暗非作用中的映像的選項。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以啟用或停用自動變暗的非作用中的映像藉由呼叫[CMFCToolBar::AutoGrayInactiveImages](#autograyinactiveimages)。  
  
##  <a name="a-nameisbasiccommanda--cmfctoolbarisbasiccommand"></a><a name="isbasiccommand"></a>CMFCToolBar::IsBasicCommand  
 判斷命令是否在基本命令的清單。  
  
```  
static BOOL IsBasicCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 指定要檢查的命令。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的命令屬於清單的基本命令的方式。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個靜態方法會判斷命令是否已由`uiCmd`屬於基本命令之全域清單。 您可以變更的基本命令清單，藉由呼叫[CMFCToolBar::AddBasicCommand](#addbasiccommand)或[CMFCToolBar::SetBasicCommands](#setbasiccommands)。  
  
##  <a name="a-nameisbuttonextrasizeavailablea--cmfctoolbarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCToolBar::IsButtonExtraSizeAvailable  
 決定工具列是否會顯示擴充框線的按鈕。  
  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果列可以顯示按鈕具有額外的框線大小。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 工具列物件傳回`TRUE`如果它可以顯示擴充框線的按鈕。 工具列按鈕時呼叫這個方法也可以處理[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)通知並據以設定其內部的額外框線大小旗標。 此內部旗標可能會稍後擷取藉由呼叫[CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)。  
  
 這個方法從衍生類別中的覆寫`CMFCToolBar`，並傳回`TRUE`如果您的列可以顯示額外的框線大小的工具列按鈕，並傳回`FALSE`否則。 預設實作會傳回 `TRUE`。  
  
##  <a name="a-nameisbuttonhighlighteda--cmfctoolbarisbuttonhighlighted"></a><a name="isbuttonhighlighted"></a>CMFCToolBar::IsButtonHighlighted  
 判斷指定的按鈕會反白顯示。  
  
```  
BOOL IsButtonHighlighted(int iButton) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iButton`  
 指定的工具列按鈕的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的按鈕會反白顯示。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameiscommandpermitteda--cmfctoolbariscommandpermitted"></a><a name="iscommandpermitted"></a>CMFCToolBar::IsCommandPermitted  
 決定是否要允許的命令。  
  
```  
static BOOL IsCommandPermitted(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 指定要檢查的命令。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果允許指定的命令。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個靜態方法會判斷命令是否已由`uiCmd`屬於非許可命令之全域清單。  
  
 您可以變更非允許的命令清單，藉由呼叫[CMFCToolBar::SetNonPermittedCommands](#setnonpermittedcommands)。  
  
##  <a name="a-nameiscommandrarelyuseda--cmfctoolbariscommandrarelyused"></a><a name="iscommandrarelyused"></a>CMFCToolBar::IsCommandRarelyUsed  
 決定是否很少使用的命令。  
  
```  
static BOOL IsCommandRarelyUsed(UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 指定要檢查的命令。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的命令很少使用。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `IsCommandRarelyUsed`方法會傳回`FALSE`一或多個下列情況發生︰  
  
-   指定的命令所屬的基本命令清單  
  
-   指定的命令是其中一個標準命令  
  
-   架構會在自訂模式  
  
-   基本命令的清單是空的  
  
-   超過 20%的命令呼叫會呼叫指定的命令。  
  
##  <a name="a-nameiscustomizemodea--cmfctoolbariscustomizemode"></a><a name="iscustomizemode"></a>CMFCToolBar::IsCustomizeMode  
 指定工具列 framework 是否為自訂模式。  
  
```  
static BOOL IsCustomizeMode();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果架構是在自訂模式。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以切換為自訂模式藉由呼叫[CMFCToolBar::SetCustomizeMode](#setcustomizemode)。  
  
 當使用者叫用自訂 對話方塊中，架構變更的模式 ( [CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md))。  
  
##  <a name="a-nameisdragbuttona--cmfctoolbarisdragbutton"></a><a name="isdragbutton"></a>CMFCToolBar::IsDragButton  
 決定是否要拖曳的工具列按鈕。  
  
```  
BOOL IsDragButton(const CMFCToolBarButton* pButton) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 工具列按鈕的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果拖曳至指定的按鈕。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisexistcustomizebuttona--cmfctoolbarisexistcustomizebutton"></a><a name="isexistcustomizebutton"></a>CMFCToolBar::IsExistCustomizeButton  
 判斷是否要包含工具列**自訂** 按鈕。  
  
```  
BOOL IsExistCustomizeButton();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列包含**自訂**按鈕; 否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果這個方法會傳回`TRUE`、 [CMFCToolBar::GetCustomizeButton](#getcustomizebutton)方法傳回的指標**自訂**出現結尾的工具列按鈕。  
  
 使用[CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton)方法來加入**自訂**至工具列按鈕。  
  
##  <a name="a-nameisfloatinga--cmfctoolbarisfloating"></a><a name="isfloating"></a>CMFCToolBar::IsFloating  
 決定是否要浮動工具列。  
  
```  
virtual BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果浮動工具列。，否則， `FALSE`。  
  
##  <a name="a-nameislargeiconsa--cmfctoolbarislargeicons"></a><a name="islargeicons"></a>CMFCToolBar::IsLargeIcons  
 指定是否在應用程式工具列目前顯示大圖示。  
  
```  
static BOOL IsLargeIcons();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果應用程式使用大圖示。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCToolBar::SetLargeIcons](#setlargeicons)大型圖示和一般圖示之間進行切換。  
  
 架構會自動變更模式，當使用者切換**大圖示**上的核取方塊**選項**頁面**自訂**對話方塊。  
  
##  <a name="a-nameislastcommandfrombuttona--cmfctoolbarislastcommandfrombutton"></a><a name="islastcommandfrombutton"></a>CMFCToolBar::IsLastCommandFromButton  
 決定是否最近執行命令用來傳送指定的工具列按鈕。  
  
```  
static BOOL IsLastCommandFromButton(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 按鈕的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果最後一個命令用來傳送 按鈕，`pButton`指定; 否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會取得變數的指標， [MSG 結構](../../mfc/reference/msg-structure1.md)藉由呼叫`CWnd::GetCurrentMessage`。 然後它會比較`HWND`與按鈕的`MSG::lParam`和`MSG::hwnd`成員，以判斷是否按鈕是命令的來源。  
  
##  <a name="a-nameislockeda--cmfctoolbarislocked"></a><a name="islocked"></a>CMFCToolBar::IsLocked  
 決定工具列是否已鎖定。  
  
```  
BOOL IsLocked() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列已鎖定。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`TRUE`當使用者無法執行自訂工作，例如重新定位工具列按鈕。  
  
 鎖定的工具列使用個別的映像清單。 如需這些影像清單的詳細資訊，請參閱[CMFCToolBar::LoadBitmapEx](#loadbitmapex)。  
  
##  <a name="a-nameisonerowwithsiblinga--cmfctoolbarisonerowwithsibling"></a><a name="isonerowwithsibling"></a>CMFCToolBar::IsOneRowWithSibling  
 判斷是否會將工具列和工具列，其同層級置於同一個資料列。  
  
```  
BOOL IsOneRowWithSibling();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列和其同層級位於相同的資料列。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 [CMFCCustomizeButton::CreatePopupMenu](http://msdn.microsoft.com/en-us/e501083e-f78e-4d8d-900c-40bd6e2bb7f8)方法會呼叫這個方法，以決定如何顯示**自訂**快顯功能表。 如果這個方法會傳回`TRUE`，架構會顯示**按鈕顯示於資料列的資料上** 按鈕。 否則，架構會顯示**按鈕顯示於兩個資料列上** 按鈕。  
  
 您通常不需要使用這個方法。 若要啟用**按鈕顯示於資料列的資料上**或**按鈕顯示於兩個資料列上**按鈕，呼叫[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)。  
  
##  <a name="a-nameisresourcechangeda--cmfctoolbarisresourcechanged"></a><a name="isresourcechanged"></a>CMFCToolBar::IsResourceChanged  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsResourceChanged() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameissiblinga--cmfctoolbarissibling"></a><a name="issibling"></a>CMFCToolBar::IsSibling  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsSibling();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisuserdefineda--cmfctoolbarisuserdefined"></a><a name="isuserdefined"></a>CMFCToolBar::IsUserDefined  
 指定工具列是否為使用者定義。  
  
```  
BOOL IsUserDefined() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列由使用者資訊。否則`FALSE`。  
  
##  <a name="a-nameloadbitmapa--cmfctoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFCToolBar::LoadBitmap  
 從應用程式資源載入工具列影像。  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiResID`  
 參考作用中工具列影像之點陣圖的資源 ID。  
  
 [in] `uiColdResID`  
 參考非作用中工具列影像之點陣圖的資源 ID。  
  
 [in] `uiMenuResID`  
 參考標準功能表影像之點陣圖的資源 ID。  
  
 [in] `bLocked`  
 `TRUE`若要鎖定工具列。否則`FALSE`。  
  
 [in] `uiDisabledResID`  
 參考已停用工具列影像之點陣圖的資源 ID。  
  
 [in] `uiMenuDisabledResID`  
 參考已停用功能表影像之點陣圖的資源 ID。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 [CMFCToolBar::LoadToolBarEx](#loadtoolbarex)方法會呼叫這個方法來載入與工具列相關聯的映像。 覆寫這個方法可執行影像資源的自訂載入。  
  
 呼叫 `LoadBitmapEx` 方法可在建立工具列之後載入其他影像。  
  
##  <a name="a-nameloadbitmapexa--cmfctoolbarloadbitmapex"></a><a name="loadbitmapex"></a>CMFCToolBar::LoadBitmapEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL LoadBitmapEx(
    CMFCToolBarInfo& params,  
    BOOL bLocked = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `params`  
 [in] `bLocked`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameloadlargeiconsstatea--cmfctoolbarloadlargeiconsstate"></a><a name="loadlargeiconsstate"></a>CMFCToolBar::LoadLargeIconsState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall LoadLargeIconsState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameloadparametersa--cmfctoolbarloadparameters"></a><a name="loadparameters"></a>CMFCToolBar::LoadParameters  
 從 Windows 登錄載入全域工具列選項。  
  
```  
static BOOL LoadParameters(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 指定 Windows 登錄機碼的相對路徑。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 這個方法會載入功能表動畫類型、 功能表陰影樣式，以及是否要顯示大圖示從 Windows 登錄等全域參數。  
  
 [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)方法會呼叫這個方法初始化程序的應用程式的一部分。  
  
##  <a name="a-nameloadstatea--cmfctoolbarloadstate"></a><a name="loadstate"></a>CMFCToolBar::LoadState  
 從 Windows 登錄載入工具列狀態資訊。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 指定 Windows 登錄機碼的相對路徑。  
  
 [in] `nIndex`  
 指定控制項 ID 的工具列。  
  
 [in] `uiID`  
 指定的資源識別碼的工具列。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法初始化程序的應用程式的一部分。 如需詳細資訊，請參閱[CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)。  
  
##  <a name="a-nameloadtoolbara--cmfctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFCToolBar::LoadToolBar  
 從應用程式資源載入工具列。  
  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0,  
    UINT uiHotResID=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiResID`  
 在工具列的資源識別碼。  
  
 [in] `uiColdResID`  
 參考非作用中工具列影像之點陣圖的資源 ID。  
  
 [in] `uiMenuResID`  
 參考標準功能表影像之點陣圖的資源 ID。  
  
 [in] `bLocked`  
 布林值，指定是否鎖定工具列。 如果這個參數是`TRUE`，工具列會鎖定。 否則，不鎖定工具列。  
  
 [in] `uiDisabledResID`  
 參考已停用工具列影像之點陣圖的資源 ID。  
  
 [in] `uiMenuDisabledResID`  
 參考已停用功能表影像之點陣圖的資源 ID。  
  
 [in] `uiHotResID`  
 參考作用中工具列影像之點陣圖的資源 ID。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 載入與工具列相關聯的映像的初始化期間，架構會呼叫這個方法。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`LoadToolBar`方法中的`CMFCToolBar`類別。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&7;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_3.cpp)]  
  
##  <a name="a-nameloadtoolbarexa--cmfctoolbarloadtoolbarex"></a><a name="loadtoolbarex"></a>CMFCToolBar::LoadToolBarEx  
 從應用程式資源載入工具列使用`CMFCToolBarInfo`helper 類別，可讓應用程式使用大量的影像。  
  
```  
virtual BOOL LoadToolBarEx(
    UINT uiToolbarResID,  
    CMFCToolBarInfo& params,  
    BOOL bLocked=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiToolbarResID`  
 在工具列的資源識別碼。  
  
 [in] `params`  
 參考`CMFCToolBarInfo`物件，其中包含工具列影像的資源 Id。  
  
 [in] `bLocked`  
 布林值，指定是否鎖定工具列。 如果這個參數是`TRUE`，工具列會鎖定。 否則，不鎖定工具列。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來從應用程式資源載入的工具列影像。  
  
##  <a name="a-namemdbllargeimageratioa--cmfctoolbarmdbllargeimageratio"></a><a name="m_dbllargeimageratio"></a>CMFCToolBar::m_dblLargeImageRatio  
 指定大量的影像維度 （高度或寬度） 與一般映像的維度之間的比率。  
  
```  
AFX_IMPORT_DATA static double m_dblLargeImageRatio;  
```  
  
### <a name="remarks"></a>備註  
 預設的比例為 2。 您可以變更此值可讓大型工具列映像，放大或縮小。  
  
 當您未指定一組大型映像時，架構會使用此資料成員。 例如，如果您提供的小型影像集合大小為 16 x 16，而且想大型映像大小 24 x 24，1.5 設定此資料成員。  
  
##  <a name="a-namenextmenua--cmfctoolbarnextmenu"></a><a name="nextmenu"></a>CMFCToolBar::NextMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL NextMenu();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonbeforeremovebuttona--cmfctoolbaronbeforeremovebutton"></a><a name="onbeforeremovebutton"></a>CMFCToolBar::OnBeforeRemoveButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnBeforeRemoveButton(
    CMFCToolBarButton* pButton,  
    DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 未使用。  
  
 [in] `dropEffect`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonchangehota--cmfctoolbaronchangehot"></a><a name="onchangehot"></a>CMFCToolBar::OnChangeHot  
 當使用者選取工具列上的按鈕，由架構呼叫。  
  
```  
virtual void OnChangeHot(int iHot);
```  
  
### <a name="parameters"></a>參數  
 [in] `iHot`  
 指定已選取; 工具列按鈕的索引或是-1，如果不選取任何工具列按鈕。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以處理程序通知使用者已選取工具列上的按鈕。  
  
##  <a name="a-nameonchangevisualmanagera--cmfctoolbaronchangevisualmanager"></a><a name="onchangevisualmanager"></a>CMFCToolBar::OnChangeVisualManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnChangeVisualManager();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonfillbackgrounda--cmfctoolbaronfillbackground"></a><a name="onfillbackground"></a>CMFCToolBar::OnFillBackground  
 從架構呼叫[CBasePane::DoPaint](../../mfc/reference/cbasepane-class.md#dopaint)工具列背景填滿。  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 [CMFCToolBar::DoPaint](#dopaint)已填入工具列的背景時呼叫這個方法。 預設實作不做任何動作。  
  
 覆寫這個方法在衍生類別中繪製自訂背景。  
  
##  <a name="a-nameonglobalfontschangeda--cmfctoolbaronglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBar::OnGlobalFontsChanged  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonreseta--cmfctoolbaronreset"></a><a name="onreset"></a>CMFCToolBar::OnReset  
 將工具列還原至其原始狀態。  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>備註  
 覆寫此方法以處理通知的工具列重設。  
  
 預設實作不做任何動作。 覆寫`OnReset`從衍生類別中`CMFCToolBar`工具列時有 dummy 工具列回到其原始狀態時，必須被取代的按鈕。  
  
##  <a name="a-nameonsetaccdataa--cmfctoolbaronsetaccdata"></a><a name="onsetaccdata"></a>CMFCToolBar::OnSetAccData  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>參數  
 [in] `lVal`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsetdefaultbuttontexta--cmfctoolbaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFCToolBar::OnSetDefaultButtonText  
 工具列按鈕的文字會還原為其預設狀態。  
  
```  
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 指向要設定其文字的按鈕。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`ifthe 文字已經順利還原;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以處理通知的工具列按鈕的文字會變成預設值。  
  
 預設實作會從應用程式資源載入按鈕的文字。  
  
##  <a name="a-nameonusertooltipa--cmfctoolbaronusertooltip"></a><a name="onusertooltip"></a>CMFCToolBar::OnUserToolTip  
 顯示按鈕的工具提示時，由架構呼叫。  
  
```  
virtual BOOL OnUserToolTip(
    CMFCToolBarButton* pButton,  
    CString& strTTText) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 工具提示便會顯示在工具列按鈕的點。  
  
 [輸出] `strTTText`  
 參考`CString`接收工具提示文字的物件。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`strTTText`已填入之工具提示文字，否則為`FALSE`。  
  
### <a name="remarks"></a>備註  
 要顯示的工具列按鈕的工具提示時，架構會呼叫這個方法。 如果`OnUserToolTip`傳回`TRUE`，架構會顯示工具提示，其中包含所傳回的文字`OnUserToolTip`中`strTTText`。 否則，工具提示會包含按鈕的文字。  
  
 覆寫`OnUserToolTip`自訂的工具列按鈕的工具提示。 預設實作會呼叫[CMFCToolBar::OnUserToolTip](#onusertooltip)取得的工具提示文字。  
  
##  <a name="a-nameprevmenua--cmfctoolbarprevmenu"></a><a name="prevmenu"></a>CMFCToolBar::PrevMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PrevMenu();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameprocesscommanda--cmfctoolbarprocesscommand"></a><a name="processcommand"></a>CMFCToolBar::ProcessCommand  
 文章`WM_COMMAND`訊息主控視窗的工具列。  
  
```  
BOOL ProcessCommand(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 指標，工具列上的按鈕。  
  
### <a name="return-value"></a>傳回值  
 這個方法一律會傳回`TRUE`。 MFC 使用`FALSE`內部值。  
  
### <a name="remarks"></a>備註  
 這個方法回傳`WM_COMMAND`主控視窗的工具列藉由呼叫訊息[CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage)和傳遞做為指定的按鈕的命令 ID`wParam`參數。  
  
 使用[ON_COMMAND](http://msdn.microsoft.com/library/f24f8bda-2cf4-49d5-aa3d-6f2e6bb003f2)巨集對應`WM_COMMAND`的成員函式的訊息。  
  
##  <a name="a-nameremoveallbuttonsa--cmfctoolbarremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCToolBar::RemoveAllButtons  
 從工具列中移除所有的按鈕和分隔符號。  
  
```  
virtual void RemoveAllButtons();
```  
  
### <a name="remarks"></a>備註  
 它會重新建立或終結工具列時，架構會呼叫這個方法。  
  
##  <a name="a-nameremovebuttona--cmfctoolbarremovebutton"></a><a name="removebutton"></a>CMFCToolBar::RemoveButton  
 從工具列中移除具有指定的索引的按鈕。  
  
```  
virtual BOOL RemoveButton(int iIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIndex`  
 指定的 [移除] 按鈕以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功，或`FALSE`如果不正確的指定的索引或索引參考**自訂** 按鈕。  
  
### <a name="remarks"></a>備註  
 這個方法會更新受影響的 [移除] 按鈕的其他工具列屬性。 例如，這個方法會從工具列中移除不必要的分隔符號，並重建的快速鍵資料表。  
  
 如需詳細資訊**自訂** 按鈕，請參閱[CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton)。  
  
##  <a name="a-nameremovestatefromregistrya--cmfctoolbarremovestatefromregistry"></a><a name="removestatefromregistry"></a>CMFCToolBar::RemoveStateFromRegistry  
 刪除 Windows 登錄中的工具列的狀態資訊。  
  
```  
virtual BOOL RemoveStateFromRegistry(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 指定的狀態資訊所在位置的登錄機碼。  
  
 [in] `nIndex`  
 工具列控制項 ID。  
  
 [in] `uiID`  
 在工具列的資源識別碼。 如果這個參數是-1，這個方法會使用[CWnd::GetDlgCtrlID](../../mfc/reference/cwnd-class.md#getdlgctrlid)方法來擷取資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 刪除使用者定義的工具列時，架構會呼叫這個方法。  
  
 如果您在 Windows 登錄中儲存其他狀態資訊，請覆寫這個方法。  
  
##  <a name="a-namereplacebuttona--cmfctoolbarreplacebutton"></a><a name="replacebutton"></a>CMFCToolBar::ReplaceButton  
 取代另一個工具列按鈕的工具列按鈕。  
  
```  
int ReplaceButton(
    UINT uiCmd,  
    const CMFCToolBarButton& button,  
    BOOL bAll=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 若要取代按鈕的命令 ID。  
  
 [in] `button`  
 參考`CMFCToolBarButton`插入。  
  
 [in] `bAll`  
 布林值，指定是否要取代所有具有所指定的命令 ID 的按鈕`uiCmd`。 如果這個參數是`TRUE`，取代所有具有指定的命令 ID 的按鈕。 否則，會取代第一個按鈕。  
  
### <a name="return-value"></a>傳回值  
 會被取代的按鈕數目。 如果不存在具有指定的命令 ID 的按鈕，這是在工具列上，這個方法會傳回 0。  
  
### <a name="remarks"></a>備註  
 當您想要加入無法從資源載入的工具列按鈕，請呼叫這個方法。 您可以在設計階段中建立預留位置 按鈕，並取代為自訂按鈕的按鈕時初始化工具列。 請參閱 VisualStudioDemo 範例，其中會使用這個方法的範例。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`ReplaceButton`方法中的`CMFCToolBar`類別。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&6;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&10;](../../mfc/reference/codesnippet/cpp/cmfctoolbar-class_5.cpp)]  
  
##  <a name="a-nameresetalla--cmfctoolbarresetall"></a><a name="resetall"></a>CMFCToolBar::ResetAll  
 將所有的工具列還原為原始狀態。  
  
```  
static void __stdcall ResetAll();
```  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CMFCToolBar::RestoreOriginalState](#restoreoriginalstate)可還原的應用程式中的每個工具列上的方法。 它會使用[CMFCToolBar::CanBeRestored](#canberestored)方法，以判斷是否可以還原工具列。  
  
##  <a name="a-nameresetallimagesa--cmfctoolbarresetallimages"></a><a name="resetallimages"></a>CMFCToolBar::ResetAllImages  
 清除所有應用程式中的工具列影像集合。  
  
```  
static void __stdcall ResetAllImages();
```  
  
### <a name="remarks"></a>備註  
 這個方法會清除已初始化的影像集合[CMFCToolBar::LoadToolBar](#loadtoolbar)和[CMFCToolBar::LoadBitmap](#loadbitmap)方法。  
  
##  <a name="a-nameresetimagesa--cmfctoolbarresetimages"></a><a name="resetimages"></a>CMFCToolBar::ResetImages  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ResetImages();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerestorefocusa--cmfctoolbarrestorefocus"></a><a name="restorefocus"></a>CMFCToolBar::RestoreFocus  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RestoreFocus();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerestoreoriginalstatea--cmfctoolbarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCToolBar::RestoreOriginalState  
 還原工具列的原始狀態。  
  
```  
virtual BOOL RestoreOriginalState();
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功即為 `TRUE`，方法失敗或工具列為使用者定義的，則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法從資源檔載入工具列使用[CMFCToolBar::LoadToolBar](#loadtoolbar)方法。  
  
 架構會呼叫這個方法，當使用者選擇**全部重設**按鈕**工具列**自訂對話方塊的頁面。  
  
##  <a name="a-namesaveparametersa--cmfctoolbarsaveparameters"></a><a name="saveparameters"></a>CMFCToolBar::SaveParameters  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall SaveParameters(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesavestatea--cmfctoolbarsavestate"></a><a name="savestate"></a>CMFCToolBar::SaveState  
 將工具列的狀態資訊儲存在 Windows 登錄。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 指定 Windows 登錄機碼的相對路徑。  
  
 [in] `nIndex`  
 工具列控制項 ID。  
  
 [in] `uiID`  
 在工具列的資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 應用程式狀態儲存至登錄時，架構會呼叫這個方法。 如需詳細資訊，請參閱[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)。  
  
##  <a name="a-namesetbasiccommandsa--cmfctoolbarsetbasiccommands"></a><a name="setbasiccommands"></a>CMFCToolBar::SetBasicCommands  
 設定當使用者開啟功能表，一定會顯示的命令清單。  
  
```  
static void __stdcall SetBasicCommands(CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>參數  
 [in] `lstCommands`  
 參考`CList`包含命令集合的物件。  
  
### <a name="remarks"></a>備註  
 開啟功能表時，一律會顯示基本命令。 當使用者選擇要檢視最近使用的命令時，這個方法是有意義。  
  
 使用[CMFCToolBar::AddBasicCommand](#addbasiccommand)方法，將命令加入至基本命令的清單。 使用[CMFCToolBar::GetBasicCommands](#getbasiccommands)方法來擷取基本命令，可由您的應用程式的清單。  
  
 請參閱總管範例，其中會使用這個方法的範例。  
  
##  <a name="a-namesetbuttoninfoa--cmfctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CMFCToolBar::SetButtonInfo  
 設定命令 ID、 樣式和影像的工具列按鈕的 ID。  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 按鈕時會設定其屬性的以零為起始的索引。  
  
 [in] `nID`  
 按鈕的命令 ID。  
  
 [in] `nStyle`  
 按鈕的樣式。 請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)可用工具列按鈕樣式清單。  
  
 [in] `iImage`  
 按鈕 （也就是集合中的工具列影像的索引） 的以零為起始的映像索引。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，設定工具列按鈕的屬性。  
  
 在偵錯組建中，這個方法會產生判斷提示失敗如果所指定的索引`nIndex`不正確。  
  
 呼叫[CMFCToolBar::SetButtonStyle](#setbuttonstyle)方法來設定按鈕的樣式。  
  
##  <a name="a-namesetbuttonsa--cmfctoolbarsetbuttons"></a><a name="setbuttons"></a>CMFCToolBar::SetButtons  
 設定工具列按鈕。  
  
```  
virtual BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount,  
    BOOL bRemapImages=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpIDArray`  
 若要插入的命令 Id 的按鈕陣列指標。  
  
 [in] `nIDCount`  
 中的項目數`lpIDArray`。  
  
 [in] `bRemapImages`  
 布林值，指定是否要將現有的按鈕影像與 [插入] 按鈕產生關聯。 如果這個參數是`TRUE`，影像會重新對應。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，從工具列移除現有的按鈕，並插入新按鈕的集合。  
  
 這個方法會加入**自訂**按鈕的工具列和傳送`AFX_WM_RESETTOOLBAR`訊息給父視窗的工具列。 如需詳細資訊**自訂** 按鈕，請參閱[CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton)。  
  
##  <a name="a-namesetbuttonstylea--cmfctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFCToolBar::SetButtonStyle  
 設定指定索引處的工具列按鈕的樣式。  
  
```  
virtual void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 設定為其樣式的工具列按鈕的以零為起始的索引。  
  
 [in] `nStyle`  
 按鈕的樣式。 請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)可用工具列按鈕樣式清單。  
  
### <a name="remarks"></a>備註  
 這個方法會移除`TBBS_PRESSED`樣式如果`nStyle`是`TBBS_DISABLED`因為使用者不能按一下 已停用的按鈕。  
  
##  <a name="a-namesetbuttontexta--cmfctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CMFCToolBar::SetButtonText  
 設定的文字標籤的工具列按鈕。  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 工具列按鈕的索引。  
  
 [in] `lpszText`  
 工具列按鈕的文字標籤。 必須為非`NULL`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`FALSE`如果提供的索引未參考有效的工具列按鈕。  
  
##  <a name="a-namesetcommandusageoptionsa--cmfctoolbarsetcommandusageoptions"></a><a name="setcommandusageoptions"></a>CMFCToolBar::SetCommandUsageOptions  
 指定當很少使用的命令未出現在應用程式的功能表中。  
  
```  
static BOOL SetCommandUsageOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage=5);
```  
  
### <a name="parameters"></a>參數  
 [in] `nStartCount`  
 指定架構顯示只有基本] 和 [最近使用過的命令之前，必須先執行命令的次數。  
  
 [in] `nMinUsagePercentage`  
 必須考量的最近使用過的命令執行命令的時間百分比。  
  
### <a name="return-value"></a>傳回值  
 `FALSE`如果`nMinUsagePercentage`等於或大於 100，否則`TRUE`。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以自訂架構使用，以判斷如何基本和最近使用的功能表項目出現的演算法。 如需基本命令的詳細資訊，請參閱[CMFCToolBar::AddBasicCommand](#addbasiccommand)。  
  
 此類別會使用`CMFCCmdUsageCount`類別來追蹤使用量的命令。 如需此類別的詳細資訊，請參閱[CMFCCmdUsageCount 類別](../../mfc/reference/cmfccmdusagecount-class.md)。  
  
##  <a name="a-namesetcustomizemodea--cmfctoolbarsetcustomizemode"></a><a name="setcustomizemode"></a>CMFCToolBar::SetCustomizeMode  
 啟用或停用應用程式中的所有工具列的自訂模式。  
  
```  
static BOOL __stdcall SetCustomizeMode(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bSet`  
 布林值，指定是否要啟用或停用自訂模式。 這個參數設定為`TRUE`啟用自訂模式或`FALSE`停用它。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果呼叫這個方法會變更自訂模式。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會調整的版面配置，並重新繪製應用程式中，每個工具列。 呼叫[CMFCToolBar::IsCustomizeMode](#iscustomizemode)方法，以判斷應用程式中自訂模式  
  
##  <a name="a-namesetgraydisabledbuttonsa--cmfctoolbarsetgraydisabledbuttons"></a><a name="setgraydisabledbuttons"></a>CMFCToolBar::SetGrayDisabledButtons  
 指定是否無法使用工具列上的按鈕會以灰色顯示，或是否要使用按鈕無法使用的映像。  
  
```  
void SetGrayDisabledButtons(BOOL bGrayDisabledButtons);
```  
  
### <a name="parameters"></a>參數  
 [in] `bGrayDisabledButtons`  
 布林值，指定如何顯示按鈕無法使用。 如果這個參數是`TRUE`，架構變暗的按鈕。 否則，架構會使用按鈕無法使用的影像的集合。  
  
### <a name="remarks"></a>備註  
 根據預設，無法使用的按鈕會呈暗灰色。  
  
##  <a name="a-namesetheighta--cmfctoolbarsetheight"></a><a name="setheight"></a>CMFCToolBar::SetHeight  
 設定工具列的高度。  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>參數  
 [in] `cyHeight`  
 在工具列中，單位為像素的高度。  
  
### <a name="remarks"></a>備註  
 將高度設定之後，這個方法會重繪工具列。  
  
##  <a name="a-namesethelpmodea--cmfctoolbarsethelpmode"></a><a name="sethelpmode"></a>CMFCToolBar::SetHelpMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall SetHelpMode(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bOn`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesethota--cmfctoolbarsethot"></a><a name="sethot"></a>CMFCToolBar::SetHot  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL SetHot(CMFCToolBarButton* pMenuButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuButton`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesethotbordera--cmfctoolbarsethotborder"></a><a name="sethotborder"></a>CMFCToolBar::SetHotBorder  
 指定工具列按鈕是否熱追蹤。  
  
```  
void SetHotBorder(BOOL bShowHotBorder);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShowHotBorder`  
 布林值，指定是否要熱追蹤工具列按鈕。 如果這個參數是`TRUE`，工具列熱追蹤它的按鈕。 否則，工具列不會不熱追蹤它的按鈕。  
  
### <a name="remarks"></a>備註  
 如果按鈕是熱追蹤，架構會反白顯示的按鈕時在滑鼠移過它。 根據預設，每個工具列熱追蹤它的按鈕。  
  
 呼叫[CMFCToolBar::GetHotBorder](#gethotborder)方法，以判斷是否工具列熱追蹤它的按鈕。  
  
##  <a name="a-namesethottextcolora--cmfctoolbarsethottextcolor"></a><a name="sethottextcolor"></a>CMFCToolBar::SetHotTextColor  
 設定作用的工具列按鈕的文字色彩。  
  
```  
static void SetHotTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>參數  
 [in] `clrText`  
 指定的熱追蹤工具列按鈕的文字色彩。  
  
### <a name="remarks"></a>備註  
 如需熱追蹤工具列按鈕的詳細資訊，請參閱[CMFCToolBar::GetHotBorder](#gethotborder)和[CMFCToolBar::SetHotBorder](#sethotborder)。  
  
##  <a name="a-namesetignoresettexta--cmfctoolbarsetignoresettext"></a><a name="setignoresettext"></a>CMFCToolBar::SetIgnoreSetText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetIgnoreSetText(BOOL bValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `bValue`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetlargeiconsa--cmfctoolbarsetlargeicons"></a><a name="setlargeicons"></a>CMFCToolBar::SetLargeIcons  
 指定工具列按鈕是否顯示大圖示。  
  
```  
static void SetLargeIcons(BOOL bLargeIcons=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bLargeIcons`  
 布林值，指定要使用的圖示。 如果這個參數是`TRUE`，架構會顯示大圖示。 否則，架構會顯示一般的圖示。  
  
### <a name="remarks"></a>備註  
 在使用者變更的狀態時，架構會呼叫這個方法**大圖示**中核取方塊**選項** 索引標籤的**自訂**對話方塊。 這個方法會調整大小的應用程式中所有的工具列。  
  
 根據預設，架構會顯示一般的圖示。  
  
 如需詳細資訊**自訂**對話方塊中，請參閱[CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)。  
  
##  <a name="a-namesetlockedsizesa--cmfctoolbarsetlockedsizes"></a><a name="setlockedsizes"></a>CMFCToolBar::SetLockedSizes  
 在工具列上設定鎖定的按鈕和鎖定的映像的大小。  
  
```  
void SetLockedSizes(
    SIZE sizeButton,  
    SIZE sizeImage,  
    BOOL bDontScale = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `sizeButton`  
 指定鎖定的工具列按鈕的大小。  
  
 [in] `sizeImage`  
 指定鎖定的工具列影像的大小。  
  
 `bDontScale`  
 指定是否要調整鎖定工具列影像在高 DPI 模式。  
  
### <a name="remarks"></a>備註  
 已鎖定 按鈕的預設大小為 23 x 22 像素。 鎖定的映像的預設大小為 16 x 15 像素。  
  
 呼叫[CMFCToolBar::GetLockedImageSize](#getlockedimagesize)方法來擷取的大小鎖定映像。 呼叫[CMFCToolBar::GetButtonSize](#getbuttonsize)方法來擷取的大小鎖定工具列按鈕。  
  
##  <a name="a-namesetmaskmodea--cmfctoolbarsetmaskmode"></a><a name="setmaskmode"></a>CMFCToolBar::SetMaskMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetMaskMode(BOOL bMasked);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMasked`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetmenusizesa--cmfctoolbarsetmenusizes"></a><a name="setmenusizes"></a>CMFCToolBar::SetMenuSizes  
 設定功能表的工具列按鈕和其影像的大小。  
  
```  
static void __stdcall SetMenuSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `sizeButton`  
 指定工具列按鈕的大小，單位為像素。  
  
 [in] `sizeImage`  
 指定工具列影像的大小，單位為像素。  
  
### <a name="remarks"></a>備註  
 根據預設，功能表按鈕和其映像有未定義的大小。  
  
 呼叫[CMFCToolBar::GetMenuButtonSize](#getmenubuttonsize)方法，以判斷功能表按鈕的大小和[CMFCToolBar::GetMenuImageSize](#getmenuimagesize)方法，以判斷功能表按鈕影像的大小。  
  
 請參閱 IEDemo 和 MSMoneyDemo 範例的範例，請使用這個方法。  
  
##  <a name="a-namesetnonpermittedcommandsa--cmfctoolbarsetnonpermittedcommands"></a><a name="setnonpermittedcommands"></a>CMFCToolBar::SetNonPermittedCommands  
 設定無法由使用者執行的命令清單。  
  
```  
static void SetNonPermittedCommands(CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>參數  
 [in] `lstCommands`  
 參考`CList`物件，其中包含無法由使用者執行的命令。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以防止使用者選取特定命令。 比方說，您可能想要防止使用者選取特定的命令，基於安全性考量。 請參閱 MDITabsDemo 和 MenuSubSet 範例的範例，請使用這個方法。  
  
 這個方法會清除前一份不允許的命令。 根據預設，不允許的命令清單是空的。  
  
##  <a name="a-namesetonerowwithsiblinga--cmfctoolbarsetonerowwithsibling"></a><a name="setonerowwithsibling"></a>CMFCToolBar::SetOneRowWithSibling  
 在工具列和其同層級置於相同的資料列。  
  
```  
void SetOneRowWithSibling();
```  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，當使用者按一下**按鈕顯示於資料列的資料上** 按鈕。  
  
 呼叫[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)方法，讓**按鈕顯示於資料列的資料上**或**按鈕顯示於兩個資料列上**按鈕。 如果您呼叫[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)工具列，同層級工具列會移至這個工具列的資料列。 否則，此工具列會移到同層級的資料列。  
  
 這個架構會呼叫[CMFCToolBar::SetTwoRowsWithSibling](#settworowswithsibling)方法，當使用者按一下**按鈕顯示於兩個資料列上** 按鈕。  
  
##  <a name="a-namesetorigbuttonsa--cmfctoolbarsetorigbuttons"></a><a name="setorigbuttons"></a>CMFCToolBar::SetOrigButtons  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetOrigButtons(const CObList& lstOrigButtons);
```  
  
### <a name="parameters"></a>參數  
 [in] `lstOrigButtons`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetpermamenta--cmfctoolbarsetpermament"></a><a name="setpermament"></a>CMFCToolBar::SetPermament  
 指定使用者是否可以關閉工具列。  
  
```  
void SetPermament(BOOL bPermament=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bPermament`  
 布林值，指定使用者是否可以關閉工具列。 如果這個參數是`TRUE`，使用者無法關閉工具列。 否則，使用者可以關閉工具列。  
  
### <a name="remarks"></a>備註  
 根據預設，使用者可以關閉每個工具列。  
  
 呼叫[CMFCToolBar::CanBeClosed](#canbeclosed)方法，以判斷使用者是否可以關閉工具列。  
  
##  <a name="a-namesetroutecommandsviaframea--cmfctoolbarsetroutecommandsviaframe"></a><a name="setroutecommandsviaframe"></a>CMFCToolBar::SetRouteCommandsViaFrame  
 指定是否在父框架或擁有者將命令傳送至工具列。  
  
```  
void SetRouteCommandsViaFrame(BOOL bValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `bValue`  
 如果這個參數是`TRUE`，父框架將命令傳送至工具列。 否則，擁有者會將命令傳送至工具列。  
  
### <a name="remarks"></a>備註  
 根據預設，父框架會將命令傳送至工具列。 呼叫[CMFCToolBar::GetRouteCommandsViaFrame](#getroutecommandsviaframe)方法，以判斷是否父框架或擁有者將命令傳送至工具列。  
  
##  <a name="a-namesetshowtooltipsa--cmfctoolbarsetshowtooltips"></a><a name="setshowtooltips"></a>CMFCToolBar::SetShowTooltips  
 指定是否，架構會顯示工具提示。  
  
```  
static void SetShowTooltips(BOOL bValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `bValue`  
 如果這個參數是`TRUE`，架構會顯示工具提示。 否則，架構會隱藏工具提示。  
  
### <a name="remarks"></a>備註  
 根據預設，架構會顯示工具提示。  
  
 呼叫[CMFCToolBar::GetShowTooltips](#getshowtooltips)方法，以判斷是否架構顯示工具提示。  
  
##  <a name="a-namesetsiblingtoolbara--cmfctoolbarsetsiblingtoolbar"></a><a name="setsiblingtoolbar"></a>CMFCToolBar::SetSiblingToolBar  
 指定工具列的同層級。  
  
```  
void SetSiblingToolBar(CMFCToolBar* pBrotherToolbar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBrotherToolbar`  
 同層級工具列指標。  
  
### <a name="remarks"></a>備註  
 這個方法可讓**按鈕顯示於資料列的資料上**或**按鈕顯示於兩個資料列上**使用者顯示時，所顯示的按鈕**自訂**快顯功能表。 當您想要讓使用者能夠指定是否要在相同的資料列或不同的資料列上顯示相關的工具列，請呼叫這個方法。  
  
 啟用之後，您呼叫這個方法**自訂**會出現在工具列的按鈕。 若要啟用**自訂** 按鈕，請呼叫[CMFCToolBar::EnableCustomizeButton](#enablecustomizebutton)方法。  
  
 若要擷取工具列的同層級，請呼叫[CMFCToolBar::GetSiblingToolBar](#getsiblingtoolbar)。  
  
##  <a name="a-namesetsizesa--cmfctoolbarsetsizes"></a><a name="setsizes"></a>CMFCToolBar::SetSizes  
 指定所有的工具列按鈕和影像的大小。  
  
```  
static void __stdcall SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `sizeButton`  
 工具列按鈕，單位為像素的大小。  
  
 [in] `sizeImage`  
 工具列按鈕影像像素為單位的大小。  
  
### <a name="remarks"></a>備註  
 工具列按鈕的預設大小為 23 x 22 像素。 工具列按鈕影像的預設大小為 16 x 15 像素。  
  
 呼叫[CMFCToolBar::GetImageSize](#getimagesize)方法來擷取工具列按鈕影像的大小。 呼叫[CMFCToolBar::GetButtonSize](#getbuttonsize)方法來擷取工具列按鈕的大小。  
  
##  <a name="a-namesettoolbarbtntexta--cmfctoolbarsettoolbarbtntext"></a><a name="settoolbarbtntext"></a>CMFCToolBar::SetToolBarBtnText  
 在工具列上，指定按鈕的屬性。  
  
```  
void SetToolBarBtnText(
    UINT nBtnIndex,  
    LPCTSTR szText=NULL,  
    BOOL bShowText=TRUE,  
    BOOL bShowImage=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nBtnIndex`  
 工具列按鈕的工具列按鈕清單中以零為起始的索引。  
  
 [in] `szText`  
 指定工具列按鈕的文字的標籤。  
  
 [in] `bShowText`  
 如果這個參數是`TRUE`，架構會顯示文字標籤。 否則，架構會隱藏文字標籤。  
  
 [in] `bShowImage`  
 如果這個參數是`TRUE`，架構會顯示工具列按鈕影像。 否則，架構會隱藏工具列按鈕影像。  
  
### <a name="remarks"></a>備註  
 根據預設，架構會顯示工具列按鈕的影像，但不會顯示的工具列按鈕的文字標籤。  
  
 在偵錯組建中，這個方法會產生判斷提示失敗如果`nBtnIndex`未參考有效的工具列按鈕或工具列按鈕是分隔符號。  
  
##  <a name="a-namesettworowswithsiblinga--cmfctoolbarsettworowswithsibling"></a><a name="settworowswithsibling"></a>CMFCToolBar::SetTwoRowsWithSibling  
 在工具列和其同層級置於個別的資料列。  
  
```  
void SetTwoRowsWithSibling();
```  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，當使用者按一下**按鈕顯示於兩個資料列上** 按鈕。  
  
 呼叫[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)方法，讓**按鈕顯示於資料列的資料上**或**按鈕顯示於兩個資料列上**按鈕。 如果您呼叫[CMFCToolBar::SetSiblingToolBar](#setsiblingtoolbar)工具列，同層級工具列會移至不同的資料列。 否則，此工具列會移至不同的資料列。  
  
 這個架構會呼叫[CMFCToolBar::SetOneRowWithSibling](#setonerowwithsibling)方法，當使用者按一下**按鈕顯示於資料列的資料上** 按鈕。  
  
##  <a name="a-namesetuserimagesa--cmfctoolbarsetuserimages"></a><a name="setuserimages"></a>CMFCToolBar::SetUserImages  
 應用程式中設定使用者定義的映像的集合。  
  
```  
static BOOL SetUserImages(CMFCToolBarImages* pUserImages);
```  
  
### <a name="parameters"></a>參數  
 [in] `pUserImages`  
 指標的使用者定義的影像集合。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功則為非零否則就是 0 指定`CMFCToolBarImages`物件無效，或在工具列的預設映像大小不同的映像大小。  
  
### <a name="remarks"></a>備註  
 架構會使用使用者定義的影像繪製由使用者自訂的工具列按鈕。 所指定的映像清單`pUserImages`共用應用程式中所有的工具列。  
  
 這個方法會產生判斷提示失敗偵錯組建中若指定`CMFCToolBarImages`物件無效，或在工具列的預設映像大小不同的映像大小。  
  
 OutlookDemo、 ToolTipDemo 和 VisualStudioDemo 範例會使用此方法來設定全域集合的使用者定義的映像。 載入名為 UserImages.bmp，位於應用程式的工作目錄中的檔案。  
  
 呼叫[CMFCToolBar::GetUserImages](#getuserimages)方法來擷取應用程式中使用者定義的映像的集合。  
  
##  <a name="a-namestretchpanea--cmfctoolbarstretchpane"></a><a name="stretchpane"></a>CMFCToolBar::StretchPane  
 垂直或水平延伸工具列，必要時重新定位的按鈕。  
  
```  
virtual CSize StretchPane(
    int nLength,  
    BOOL bVert);
```  
  
### <a name="parameters"></a>參數  
 [in] `nLength`  
 用來拉長窗格像素為單位數量。  
  
 [in] `bVert`  
 如果`TRUE`，垂直延伸 窗格。 如果`FALSE`，水平延伸 窗格。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，指定工具列工作區的大小。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CMFCToolBar::WrapToolBar](#wraptoolbar)重新定位內延展工具列按鈕。  
  
 傳回值由呼叫[CMFCToolBar::CalcSize](#calcsize)。  
  
##  <a name="a-nametranslatechara--cmfctoolbartranslatechar"></a><a name="translatechar"></a>CMFCToolBar::TranslateChar  
 如果指定的按鍵碼對應至有效的鍵盤快速鍵，請執行按鈕命令。  
  
```  
virtual BOOL TranslateChar(UINT nChar);
```  
  
### <a name="parameters"></a>參數  
 [in] `nChar`  
 指定以虛擬按鍵碼。 如需標準虛擬按鍵碼的清單，請參閱 winuser.h.  
  
### <a name="return-value"></a>傳回值  
 `FALSE`如果指定的按鍵碼無法列印，或者沒有對應至有效的鍵盤快速鍵。`TRUE` ，如果指定的按鍵碼對應至下拉式選單選項; 否則傳回值從[CMFCToolBar::ProcessCommand](#processcommand)。  
  
### <a name="remarks"></a>備註  
 按鍵與 Alt 鍵時，架構會呼叫這個方法。  
  
##  <a name="a-nameupdatebuttona--cmfctoolbarupdatebutton"></a><a name="updatebutton"></a>CMFCToolBar::UpdateButton  
 更新指定的按鍵的狀態。  
  
```  
void UpdateButton(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 指定的 [更新] 按鈕以零為起始的索引。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namewraptoolbara--cmfctoolbarwraptoolbar"></a><a name="wraptoolbar"></a>CMFCToolBar::WrapToolBar  
 重新放置在指定的維度內的工具列按鈕。  
  
```  
int WrapToolBar(
    int nWidth,  
    int nHeight = 32767,  
    CDC* pDC = NULL,  
    int nColumnWidth = -1,  
    int nRowHeight = -1);
```  
  
### <a name="parameters"></a>參數  
 [in] `nWidth`  
 在工具列的最大寬度。  
  
 [in] `nHeight`  
 在工具列的最大高度。 如果不會使用浮動工具列。  
  
 [in] `pDC`  
 裝置內容的指標。 如果是 NULL，則會使用工具列的裝置內容。  
  
 [in] `nColumnWidth`  
 按鈕的寬度。 如果為-1，則會使用目前的寬度。  
  
 [] in m`nRowHeight`  
 按鈕的高度。 如果為-1，則會使用目前的高度。  
  
### <a name="return-value"></a>傳回值  
 工具列按鈕的資料列數目。  
  
### <a name="remarks"></a>備註  
 這個方法會重新定位在包裝其他資料列，如有必要的按鈕的工具列中的按鈕。  
  
##  <a name="a-namembdontscaleimagesa--cmfctoolbarmbdontscaleimages"></a><a name="m_bdontscaleimages"></a>CMFCToolBar::m_bDontScaleImages  
 指定要在高 DPI 模式中調整工具列影像。  
  
```  
AFX_IMPORT_DATA static BOOL m_bDontScaleImages;  
```  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCMenuBar 類別](../../mfc/reference/cmfcmenubar-class.md)   
 [CMFCPopupMenuBar 類別](../../mfc/reference/cmfcpopupmenubar-class.md)   
 [CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [逐步解說︰ 將放在工具列上的控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)




