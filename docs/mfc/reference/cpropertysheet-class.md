---
title: "CPropertySheet Class | Microsoft Docs"
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
  - "CPropertySheet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertySheet class"
  - "對話方塊, 索引標籤"
  - "屬性工作表, CPropertySheet class"
  - "索引標籤對話方塊"
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
caps.latest.revision: 30
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPropertySheet Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示屬性工作表，也稱為選項\] 對話方塊。  
  
## 語法  
  
```  
class CPropertySheet : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPropertySheet::CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md)|建構 `CPropertySheet` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md)|將頁面加入至屬性工作表。|  
|[CPropertySheet::Construct](../Topic/CPropertySheet::Construct.md)|建構 `CPropertySheet` 物件。|  
|[CPropertySheet::Create](../Topic/CPropertySheet::Create.md)|顯示非強制回應的屬性工作表。|  
|[CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md)|顯示強制回應屬性工作表。|  
|[CPropertySheet::EnableStackedTabs](../Topic/CPropertySheet::EnableStackedTabs.md)|這個屬性工作表使用直式或捲動索引標籤。|  
|[CPropertySheet::EndDialog](../Topic/CPropertySheet::EndDialog.md)|結束屬性工作表。|  
|[CPropertySheet::GetActiveIndex](../Topic/CPropertySheet::GetActiveIndex.md)|擷取屬性工作表的使用中的頁面的索引。|  
|[CPropertySheet::GetActivePage](../Topic/CPropertySheet::GetActivePage.md)|傳回使用中的頁面物件。|  
|[CPropertySheet::GetPage](../Topic/CPropertySheet::GetPage.md)|擷取指標設定為指定的頁面。|  
|[CPropertySheet::GetPageCount](../Topic/CPropertySheet::GetPageCount.md)|擷取頁面數目屬性工作表的。|  
|[CPropertySheet::GetPageIndex](../Topic/CPropertySheet::GetPageIndex.md)|擷取屬性工作表中指定的頁面索引。|  
|[CPropertySheet::GetTabControl](../Topic/CPropertySheet::GetTabControl.md)|擷取指標索引標籤控制項。|  
|[CPropertySheet::MapDialogRect](../Topic/CPropertySheet::MapDialogRect.md)|轉換矩形的對話方塊單位篩選單位。|  
|[CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md)|擴充屬性工作表初始化的覆寫。|  
|[CPropertySheet::PressButton](../Topic/CPropertySheet::PressButton.md)|模擬指定按鈕的  屬性工作表的。|  
|[CPropertySheet::RemovePage](../Topic/CPropertySheet::RemovePage.md)|從屬性工作表移除網頁。|  
|[CPropertySheet::SetActivePage](../Topic/CPropertySheet::SetActivePage.md)|以程式設計方式設定使用中的頁面物件。|  
|[CPropertySheet::SetFinishText](../Topic/CPropertySheet::SetFinishText.md)|設定結束按鈕的文字。|  
|[CPropertySheet::SetTitle](../Topic/CPropertySheet::SetTitle.md)|將屬性工作表的標題。|  
|[CPropertySheet::SetWizardButtons](../Topic/CPropertySheet::SetWizardButtons.md)|精靈啟用按鈕。|  
|[CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)|啟動精靈模式。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPropertySheet::m\_psh](../Topic/CPropertySheet::m_psh.md)|視窗 [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) 結構。  提供對基本屬性工作表參數。|  
  
## 備註  
 屬性工作表包含 `CPropertySheet` 物件和一或多個 [CPropertyPage](../../mfc/reference/cpropertypage-class.md) 物件。  這個架構顯示屬性工作表為包含目前所選取之頁面的一組視窗索引標籤和區域。  使用適當的索引標籤，使用者巡覽至特定頁面。  
  
 `CPropertySheet` 為 [!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)] 和 Windows NT 引入的展開 [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) 結構支援 2000 年。  結構包含使用「浮水印」幕後點陣圖，支援的額外旗標和成員。  
  
 若要自動顯示這些新影像在屬性工作表物件，請將點陣圖和調色盤影像的有效值在對的呼叫 [CPropertySheet::Construct](../Topic/CPropertySheet::Construct.md) 或 [CPropertySheet::CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md)。  
  
 即使 `CPropertySheet` 從 [CDialog](../../mfc/reference/cdialog-class.md)並非衍生自類別，處理 `CPropertySheet` 物件與處理 `CDialog` 物件。  例如，屬性工作表的建立需要兩部分語法結構:呼叫建構函式，然後呼叫強制回應屬性工作表的非強制回應屬性工作表的 [DoModal](../Topic/CPropertySheet::DoModal.md) 或 [建立](../Topic/CPropertySheet::Create.md) 。  `CPropertySheet` 建構函式 \(Constructor\) 有兩種: [CPropertySheet::Construct](../Topic/CPropertySheet::Construct.md) 和 [CPropertySheet::CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md)。  
  
 當您 `CPropertySheet` 建構物件時，某些 [視窗樣式](../../mfc/reference/window-styles.md) 可能會讓第一個可能發生的例外狀況 \(Exception\)。  在工作表建立之前，這是因為與嘗試這個系統變更屬性工作表的樣式。  若要避免這個例外狀況，請確定您已將下列模式，當您建置 `CPropertySheet`時:  
  
-   DS\_3DLOOK  
  
-   DS\_CONTROL  
  
-   WS\_CHILD  
  
-   WS\_TABSTOP  
  
 下列模式是選擇性的並不會產生第一個可能發生的例外狀況:  
  
-   DS\_SHELLFONT  
  
-   DS\_LOCALEDIT  
  
-   WS\_CLIPCHILDREN。  
  
 任何其他 `Window Styles` 禁止，而且您不應該讓它們。  
  
 在 `CPropertySheet` 物件和外部物件之間交換資料類似於使用物件 `CDialog` 交換資料。  主要差異是屬性工作表的設定通常是 `CPropertyPage` 物件的成員變數而不是 `CPropertySheet` 物件。  
  
 您可以建立名為精靈的 \[選項\] 對話方塊的型別，其中包括使用屬性頁序列的屬性工作表透過作業步驟引導使用者的動作，例如設定裝置或建立目前通訊。  在精靈的  索引標籤的  對話方塊中，  屬性頁沒有索引標籤，然後，只有一個屬性頁一次只能看見。  此外，並非 \[**確定**\] 和 \[**現在套用**\] 按鈕，一個精靈類型的索引標籤對話方塊有一個 \[**背景**\] 按鈕、一個 \[**下一個**\] 或 \[**完成**\] 按鈕、一個 \[**取消**\] 按鈕和一個 \[**說明**\] 按鈕。  
  
 若要建立精靈類型的對話方塊，請遵循您會遵循建立標準屬性工作表的相同步驟，但是，呼叫 [SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md) ，在您呼叫之前 [DoModal](../Topic/CPropertySheet::DoModal.md)。  若要啟用精靈按鈕，請呼叫 [SetWizardButtons](../Topic/CPropertySheet::SetWizardButtons.md)旗標，用來自訂其函式和外觀。  在使用者稍後要啟用 \[**完成**\] 按鈕，呼叫 [SetFinishText](../Topic/CPropertySheet::SetFinishText.md) 採用到精靈的最後一頁的動作。  
  
 如需如何使用 `CPropertySheet` 物件的詳細資訊，請參閱本文 [屬性工作表的屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)。  此外，請參閱知識庫文件 Q146916:HOWTO:建立具有標準按鈕和文件 Q300606 的非強制回應 CPropertySheet:HOWTO:設計可調整大小的 MFC 屬性工作表。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## 需求  
 **標題:** afxdlgs.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL1](../../top/visual-cpp-samples.md)   
 [MFC 範例 CMNCTRL2](../../top/visual-cpp-samples.md)   
 [MFC PROPDLG 範例](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW 範例](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)