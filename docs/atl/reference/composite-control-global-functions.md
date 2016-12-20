---
title: "Composite Control Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "複合控制項, 全域函式"
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
caps.latest.revision: 20
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Composite Control Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些函式支援分別建立對話方塊來建立，並允許裝載 ActiveX 控制項。  
  
> [!IMPORTANT]
>  下表中列出的函式不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
|||  
|-|-|  
|[AtlAxDialogBox](../Topic/AtlAxDialogBox.md)|若要從使用者提供的對話方塊樣板的強制回應對話方塊。  所產生的對話方塊中可以包含 ActiveX 控制項。|  
|[AtlAxCreateDialog](../Topic/AtlAxCreateDialog.md)|若要從使用者提供的對話方塊樣板的非強制回應對話方塊。  所產生的對話方塊中可以包含 ActiveX 控制項。|  
|[AtlAxCreateControl](../Topic/AtlAxCreateControl.md)|建立 ActiveX 控制項，將它初始化，並將它裝載在指定的視窗。|  
|[AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)|建立 ActiveX 控制項，將它初始化，將它裝載在指定的視窗，並從控制項擷取介面指標 \(或指標\)。|  
|[AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)|建立已授權的 ActiveX 控制項，將它初始化，並將它裝載在指定的視窗。|  
|[AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)|建立已授權的 ActiveX 控制項，將它初始化，將它裝載在指定的視窗，並從控制項擷取介面指標 \(或指標\)。|  
|[AtlAxAttachControl](../Topic/AtlAxAttachControl.md)|將先前建立的控制項加入至指定的視窗。|  
|[AtlAxGetHost](../Topic/AtlAxGetHost.md)|用來取得簡單介面指標到指定之視窗的容器 \(如果有的話\) 指定的控制代碼。|  
|[AtlAxGetControl](../Topic/AtlAxGetControl.md)|用來取得簡單介面指標控制項內含的所指定之視窗 \(如果有的話\) 指定的控制代碼。|  
|[AtlSetChildSite](../Topic/AtlSetChildSite.md)|初始化子網站的 **IUnknown** 。|  
|[AtlAxWinInit](../Topic/AtlAxWinInit.md)|初始化 AxWin 物件的裝載程式碼。|  
|[AtlAxWinTerm](../Topic/AtlAxWinTerm.md)|Uninitializes AxWin 物件的裝載程式碼。|  
|[AtlGetObjectSourceInterface](../Topic/AtlGetObjectSourceInterface.md)|如需物件的預設來源介面的傳回資訊。|  
  
## 請參閱  
 [函式](../../atl/reference/atl-functions.md)   
 [Composite Control Macros](../../atl/reference/composite-control-macros.md)