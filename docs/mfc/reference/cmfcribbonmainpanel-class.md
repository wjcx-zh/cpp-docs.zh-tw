---
title: "CMFCRibbonMainPanel Class | Microsoft Docs"
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
  - "CMFCRibbonMainPanel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonMainPanel class"
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonMainPanel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作所顯示的一個功能區面板時按一下 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)。  
  
## 語法  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|預設建構函式。|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCRibbonMainPanel::Add](../Topic/CMFCRibbonMainPanel::Add.md)|將功能區項目加入至應用程式的按鈕面板的左窗格。  \(覆寫 [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md)\)。|  
|[CMFCRibbonMainPanel::AddRecentFilesList](../Topic/CMFCRibbonMainPanel::AddRecentFilesList.md)|將文字字串加入至最近使用的檔案清單功能表。|  
|[CMFCRibbonMainPanel::AddToBottom](../Topic/CMFCRibbonMainPanel::AddToBottom.md)|將功能區項目加入至功能區應用程式面板的下方窗格中。|  
|[CMFCRibbonMainPanel::AddToRight](../Topic/CMFCRibbonMainPanel::AddToRight.md)|將功能區項目加入至應用程式的按鈕面板的右窗格中。|  
|`CMFCRibbonMainPanel::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCRibbonMainPanel::GetCommandsFrame](../Topic/CMFCRibbonMainPanel::GetCommandsFrame.md)|傳回表示主要功能區面板的區域的矩形。|  
|`CMFCRibbonMainPanel::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
  
## 備註  
 當您開啟應用程式面板時，架構會顯示 `CMFCRibbonMainPanel` 。  它含有三個窗格:  
  
-   左窗格包含命令相關聯的檔案，例如 \[**開啟**\]、 \[**儲存**\]、 \[**列印**\] 和 \[**關閉**\]。  若要將命令加入至  窗格中，請呼叫 [CMFCRibbonMainPanel::Add](../Topic/CMFCRibbonMainPanel::Add.md)。  
  
-   右窗格包含修改命令在左窗格中按一下的選項。  例如，如果您按一下 ，從左窗格中的 \[**另存新檔**\] ，右邊窗格會顯示可用的檔案類型。  若要將項目加入至這個窗格，請呼叫 [CMFCRibbonMainPanel::AddToRight](../Topic/CMFCRibbonMainPanel::AddToRight.md)。  
  
-   的下方窗格包含可讓您變更應用程式的設定和關閉程式的按鈕。  若要將項目加入至這個窗格，請呼叫 [CMFCRibbonMainPanel::AddToBottom](../Topic/CMFCRibbonMainPanel::AddToBottom.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## 需求  
 **標題:** afxRibbonMainPanel.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel Class](../../mfc/reference/cmfcribbonpanel-class.md)