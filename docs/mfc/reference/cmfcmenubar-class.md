---
title: "CMFCMenuBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuBar class
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
caps.latest.revision: 36
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
ms.openlocfilehash: ab2896f5ebab0df894f70e5ddb85bae3a5e1d5af
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar 類別
實作停駐的功能表列。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(覆寫 `CMFCToolBar::AdjustLocations`。)|  
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|指定是否可以顯示文字標籤影像的工具列按鈕下方。 (覆寫[CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels)。)|  
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(覆寫 `CPane::AllowShowOnPaneMenu`。)|  
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|計算的水平大小的工具列。 (覆寫[CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout)。)|  
|[CMFCMenuBar::CalcLayout](#calclayout)|(覆寫 `CMFCToolBar::CalcLayout`。)|  
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|計算工具列中按鈕的最大高度。 (覆寫[CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight)。)|  
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|指定使用者是否可以關閉工具列。 (覆寫[CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed)。)|  
|[CMFCMenuBar::CanBeRestored](#canberestored)|決定是否系統可以工具列後還原到其原始狀態的自訂。 (覆寫[CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|  
|[CMFCMenuBar::Create](#create)|建立功能表控制項並將它附加`CMFCMenuBar`物件。|  
|[CMFCMenuBar::CreateEx](#createex)|建立`CMFCMenuBar`具有其他樣式選項物件。|  
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|初始化`CMFCMenuBar`物件。 接受`HMENU`做為填入範本的參數`CMFCMenuBar`。|  
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|可讓**協助**位於功能表列右邊的下拉式方塊。|  
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|指定是否要顯示快顯功能表的陰影。|  
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(覆寫[CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize)。)|  
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|傳回的工具列按鈕的寬度。 (覆寫[CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth)。)|  
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|傳回原始的功能表資源檔中的控制代碼。|  
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|傳回資源檔中的 [原始] 功能表上的資源識別碼。|  
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||  
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||  
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|傳回的指標**協助**下拉式方塊。|  
|[CMFCMenuBar::GetHMenu](#gethmenu)|傳回連接到 功能表上的控制代碼`CMFCMenuBar`物件。|  
|[CMFCMenuBar::GetMenuFont](#getmenufont)|傳回目前全域字型功能表物件。|  
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|傳回與提供項目索引相關聯的工具列按鈕。|  
|[CMFCMenuBar::GetRowHeight](#getrowheight)|傳回工具列按鈕的高度。 (覆寫[CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight)。)|  
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||  
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||  
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||  
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|指出是否已停用的功能表項目會反白顯示。|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|決定工具列是否會顯示擴充框線的按鈕。 (覆寫[CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable)。)|  
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|指出是否停用項目會反白顯示。|  
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|指出是否繪製陰影，以供快顯功能表。|  
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|指出是否在功能表列上顯示最近使用的功能表命令。|  
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|表示快顯功能表是否顯示所有命令。|  
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|表示功能表是否顯示在短暫延遲之後的所有命令。|  
|[CMFCMenuBar::LoadState](#loadstate)|載入的狀態`CMFCMenuBar`登錄中的物件。|  
|[CMFCMenuBar::OnChangeHot](#onchangehot)|當使用者選取工具列上的按鈕，由架構呼叫。 (覆寫[CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot)。)|  
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|框架視窗從資源檔載入預設功能表時，由架構呼叫。|  
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(覆寫 `CMFCToolBar::OnSendCommand`。)|  
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|當功能表會在自訂模式，並在使用者變更功能表項目的文字，由架構呼叫。|  
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(覆寫 `CMFCToolBar::OnToolHitTest`。)|  
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(覆寫 `CMFCToolBar::PreTranslateMessage`。)|  
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|功能表會在自訂模式和使用者選取時，由框架呼叫**重設**功能表列。|  
|[CMFCMenuBar::SaveState](#savestate)|儲存的狀態`CMFCMenuBar`登錄的物件。|  
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|資源檔中設定的原始的功能表。|  
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||  
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|MDI 子視窗變更它的顯示模式時，由架構呼叫。 如果 MDI 子視窗新最大化或不再最大化時，這個方法會更新功能表列。|  
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|設定使用者以動態方式建立功能表按鈕時，會產生執行階段類別資訊。|  
|[CMFCMenuBar::SetMenuFont](#setmenufont)|設定應用程式中的所有功能表字型。|  
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|指定是否功能表列會顯示最近使用的功能表命令。|  
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|指定是否在功能表列會顯示所有命令。|  
  
## <a name="remarks"></a>備註  
 `CMFCMenuBar`類別會實作停駐功能的功能表列。 它類似於工具列中，雖然無法關閉-一律會顯示。  
  
 `CMFCMenuBar`支援的選項，顯示最近使用的功能表項目物件。 如果已啟用此選項，`CMFCMenuBar`僅會顯示可用命令的第一個檢視。 此後，最近使用的命令會顯示，以及原始命令的子集。 此外，使用者永遠可以展開要檢視所有可用命令的功能表。 因此，每個可用的命令被設定為顯示一直在改變，或具有最近選取時，才會顯示。  
  
 若要使用`CMFCMenuBar`物件，將它內嵌在主視窗框架物件。 處理時`WM_CREATE`訊息，請呼叫`CMFCMenuBar::Create`或`CMFCMenuBar::CreateEx`。 不論其建立函式您可以使用，傳入到主框架視窗的指標。 然後啟用 停駐藉由呼叫[CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking)。 藉由呼叫停駐這個功能表[CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCMenuBar`類別。 此範例示範如何設定窗格的樣式，啟用 自訂 按鈕，啟用 方塊、 啟用陰影的快顯功能表，以及更新功能表列。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&1;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&3;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 `CMFCMenuBar`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmenubar.h  
  
##  <a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations  
 調整在功能表列上的功能表項目的位置。  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels  
 決定是否允許文字標籤底下的功能表列中的映像。  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果使用者可以選擇顯示影像下方文字標籤。  
  
### <a name="remarks"></a>備註  
  
##  <a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="calclayout"></a>CMFCMenuBar::CalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize CalcLayout(
    DWORD dwMode,  
    int nLength = -1);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwMode`  
 [in] `nLength`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int CalcMaxButtonHeight();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="canbeclosed"></a>CMFCMenuBar::CanBeClosed  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="canberestored"></a>CMFCMenuBar::CanBeRestored  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeRestored() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="create"></a>CMFCMenuBar::Create  
 建立功能表控制項並將它附加[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT nID = AFX_IDW_MENUBAR);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParentWnd`  
 新的父視窗的指標`CMFCMenuBar`物件。  
  
 [in] `dwStyle`  
 新的功能表列的樣式。  
  
 [in] `nID`  
 子視窗功能表列的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 在建構之後`CMFCMenuBar`物件，您必須呼叫`Create`。 這個方法會建立`CMFCMenuBar`控制，並將它附加`CMFCMenuBar`物件。  
  
 如需有關 toolbar 樣式的詳細資訊，請參閱[CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)。  
  
##  <a name="createex"></a>CMFCMenuBar::CreateEx  
 建立[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件與指定的延伸樣式。  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = TBSTYLE_FLAT,  
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,  
    CRect rcBorders = CRect(1,
    1,
    1,
    1),  
    UINT nID =AFX_IDW_MENUBAR);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParentWnd`  
 新的父視窗的指標`CMFCMenuBar`物件。  
  
 [in] `dwCtrlStyle`  
 新的功能表列的其他樣式。  
  
 [in] `dwStyle`  
 新的功能表列的主要的樣式。  
  
 [in] `rcBorders`  
 A`CRect`參數，指定的框線大小`CMFCMenuBar`物件。  
  
 [in] `nID`  
 子視窗功能表列的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您應該使用此函式，而不是[CMFCMenuBar::Create](#create)當您想要指定除了工具列樣式的樣式。 某些經常使用的其他樣式`TBSTYLE_TRANSPARENT`和`CBRS_TOP`。  
  
 如需其他樣式的清單，請參閱[工具列控制項和按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb760439)，[常用的控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775498)，和[常用的視窗樣式](http://msdn.microsoft.com/library/windows/desktop/ms632600)。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`CreateEx`方法`CMFCMenuBar`類別。 此程式碼片段是一部分[IE 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_IEDemo #&1;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo #&2;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]  
  
##  <a name="createfrommenu"></a>CMFCMenuBar::CreateFromMenu  
 初始化[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。 此方法模型`CMFCMenuBar`物件之後`HMENU`參數。  
  
```  
virtual void CreateFromMenu(
    HMENU hMenu,  
    BOOL bDefaultMenu = FALSE,  
    BOOL bForceUpdate = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenu`  
 功能表資源控制代碼。 `CreateFromMenu`使用這項資源的範本為`CMFCMenuBar`。  
  
 [in] `bDefaultMenu`  
 布林值，指出新的功能表是否為預設的功能表。  
  
 [in] `bForceUpdate`  
 布林值，指出這個方法是否會強制功能表更新。  
  
### <a name="remarks"></a>備註  
 如果您想要有相同的功能表項目，做為功能表資源的功能表控制項，請使用這個方法。 您可以呼叫之後，呼叫這個方法[CMFCMenuBar::Create](#create)或[CMFCMenuBar::CreateEx](#createex)。  
  
##  <a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox  
 可讓**協助**位於功能表列右邊的下拉式方塊。  
  
```  
void EnableHelpCombobox(
    UINT uiID,  
    LPCTSTR lpszPrompt = NULL,  
    int nComboBoxWidth = 150);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 命令 ID 的按鈕**協助**下拉式方塊。  
  
 [in] `lpszPrompt`  
 字串，其中包含的文字，架構會顯示在下拉式方塊中，如果它是空的不會啟用。 比方說，「 輸入的文字 」。  
  
 [in] `nComboBoxWidth`  
 像素為單位的下拉式方塊按鈕的寬度。  
  
### <a name="remarks"></a>備註  
 **協助**下拉式方塊類似於**協助**下拉式方塊中的功能表列[!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)]。  
  
 當您呼叫這個方法與`uiID`設為 0，這個方法會隱藏下拉式方塊。 否則，這個方法下拉式方塊會自動顯示在功能表列的右邊。 呼叫這個方法之後，請呼叫[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)以取得所插入的指標[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件。  
  
##  <a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows  
 啟用快顯功能表的陰影。  
  
```  
static void EnableMenuShadows(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值的參數，指出是否應該啟用快顯功能表的陰影。  
  
### <a name="remarks"></a>備註  
 這個方法會使用的演算法很複雜，而且可能會降低速度較慢的系統上的應用程式的效能。  
  
##  <a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableExpandSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetColumnWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu  
 擷取原始的功能表上的控制代碼。 架構會從資源檔載入原始的功能表。  
  
```  
HMENU GetDefaultMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能表資源控制代碼。  
  
### <a name="remarks"></a>備註  
 如果您的應用程式自訂功能表，您可以使用這個方法來擷取 [原始] 功能表上的控制代碼。  
  
##  <a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId  
 擷取預設的功能表資源識別項。  
  
```  
UINT GetDefaultMenuResId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能表資源的識別項。  
  
### <a name="remarks"></a>備註  
 架構便會載入預設功能表`CMFCMenuBar`資源檔中的物件。  
  
##  <a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetForceDownArrows();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox  
 傳回的指標**協助**下拉式方塊。  
  
```  
CMFCToolBarComboBoxButton* GetHelpCombobox();
```  
  
### <a name="return-value"></a>傳回值  
 指標**協助**下拉式方塊。 `NULL`如果**協助**隱藏或未啟用下拉式方塊。  
  
### <a name="remarks"></a>備註  
 **協助**下拉式方塊位於功能表列的右側。 呼叫方法[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)若要啟用此下拉式方塊。  
  
##  <a name="gethmenu"></a>CMFCMenuBar::GetHMenu  
 擷取附加至 功能表上的控制代碼[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。  
  
```  
HMENU GetHMenu() const;  
```  
  
##  <a name="getmenufont"></a>CMFCMenuBar::GetMenuFont  
 擷取目前的功能表字型。  
  
```  
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bHorz`  
 布林值的參數，指定是否要傳回的水平或垂直字型。 `TRUE`表示水平字型。  
  
### <a name="return-value"></a>傳回值  
 指標[CFont](../../mfc/reference/cfont-class.md)參數，其中包含目前的功能表列字型。  
  
### <a name="remarks"></a>備註  
 傳回的字型是應用程式的全域參數。 兩個通用的字型會維護所有`CMFCMenuBar`物件。 水平和垂直的功能表列會使用這些不同的字型。  
  
##  <a name="getmenuitem"></a>CMFCMenuBar::GetMenuItem  
 擷取[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件在功能表列上的，根據項目索引。  
  
```  
CMFCToolBarButton* GetMenuItem(int iItem) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iItem`  
 傳回功能表項目的索引。  
  
### <a name="return-value"></a>傳回值  
 指標`CMFCToolBarButton`符合指定的索引物件`iItem`。 `NULL`如果索引無效。  
  
##  <a name="getrowheight"></a>CMFCMenuBar::GetRowHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getsystembutton"></a>CMFCMenuBar::GetSystemButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,  
    BOOL bByCommand = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `uiBtn`  
 [in] `bByCommand`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSystemButtonsCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolBarSystemMenuButton* GetSystemMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems  
 控制是否在 framework 反白顯示已停用的功能表項目。  
  
```  
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bHighlight`  
 布林值的參數，指出是否在 framework 反白顯示無法使用的功能表項目。  
  
### <a name="remarks"></a>備註  
 根據預設，架構不醒目提示無法使用的功能表項目時，使用者將滑鼠指標停留。  
  
##  <a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtraSizeAvailable  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems  
 指出是否在 framework 反白顯示無法使用的功能表項目。  
  
```  
static BOOL IsHighlightDisabledItems();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果無法使用的功能表項目會反白顯示。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，架構不醒目提示無法使用的功能表項目時，使用者將滑鼠指標停留。 使用[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)方法，以啟用這項功能。  
  
##  <a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows  
 指出架構是否繪製陰影的快顯功能表。  
  
```  
static BOOL IsMenuShadows();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果架構繪製功能表陰影;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)方法，以啟用或停用此功能。  
  
##  <a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus  
 指出是否在功能表列上顯示最近使用的功能表命令。  
  
```  
static BOOL IsRecentlyUsedMenus();
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CMFCMenuBar`物件也會顯示最近使用功能表命令，否則傳回 0。  
  
### <a name="remarks"></a>備註  
 使用函數[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)控制功能表是否顯示最近使用的功能表命令。  
  
##  <a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands  
 表示功能表是否顯示所有命令。  
  
```  
static BOOL IsShowAllCommands();
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CMFCMenuBar`會顯示所有命令，否則傳回 0。  
  
### <a name="remarks"></a>備註  
 A`CMFCMenuBar`物件可以設定為顯示所有命令，或僅都顯示部分的命令。 如需這項功能的詳細資訊，請參閱[CMFCMenuBar 類別](../../mfc/reference/cmfcmenubar-class.md)。  
  
 `IsShowAllCommands`會告訴您如何設定這項功能的`CMFCMenuBar`物件。 若要控制顯示的功能表命令，使用方法[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)和[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)。  
  
##  <a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay  
 指出是否[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件會顯示在短暫延遲之後的所有命令。  
  
```  
static BOOL IsShowAllCommandsDelay();
```  
  
### <a name="return-value"></a>傳回值  
 如果功能表列會顯示完整的功能表在短暫的延遲; 之後，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 當您設定的功能表列，顯示最近使用過的項目時，功能表列會顯示完整的功能表中有兩種︰  
  
-   當游標停留在功能表底部的箭號，從程式化的延遲之後顯示完整的功能表。  
  
-   在使用者按一下功能表底部的箭頭之後，請顯示完整的功能表。  
  
 根據預設，所有`CMFCMenuBar`物件使用短暫的延遲之後會出現完整的功能表選項。 無法變更此選項以程式設計方式在`CMFCMenuBar`類別。 不過，使用者可以變更行為工具列自訂期間使用**自訂**對話方塊...  
  
##  <a name="loadstate"></a>CMFCMenuBar::LoadState  
 從 Windows 登錄載入功能表列的狀態。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 字串，其中包含 Windows 登錄機碼路徑。  
  
 [in] `nIndex`  
 功能表列的控制項 ID。  
  
 [in] `uiID`  
 保留的值。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CMFCMenuBar::SaveState](#savestate)方法，將功能表列的狀態儲存至登錄。 已儲存的資訊包括功能表項目、 停駐狀態和功能表列的位置。  
  
 在大部分情況下您的應用程式不會呼叫`LoadState`。 初始化工作區時，架構會呼叫這個方法。  
  
##  <a name="onchangehot"></a>CMFCMenuBar::OnChangeHot  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnChangeHot(int iHot);
```  
  
### <a name="parameters"></a>參數  
 [in] `iHot`  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded  
 從資源檔載入功能表資源時，架構會呼叫這個方法。  
  
```  
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenu`  
 功能表的控制代碼會附加至`CMFCMenuBar`物件。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作不做任何動作。 覆寫這個函式來執行自訂程式碼之後，架構會從資源檔載入功能表資源。  
  
##  <a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText  
 在使用者變更的項目在功能表列上的文字時，架構會呼叫這個方法。  
  
```  
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 指標[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)使用者想要自訂的物件。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果架構適用於使用者變更至功能表列。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法的預設實作會變更為使用者提供文字的按鈕的文字。  
  
##  <a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 [in] `pTI`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="pretranslatemessage"></a>CMFCMenuBar::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMsg`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate  
 當使用者選取時，由框架呼叫**重設**從**自訂**對話方塊。  
  
```  
virtual BOOL RestoreOriginalstate();
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 當使用者選取時，會呼叫這個方法**重設**從自訂功能表。 您可以手動呼叫這個方法，以程式設計方式重設功能表列的狀態。 這個方法會從資源檔載入的原始狀態。  
  
 覆寫這個方法，如果您想要執行任何處理，當使用者選取**重設**選項。  
  
##  <a name="savestate"></a>CMFCMenuBar::SaveState  
 儲存的狀態[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件至 Windows 登錄。  
  
```  
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 字串，其中包含 Windows 登錄機碼路徑。  
  
 [in] `nIndex`  
 功能表列的控制項 ID。  
  
 [in] `uiID`  
 保留的值。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。，否則`FALSE`;  
  
### <a name="remarks"></a>備註  
 通常，您的應用程式未呼叫`SaveState`。 序列化的工作區時，架構會呼叫這個方法。 如需詳細資訊，請參閱[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)。  
  
 已儲存的資訊包括功能表項目、 停駐狀態和功能表列的位置。  
  
##  <a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId  
 設定的預設功能表[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件會根據資源識別碼。  
  
```  
void SetDefaultMenuResId(UINT uiResId);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiResId`  
 新的預設功能表資源識別碼。  
  
### <a name="remarks"></a>備註  
 [CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)方法會從資源檔來還原預設功能表。  
  
 使用[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)方法來擷取預設功能表不會還原。  
  
##  <a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetForceDownArrows(BOOL bValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `bValue`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setmaximizemode"></a>CMFCMenuBar::SetMaximizeMode  
 當 MDI 改變它的顯示模式，且必須更新功能表列時，架構會呼叫這個方法。  
  
```  
void SetMaximizeMode(
    BOOL bMax,  
    CWnd* pWnd = NULL,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMax`  
 布林值，指定的模式。 如需詳細資訊，請參閱＜備註＞一節。  
  
 [in] `pWnd`  
 MDI 子視窗會變更指標。  
  
 [in] `bRecalcLayout`  
 布林值，指定是否要立即計算功能表列的配置。  
  
### <a name="remarks"></a>備註  
 MDI 子視窗會最大化時，附加至 MDI 主框架視窗的功能表列會顯示 [系統] 功能表和**最小化**，**最大化**和**關閉**按鈕。 如果`bMax`是`TRUE`和`pWnd`不`NULL`、 MDI 子視窗最大化視窗和功能表列必須併入額外的控制項。 否則，在功能表列會傳回其規則的狀態。  
  
##  <a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC  
 設定使用者建立功能表按鈕時，架構會使用執行階段類別資訊。  
  
```  
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenuButtonRTC`  
 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)類別的資訊衍生自[CMFCMenuButton 類別](../../mfc/reference/cmfcmenubutton-class.md)。  
  
### <a name="remarks"></a>備註  
 當使用者將新按鈕新增至功能表列中時，架構會以動態方式建立按鈕。 根據預設，它會建立`CMFCMenuButton`物件。 覆寫這個方法，以變更此架構會建立的按鈕物件的型別。  
  
##  <a name="setmenufont"></a>CMFCMenuBar::SetMenuFont  
 在您的應用程式中設定所有的功能表列的字型。  
  
```  
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpLogFont`  
 指標[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/bb773327)結構，定義設定的字型。  
  
 [in] `bHorz`  
 如果您想要則為 TRUE`lpLogFont`參數，如果想要用於水平字型，要用於垂直字型，也就是 FALSE。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 兩種字型會用於所有`CMFCMenuBar`物件。 水平和垂直的功能表列會使用這些不同的字型。  
  
 字型設定是全域變數，而且會影響所有`CMFCMenuBar`物件。  
  
##  <a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus  
 功能表列是否顯示最近使用的功能表命令的控制項。  
  
```  
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bOn`  
 布林值，控制是否會顯示最近使用的功能表命令。  
  
##  <a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands  
 控制是否功能表會顯示所有可用的命令。  
  
```  
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShowAllCommands`  
 布林值的參數，指定是否快顯功能表會顯示所有的功能表命令。  
  
### <a name="remarks"></a>備註  
 如果功能表未顯示所有的功能表命令時，它會隱藏很少使用的命令。 如需顯示功能表命令的詳細資訊，請參閱[CMFCMenuBar 類別](../../mfc/reference/cmfcmenubar-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)

