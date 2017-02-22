---
title: "CSmartDockingInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSmartDockingInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSmartDockingInfo class"
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CSmartDockingInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義智慧標籤的停駐標記隨即出現。  
  
## 語法  
  
```  
class CSmartDockingInfo : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CSmartDockingInfo::CSmartDockingInfo`|預設建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSmartDockingInfo::CopyTo](../Topic/CSmartDockingInfo::CopyTo.md)|複製目前智慧標籤的內建的資訊參數傳遞至提供的 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) 物件。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CSmartDockingInfo::m\_bUseThemeColorInShading](../Topic/CSmartDockingInfo::m_bUseThemeColorInShading.md)|指定是否使用目前的佈景主題色彩架構時會顯示智慧標籤的停駐標記。|  
|[CSmartDockingInfo::m\_clrBaseBackground](../Topic/CSmartDockingInfo::m_clrBaseBackground.md)|指定智慧停駐標記基本的背景色彩。|  
|[CSmartDockingInfo::m\_clrToneDest](../Topic/CSmartDockingInfo::m_clrToneDest.md)|指定取代智慧停駐記號點陣圖的 `m_clrToneSrc` 的色彩。|  
|[CSmartDockingInfo::m\_clrToneSrc](../Topic/CSmartDockingInfo::m_clrToneSrc.md)|指定智慧停駐標記點陣圖色彩。|  
|[CSmartDockingInfo::m\_clrTransparent](../Topic/CSmartDockingInfo::m_clrTransparent.md)|其透明時，指定智慧停駐標記點陣圖色彩。|  
|[CSmartDockingInfo::m\_nCentralGroupOffset](../Topic/CSmartDockingInfo::m_nCentralGroupOffset.md)|指定智慧停駐標記的中央群組的位移從中央群組矩形的界限。|  
|[CSmartDockingInfo::m\_sizeTotal](../Topic/CSmartDockingInfo::m_sizeTotal.md)|在群組中指定所有智慧標籤的停駐標記的總大小。|  
|[CSmartDockingInfo::m\_uiMarkerBmpResID](../Topic/CSmartDockingInfo::m_uiMarkerBmpResID.md)|定義這個架構智慧型停駐標記使用未反白顯示點陣圖的資源 ID。|  
|[CSmartDockingInfo::m\_uiMarkerLightBmpResID](../Topic/CSmartDockingInfo::m_uiMarkerLightBmpResID.md)|定義這個架構智慧型停駐標記使用反白顯示點陣圖的資源 ID。|  
  
## 備註  
 這個架構內部管理智慧標籤的停駐標記。  下圖顯示標準智慧停駐標記:  
  
 ![智慧停駐的標準標記](../../mfc/reference/media/nextsdmarkers.png "nextSDmarkers")  
  
 在圖中，影像左邊顯示沒有停駐要啟用之索引標籤的中央群組智慧停駐標記。  在中間的影像顯示的右邊緣智慧停駐標記。  在右邊的影像顯示的使用停駐要啟用之索引標籤的中央群組智慧停駐標記。  中央群組智慧停駐標記有主要點陣圖和五個智慧標籤的停駐標記點陣圖。  
  
 您可以自訂智慧標籤的停駐標記下列參數:  
  
-   色彩  例如，您可以用任何使用者定義的色彩取代標記的藍色在圖形的起始點。  
  
-   透明色彩。  
  
-   一個智慧停駐的正負號位移在中央群組中從週框的框線。  
  
-   表示中央群組的主要點陣圖。  
  
-   表示規則和反白顯示智慧標籤的停駐標記的點陣圖。  
  
 下圖顯示自訂智慧標籤的停駐標記的範例:  
  
 ![智慧停駐的自訂標記](../Image/nextSDmarkersCustom.png "nextSDmarkersCustom")  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)  
  
## 需求  
 **標題:** afxDockingManager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)