---
title: "CMFCToolBarButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarButton class"
ms.assetid: 8a6ecffb-86b0-4f5c-8211-a9146b463efd
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 36
---
# CMFCToolBarButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供按鈕功能讓工具列。  
  
## 語法  
  
```  
class CMFCToolBarButton : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarButton::CMFCToolBarButton](../Topic/CMFCToolBarButton::CMFCToolBarButton.md)|建構和 `CMFCToolBarButton` 初始化物件。|  
|`CMFCToolBarButton::~CMFCToolBarButton`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarButton::CanBeDropped](../Topic/CMFCToolBarButton::CanBeDropped.md)|指定使用者是否可以放置在工具列按鈕或功能表在自訂中。|  
|[CMFCToolBarButton::CanBeStored](../Topic/CMFCToolBarButton::CanBeStored.md)|指定是否可儲存按鈕。|  
|[CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md)|指定使用者是否可以在自訂中自動縮放的按鈕。|  
|[CMFCToolBarButton::CompareWith](../Topic/CMFCToolBarButton::CompareWith.md)|這個執行個體與提供的物件相比較。 `CMFCToolBarButton`|  
|[CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)|複製到另一個工具列按鈕的屬性設定為目前的按鈕。|  
|[CMFCToolBarButton::CreateFromOleData](../Topic/CMFCToolBarButton::CreateFromOleData.md)|若要從提供的 `COleDataObject` 物件的 `CMFCToolBarButton` 物件。|  
|`CMFCToolBarButton::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCToolBarButton::EnableWindow](../Topic/CMFCToolBarButton::EnableWindow.md)|啟用或停用滑鼠和鍵盤輸入。|  
|[CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md)|複製的工具列按鈕上的文字加入至功能表。|  
|[CMFCToolBarButton::GetClipboardFormat](../Topic/CMFCToolBarButton::GetClipboardFormat.md)|擷取應用程式的全域剪貼簿格式。|  
|[CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md)|擷取與工具列按鈕的視窗控制代碼。|  
|[CMFCToolBarButton::GetImage](../Topic/CMFCToolBarButton::GetImage.md)|擷取按鈕的影像索引。|  
|[CMFCToolBarButton::GetInvalidateRect](../Topic/CMFCToolBarButton::GetInvalidateRect.md)|擷取按鈕的工作區的本機必須重繪。|  
|[CMFCToolBarButton::GetParentWnd](../Topic/CMFCToolBarButton::GetParentWnd.md)|擷取按鈕的父視窗。|  
|[CMFCToolBarButton::GetProtectedCommands](../Topic/CMFCToolBarButton::GetProtectedCommands.md)|擷取使用者無法自訂命令的清單。|  
|[CMFCToolBarButton::GetTextSize](../Topic/CMFCToolBarButton::GetTextSize.md)|擷取按鈕文字的大小。|  
|[CMFCToolBarButton::HasFocus](../Topic/CMFCToolBarButton::HasFocus.md)|判斷按鈕目前是否具有輸入焦點。|  
|[CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)|確定按鈕的框線是否顯示，當使用者選取按鈕。|  
|[CMFCToolBarButton::IsDrawImage](../Topic/CMFCToolBarButton::IsDrawImage.md)|判斷影像是否顯示在按鈕上。|  
|[CMFCToolBarButton::IsDrawText](../Topic/CMFCToolBarButton::IsDrawText.md)|判斷文字標籤是顯示在按鈕上。|  
|[CMFCToolBarButton::IsDroppedDown](../Topic/CMFCToolBarButton::IsDroppedDown.md)|判斷  按鈕是否顯示子功能表。|  
|[CMFCToolBarButton::IsEditable](../Topic/CMFCToolBarButton::IsEditable.md)|判斷按鈕是否可以自訂。|  
|[CMFCToolBarButton::IsExtraSize](../Topic/CMFCToolBarButton::IsExtraSize.md)|判斷按鈕是否可以顯示具有擴充的框線。|  
|[CMFCToolBarButton::IsFirstInGroup](../Topic/CMFCToolBarButton::IsFirstInGroup.md)|判斷  按鈕是否在第一個位置在其按鈕群組中。|  
|[CMFCToolBarButton::IsHidden](../Topic/CMFCToolBarButton::IsHidden.md)|判斷  按鈕是否隱藏。|  
|[CMFCToolBarButton::IsHorizontal](../Topic/CMFCToolBarButton::IsHorizontal.md)|判斷  按鈕是否位於一個層級的工具列。|  
|[CMFCToolBarButton::IsLastInGroup](../Topic/CMFCToolBarButton::IsLastInGroup.md)|指定按鈕是否在最後一個位置在其按鈕群組中。|  
|[CMFCToolBarButton::IsLocked](../Topic/CMFCToolBarButton::IsLocked.md)|判斷  按鈕是否已鎖定 \(不可自訂的工具列\)。|  
|[CMFCToolBarButton::IsOwnerOf](../Topic/CMFCToolBarButton::IsOwnerOf.md)|判斷  按鈕是否為所提供的視窗控制代碼的擁有人。|  
|[CMFCToolBarButton::IsVisible](../Topic/CMFCToolBarButton::IsVisible.md)|決定工具列按鈕是否為可見。|  
|[CMFCToolBarButton::IsWindowVisible](../Topic/CMFCToolBarButton::IsWindowVisible.md)|決定按鈕的基礎視窗控制代碼是否為可見。|  
|[CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)|指定按鈕是否處理 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 訊息。|  
|[CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md)|呼叫框架，該按鈕會加入 \[**自訂**\] 對話方塊。|  
|[CMFCToolBarButton::OnBeforeDrag](../Topic/CMFCToolBarButton::OnBeforeDrag.md)|指定按鈕是否可以拖曳。|  
|[CMFCToolBarButton::OnBeforeDrop](../Topic/CMFCToolBarButton::OnBeforeDrop.md)|指定使用者是否可以置放目標工具列上的按鈕。|  
|[CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)|呼叫框架計算按鈕的大小指定的裝置內容和停駐狀態的。|  
|[CMFCToolBarButton::OnCancelMode](../Topic/CMFCToolBarButton::OnCancelMode.md)|呼叫由架構處理 [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) 訊息。|  
|[CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)|呼叫框架，在按一下插入新的工具列。|  
|[CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)|呼叫框架，當使用者按一下滑鼠按鈕。|  
|[CMFCToolBarButton::OnClickUp](../Topic/CMFCToolBarButton::OnClickUp.md)|呼叫框架，使用者放開滑鼠按鈕。|  
|[CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md)|呼叫框架，其在父代 \(Parent\) 工具列處理 `WM_HELPHITTEST` 訊息。|  
|[CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md)|呼叫框架，其在父代 \(Parent\) 工具列處理 `WM_CTLCOLOR` 訊息。|  
|[CMFCToolBarButton::OnCustomizeMenu](../Topic/CMFCToolBarButton::OnCustomizeMenu.md)|當應用程式會在父代 \(Parent\) 工具列時，就會使用捷徑功能表可以讓按鈕修改所提供的功能表。|  
|[CMFCToolBarButton::OnDblClk](../Topic/CMFCToolBarButton::OnDblClk.md)|呼叫框架，其在父代 \(Parent\) 工具列處理 [WM\_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) 訊息。|  
|[CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)|使用指定的樣式和選項，會由架構來繪製按鈕。|  
|[CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)|呼叫框架會在 \[**自訂**\] 對話方塊的 \[**命令**\] 窗格的按鈕。|  
|[CMFCToolBarButton::OnGetCustomToolTipText](../Topic/CMFCToolBarButton::OnGetCustomToolTipText.md)|呼叫由架構擷取按鈕的自訂工具提示文字。|  
|[CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md)|呼叫框架，其在全域已經變更。|  
|[CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md)|呼叫框架，其在父代 \(Parent\) 工具列移動。|  
|[CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md)|呼叫框架，該按鈕會變成可見或不可見的。|  
|[CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md)|呼叫，便會由架構父代 \(Parent\) 工具列變更時的大小或位置和這個變更要求按鈕得以變更大小。|  
|[CMFCToolBarButton::OnToolHitTest](../Topic/CMFCToolBarButton::OnToolHitTest.md)|呼叫框架，其在父代 \(Parent\) 工具列必須判斷某個點是否在按鈕的週框 \(Bounding Rectangle\)。|  
|[CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md)|呼叫框架，其在父代 \(Parent\) 工具列更新它的工具提示文字。|  
|[CMFCToolBarButton::PrepareDrag](../Topic/CMFCToolBarButton::PrepareDrag.md)|呼叫框架，該按鈕會執行拖放作業。|  
|[CMFCToolBarButton::Rect](../Topic/CMFCToolBarButton::Rect.md)|擷取按鈕的週框 \(Bounding Rectangle\)。|  
|[CMFCToolBarButton::ResetImageToDefault](../Topic/CMFCToolBarButton::ResetImageToDefault.md)|設定為預設值與按鈕關聯的影像。|  
|[CMFCToolBarButton::SaveBarState](../Topic/CMFCToolBarButton::SaveBarState.md)|將工具列按鈕的狀態。|  
|[CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)|從檔案讀取或寫入的這個物件為檔案。  \(覆寫 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。|  
|[CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md)|填入可及性資料所提供的 `CAccessibilityData` 物件從工具列按鈕。|  
|[CMFCToolBarButton::SetClipboardFormatName](../Topic/CMFCToolBarButton::SetClipboardFormatName.md)|指定全域剪貼簿格式。|  
|[CMFCToolBarButton::SetImage](../Topic/CMFCToolBarButton::SetImage.md)|將按鈕的影像索引。|  
|[CMFCToolBarButton::SetProtectedCommands](../Topic/CMFCToolBarButton::SetProtectedCommands.md)|設定使用者無法自訂命令的清單。|  
|[CMFCToolBarButton::SetRadio](../Topic/CMFCToolBarButton::SetRadio.md)|呼叫框架，在按一下變更的核取狀態。|  
|[CMFCToolBarButton::SetRect](../Topic/CMFCToolBarButton::SetRect.md)|將按鈕的週框 \(Bounding Rectangle\)。|  
|[CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)|設定按鈕的樣式。|  
|[CMFCToolBarButton::SetVisible](../Topic/CMFCToolBarButton::SetVisible.md)|指定按鈕是否為可見。|  
|[CMFCToolBarButton::Show](../Topic/CMFCToolBarButton::Show.md)|顯示或隱藏按鈕。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarButton::m\_bImage](../Topic/CMFCToolBarButton::m_bImage.md)|指定影像是否顯示在按鈕上。|  
|[CMFCToolBarButton::m\_bText](../Topic/CMFCToolBarButton::m_bText.md)|指定文字標籤是否顯示在按鈕上。|  
|[CMFCToolBarButton::m\_bTextBelow](../Topic/CMFCToolBarButton::m_bTextBelow.md)|指定文字標籤是在按鈕上的影像便會顯示。|  
|[CMFCToolBarButton::m\_bUserButton](../Topic/CMFCToolBarButton::m_bUserButton.md)|指定按鈕是否有使用者定義的影像。|  
|[CMFCToolBarButton::m\_bWholeText](../Topic/CMFCToolBarButton::m_bWholeText.md)|指定按鈕是否會顯示出全文標籤，即使不相容的週框 \(Bounding Rectangle\)。|  
|[CMFCToolBarButton::m\_bWrap](../Topic/CMFCToolBarButton::m_bWrap.md)|指定在分隔符號旁邊的按鈕是否在下一個資料列會放置。|  
|[CMFCToolBarButton::m\_bWrapText](../Topic/CMFCToolBarButton::m_bWrapText.md)|指定多行文字標籤是否已啟用。|  
|[CMFCToolBarButton::m\_nID](../Topic/CMFCToolBarButton::m_nID.md)|按鈕的命令 ID。|  
|[CMFCToolBarButton::m\_nStyle](../Topic/CMFCToolBarButton::m_nStyle.md)|按鈕的樣式。|  
|[CMFCToolBarButton::m\_strText](../Topic/CMFCToolBarButton::m_strText.md)|按鈕的文字標籤。|  
  
