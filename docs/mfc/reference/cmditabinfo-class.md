---
title: "CMDITabInfo Class | Microsoft Docs"
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
  - "CMDITabInfo"
  - "CMDITabInfo.CMDITabInfo"
  - "CMDITabInfo::CMDITabInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDITabInfo class"
  - "CMDITabInfo class, 建構函式"
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
caps.latest.revision: 37
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMDITabInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMDITabInfo` 類別是用來將參數加入至 [CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md) 方法。  這個類別之成員的控制項 MDI 索引標籤的群組行為。  
  
## 語法  
  
```  
class CMDITabInfo   
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMDITabInfo::CMDITabInfo`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMDITabInfo::Serialize](../Topic/CMDITabInfo::Serialize.md)|讀取或寫入這個物件從或其中的檔案。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMDITabInfo::m\_bActiveTabCloseButton;](../Topic/CMDITabInfo::m_bActiveTabCloseButton;.md)|指定 \[**關閉**\] 按鈕是否在作用中的索引標籤的標籤中。|  
|[CMDITabInfo::m\_bAutoColor](../Topic/CMDITabInfo::m_bAutoColor.md)|指定是否將 MDI 索引標籤。|  
|[CMDITabInfo::m\_bDocumentMenu](../Topic/CMDITabInfo::m_bDocumentMenu.md)|指定索引標籤群組是否會顯示開啟的文件清單或顯示捲軸按鈕的快顯功能表。|  
|[CMDITabInfo::m\_bEnableTabSwap](../Topic/CMDITabInfo::m_bEnableTabSwap.md)|指定使用者是否可以拖曳交換索引標籤的位置。|  
|[CMDITabInfo::m\_bFlatFrame](../Topic/CMDITabInfo::m_bFlatFrame.md)|指定索引標籤是否有平面框架。|  
|[CMDITabInfo::m\_bTabCloseButton](../Topic/CMDITabInfo::m_bTabCloseButton.md)|指定每個索引標籤的標籤是否顯示 \[**關閉**\] 按鈕。|  
|[CMDITabInfo::m\_bTabCustomTooltips](../Topic/CMDITabInfo::m_bTabCustomTooltips.md)|指定自訂工具提示是否已啟用。|  
|[CMDITabInfo::m\_bTabIcons](../Topic/CMDITabInfo::m_bTabIcons.md)|指定是否顯示在 MDI 索引標籤的圖示。|  
|[CMDITabInfo::m\_nTabBorderSize](../Topic/CMDITabInfo::m_nTabBorderSize.md)|指定每個索引標籤視窗的框線大小。|  
|[CMDITabInfo::m\_style](../Topic/CMDITabInfo::m_style.md)|指定索引標籤的標籤的樣式。|  
|[CMDITabInfo::m\_tabLocation](../Topic/CMDITabInfo::m_tabLocation.md)|指定索引標籤的標籤是否位於上方或下方的頁面。|  
  
## 備註  
 這個類別會指定架構建立 MDI 索引標籤群組的參數。  
  
## 範例  
 下列範例示範如何將各種成員變數的值。 `CMDITabInfo` 類別的。  
  
 [!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/CPP/cmditabinfo-class_1.cpp)]  
  
## 繼承階層架構  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## 需求  
 **標題:** afxmdiclientareawnd.h  
  
## 請參閱  
 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)   
 [MDI 索引標籤式群組](../../mfc/mdi-tabbed-groups.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)