---
title: "CMDIChildWndEx 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx::ActivateTopLevelFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AdjustDockingLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnMDITabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnTaskBarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnWindowsList
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPaneLeftOf
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableAutoHidePanes
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableDocking
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDockingManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDocumentName
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameIcon
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameText
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabProxyWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarPreviewWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetToolbarButtonToolTipText
- AFXMDICHILDWNDEX/CMDIChildWndEx::InsertPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::InvalidateIconicBitmaps
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsPointNearDockSite
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsReadOnly
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsRegisteredWithTaskbarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarTabsSupportEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicLivePreviewBitmap
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicThumbnail
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnMoveMiniFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnSetPreviewMode
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailStretch
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnUpdateFrameTitle
- AFXMDICHILDWNDEX/CMDIChildWndEx::PaneFromPoint
- AFXMDICHILDWNDEX/CMDIChildWndEx::RecalcLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::RegisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::RemovePaneFromDockManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabActive
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabOrder
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabProperties
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::ShowPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::UnregisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::UpdateTaskbarTabIcon
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWndEx class
- ActivateFrame method
- PreTranslateMessage method
- GetThisClass method
- CreateObject method
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
caps.latest.revision: 35
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 016de8fdade75376f9f081539c0f160a6502bc37
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmdichildwndex-class"></a>CMDIChildWndEx 類別
`CMDIChildWndEx`類別提供的 Windows 功能多重文件介面 (MDI) 子視窗。 該擴充功能的[CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)。 當 MDI 應用程式使用特定 MFC 類別時，Framework 必須有這個類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CMDIChildWndEx : public CMDIChildWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMDIChildWndEx::ActivateTopLevelFrame](#activatetoplevelframe)|啟用層級的最上層框架時應該從工作列 索引標籤中啟動應用程式架構在內部呼叫。|  
|`CMDIChildWndEx::AddDockSite`|這個方法不會使用或實作。|  
|[CMDIChildWndEx::AddPane](#addpane)|加入窗格。|  
|[CMDIChildWndEx::AddTabbedPane](#addtabbedpane)|加入索引標籤式的窗格。|  
|[CMDIChildWndEx::AdjustDockingLayout](#adjustdockinglayout)|調整停駐配置。|  
|[CMDIChildWndEx::CanShowOnMDITabs](#canshowonmditabs)||  
|[CMDIChildWndEx::CanShowOnTaskBarTabs](#canshowontaskbartabs)|會告知 framework 是否顯示此 MDI 子系，Windows 7 工作列 索引標籤上。|  
|[CMDIChildWndEx::CanShowOnWindowsList](#canshowonwindowslist)|傳回`TRUE`如果 MDI 子視窗名稱可以顯示在[CMFCWindowsManagerDialog 類別](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)對話方塊。 否則傳回 `FALSE`。|  
|`CMDIChildWndEx::CreateObject`|若要建立此類別類型的動態執行個體架構呼叫。|  
|[CMDIChildWndEx::DockPane](#dockpane)|停駐窗格。|  
|[CMDIChildWndEx::DockPaneLeftOf](#dockpaneleftof)|將窗格停駐在另一個窗格的左邊。|  
|[CMDIChildWndEx::EnableAutoHidePanes](#enableautohidepanes)|啟用自動隱藏窗格模式時指定的側邊的視窗停駐。|  
|[CMDIChildWndEx::EnableDocking](#enabledocking)|啟用的子視窗停駐到主框架。|  
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](#enabletaskbarthumbnailcliprect)|啟用或停用自動選擇視窗的工作區，以顯示該視窗的工作列中的縮圖的一部分。|  
|[CMDIChildWndEx::GetDockingManager](#getdockingmanager)||  
|[CMDIChildWndEx::GetDocumentName](#getdocumentname)|傳回在 MDI 子視窗中顯示的文件的名稱。|  
|[CMDIChildWndEx::GetFrameIcon](#getframeicon)|若要擷取的 MDI 子視窗圖示架構呼叫。|  
|[CMDIChildWndEx::GetFrameText](#getframetext)|若要擷取的 MDI 子視窗的文字架構呼叫。|  
|[CMDIChildWndEx::GetPane](#getpane)|尋找窗格中所指定的控制項 id。|  
|[CMDIChildWndEx::GetRelatedTabGroup](#getrelatedtabgroup)||  
|[CMDIChildWndEx::GetTabbedPane](#gettabbedpane)|傳回已轉換為索引標籤式文件內嵌停駐窗格的指標。|  
|[CMDIChildWndEx::GetTabProxyWnd](#gettabproxywnd)|傳回索引標籤上的 proxy 視窗，實際上向 Windows 7 工作列 索引標籤。|  
|[CMDIChildWndEx::GetTaskbarPreviewWnd](#gettaskbarpreviewwnd)|若要取得 Windows 7 工作列 索引標籤的縮圖上顯示的子視窗 （通常是檢視或分隔視窗） 需要時，由架構呼叫。|  
|[CMDIChildWndEx::GetTaskbarThumbnailClipRect](#gettaskbarthumbnailcliprect)|需要選取視窗的工作區，以顯示該視窗的工作列中的縮圖的一部分時，由架構呼叫。|  
|`CMDIChildWndEx::GetThisClass`|若要取得的指標，架構呼叫[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMDIChildWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|若要擷取的工具列按鈕的工具提示架構呼叫。|  
|[CMDIChildWndEx::InsertPane](#insertpane)|連接管理員會向指定的窗格。|  
|[CMDIChildWndEx::InvalidateIconicBitmaps](#invalidateiconicbitmaps)|失效的 MDI 子系圖示的點陣圖表示法。|  
|[CMDIChildWndEx::IsPointNearDockSite](#ispointneardocksite)|判斷指定的點是否停駐位置附近。|  
|[CMDIChildWndEx::IsReadOnly](#isreadonly)|傳回`TRUE`子視窗中顯示的文件是唯讀。 否則傳回 `FALSE`。|  
|[CMDIChildWndEx::IsRegisteredWithTaskbarTabs](#isregisteredwithtaskbartabs)|如果 Windows 7 工作列 索引標籤已成功註冊的 MDI 子系，則傳回 TRUE。|  
|[CMDIChildWndEx::IsTabbedPane](#istabbedpane)|傳回`TRUE`如果 MDI 子視窗包含的停駐窗格。 否則傳回 `FALSE`。|  
|[CMDIChildWndEx::IsTaskbarTabsSupportEnabled](#istaskbartabssupportenabled)|會告訴 Windows 7 工作列 索引標籤上是否可以顯示 MDI 子視窗。|  
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](#istaskbarthumbnailcliprectenabled)|指示是否啟用或停用自動選擇視窗的工作區，以顯示該視窗的工作列中的縮圖的一部分。|  
|[CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags](#m_dwdefaulttaskbartabpropertyflags)|要登錄旗標的組合，由架構傳遞至 SetTaskbarTabProperties 方法中，當 索引標籤 （MDI 子系） 與 Windows 7 工作列 索引標籤。 預設的組合是 STPF_USEAPPTHUMBNAILWHENACTIVE |STPF_USEAPPPEEKWHENACTIVE。|  
|[CMDIChildWndEx::OnGetIconicLivePreviewBitmap](#ongeticoniclivepreviewbitmap)|需要取得即時預覽的 MDI 子系的點陣圖時，由架構呼叫。|  
|[CMDIChildWndEx::OnGetIconicThumbnail](#ongeticonicthumbnail)|需要取得圖示的 MDI 子視窗的縮圖的點陣圖時，由架構呼叫。|  
|[CMDIChildWndEx::OnMoveMiniFrame](#onmoveminiframe)|若要移動的迷你框架視窗，架構呼叫。|  
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](#onpresstaskbarthmbnailclosebutton)|當使用者按下工作列 索引標籤的縮圖上的 關閉 按鈕時，由框架呼叫...|  
|[CMDIChildWndEx::OnSetPreviewMode](#onsetpreviewmode)|進入或結束預覽列印模式架構呼叫。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailActivate](#ontaskbartabthumbnailactivate)|當工作列 索引標籤縮圖應處理 WM_ACTIVATE 訊息時，由架構呼叫。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate](#ontaskbartabthumbnailmouseactivate)|當工作列 索引標籤縮圖應處理 WM_MOUSEACTIVATE 訊息時，由架構呼叫。|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](#ontaskbartabthumbnailstretch)|需要自動縮放的 MDI 子系的 Windows 7 工作列 索引標籤縮圖預覽的點陣圖時，由架構呼叫。|  
|[CMDIChildWndEx::OnUpdateFrameTitle](#onupdateframetitle)|若要更新框架標題架構呼叫。 (覆寫 `CMDIChildWnd::OnUpdateFrameTitle`。)|  
|[CMDIChildWndEx::PaneFromPoint](#panefrompoint)|傳回包含指定的點的窗格。|  
|`CMDIChildWndEx::PreTranslateMessage`|類別所使用的[CWinApp](../../mfc/reference/cwinapp-class.md)轉譯視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMDIChildWndEx::RecalcLayout](#recalclayout)|重新計算視窗配置。|  
|[CMDIChildWndEx::RegisterTaskbarTab](#registertaskbartab)|向 Windows 7 工作列 索引標籤中的 MDI 子系。|  
|[CMDIChildWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|移除連接管理員 窗格。|  
|[CMDIChildWndEx::SetRelatedTabGroup](#setrelatedtabgroup)||  
|[CMDIChildWndEx::SetTaskbarTabActive](#settaskbartabactive)|啟動對應的 Windows 7 工作列 索引標籤。|  
|[CMDIChildWndEx::SetTaskbarTabOrder](#settaskbartaborder)|插入之前 Windows 7 工作列 索引標籤上指定之視窗的 MDI 子系。|  
|[CMDIChildWndEx::SetTaskbarTabProperties](#settaskbartabproperties)|設定 [Windows 7 工作列] 索引標籤的屬性。|  
|[CMDIChildWndEx::SetTaskbarThumbnailClipRect](#settaskbarthumbnailcliprect)|若要設定裁剪矩形來選取視窗的工作區，以顯示該視窗的縮圖，在工作列中的部分架構在內部呼叫。|  
|[CMDIChildWndEx::ShowPane](#showpane)||  
|[CMDIChildWndEx::UnregisterTaskbarTab](#unregistertaskbartab)|移除 Windows 7 工作列 索引標籤中的 MDI 子系。|  
|[CMDIChildWndEx::UpdateTaskbarTabIcon](#updatetaskbartabicon)|更新 Windows 7 工作列 索引標籤的圖示。|  
  
## <a name="remarks"></a>備註  
 MDI 應用程式中利用停駐的擴充功能，衍生您的應用程式的 MDI 子視窗類別`CMDIChildWndEx`而不是[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)。  
  
## <a name="example"></a>範例  
 下列範例是衍生自`CMDIChildWndEx`。 此程式碼片段來自[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&3;](../../mfc/codesnippet/cpp/cmdichildwndex-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)  
  
 [CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxMDIChildWndEx.h  
  
##  <a name="addpane"></a>CMDIChildWndEx::AddPane  
 加入窗格。  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 窗格的指標。  
  
 [in] `bTail`  
 `TRUE`若要將停駐管理員時，窗格的清單結尾新增窗格否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果連接管理員時，已成功註冊窗格，否則， `FALSE`。  
  
##  <a name="addtabbedpane"></a>CMDIChildWndEx::AddTabbedPane  
 加入索引標籤式的窗格。  
  
```  
void AddTabbedPane(CDockablePane* pControlBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 窗格的指標。  
  
##  <a name="adjustdockinglayout"></a>CMDIChildWndEx::AdjustDockingLayout  
 調整停駐配置。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `hdwp`  
 延後的視窗位置結構的控制代碼。  
  
##  <a name="canshowonmditabs"></a>CMDIChildWndEx::CanShowOnMDITabs  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanShowOnMDITabs();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="canshowonwindowslist"></a>CMDIChildWndEx::CanShowOnWindowsList  
 指定是否可以在顯示 MDI 子視窗名稱[CMFCWindowsManagerDialog 類別](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)對話方塊。  
  
```  
virtual BOOL CanShowOnWindowsList();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果視窗可以顯示在**Windows**  對話方塊中，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別中的，並傳回`FALSE`不會顯示在視窗中，如果**Windows**對話方塊。 此函式會從呼叫`CMFCWindowsManagerDialog`。  
  
##  <a name="dockpane"></a>CMDIChildWndEx::DockPane  
 停駐窗格。  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 窗格的指標。  
  
 [in] `nDockBarID`  
 窗格的識別碼。  
  
 [in] `lpRect`  
 矩形的指標。  
  
### <a name="remarks"></a>備註  
 `lpRect`不使用參數。  
  
##  <a name="dockpaneleftof"></a>CMDIChildWndEx::DockPaneLeftOf  
 將窗格停駐在另一個窗格的左邊。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>參數  
 `pBar`  
 指標是可停駐窗格。  
  
 `pLeftOf`  
 指標，此窗格，可做為參考點。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功，`FALSE`失敗。  
  
### <a name="remarks"></a>備註  
 這個方法會採用所指定的窗格`pBar`並固定在左側窗格中所指定的`pLeftOf`。  
  
 當您想要停駐在預先定義的順序中的幾個窗格，請呼叫這個方法。  
  
##  <a name="enableautohidepanes"></a>CMDIChildWndEx::EnableAutoHidePanes  
 啟用自動隱藏窗格模式時指定的側邊的視窗停駐。  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
 指定已啟用的主框架視窗的側邊。 使用一或多個下列旗標。  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功。否則`FALSE`。  
  
##  <a name="enabledocking"></a>CMDIChildWndEx::EnableDocking  
 啟用的子視窗停駐到主框架。  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
 指定要啟用的停駐對齊。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來啟用停駐於主框架的對齊方式。 您可以傳遞 CBRS_ALIGN_ 旗標的組合 (如需詳細資訊，請參閱[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking))。  
  
##  <a name="getdockingmanager"></a>CMDIChildWndEx::GetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getdocumentname"></a>CMDIChildWndEx::GetDocumentName  
 傳回在 MDI 子視窗中顯示的文件的名稱。  
  
```  
virtual LPCTSTR GetDocumentName(CObject** pObj);
```  
  
### <a name="return-value"></a>傳回值  
 包含文件名稱的字串指標。  
  
### <a name="remarks"></a>備註  
 文件是 MDI 子視窗會顯示。 一般而言，視窗會顯示從載入或儲存到檔案中的資料。 因此，文件的名稱是檔案的名稱。 預設實作`GetDocumentName`傳回字串，取自`CDocument::GetPathName`。  
  
 如果此視窗會顯示不從檔案載入的文件，覆寫這個方法在衍生類別中的，並傳回唯一的文件識別碼。  
  
 `GetDocumentName`是由架構呼叫，它會將儲存所有開啟的文件的狀態時。 傳回的字串會寫入登錄。  
  
 文件名稱時，架構稍後還原狀態，會從登錄讀取，傳遞至[CMDIFrameWndEx::CreateDocumentWindow](../../mfc/reference/cmdiframewndex-class.md#createdocumentwindow)。 覆寫這個方法在[cmdiframewndex 是](../../mfc/reference/cmdiframewndex-class.md)-衍生的類別，建立或開啟具有此名稱的文件並在具有此名稱的檔案中讀取。 如果檔案不以基礎文件，根據建立文件本身的文件識別碼。 只有當您想要儲存和還原的文件，您應該執行上述動作。  
  
### <a name="example"></a>範例  
 下列範例示範 `GetDocumentName` 方法的用法。 此程式碼片段來自[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&17;](../../mfc/codesnippet/cpp/cmdichildwndex-class_2.cpp)]  
  
##  <a name="getframeicon"></a>CMDIChildWndEx::GetFrameIcon  
 若要擷取之 MDI 子視窗圖示架構呼叫。  
  
```  
virtual HICON GetFrameIcon() const;  
```  
  
### <a name="return-value"></a>傳回值  
 視窗圖示的控制代碼。  
  
### <a name="remarks"></a>備註  
 判斷哪個圖示来顯示在包含 MDI 子框架視窗的 MDI 索引標籤上的架構會呼叫這個方法。  
  
 依預設這個方法會傳回視窗圖示。 覆寫`GetFrameIcon`中`CMDIChildWndEx`-衍生類別，即可自訂這個行為。  
  
##  <a name="getframetext"></a>CMDIChildWndEx::GetFrameText  
 若要擷取的 MDI 子視窗的文字架構呼叫。  
  
```  
virtual CString GetFrameText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含框架視窗的文字。  
  
### <a name="remarks"></a>備註  
 決定所要包含 MDI 子框架視窗的 MDI 索引標籤上顯示文字的架構會呼叫這個方法。  
  
 依預設這個方法會傳回視窗文字。 覆寫`GetFrameText`中`CMDIChildWndEx`-衍生類別，即可自訂這個行為。  
  
##  <a name="getpane"></a>CMDIChildWndEx::GetPane  
 尋找窗格中所指定的控制項 id。  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 若要尋找窗格的控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 窗格的指標如果找到，否則`NULL`。  
  
##  <a name="getrelatedtabgroup"></a>CMDIChildWndEx::GetRelatedTabGroup  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCTabCtrl* GetRelatedTabGroup();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettabbedpane"></a>CMDIChildWndEx::GetTabbedPane  
 傳回的指標是一群 MDI 一部分的停駐窗格的索引標籤式文件。  
  
```  
CDockablePane* GetTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標停駐窗格屬於群組中的 MDI 索引標籤式文件。  
  
##  <a name="gettoolbarbuttontooltiptext"></a>CMDIChildWndEx::GetToolbarButtonToolTipText  
 若要擷取的工具列按鈕的工具提示架構呼叫。  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton*, 
    CString&);
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已顯示工具提示。 預設實作會傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果您想要顯示的工具列按鈕的自訂工具提示，請覆寫這個方法。  
  
##  <a name="insertpane"></a>CMDIChildWndEx::InsertPane  
 連接管理員會向指定的窗格。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 要插入窗格指標。  
  
 [in] `pTarget`  
 指標，相鄰的窗格。  
  
 [in] `bAfter`  
 如果`TRUE`，`pControlBar`後面插入`pTarget`。 如果`FALSE`，`pControlBar`之前，插入`pTarget`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功，`FALSE`否則。  
  
##  <a name="ispointneardocksite"></a>CMDIChildWndEx::IsPointNearDockSite  
 判斷指定的點是否停駐位置附近。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指定的點。  
  
 [in] `dwBarAlignment`  
 指定的點是附近的邊緣。 可能的值為`CBRS_ALIGN_LEFT`， `CBRS_ALIGN_RIGHT`， `CBRS_ALIGN_TOP`，並`CBRS_ALIGN_BOTTOM`  
  
 [in] `bOuterEdge`  
 `TRUE`如果點很近外框的停駐位置。`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果點附近的停駐位置。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 重點是停駐位置附近時中設定連接管理員中的敏感度。 預設區分大小寫為 15 像素。  
  
##  <a name="isreadonly"></a>CMDIChildWndEx::IsReadOnly  
 指定顯示在子視窗的文件是否為唯讀。  
  
```  
virtual BOOL IsReadOnly();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果文件是唯讀的。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 此函式用來防止唯讀文件儲存。  
  
### <a name="example"></a>範例  
 下列範例示範如何覆寫`IsReadOnly`方法。 此程式碼片段來自[VisualStudioDemo 範例︰ Visual Studio 應用程式的 MFC](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&2;](../../mfc/codesnippet/cpp/cmdichildwndex-class_3.cpp)]  
  
##  <a name="istabbedpane"></a>CMDIChildWndEx::IsTabbedPane  
 指定 MDI 子視窗是否包含停駐窗格。  
  
```  
BOOL IsTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 MDI 子視窗會包含已轉換為索引標籤式文件的停駐窗格否則`FALSE`。  
  
##  <a name="onmoveminiframe"></a>CMDIChildWndEx::OnMoveMiniFrame  
 若要移動的迷你框架視窗，架構呼叫。  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFrame`  
 迷你框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功，否則`FALSE`。  
  
##  <a name="onsetpreviewmode"></a>CMDIChildWndEx::OnSetPreviewMode  
 進入或結束預覽列印模式架構呼叫。  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>參數  
 [in] `bPreview`  
 如果`TRUE`，進入 預覽列印模式。 如果`FALSE`，結束預覽列印模式。  
  
 [in] `pState`  
 預覽列印狀態結構的指標。  
  
##  <a name="onupdateframetitle"></a>CMDIChildWndEx::OnUpdateFrameTitle  
 若要更新框架標題架構呼叫。  
  
```  
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAddToTitle`  
 如果`TRUE`，標題中加入文件名稱。  
  
##  <a name="panefrompoint"></a>CMDIChildWndEx::PaneFromPoint  
 傳回包含指定的點的窗格。  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar,  
    CRuntimeClass* pRTCBarType) const;  
  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 若要檢查的螢幕座標中指定點。  
  
 [in] `nSensitivity`  
 搜尋區域增加此數量。 如果指定的點落在增加區域窗格可滿足搜尋條件。  
  
 [in] `bExactBar`  
 `TRUE`若要忽略`nSensitivity`參數，否則`FALSE`。  
  
 [in] `pRTCBarType`  
 如果不是`NULL`，該方法會搜尋窗格指定的型別。  
  
 [in] `dwAlignment`  
 如果指定點上找到一個窗格，則此參數會包含窗格是最接近指定點的側邊。 如需詳細資訊，請參閱＜備註＞一節。  
  
### <a name="return-value"></a>傳回值  
 指標`CBasePane`-衍生物件，其中包含指定的點或`NULL`如果找不到任何窗格。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來判斷窗格是否包含指定的點，根據指定的條件，例如執行階段類別和可視性。  
  
 當函式會傳回，而且找不到一個窗格，`dwAlignment`包含指定點的對齊方式。 例如，如果點為最接近工作窗格中，頂端`dwAlignment`設為`CBRS_ALIGN_TOP`。  
  
##  <a name="recalclayout"></a>CMDIChildWndEx::RecalcLayout  
 重新計算視窗配置。  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bNotify`  
 如果`TRUE`，使用中視窗的就地項目接收配置變更的通知。  
  
##  <a name="removepanefromdockmanager"></a>CMDIChildWndEx::RemovePaneFromDockManager  
 移除連接管理員 窗格。  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>參數  
 [in] `pControlBar`  
 若要移除窗格指標。  
  
 [in] `bDestroy`  
 如果`TRUE`，終結已移除的窗格。  
  
 [in] `bAdjustLayout`  
 如果`TRUE`，立即調整停駐配置。  
  
 [in] `bAutoHide`  
 如果`TRUE`，停駐配置相關的自動隱藏列清單。 如果`FALSE`，停駐配置與一般窗格的清單。  
  
 [in] `pBarReplacement`  
 指標，會取代 [移除] 窗格的窗格。  
  
##  <a name="setrelatedtabgroup"></a>CMDIChildWndEx::SetRelatedTabGroup  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetRelatedTabGroup(CMFCTabCtrl* p);
```  
  
### <a name="parameters"></a>參數  
 [in] `p`  
  
### <a name="remarks"></a>備註  
  
##  <a name="showpane"></a>CMDIChildWndEx::ShowPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 [in] `bShow`  
 [in] `bDelay`  
 [in] `bActivate`  
  
### <a name="remarks"></a>備註  
  
##  <a name="updatetaskbartabicon"></a>CMDIChildWndEx::UpdateTaskbarTabIcon  
 更新 Windows 7 工作列 索引標籤的圖示。  
  
```  
virtual void UpdateTaskbarTabIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 `hIcon`  
 在 Windows 7 工作列 索引標籤上顯示圖示的控制代碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="unregistertaskbartab"></a>CMDIChildWndEx::UnregisterTaskbarTab  
 移除 Windows 7 工作列 索引標籤中的 MDI 子視窗。  
  
```  
void UnregisterTaskbarTab(BOOL bCheckRegisteredMDIChildCount = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bCheckRegisteredMDIChildCount`  
 指定此函式是否須檢查向 MDI 索引標籤的 MDI 子系數目。 如果這個數字為 0，此函式會移除裁剪方框從應用程式的工作列縮圖。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settaskbarthumbnailcliprect"></a>CMDIChildWndEx::SetTaskbarThumbnailClipRect  
 若要設定裁剪方框選取視窗的工作區，以顯示該視窗的縮圖，在工作列中的部分架構呼叫。  
  
```  
virtual BOOL SetTaskbarThumbnailClipRect(CRect rect);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 指定新的裁剪方框。 如果矩形是空白或 null，則會移除裁剪。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settaskbartabproperties"></a>CMDIChildWndEx::SetTaskbarTabProperties  
 設定 [Windows 7 工作列] 索引標籤的屬性。  
  
```  
void SetTaskbarTabProperties(DWORD dwFlags);
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 STPFLAG 值的組合。 如需詳細資訊，請參閱[itaskbarlist4:: Settabproperties](http://msdn.microsoft.com/library/dd562049\(vs.85\).aspx)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settaskbartaborder"></a>CMDIChildWndEx::SetTaskbarTabOrder  
 插入之前 Windows 7 工作列 索引標籤上指定的視窗的 MDI 子系。  
  
```  
void SetTaskbarTabOrder(CMDIChildWndEx* pWndBefore = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pWndBefore`  
 MDI 子視窗的縮圖左方插入指標。 這個視窗必須已登錄到`RegisterTaskbarTab`。 如果此值為`NULL`，新的縮圖會加入至清單的結尾。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settaskbartabactive"></a>CMDIChildWndEx::SetTaskbarTabActive  
 啟動對應的 Windows 7 工作列 索引標籤。  
  
```  
void SetTaskbarTabActive();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="registertaskbartab"></a>CMDIChildWndEx::RegisterTaskbarTab  
 向 Windows 7 工作列 索引標籤中的 MDI 子視窗。  
  
```  
virtual void RegisterTaskbarTab(CMDIChildWndEx* pWndBefore = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pWndBefore`  
 MDI 子視窗的縮圖左方插入指標。 這個視窗必須已登錄到`RegisterTaskbarTab`。 如果此值為`NULL`，新的縮圖會加入至清單的結尾。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ontaskbartabthumbnailstretch"></a>CMDIChildWndEx::OnTaskbarTabThumbnailStretch  
 需要自動縮放的 MDI 子系的 Windows 7 工作列 索引標籤縮圖預覽的點陣圖時，由架構呼叫。  
  
```  
virtual BOOL OnTaskbarTabThumbnailStretch(
    HBITMAP hBmpDst,  
    const CRect& rectDst,  
    HBITMAP hBmpSrc,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>參數  
 `hBmpDst`  
 目的點陣圖控制代碼。  
  
 `rectDst`  
 指定目的地矩形。  
  
 `hBmpSrc`  
 來源點陣圖控制代碼。  
  
 `rectSrc`  
 指定來源矩形。  
  
### <a name="remarks"></a>備註  
 Requirementher 或他他他他他他他**:** afxmdichildwndex.h  
  
##  <a name="ontaskbartabthumbnailmouseactivate"></a>CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate  
 工作列 索引標籤縮圖應處理 WM_MOUSEACTIVATE 訊息時，由架構呼叫。  
  
```  
virtual int OnTaskbarTabThumbnailMouseActivate(
    CWnd* pDesktopWnd,  
    UINT nHitTest,  
    UINT message);
```  
  
### <a name="parameters"></a>參數  
 `pDesktopWnd`  
 指定正在啟動視窗的最上層的父視窗的指標。 指標可能是暫時性的不會儲存。  
  
 `nHitTest`  
 指定的點擊測試區域代碼。 點擊的測試是測試，決定游標的位置。  
  
 `message`  
 指定滑鼠訊息數目。  
  
### <a name="remarks"></a>備註  
 預設實作會啟動相關的 MDI 子框架。  
  
##  <a name="ontaskbartabthumbnailactivate"></a>CMDIChildWndEx::OnTaskbarTabThumbnailActivate  
 工作列 索引標籤縮圖應處理 WM_ACTIVATE 訊息時，由架構呼叫。  
  
```  
virtual void OnTaskbarTabThumbnailActivate(
    UINT nState,  
    CWnd* pWndOther,  
    BOOL bMinimized);
```  
  
### <a name="parameters"></a>參數  
 `nState`  
 指定是否`CWnd`啟動或停用。  
  
 `pWndOther`  
 指標`CWnd`正在啟動或停用。 指標可以是`NULL`，而且可能是暫時性。  
  
 `bMinimized`  
 指定的最小化的狀態`CWnd`正在啟動或停用。 值為`TRUE`指出視窗最小化。  
  
### <a name="remarks"></a>備註  
 預設實作會啟動相關的 MDI 子框架。  
  
##  <a name="onpresstaskbarthmbnailclosebutton"></a>CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton  
 當使用者按下 [關閉] 按鈕，在 [工作列] 索引標籤縮圖上時，由架構呼叫。  
  
```  
virtual void OnPressTaskbarThmbnailCloseButton();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="ongeticonicthumbnail"></a>CMDIChildWndEx::OnGetIconicThumbnail  
 需要取得圖示的縮圖的 MDI 子系的點陣圖時，由架構呼叫。  
  
```  
virtual HBITMAP OnGetIconicThumbnail(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 指定所需的點陣圖的寬度。  
  
 `nHeight`  
 指定所需的點陣圖的高度。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ongeticoniclivepreviewbitmap"></a>CMDIChildWndEx::OnGetIconicLivePreviewBitmap  
 需要取得的 MDI 子視窗的即時預覽的點陣圖時，由架構呼叫。  
  
```  
virtual HBITMAP OnGetIconicLivePreviewBitmap(
    BOOL bIsMDIChildActive,  
    CPoint& ptLocation);
```  
  
### <a name="parameters"></a>參數  
 `bIsMDIChildActive`  
 這個參數是`TRUE`點陣圖的 MDI 子系的要求時，如果這目前作用中，主視窗沒有最小化。 預設在此情況下處理會在主視窗的快照集。  
  
 `ptLocation`  
 指定點陣圖的位置 （最上層） 主視窗工作區座標。 應由被呼叫端提供此點。  
  
### <a name="return-value"></a>傳回值  
 如果處理，傳回的控制代碼有效 32bpp 點陣圖，否則`NULL`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別中的，並傳回有效的 32bpp 點陣圖的 MDI 子視窗的即時預覽。 MDI 子視窗會顯示 Windows 7 工作列 索引標籤上時，才會呼叫這個方法。 如果您傳回`NULL`，MFC 呼叫的預設處理常式，並取得使用點陣圖`PrintClient`或`PrintWindow`。  
  
##  <a name="m_dwdefaulttaskbartabpropertyflags"></a>CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags  
 旗標的組合，這會由架構傳遞`SetTaskbarTabProperties`方法中，當 索引標籤 （MDI 子系） 已向 Windows 7 工作列 索引標籤。  
  
```  
AFX_IMPORT_DATA static DWORD m_dwDefaultTaskbarTabPropertyFlags;  
```  
  
### <a name="remarks"></a>備註  
 預設的組合是 STPF_USEAPPTHUMBNAILWHENACTIVE |STPF_USEAPPPEEKWHENACTIVE。  
  
##  <a name="istaskbarthumbnailcliprectenabled"></a>CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled  
 指示是否啟用或停用自動選擇視窗的工作區，以顯示該視窗的工作列中的縮圖的一部分。  
  
```  
BOOL IsTaskbarThumbnailClipRectEnabled() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`自動選擇的顯示視窗的工作區的部分是否已啟用，否則為`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="istaskbartabssupportenabled"></a>CMDIChildWndEx::IsTaskbarTabsSupportEnabled  
 會告訴 Windows 7 工作列 索引標籤上是否可以顯示 MDI 子視窗。  
  
```  
BOOL IsTaskbarTabsSupportEnabled();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 MDI 子系可以出現在 Windows 7 工作列 索引標籤。`FALSE`如果 MDI 子視窗可以顯示 Windows 7 工作列 索引標籤上。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isregisteredwithtaskbartabs"></a>CMDIChildWndEx::IsRegisteredWithTaskbarTabs  
 傳回`TRUE`如果 MDI 子系已成功註冊 Windows 7 工作列 索引標籤。  
  
```  
BOOL IsRegisteredWithTaskbarTabs();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 MDI 子系向 Windows 7 工作列 索引標籤。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="invalidateiconicbitmaps"></a>CMDIChildWndEx::InvalidateIconicBitmaps  
 失效的 MDI 子系的圖示的點陣圖表示法。  
  
```  
BOOL InvalidateIconicBitmaps();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`FALSE`如果 Windows 7 工作列支援已停用或未註冊的 MDI 子系 Windows 7 工作列 索引標籤; 否則會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 實況內容或 MDI 子系的大小已變更時，應該呼叫。  
  
##  <a name="gettaskbarthumbnailcliprect"></a>CMDIChildWndEx::GetTaskbarThumbnailClipRect  
 需要選取視窗的工作區，以顯示該視窗的工作列中的縮圖的一部分時，由架構呼叫。  
  
```  
virtual CRect GetTaskbarThumbnailClipRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在 windows 座標的矩形。 此矩形會對應到工作區的最上層框架。 矩形應該是空的才能清除裁剪方框。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettaskbarpreviewwnd"></a>CMDIChildWndEx::GetTaskbarPreviewWnd  
 若要取得 Windows 7 工作列 索引標籤縮圖上顯示的子視窗 （通常是檢視或分隔視窗） 需要時，由架構呼叫。  
  
```  
virtual CWnd* GetTaskbarPreviewWnd();
```  
  
### <a name="return-value"></a>傳回值  
 應該傳回的有效指標`CWnd`這個 MDI 子系的相關的物件，其預覽也應該顯示在 Windows 7 工作列 索引標籤。 預設實作會傳回這個 AFX_IDW_PANE_FIRST 控制項 id 的 MDI 子系的子視窗 (通常是`CView`-衍生的類別)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettabproxywnd"></a>CMDIChildWndEx::GetTabProxyWnd  
 傳回向 Windows 7 工作列 索引標籤的 proxy 索引標籤 視窗。  
  
```  
CMDITabProxyWnd* GetTabProxyWnd();
```  
  
### <a name="return-value"></a>傳回值  
 指標`CMDITabProxyWnd`物件，它會向 Windows 7 工作列 索引標籤。  
  
### <a name="remarks"></a>備註  
  
##  <a name="enabletaskbarthumbnailcliprect"></a>CMDIChildWndEx::EnableTaskbarThumbnailClipRect  
 啟用或停用自動選擇視窗的工作區，以顯示該視窗的工作列中的縮圖的一部分。  
  
```  
void EnableTaskbarThumbnailClipRect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bEnable`  
 指定是否要啟用 ( `TRUE`)，或停用 ( `FALSE`) 自動選擇来顯示的視窗的用戶端區域的一部分。  
  
### <a name="remarks"></a>備註  
  
##  <a name="canshowontaskbartabs"></a>CMDIChildWndEx::CanShowOnTaskBarTabs  
 會告知 framework 是否顯示此 MDI 子系，Windows 7 工作列 索引標籤上。  
  
```  
virtual BOOL CanShowOnTaskBarTabs();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以在 Windows 7 工作列縮圖上顯示 MDI 子視窗的內容。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別中的，並傳回`FALSE`停用這個 MDI 子系，Windows 7 工作列 索引標籤上的外觀。  
  
##  <a name="activatetoplevelframe"></a>CMDIChildWndEx::ActivateTopLevelFrame  
 若要從工作列 索引標籤啟動應用程式時，啟用最上層框架架構呼叫。  
  
```  
virtual void ActivateTopLevelFrame();
```  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMDIChildWnd 類別](../../mfc/reference/cmdichildwnd-class.md)   
 [CMFCWindowsManagerDialog 類別](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)   
 [Cmdiframewndex 是類別](../../mfc/reference/cmdiframewndex-class.md)