## 備註  
 `CMFCToolbarButton` 物件就是位於工具列上的控制項。  它的行為類似一般按鈕。  您可以將影像和文字標籤加入至物件。  工具列按鈕也可以有一個命令 ID。.  當使用者按一下  工具列按鈕時，架構會執行這個 ID 指定的命令。  
  
 一般來說，工具列按鈕可以自訂:使用者可以從拖曳一個工具列的按鈕加入至另一個、複製、貼上、刪除和編輯文字標籤和影像。  若要防止使用者自訂工具列，您可以用兩種方式來鎖定工具列。  其中一個設定為 `TRUE` 的 `bLocked` 旗標，當您呼叫 [CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md)時使用 [CMFCToolBarButton::SetProtectedCommands](../Topic/CMFCToolBarButton::SetProtectedCommands.md) 方法，或將個別按鈕的命令 ID 給受保護命令全域清單。  
  
 `CMFCToolBarButton` 物件從工具列影像的全域集合上顯示影像在應用程式中。  這些集合是由父代 \(Parent\) 工具列， [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)維護。  如需詳細資訊，請參閱 [CMFCToolBarImages Class](../../mfc/reference/cmfctoolbarimages-class.md)。  
  
 當使用者按一下  工具列按鈕時，它的父代 \(Parent\) 工具列處理滑鼠訊息和溝通適當行為加入至按鈕。  如果按鈕有有效的命令 ID，父代 \(Parent\) 工具列 `WM_COMMAND` 資訊傳送至父框架。  
  
 `CMFCToolBarButton` 類別為其他工具列按鈕類別的基底類別，例如、和 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md)[CMFCToolBarEditBoxButton Class](../../mfc/reference/cmfctoolbareditboxbutton-class.md)[CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。  
  
## 範例  
 您可以使用類別，在 `CMFCToolBarButton` 的各種方法。下列範例將示範如何設定 `CMFCToolBarButton` 物件。  範例會說明如何啟用滑鼠和鍵盤輸入，將按鈕的影像索引，請將按鈕的週框和呈現按鈕為可見。  這個程式碼片段是 [索引標籤控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_TabControl#1](../../mfc/reference/codesnippet/CPP/cmfctoolbarbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_TabControl#2](../../mfc/reference/codesnippet/CPP/cmfctoolbarbutton-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## 需求  
 **標題:** afxtoolbarbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarImages Class](../../mfc/reference/cmfctoolbarimages-class.md)   
 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)   
 [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)