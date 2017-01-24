---
title: "CToolBarCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl class"
  - "工具提示 [C++], 告知"
  - "工具列控制項 [MFC], CToolBarCtrl class"
  - "Windows common controls [C++], CToolBarCtrl"
ms.assetid: 8f2f8ad2-05d7-4975-8715-3f2eed795248
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CToolBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供視窗工具列上的通用控制項的功能。  
  
## 語法  
  
```  
class CToolBarCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CToolBarCtrl::CToolBarCtrl](../Topic/CToolBarCtrl::CToolBarCtrl.md)|建構 `CToolBarCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CToolBarCtrl::AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md)|將一或多個點陣圖按鈕設定為影像按鈕影像清單中可用的工具列控制項。|  
|[CToolBarCtrl::AddButtons](../Topic/CToolBarCtrl::AddButtons.md)|將一個或多個按鈕加入至工具列控制項。|  
|[CToolBarCtrl::AddString](../Topic/CToolBarCtrl::AddString.md)|將新的字串，做為資源 ID，將資料工具列的內部清單中。|  
|[CToolBarCtrl::AddStrings](../Topic/CToolBarCtrl::AddStrings.md)|將新的字串或字串，傳遞，指標空格分隔字串緩衝區，字串至工具列的內部清單中。|  
|[CToolBarCtrl::AutoSize](../Topic/CToolBarCtrl::AutoSize.md)|調整大小的工具列控制項。|  
|[CToolBarCtrl::ChangeBitmap](../Topic/CToolBarCtrl::ChangeBitmap.md)|變更一個按鈕的點陣圖目前工具列控制項。|  
|[CToolBarCtrl::CheckButton](../Topic/CToolBarCtrl::CheckButton.md)|選取或清除  工具列控制項的特定按鈕。|  
|[CToolBarCtrl::CommandToIndex](../Topic/CToolBarCtrl::CommandToIndex.md)|擷取按鈕的以零起始的索引與指定的命令識別項。|  
|[CToolBarCtrl::Create](../Topic/CToolBarCtrl::Create.md)|建立工具列控制項並將其附加至 `CToolBarCtrl` 物件。|  
|[CToolBarCtrl::CreateEx](../Topic/CToolBarCtrl::CreateEx.md)|建立擁有指定之視窗的延伸樣式的工具列控制項並將其附加至 `CToolBarCtrl` 物件。|  
|[CToolBarCtrl::Customize](../Topic/CToolBarCtrl::Customize.md)|顯示自訂工具列的  對話方塊。|  
|[CToolBarCtrl::DeleteButton](../Topic/CToolBarCtrl::DeleteButton.md)|刪除工具列控制項中的按鈕。|  
|[CToolBarCtrl::EnableButton](../Topic/CToolBarCtrl::EnableButton.md)|啟用或停用在工具列控制項指定的按鈕。|  
|[CToolBarCtrl::GetAnchorHighlight](../Topic/CToolBarCtrl::GetAnchorHighlight.md)|擷取工具列的錨定反白顯示設定。|  
|[CToolBarCtrl::GetBitmap](../Topic/CToolBarCtrl::GetBitmap.md)|擷取點陣圖的索引與工具列上的按鈕。|  
|[CToolBarCtrl::GetBitmapFlags](../Topic/CToolBarCtrl::GetBitmapFlags.md)|取得旗標與工具列的點陣圖。|  
|[CToolBarCtrl::GetButton](../Topic/CToolBarCtrl::GetButton.md)|擷取與指定之按鈕的資訊在工具列控制項。|  
|[CToolBarCtrl::GetButtonCount](../Topic/CToolBarCtrl::GetButtonCount.md)|目前擷取按鈕的計數\] 工具列控制項。|  
|[CToolBarCtrl::GetButtonInfo](../Topic/CToolBarCtrl::GetButtonInfo.md)|擷取一個按鈕的資訊在工具列上的 。|  
|[CToolBarCtrl::GetButtonSize](../Topic/CToolBarCtrl::GetButtonSize.md)|擷取目前寬度和高度工具列按鈕，以像素為單位\)。|  
|[CToolBarCtrl::GetColorScheme](../Topic/CToolBarCtrl::GetColorScheme.md)|擷取目前的工具列控制項的色彩配置。|  
|[CToolBarCtrl::GetDisabledImageList](../Topic/CToolBarCtrl::GetDisabledImageList.md)|擷取工具列控制項用來顯示停用的按鈕影像清單。|  
|[CToolBarCtrl::GetDropTarget](../Topic/CToolBarCtrl::GetDropTarget.md)|擷取工具列控制項的 [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) 介面。|  
|[CToolBarCtrl::GetExtendedStyle](../Topic/CToolBarCtrl::GetExtendedStyle.md)|擷取工具列控制項的延伸樣式。|  
|[CToolBarCtrl::GetHotImageList](../Topic/CToolBarCtrl::GetHotImageList.md)|擷取工具列控制項用來顯示「作用中」按鈕的影像清單。  表示當滑鼠指標在其上方時，項目群組的作用中按鈕會反白顯示。|  
|[CToolBarCtrl::GetHotItem](../Topic/CToolBarCtrl::GetHotItem.md)|要擷取索引之項目的索引會在工具列上的。|  
|[CToolBarCtrl::GetImageList](../Topic/CToolBarCtrl::GetImageList.md)|擷取工具列控制項用來顯示在它們的預設狀態的按鈕的影像清單。|  
|[CToolBarCtrl::GetInsertMark](../Topic/CToolBarCtrl::GetInsertMark.md)|擷取工具列的目前插入標記。|  
|[CToolBarCtrl::GetInsertMarkColor](../Topic/CToolBarCtrl::GetInsertMarkColor.md)|擷取用於將色彩繪製工具列的插入標記。|  
|[CToolBarCtrl::GetItemRect](../Topic/CToolBarCtrl::GetItemRect.md)|擷取一個按鈕的週框 \(Bounding Rectangle\) 工具列控制項的。|  
|[CToolBarCtrl::GetMaxSize](../Topic/CToolBarCtrl::GetMaxSize.md)|擷取所有的總大小可見的按鈕和分隔符號在工具列上的 。|  
|[CToolBarCtrl::GetMaxTextRows](../Topic/CToolBarCtrl::GetMaxTextRows.md)|擷取文字行的最大數目顯示於工具列按鈕上的。|  
|[CToolBarCtrl::GetMetrics](../Topic/CToolBarCtrl::GetMetrics.md)|擷取工具列控制項的度量資訊。|  
|[CToolBarCtrl::GetPadding](../Topic/CToolBarCtrl::GetPadding.md)|擷取目前的工具列控制項的水平和垂直的邊框距離。|  
|[CToolBarCtrl::GetPressedImageList](../Topic/CToolBarCtrl::GetPressedImageList.md)|擷取目前的工具列控制項用來表示處於已按下狀態的按鈕的影像清單。|  
|[CToolBarCtrl::GetRect](../Topic/CToolBarCtrl::GetRect.md)|擷取指定的工具列按鈕的週框 \(Bounding Rectangle\)。|  
|[CToolBarCtrl::GetRows](../Topic/CToolBarCtrl::GetRows.md)|擷取資料列數工具列目前顯示的按鈕。|  
|[CToolBarCtrl::GetState](../Topic/CToolBarCtrl::GetState.md)|擷取所指定的按鈕狀態資訊是以工具列控制項的，例如它是否已啟用，已按下或已核取。|  
|[CToolBarCtrl::GetString](../Topic/CToolBarCtrl::GetString.md)|擷取工具列字串。|  
|[CToolBarCtrl::GetStyle](../Topic/CToolBarCtrl::GetStyle.md)|擷取樣式目前使用中的工具列控制項。|  
|[CToolBarCtrl::GetToolTips](../Topic/CToolBarCtrl::GetToolTips.md)|擷取工具提示控制項的控制代碼，如果有的話，與工具列控制項。|  
|[CToolBarCtrl::HideButton](../Topic/CToolBarCtrl::HideButton.md)|隱藏或顯示在工具列控制項指定的按鈕。|  
|[CToolBarCtrl::HitTest](../Topic/CToolBarCtrl::HitTest.md)|判斷某個點位於工具列控制項。|  
|[CToolBarCtrl::Indeterminate](../Topic/CToolBarCtrl::Indeterminate.md)|設定或明確指定按鈕的不定狀態 \(灰色\) 在工具列控制項的。|  
|[CToolBarCtrl::InsertButton](../Topic/CToolBarCtrl::InsertButton.md)|在工具列控制項插入按鈕。|  
|[CToolBarCtrl::InsertMarkHitTest](../Topic/CToolBarCtrl::InsertMarkHitTest.md)|擷取點的插入標記資訊\] 工具列上的 。|  
|[CToolBarCtrl::IsButtonChecked](../Topic/CToolBarCtrl::IsButtonChecked.md)|會在工具列控制項指定的按鈕是否已核取。|  
|[CToolBarCtrl::IsButtonEnabled](../Topic/CToolBarCtrl::IsButtonEnabled.md)|會在工具列控制項的指定是否已啟用按鈕。|  
|[CToolBarCtrl::IsButtonHidden](../Topic/CToolBarCtrl::IsButtonHidden.md)|會在工具列控制項指定的按鈕是否為隱藏。|  
|[CToolBarCtrl::IsButtonHighlighted](../Topic/CToolBarCtrl::IsButtonHighlighted.md)|檢查工具列按鈕的焦點狀態。|  
|[CToolBarCtrl::IsButtonIndeterminate](../Topic/CToolBarCtrl::IsButtonIndeterminate.md)|會指定按鈕的狀態在工具列控制項的是否為不定 \(灰色\)。|  
|[CToolBarCtrl::IsButtonPressed](../Topic/CToolBarCtrl::IsButtonPressed.md)|會在工具列控制項指定的按鈕是否已按下按鈕。|  
|[CToolBarCtrl::LoadImages](../Topic/CToolBarCtrl::LoadImages.md)|載入點陣圖為工具列控制項的影像中列出。|  
|[CToolBarCtrl::MapAccelerator](../Topic/CToolBarCtrl::MapAccelerator.md)|將一個快速鍵字元加入工具列按鈕。|  
|[CToolBarCtrl::MarkButton](../Topic/CToolBarCtrl::MarkButton.md)|設定指定之按鈕的反白狀態在工具列控制項的。|  
|[CToolBarCtrl::MoveButton](../Topic/CToolBarCtrl::MoveButton.md)|從某個索引捲動按鈕加入至另一個。|  
|[CToolBarCtrl::PressButton](../Topic/CToolBarCtrl::PressButton.md)|按下或版本在工具列控制項指定的按鈕。|  
|[CToolBarCtrl::ReplaceBitmap](../Topic/CToolBarCtrl::ReplaceBitmap.md)|以新的點陣圖取代目前工具列控制項的現有的點陣圖。|  
|[CToolBarCtrl::RestoreState](../Topic/CToolBarCtrl::RestoreState.md)|還原工具列控制項的狀態。|  
|[CToolBarCtrl::SaveState](../Topic/CToolBarCtrl::SaveState.md)|儲存工具列控制項的狀態。|  
|[CToolBarCtrl::SetAnchorHighlight](../Topic/CToolBarCtrl::SetAnchorHighlight.md)|將工具列的錨定反白顯示設定。|  
|[CToolBarCtrl::SetBitmapSize](../Topic/CToolBarCtrl::SetBitmapSize.md)|設定要加入的點陣影像的大小加入至工具列控制項。|  
|[CToolBarCtrl::SetButtonInfo](../Topic/CToolBarCtrl::SetButtonInfo.md)|設定現有按鈕的資訊在工具列上的 。|  
|[CToolBarCtrl::SetButtonSize](../Topic/CToolBarCtrl::SetButtonSize.md)|設定要加入之按鈕的大小加入至工具列控制項。|  
|[CToolBarCtrl::SetButtonStructSize](../Topic/CToolBarCtrl::SetButtonStructSize.md)|指定 `TBBUTTON` 結構的大小。|  
|[CToolBarCtrl::SetButtonWidth](../Topic/CToolBarCtrl::SetButtonWidth.md)|會設定工具列控制項的最小和最大按鈕寬度。|  
|[CToolBarCtrl::SetCmdID](../Topic/CToolBarCtrl::SetCmdID.md)|指定的按鈕時，設定要傳送的命令識別項至主控視窗。|  
|[CToolBarCtrl::SetColorScheme](../Topic/CToolBarCtrl::SetColorScheme.md)|設定目前工具列控制項的色彩配置。|  
|[CToolBarCtrl::SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md)|設定工具列控制項用於顯示停用的按鈕影像清單。|  
|[CToolBarCtrl::SetDrawTextFlags](../Topic/CToolBarCtrl::SetDrawTextFlags.md)|設定在 Win32 函式， [DrawText](http://msdn.microsoft.com/library/windows/desktop/dd162498)的旗標可用來在指定矩形的文字格式化，以旗標如何設定。|  
|[CToolBarCtrl::SetExtendedStyle](../Topic/CToolBarCtrl::SetExtendedStyle.md)|設定工具列控制項的延伸樣式。|  
|[CToolBarCtrl::SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md)|設定工具列控制項用於顯示「作用中」按鈕的影像清單。|  
|[CToolBarCtrl::SetHotItem](../Topic/CToolBarCtrl::SetHotItem.md)|在  工具列上設定作用中的項目。|  
|[CToolBarCtrl::SetImageList](../Topic/CToolBarCtrl::SetImageList.md)|將工具列將用來顯示按鈕在它們的預設狀態的影像清單。|  
|[CToolBarCtrl::SetIndent](../Topic/CToolBarCtrl::SetIndent.md)|將第一個按鈕的縮排、工具列控制項。|  
|[CToolBarCtrl::SetInsertMark](../Topic/CToolBarCtrl::SetInsertMark.md)|將工具列的目前插入標記。|  
|[CToolBarCtrl::SetInsertMarkColor](../Topic/CToolBarCtrl::SetInsertMarkColor.md)|設定用於的色彩繪製工具列的插入標記。|  
|[CToolBarCtrl::SetMaxTextRows](../Topic/CToolBarCtrl::SetMaxTextRows.md)|將文字行的最大數目顯示於工具列按鈕上的。|  
|[CToolBarCtrl::SetMetrics](../Topic/CToolBarCtrl::SetMetrics.md)|設定工具列控制項的度量資訊。|  
|[CToolBarCtrl::SetOwner](../Topic/CToolBarCtrl::SetOwner.md)|設定視窗接收來自工具列控制項的通知訊息。|  
|[CToolBarCtrl::SetPadding](../Topic/CToolBarCtrl::SetPadding.md)|設定目前工具列控制項的水平和垂直的邊框距離。|  
|[CToolBarCtrl::SetPressedImageList](../Topic/CToolBarCtrl::SetPressedImageList.md)|設定目前工具列控制項用來表示處於已按下狀態的按鈕的影像清單。|  
|[CToolBarCtrl::SetRows](../Topic/CToolBarCtrl::SetRows.md)|設定資料列數工具列顯示的按鈕。|  
|[CToolBarCtrl::SetState](../Topic/CToolBarCtrl::SetState.md)|設定指定之按鈕的狀態在工具列控制項。|  
|[CToolBarCtrl::SetStyle](../Topic/CToolBarCtrl::SetStyle.md)|設定工具列控制項的樣式。|  
|[CToolBarCtrl::SetToolTips](../Topic/CToolBarCtrl::SetToolTips.md)|與工具提示控制項與工具列控制項。|  
|[CToolBarCtrl::SetWindowTheme](../Topic/CToolBarCtrl::SetWindowTheme.md)|設定工具列控制項的視覺化樣式。|  
  
## 備註  
 這個控制項 \(也 `CToolBarCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 視窗工具列通用控制項是包含一或多個按鈕之矩形的子視窗。  這些按鈕可以顯示點陣圖影像，字串或兩者。  當使用者選取按鈕時，它會將命令傳送訊息至工具列的主控視窗。  一般而言，在工具列上的按鈕對應於應用程式的功能表項目，它們會為使用者提供一種直接的方式存取應用程式的命令。  
  
 `CToolBarCtrl` 物件包含數個重要內部資料結構:按鈕影像點陣圖清單或影像清單、按鈕標籤字串清單與關聯的影像和字串具有按鈕的位置、樣式、狀態和命令 ID 的 `TBBUTTON` 結構清單。  每一種資料結構的項目之以零起始的索引參考。  在您可以使用 `CToolBarCtrl` 物件之前，您必須將這些資料結構。  字串清單可以為按鈕標籤只使用;您無法從工具列來擷取字串。  
  
 若要使用 `CToolBarCtrl` 物件，您通常會執行下列步驟:  
  
1.  `CToolBarCtrl` 建構物件。  
  
2.  呼叫 [建立](../Topic/CToolBarCtrl::Create.md) 建立視窗工具列上的通用控制項並將它附加至 `CToolBarCtrl` 物件。  表示工具列樣式使用樣式，例如透明工具列的支援下拉式樣式按鈕的工具列上的 **TBSTYLE\_TRANSPARENT** 或 **TBSTYLE\_DROPDOWN** 。  
  
3.  識別如何所要顯示的工具列上的按鈕:  
  
    -   為按鈕要使用點陣圖影像，將按鈕點陣圖為工具列藉由呼叫 [AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md)。  
  
    -   若要使用影像顯示的影像按鈕清單，藉由呼叫 [SetImageList](../Topic/CToolBarCtrl::SetImageList.md)、 [SetHotImageList](../Topic/CToolBarCtrl::SetHotImageList.md)或 [SetDisabledImageList](../Topic/CToolBarCtrl::SetDisabledImageList.md)指定影像清單。  
  
    -   為按鈕要使用資料標記，請將字串加入至工具列藉由呼叫 [AddString](../Topic/CToolBarCtrl::AddString.md) 和 [AddStrings](../Topic/CToolBarCtrl::AddStrings.md)。  
  
4.  將按鈕加入至工具列結構藉由呼叫 [AddButtons](../Topic/CToolBarCtrl::AddButtons.md)。  
  
5.  如果您想要一個工具列按鈕的工具提示在不是 `CFrameWnd`的主控視窗，您需要處理工具列上的主控視窗的 **TTN\_NEEDTEXT** 訊息 [管理工具提示告知](../../mfc/handling-tool-tip-notifications.md)\(如中所述。  如果工具列的父視窗 `CFrameWnd`從衍生，工具提示會顯示，但不會從您的任何額外工作，因為 `CFrameWnd` 提供預設處理常式。  
  
6.  如果您想要讓使用者自訂工具列，請處理自訂在主控視窗的通知訊息 [管理自訂告知](../../mfc/handling-customization-notifications.md)\(如中所述。  
  
 您可以使用 [SaveState](../Topic/CToolBarCtrl::SaveState.md) 儲存工具列控制項的目前狀態中註冊和 [RestoreState](../Topic/CToolBarCtrl::RestoreState.md) 還原根據資訊的狀態先前儲存在登錄中。  除了儲存在應用程式中使用的之間工具列狀態，應用程式通常會儲存狀態，在使用者啟動自訂工具列之前，當使用者之後若要還原工具列回其原始狀態。  
  
## 為 Internet Explorer 4.0 \(含\) 以後版本不支援  
 若要支援在 Internet Explorer 中加入的功能，版本 4.0 \(含\) 以後版本中， MFC 會針對工具列控制項提供影像清單和支援透明和平面樣式。  
  
 透明工具列可讓用戶端在工具列的來顯示。  若要建立透明的工具列中，使用 **TBSTYLE\_FLAT** 和 **TBSTYLE\_TRANSPARENT** 樣式。  透明工具列的熱追蹤和功能，也就是說，當滑鼠指標移至  工具列上的按鈕的按鈕時，按鈕的外觀會變更。  工具列建立 **TBSTYLE\_FLAT** 模式會包含不透明按鈕。  
  
 影像清單支援提供控制項的預設行為、作用中影像和停用影像的更大的彈性。  使用 [GetImageList](../Topic/CToolBarCtrl::GetImageList.md)、 [GetHotImageList](../Topic/CToolBarCtrl::GetHotImageList.md)和 [GetDisabledImageList](../Topic/CToolBarCtrl::GetDisabledImageList.md) 以透明工具列會根據其狀態管理影像:  
  
 如需使用 `CToolBarCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CToolBarCtrl](../../mfc/using-ctoolbarctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolBarCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL1](../../top/visual-cpp-samples.md)   
 [MFC 範例 MFCIE](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)