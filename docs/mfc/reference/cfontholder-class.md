---
title: "CFontHolder Class | Microsoft Docs"
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
  - "CFontHolder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFontHolder class"
  - "custom fonts"
  - "字型, ActiveX 控制項"
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFontHolder Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作內建的字型屬性和封裝 Windows、字型物件和 `IFont` 介面的功能。  
  
## 語法  
  
```  
class CFontHolder  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFontHolder::CFontHolder](../Topic/CFontHolder::CFontHolder.md)|建構 `CFontHolder` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFontHolder::GetDisplayString](../Topic/CFontHolder::GetDisplayString.md)|擷取容器的屬性瀏覽器中顯示的字串。|  
|[CFontHolder::GetFontDispatch](../Topic/CFontHolder::GetFontDispatch.md)|傳回的字型 `IDispatch` 介面。|  
|[CFontHolder::GetFontHandle](../Topic/CFontHolder::GetFontHandle.md)|將控制代碼傳回給 Windows 字型。|  
|[CFontHolder::InitializeFont](../Topic/CFontHolder::InitializeFont.md)|初始化 `CFontHolder` 物件。|  
|[CFontHolder::QueryTextMetrics](../Topic/CFontHolder::QueryTextMetrics.md)|擷取相關字型的資訊。|  
|[CFontHolder::ReleaseFont](../Topic/CFontHolder::ReleaseFont.md)|從 `IFont` 和 `IFontNotification` 介面不同 `CFontHolder` 物件。|  
|[CFontHolder::Select](../Topic/CFontHolder::Select.md)|選取字型資源到裝置內容中。|  
|[CFontHolder::SetFont](../Topic/CFontHolder::SetFont.md)|連接至 `IFont``CFontHolder` 介面的物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFontHolder::m\_pFont](../Topic/CFontHolder::m_pFont.md)|為 `CFontHolder` 物件的 `IFont` 介面的指標。|  
  
## 備註  
 `CFontHolder` 不具有基底類別。  
  
 使用這個類別會實作控制項的自訂字型屬性。  如需建立此屬性的詳細資訊，請參閱本文 [ActiveX 控制項:使用字型](../../mfc/mfc-activex-controls-using-fonts.md)。  
  
## 繼承階層架構  
 `CFontHolder`  
  
## 需求  
 **Header:** afxctl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPropExchange Class](../../mfc/reference/cpropexchange-class.md)