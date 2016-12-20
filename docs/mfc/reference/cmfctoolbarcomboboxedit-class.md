---
title: "CMFCToolBarComboBoxEdit Class | Microsoft Docs"
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
  - "CMFCComboEdit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarComboBoxEdit class"
  - "CMFCToolBarComboBoxEdit::PreTranslateMessage method"
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
caps.latest.revision: 25
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarComboBoxEdit Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

架構會使用 `CMFCToolBarComboBoxEdit` 類別建立像編輯的下拉式方塊控制項的工具列按鈕。  
  
## 語法  
  
```  
class CMFCToolBarComboBoxEdit : public CEdit  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](../Topic/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit.md)|建構 `CMFCToolBarComboBoxEdit` 物件。|  
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|包含會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前，將 Windows 訊息。  \(覆寫 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\)。|  
  
### 備註  
 從 `CMFCToolBarComboBoxEdit` 類別衍生類別來自訂它的編輯作業。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)  
  
## 需求  
 **標題:** afxtoolbarcomboboxbutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)   
 [CMFCToolBarComboBoxButton::CreateEdit](../Topic/CMFCToolBarComboBoxButton::CreateEdit.md)