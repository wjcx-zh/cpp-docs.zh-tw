---
title: "IAxWinHostWindowLic Interface | Microsoft Docs"
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
  - "IAxWinHostWindowLic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinHostWindowLic interface"
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAxWinHostWindowLic Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個介面會管理授權控制項及其主應用程式物件的方法。  
  
## 語法  
  
```  
  
interface IAxWinHostWindowLic : IAxWinHostWindow  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[CreateControlLic](../Topic/IAxWinHostWindowLic::CreateControlLic.md)|建立授權控制項並將其附加至主應用程式物件。|  
|[CreateControlLicEx](../Topic/IAxWinHostWindowLic::CreateControlLicEx.md)|建立授權控制項，將它附加至主應用程式物件並選擇性地將事件處理常式。|  
  
## 備註  
 `IAxWinHostWindowLic` 從 [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) 繼承並加入支援授權控制項的方法。  
  
 使用這個介面成員的範例參閱 [載入使用 ATL AXHost 的 ActiveX 控制項](../../atl/hosting-activex-controls-using-atl-axhost.md) 。  
  
## 需求  
 這個介面的定義是以 IDL 或 C\+\+，如下所示。  
  
|定義型別|檔案|  
|----------|--------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(也包含在 ATLBase.h\)|