---
title: "CAxWindow Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAxWindowT"
  - "CAxWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 裝載 ActiveX 控制項"
  - "CAxWindow class"
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CAxWindow Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供方法來裝載 \(Host\) ActiveX 控制項的這個類別會管理這些視窗。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CAxWindow : public CWindow  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[AttachControl](../Topic/CAxWindow::AttachControl.md)|將現有的 ActiveX 控制項至 `CAxWindow` 物件。|  
|[CAxWindow](../Topic/CAxWindow::CAxWindow.md)|建構 `CAxWindow` 物件。|  
|[CreateControl](../Topic/CAxWindow::CreateControl.md)|建立 ActiveX 控制項，將它初始化，並將它裝載在 `CAxWindow` 視窗。|  
|[CreateControlEx](../Topic/CAxWindow::CreateControlEx.md)|建立 ActiveX 控制項並擷取控制項的介面指標 \(或指標\)。|  
|[GetWndClassName](../Topic/CAxWindow::GetWndClassName.md)|\(靜態\) 擷取 `CAxWindow` 物件之預先定義的類別名稱。|  
|[QueryControl](../Topic/CAxWindow::QueryControl.md)|擷取裝載 ActiveX 控制項的 **IUnknown** 。|  
|[QueryHost](../Topic/CAxWindow::QueryHost.md)|擷取物件的 `CAxWindow`**IUnknown** 指標。|  
|[SetExternalDispatch](../Topic/CAxWindow::SetExternalDispatch.md)|設定 `CAxWindow` 物件使用的外部分派介面。|  
|[SetExternalUIHandler](../Topic/CAxWindow::SetExternalUIHandler.md)|設定 `CAxWindow` 物件使用的外部 **IDocHostUIHandler** 介面。|  
  
### 運算子  
  
|||  
|-|-|  
|[\=運算子](../Topic/CAxWindow::operator%20=.md)|**HWND** 指派至現有的**CAxWindow** 物件。|  
  
## 備註  
 這個類別會提供管理裝載 ActiveX 控制項的視窗的方法。  「**AtlAxWin80"**提供載入，以 `CAxWindow`包裝。  
  
 類別 `CAxWindow` 實作為 `CAxWindowT` 類別的特製化。  此特製化宣告如下所示:  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 如果您需要變更基底類別，您可以使用 `CAxWindowT` 並指定新的基底類別當做樣板引數使用。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [ATLCON 範例](../../top/visual-cpp-samples.md)   
 [CWindow Class](../../atl/reference/cwindow-class.md)   
 [複合控制項基本概念](../../atl/atl-composite-control-fundamentals.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [控制項內含項目常見問題集](../../atl/atl-control-containment-faq.md)