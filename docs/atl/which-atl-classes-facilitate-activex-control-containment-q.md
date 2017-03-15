---
title: "Which ATL Classes Facilitate ActiveX Control Containment? | Microsoft Docs"
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
  - "ActiveX 控制項容器 [C++], ATL control hosting"
  - "hosting controls using ATL"
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Which ATL Classes Facilitate ActiveX Control Containment?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 控制項的裝載程式碼不需要使用任何 ATL 類別;您可以建立 **"AtlAxWin80"** 視窗，並使用控制項裝載 API \(如需詳細資訊，請參閱 [什麼是 ATL 控制項裝載 API?](../atl/what-is-the-atl-control-hosting-api-q.md)\)。  不過，下列類別讓內含項目功能更易於使用。  
  
|類別|描述|  
|--------|--------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|包裝 **"AtlAxWin80"** 視窗，提供方法來建立視窗，建立控制項和 \(或\) 將控制項附加至視窗並擷取介面指標在主應用程式物件。|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|包裝 **"AtlAxWinLic80"** 視窗，提供方法來建立視窗，建立控制項和 \(或\) 附加授權控制項加入至  視窗和擷取介面指標在主應用程式物件。|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|做為依據對話方塊資源中的 ActiveX 控制項類別的基底類別。  這類控制項可以包含其他 ActiveX 控制項。|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|做為依據對話方塊資源的對話方塊類別的基底類別。  此對話方塊可包含 ActiveX 控制項。|  
|[CWindow](../atl/reference/cwindow-class.md)|提供方法， [GetDlgControl](../Topic/CWindow::GetDlgControl.md)，會傳回控制項的介面指標將其主視窗 ID。  此外， `CWindow` 公開的 Windows API 包裝函式縮小視窗管理更為容易。|  
  
## 請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)