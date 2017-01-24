---
title: "CMFCFontComboBox Class | Microsoft Docs"
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
  - "CMFCFontComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFontComboBox class"
  - "CMFCFontComboBox::CompareItem method"
  - "CMFCFontComboBox::DrawItem method"
  - "CMFCFontComboBox::MeasureItem method"
  - "CMFCFontComboBox::PreTranslateMessage method"
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
caps.latest.revision: 29
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCFontComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCFontComboBox` 類別建立包含字型清單的下拉式方塊控制項。  
  
## 語法  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCFontComboBox::CMFCFontComboBox](../Topic/CMFCFontComboBox::CMFCFontComboBox.md)|建構 `CMFCFontComboBox` 物件。|  
|`CMFCFontComboBox::~CMFCFontComboBox`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCFontComboBox::CompareItem`|呼叫由架構判斷新項目的相對位置以目前的字型下拉式方塊控制項的排序的清單方塊。  \(覆寫 [CComboBox::CompareItem](../Topic/CComboBox::CompareItem.md)\)。|  
|`CMFCFontComboBox::DrawItem`|呼叫框架會在目前的字型下拉式方塊控制項中指定之項目的。  \(覆寫 [CComboBox::DrawItem](../Topic/CComboBox::DrawItem.md)\)。|  
|[CMFCFontComboBox::GetSelFont](../Topic/CMFCFontComboBox::GetSelFont.md)|擷取目前選取的字型的資訊。|  
|`CMFCFontComboBox::MeasureItem`|呼叫以告知框架視窗清單方塊的大小以目前的字型下拉式方塊控制項。  \(覆寫 [CComboBox::MeasureItem](../Topic/CComboBox::MeasureItem.md)\)。|  
|`CMFCFontComboBox::PreTranslateMessage`|包含會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前，將 Windows 訊息。  \(覆寫 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\)。|  
|[CMFCFontComboBox::SelectFont](../Topic/CMFCFontComboBox::SelectFont.md)|選取符合字型下拉式方塊中所指定之準則的字型。|  
|[CMFCFontComboBox::Setup](../Topic/CMFCFontComboBox::Setup.md)|初始化此字型下拉式方塊的項目清單。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCFontComboBox::m\_bDrawUsingFont](../Topic/CMFCFontComboBox::m_bDrawUsingFont.md)|表示要使用的字型繪製項目的目前字型下拉式方塊標記的框架。|  
  
## 備註  
 若要使用 `CMFCFontComboBox` 物件在  對話方塊中，將 `CMFCFontComboBox` 變數加入至對話方塊類別。  然後在對話方塊類別的 `OnInitDialog` 方法，請呼叫方法 [CMFCFontComboBox::Setup](../Topic/CMFCFontComboBox::Setup.md) 初始化下拉式方塊控制項中的項目清單。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## 需求  
 **標題:** afxfontcombobox.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md)