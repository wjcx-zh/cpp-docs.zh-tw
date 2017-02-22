---
title: "CPropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertyPage class"
  - "對話方塊, 索引標籤"
  - "屬性頁, CPropertyPage class"
  - "索引標籤對話方塊"
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示屬性工作表的個別網頁，也稱為"選項\] 對話方塊。  
  
## 語法  
  
```  
class CPropertyPage : public CDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPropertyPage::CPropertyPage](../Topic/CPropertyPage::CPropertyPage.md)|建構 `CPropertyPage` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPropertyPage::CancelToClose](../Topic/CPropertyPage::CancelToClose.md)|變更 \[確定\] 按鈕會關閉，而且在強制回應屬性工作表的頁面上一個無法復原的變更之後停用，取消按鈕。|  
|[CPropertyPage::Construct](../Topic/CPropertyPage::Construct.md)|建構 `CPropertyPage` 物件。  請使用 `Construct` ，如果您要指定您的參數在執行階段，或者，如果您使用陣列。|  
|[CPropertyPage::GetPSP](../Topic/CPropertyPage::GetPSP.md)|擷取視窗 [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) 結構與 `CPropertyPage` 物件。|  
|[CPropertyPage::OnApply](../Topic/CPropertyPage::OnApply.md)|呼叫，便會由架構套用現在按下時按一下 。|  
|[CPropertyPage::OnCancel](../Topic/CPropertyPage::OnCancel.md)|呼叫框架，當按一下取消按鈕。|  
|[CPropertyPage::OnKillActive](../Topic/CPropertyPage::OnKillActive.md)|呼叫框架，在目前頁面不在使用中的頁面。  在此執行資料驗證|  
|[CPropertyPage::OnOK](../Topic/CPropertyPage::OnOK.md)|呼叫，便會由架構判斷，現在時套用或關閉按鈕按一下 。|  
|[CPropertyPage::OnQueryCancel](../Topic/CPropertyPage::OnQueryCancel.md)|呼叫，便會由架構取消按鈕按下時和在移除之前發生。|  
|[CPropertyPage::OnReset](../Topic/CPropertyPage::OnReset.md)|呼叫框架，當按一下取消按鈕。|  
|[CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md)|呼叫框架，該頁面會使用中的頁面。|  
|[CPropertyPage::OnWizardBack](../Topic/CPropertyPage::OnWizardBack.md)|呼叫框架，當按一下一頁按鈕，當使用的精靈類型的屬性工作表時。|  
|[CPropertyPage::OnWizardFinish](../Topic/CPropertyPage::OnWizardFinish.md)|呼叫框架，在完成按鈕按一下 ，當使用的精靈類型的屬性工作表時。|  
|[CPropertyPage::OnWizardNext](../Topic/CPropertyPage::OnWizardNext.md)|呼叫下一個框架，當按一下  按鈕，當使用的精靈類型的屬性工作表時。|  
|[CPropertyPage::QuerySiblings](../Topic/CPropertyPage::QuerySiblings.md)|將訊息轉寄至屬性工作表的每個網頁。|  
|[CPropertyPage::SetModified](../Topic/CPropertyPage::SetModified.md)|啟用或停用套用呼叫現在按下。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPropertyPage::m\_psp](../Topic/CPropertyPage::m_psp.md)|視窗 [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) 結構。  提供對基本屬性頁參數。|  
  
## 備註  
 與標準對話方塊，您可以從每個頁面的 `CPropertyPage` 衍生類別中的屬性工作表。  若要使用 `CPropertyPage`衍生物件，請先建立 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) 物件，接著在屬性工作表" \(User Control\) 的每個網頁上的物件。  呼叫每個頁面的 [CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md) 工作表，藉由呼叫強制回應屬性工作表的 [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md) 然後顯示非強制回應屬性工作表的屬性工作表或 [CPropertySheet::Create](../Topic/CPropertySheet::Create.md) 。  
  
 您可以建立名為精靈的 \[選項\] 對話方塊的型別，其中包括使用屬性頁序列的屬性工作表透過作業步驟引導使用者的動作，例如設定裝置或建立目前通訊。  在精靈的  索引標籤的  對話方塊中，  屬性頁沒有索引標籤，然後，只有一個屬性頁一次只能看見。  此外，除了會判斷和現在應用按鈕，一個精靈類型的索引標籤對話方塊有上一頁\] 按鈕，或已完成按鈕和取消按鈕。  
  
 如需建立做為精靈之屬性工作表的詳細資訊，請參閱 [CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)。  如需使用 `CPropertyPage` 物件的詳細資訊，請參閱本文 [屬性工作表的屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## 需求  
 **Header:** afxdlgs.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL1](../../top/visual-cpp-samples.md)   
 [MFC 範例 CMNCTRL2](../../top/visual-cpp-samples.md)   
 [MFC PROPDLG 範例](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW 範例](../../top/visual-cpp-samples.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)