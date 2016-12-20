---
title: "CToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "點陣圖 [C++], button controls"
  - "按鈕 [C++], MFC toolbars"
  - "control bars [C++], CToolBar class"
  - "CToolBar class"
  - "工具列 [C++], CToolBar class"
  - "Windows common controls [C++], CToolBar class"
  - "Windows toolbar common controls [C++]"
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得點陣圖按鈕和選擇性分隔列的控制列。  
  
## 語法  
  
```  
class CToolBar : public CControlBar  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CToolBar::CToolBar](../Topic/CToolBar::CToolBar.md)|建構 `CToolBar` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CToolBar::CommandToIndex](../Topic/CToolBar::CommandToIndex.md)|傳回一個按鈕的索引具有指定的命令 ID 的 .|  
|[CToolBar::Create](../Topic/CToolBar::Create.md)|建立視窗工具列並將其附加至 `CToolBar` 物件。|  
|[CToolBar::CreateEx](../Topic/CToolBar::CreateEx.md)|建立含有其他樣式的 `CToolBar` 物件 `CToolBarCtrl` 內嵌物件的。|  
|[CToolBar::GetButtonInfo](../Topic/CToolBar::GetButtonInfo.md)|擷取按鈕的 ID、樣式和影像的數字。|  
|[CToolBar::GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md)|擷取按鈕的樣式。|  
|[CToolBar::GetButtonText](../Topic/CToolBar::GetButtonText.md)|擷取將會顯示在按鈕上的文字。|  
|[CToolBar::GetItemID](../Topic/CToolBar::GetItemID.md)|傳回按鈕或分隔符號的命令 ID 指定索引處的。|  
|[CToolBar::GetItemRect](../Topic/CToolBar::GetItemRect.md)|擷取項目的顯示矩形指定索引處的。|  
|[CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md)|允許傳送至基礎通用控制項的直接存取。|  
|[CToolBar::LoadBitmap](../Topic/CToolBar::LoadBitmap.md)|載入包含點陣圖按鈕影像的點陣圖。|  
|[CToolBar::LoadToolBar](../Topic/CToolBar::LoadToolBar.md)|使用資源編輯器載入所建立的。|  
|[CToolBar::SetBitmap](../Topic/CToolBar::SetBitmap.md)|設定點陣圖複製影像。|  
|[CToolBar::SetButtonInfo](../Topic/CToolBar::SetButtonInfo.md)|將按鈕的 ID、樣式和影像的數字。|  
|[CToolBar::SetButtons](../Topic/CToolBar::SetButtons.md)|將按鈕樣式和按鈕影像索引點陣圖中的。|  
|[CToolBar::SetButtonStyle](../Topic/CToolBar::SetButtonStyle.md)|設定按鈕的樣式。|  
|[CToolBar::SetButtonText](../Topic/CToolBar::SetButtonText.md)|設定會在按鈕上的文字。|  
|[CToolBar::SetHeight](../Topic/CToolBar::SetHeight.md)|將工具列的高度。|  
|[CToolBar::SetSizes](../Topic/CToolBar::SetSizes.md)|將按鈕和它們的點陣圖大小。|  
  
## 備註  
 按鈕時就像按鈕、核取方塊按鈕、選項按鈕。  `CToolBar` 物件通常是框架視窗物件的內嵌的成員從類別衍生的 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 或 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)。  
  
 [CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md)，成員函式新增至 MFC 4.0，可讓您利用 Windows 通用控制項支援自訂工具列和其他功能。  `CToolBar` 成員函式讓您最新 Windows 通用控制項的功能，不過，在中，當您呼叫 `GetToolBarCtrl`時，您可以為工具列 Windows 95 特性\/98 工具列。  當您呼叫 `GetToolBarCtrl`，它將會傳回 `CToolBarCtrl` 物件的參考。  使用 Windows 通用控制項，請參閱 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 有關設計工具列的詳細資訊。  如需通用控制項的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)][通用控制項](http://msdn.microsoft.com/library/windows/desktop/bb775493) 。  
  
 Visual C\+\+ 提供兩種方法都會建立工具列。  使用資源編輯器，若要建立工具列資源，請依照下列步驟執行:  
  
1.  建立工具列資源。  
  
2.  `CToolBar` 建構物件。  
  
3.  呼叫 [建立](../Topic/CToolBar::Create.md) \(或\) [CreateEx](../Topic/CToolBar::CreateEx.md)函式建立視窗工具列並附加至 `CToolBar` 物件。  
  
4.  呼叫載入工具列資源的 [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) 。  
  
 否則，請遵循下列步驟：  
  
1.  `CToolBar` 建構物件。  
  
2.  呼叫 [建立](../Topic/CToolBar::Create.md) \(或\) [CreateEx](../Topic/CToolBar::CreateEx.md)函式建立視窗工具列並附加至 `CToolBar` 物件。  
  
3.  呼叫 [LoadBitmap](../Topic/CToolBar::LoadBitmap.md) 載入包含工具列按鈕影像的點陣圖。  
  
4.  呼叫 [SetButtons](../Topic/CToolBar::SetButtons.md) 設定按鈕樣式和相關聯的每個按鈕在點陣圖的影像。  
  
 在工具列的按鈕影像從點陣圖中取得，必須包含每個按鈕的影像。  所有影像大小必須與;預設寬度為 16 像素、高 15 像素\)。  影像必須是並行在點陣圖。  
  
 `SetButtons` 函式使用指標在陣列指定之元素數目的陣列和控制項 ID 的整數。  函式將每個按鈕的 ID 設定為陣列的對應元素的值並將每個按鈕影像索引，點陣圖中指定按鈕的影像位置。  如果陣列元素的值， **ID\_SEPARATOR**影像索引未指派。  
  
 影像的命令將點陣圖中通常是它們在螢幕上繪製的命令，不過，您可以使用 [SetButtonInfo](../Topic/CToolBar::SetButtonInfo.md) 函式變更影像順序和繪圖命令之間的關聯性。  
  
 在  工具列中的所有按鈕的大小是否相同。  預設為 24 x 22 像素，與 *Windows 軟體設計介面的方針符合*。  在影像和按鈕維度之間的所有額外空間用於在影像周圍組成框線。  
  
 每個按鈕的影像。  各種按鈕狀態和樣式 \(已按下，，關閉，停用，停用關閉，而不會決定\) 從該影像產生。  雖然點陣圖可以是任何色彩，您可以取得與影像的最佳結果可能為黑色和灰階。  
  
> [!WARNING]
>  `CToolBar` 支援最多的點陣圖 16 個色彩。  當您載入影像的工具列編輯器時，如果需要， Visual Studio 會自動將影像轉換成 16 色彩的點陣圖，而會顯示警告訊息，則影像會轉換為。  如果使用超過 16 個色彩的影像 \(使用編輯外部的編輯器影像\)，應用程式可能無法如預期般運作。  
  
 預設工具列按鈕遵循按鈕。  不過，工具列按鈕也可以依照按鈕、核取方塊或選項按鈕。  核取方塊按鈕有三種狀態:檢查，清除，和不定。  選項按鈕只有兩個狀態:檢查和清除。  
  
 若要設定個別按鈕或分隔符號樣式，而不會指向陣列，請呼叫 [GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md) 擷取這個樣式，然後呼叫 [SetButtonStyle](../Topic/CToolBar::SetButtonStyle.md) 而不是 `SetButtons`。  例如，當您想要變更按鈕的樣式在執行階段時，`SetButtonStyle` 十分實用。  
  
 若要將文字會顯示在按鈕上時，請呼叫 [GetButtonText](../Topic/CToolBar::GetButtonText.md) 擷取文字會出現在  按鈕，然後呼叫 [SetButtonText](../Topic/CToolBar::SetButtonText.md) 設定文字。  
  
 建立核取方塊按鈕，將其指派給樣式 **TBBS\_CHECKBOX** 或使用 `CCmdUI` 物件的 `SetCheck` 成員函式在 `ON_UPDATE_COMMAND_UI` 處理常式。  呼叫 `SetCheck` 保留一個按鈕變更核取方塊按鈕。  藉由 `SetCheck` 引數 0 unchecked， 1 核取或不定。2  
  
 若要建立選項按鈕，請呼叫 [CCmdUI](../../mfc/reference/ccmdui-class.md) 物件的 [SetRadio](../Topic/CCmdUI::SetRadio.md) 從 `ON_UPDATE_COMMAND_UI` 管理員的成員函式。  藉由 `SetRadio` 引數 0 未核取或非零的檢查。  為了提供一個無線群組的互斥 \(Mutually Exclusive\) 的行為，您必須在群組中必須有任何的 `ON_UPDATE_COMMAND_UI` 管理員按鈕。  
  
 如需使用 `CToolBar`的詳細資訊，請參閱本文 [MFC 工具列實作](../../mfc/mfc-toolbar-implementation.md) 和 [Technical Note 31:控制項陣列。](../../mfc/tn031-control-bars.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 CTRLBARS](../../top/visual-cpp-samples.md)   
 [MFC 範例 DLG CBR32](../../top/visual-cpp-samples.md)   
 [MFC DOCKTOOL 範例](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl Class](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [CToolBar::Create](../Topic/CToolBar::Create.md)   
 [CToolBar::LoadBitmap](../Topic/CToolBar::LoadBitmap.md)   
 [CToolBar::SetButtons](../Topic/CToolBar::SetButtons.md)   
 [CCmdUI::SetCheck](../Topic/CCmdUI::SetCheck.md)   
 [CCmdUI::SetRadio](../Topic/CCmdUI::SetRadio.md)