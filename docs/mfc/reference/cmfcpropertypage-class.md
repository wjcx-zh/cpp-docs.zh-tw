---
title: "CMFCPropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyPage class"
  - "CMFCPropertyPage::CreateObject method"
  - "CMFCPropertyPage::OnSetActive method"
  - "CMFCPropertyPage::PreTranslateMessage method"
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertyPage` 類別支援快顯功能表顯示  屬性頁上的。  
  
## 語法  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCPropertyPage::CMFCPropertyPage](../Topic/CMFCPropertyPage::CMFCPropertyPage.md)|建構 `CMFCPropertyPage` 物件。|  
|`CMFCPropertyPage::~CMFCPropertyPage`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCPropertyPage::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|`CMFCPropertyPage::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|`CMFCPropertyPage::OnSetActive`|網頁，讓使用者選取並成為使用中的頁面時，此成員函式由架構呼叫。  \(覆寫 [CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md)\)。|  
|`CMFCPropertyPage::PreTranslateMessage`|包含會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前，將 Windows 訊息。  如需詳細資訊和方法語法的詳細資訊，請參閱 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。  \(覆寫 `CPropertyPage::PreTranslateMessage`\)。|  
  
## 備註  
 `CMFCPropertyPage` 類別表示屬性工作表的個別網頁，也稱為"選項\] 對話方塊。  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) 與類別一起使用 `CMFCPropertyPage` 類別。  若要使用屬性中的功能表以 `CMFCPropertyPage` 類別呼叫，取代 `CPropertyPage` 類別的所有執行個體。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## 需求  
 **標題:** afxpropertypage.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertySheet Class](../../mfc/reference/cmfcpropertysheet-class.md)