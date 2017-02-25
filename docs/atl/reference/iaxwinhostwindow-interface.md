---
title: "IAxWinHostWindow Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAxWinHostWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinHostWindow interface"
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# IAxWinHostWindow Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個介面會管理控制項和其裝載物件的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
interface IAxWinHostWindow : IUnknown  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[AttachControl](../Topic/IAxWinHostWindow::AttachControl.md)|將現有的控制項至主應用程式物件。|  
|[CreateControl](../Topic/IAxWinHostWindow::CreateControl.md)|建立控制項並將其附加至主應用程式物件。|  
|[CreateControlEx](../Topic/IAxWinHostWindow::CreateControlEx.md)|建立控制項，將它附加至主應用程式物件並選擇性地將事件處理常式。|  
|[QueryControl](../Topic/IAxWinHostWindow::QueryControl.md)|傳回介面指標至裝載的控制項。|  
|[SetExternalDispatch](../Topic/IAxWinHostWindow::SetExternalDispatch.md)|設定外部 `IDispatch` 介面。|  
|[SetExternalUIHandler](../Topic/IAxWinHostWindow::SetExternalUIHandler.md)|設定外部 `IDocHostUIHandlerDispatch` 介面。|  
  
## 備註  
 這個介面是由裝載物件的 ATL 的 ActiveX 控制項公開 \(Expose\)。  裝載時， Web 瀏覽器後，請呼叫的方法以建立和 \(或\) 將控制項附加至主應用程式物件，從所裝載控制項取得介面，或設定外部分配介面 \(Dispinterface\) 或 UI 處理常式使用。  
  
## 需求  
 這個介面的定義是以 IDL 或 C\+\+，如下所示。  
  
|定義型別|檔案|  
|----------|--------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(也包含在 ATLBase.h\)|  
  
## 請參閱  
 [IAxWinAmbientDispatch Interface](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../Topic/CAxWindow::QueryHost.md)   
 [AtlAxGetHost](../Topic/AtlAxGetHost.md)