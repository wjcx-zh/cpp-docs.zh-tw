---
title: "CMFCRibbonQuickAccessToolBarDefaultState Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonQuickAccessToolBarDefaultState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonQuickAccessToolBarDefaultState class"
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCRibbonQuickAccessToolBarDefaultState Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理快速存取工具列的預設狀態功能區列上的 Helper 類別 \([CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)\) 上。  
  
## 語法  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState.md)|建構 `CMFCRibbonQuickAccessToolbarDefaultState` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand.md)|將命令加入至快速存取工具列的預設狀態。  這不會變更工具列。|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom.md)|複製快速存取工具列複製到另一個。|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll.md)|從快速存取工具列移除所有命令。  這不會變更工具列。|  
  
## 備註  
 在您建立應用程式的快速存取工具列時，首先呼叫 [CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md)建議您將其預設狀態。  當使用者在應用程式中 \[**選項**\] 對話方塊時， \[**自訂**\] 頁面上按一下  按鈕 \[**重設**\] 這種預設狀態還原。  
  
## 繼承階層架構  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## 範例  
 下列範例示範如何建構物件 `CMFCRibbonQuickAccessToolbarDefaultState` 類別以及如何將命令加入至快速存取工具列的預設狀態。  
  
 [!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/CPP/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## 需求  
 **標題:** afxribbonquickaccesstoolbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md)