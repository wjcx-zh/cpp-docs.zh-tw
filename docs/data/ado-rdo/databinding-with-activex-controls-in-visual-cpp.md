---
title: "在 Visual C++ 中使用 ActiveX 控制項進行資料繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 資料繫結"
  - "繫結控制項 [C++], ActiveX"
  - "控制項 [C++], 資料繫結"
  - "資料繫結 [C++], ActiveX 控制項"
  - "資料繫結控制項 [C++], ActiveX"
ms.assetid: afe11d2b-eefe-43ce-958d-82d3d4dee158
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual C++ 中使用 ActiveX 控制項進行資料繫結
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

資料繫結是由兩種 ActiveX 控制項來實作：資料控制項和資料繫結控制項。  
  
 **資料控制項**  
 資料控制項負責封裝資料庫查詢和擷取到的資料列集 \(Rowset\)。  Microsoft 資料控制項提供的使用者介面，包含一系列可以逐一查看資料的按鈕。  Visual C\+\+ 提供兩種資料存取技術來處理資料控制項：[ADO 和 RDO](../../data/ado-rdo/data-access-ado-and-rdo.md)。  
  
> [!IMPORTANT]
>  ADO 和 RDO 資料控制項是 Visual Studio 舊版發行的舊式技術，您目前使用的版本可能不適用。  若要使用本節中的資訊，您可能需要取得較早的版本以取得適當的控制項。  
  
 **資料繫結控制項**  
 資料繫結控制項負責展示資料。  資料繫結控制項會連接到資料控制項來接收資料，並透過各種使用者介面展示資料。  Visual C\+\+ 應用程式也可將變數繫結至資料繫結控制項的資料值集合；請參閱 [CWnd::BindProperty](../Topic/CWnd::BindProperty.md)。  
  
 如需資料繫結的詳細資訊，請參閱：  
  
-   [MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結](../../mfc/mfc-activex-controls-using-data-binding-in-an-activex-control.md)  
  
-   [資料存取：ADO 和 RDO](../../data/ado-rdo/data-access-ado-and-rdo.md)  
  
-   [ADO 資料繫結](../../data/ado-rdo/ado-databinding.md)  
  
-   [RDO 資料繫結](../../data/ado-rdo/rdo-databinding.md)  
  
-   [包裝函式類別](../../data/ado-rdo/wrapper-classes.md)  
  
-   [在 ActiveX 控制項設定事件處理常式](../../data/ado-rdo/setting-event-handlers-on-activex-controls.md)  
  
-   [錯誤截取](../../data/ado-rdo/error-trapping.md)  
  
-   [資料繫結限制](../../data/ado-rdo/limitations-of-databinding.md)  
  
## 請參閱  
 [資料繫結控制項 \(ADO 和 RDO\)](../../data/ado-rdo/data-bound-controls-ado-and-rdo.md)