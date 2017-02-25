---
title: "COlePropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COlePropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePropertyPage class"
  - "自訂控制項 [MFC], 屬性"
  - "displaying properties"
  - "OLE property pages"
  - "屬性 [C++], 顯示"
  - "屬性頁, OLE"
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COlePropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用來顯示自訂控制項的屬性會有圖形介面的，類似於  對話方塊。  
  
## 語法  
  
```  
class AFX_NOVTABLE COlePropertyPage : public CDialog  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COlePropertyPage::COlePropertyPage](../Topic/COlePropertyPage::COlePropertyPage.md)|建構 `COlePropertyPage` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COlePropertyPage::GetControlStatus](../Topic/COlePropertyPage::GetControlStatus.md)|表示使用者是否修改過控制項中的值。|  
|[COlePropertyPage::GetObjectArray](../Topic/COlePropertyPage::GetObjectArray.md)|傳回屬性頁面編譯的物件陣列。|  
|[COlePropertyPage::GetPageSite](../Topic/COlePropertyPage::GetPageSite.md)|傳回指向屬性頁的 `IPropertyPageSite` 介面。|  
|[COlePropertyPage::IgnoreApply](../Topic/COlePropertyPage::IgnoreApply.md)|判斷哪個控制項都不會套用  按鈕。|  
|[COlePropertyPage::IsModified](../Topic/COlePropertyPage::IsModified.md)|表示使用者是否修改過屬性頁。|  
|[COlePropertyPage::OnEditProperty](../Topic/COlePropertyPage::OnEditProperty.md)|呼叫框架，當使用者編輯屬性。|  
|[COlePropertyPage::OnHelp](../Topic/COlePropertyPage::OnHelp.md)|呼叫框架，當使用者叫用說明。|  
|[COlePropertyPage::OnInitDialog](../Topic/COlePropertyPage::OnInitDialog.md)|呼叫框架，其在屬性頁初始化。|  
|[COlePropertyPage::OnObjectsChanged](../Topic/COlePropertyPage::OnObjectsChanged.md)|呼叫框架，而另一個 OLE 控制項，使用新的屬性，選取。|  
|[COlePropertyPage::OnSetPageSite](../Topic/COlePropertyPage::OnSetPageSite.md)|呼叫框架，當屬性架構提供頁面的網站。|  
|[COlePropertyPage::SetControlStatus](../Topic/COlePropertyPage::SetControlStatus.md)|設定會指示使用者能否旗標已修改控制項中的值。|  
|[COlePropertyPage::SetDialogResource](../Topic/COlePropertyPage::SetDialogResource.md)|設定  屬性頁的對話方塊資源。|  
|[COlePropertyPage::SetHelpInfo](../Topic/COlePropertyPage::SetHelpInfo.md)|設定  屬性頁的簡短說明文字、說明檔的名稱和它的說明內容。|  
|[COlePropertyPage::SetModifiedFlag](../Topic/COlePropertyPage::SetModifiedFlag.md)|設定指示使用者是否修改過旗標屬性頁。|  
|[COlePropertyPage::SetPageName](../Topic/COlePropertyPage::SetPageName.md)|設定 屬性頁的名稱 \(標頭\)。|  
  
## 備註  
 例如，屬性頁可能包含可以讓使用者檢視及修改控制項的標題屬性的編輯控制項。  
  
 每個自訂或庫存控制項的屬性會有必要時允許使用者檢視控制項的屬性值和修改該值的對話方塊控制項。  
  
 如需使用 `COlePropertyPage`的詳細資訊，請參閱本文 [ActiveX 控制項:屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `COlePropertyPage`  
  
## 需求  
 **Header:** afxctl.h  
  
## 請參閱  
 [MFC 範例 CIRC3](../../top/visual-cpp-samples.md)   
 [MFC TESTHELP 範例](../../top/visual-cpp-samples.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)