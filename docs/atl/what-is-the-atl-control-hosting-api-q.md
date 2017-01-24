---
title: "What Is the ATL Control-Hosting API? | Microsoft Docs"
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
  - "API [C++], 裝載"
  - "control-hosting API"
  - "控制項 [ATL], 裝載 API"
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
caps.latest.revision: 15
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# What Is the ATL Control-Hosting API?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 控制項的裝載 API 是允許所有視窗為 ActiveX 控制項容器的一組函式。  這些函式可以靜態或動態方式連結至您的專案中，因為它們可做為原始程式碼以及 ATL90.dll 公開。  控制項載入函式在下表中列出。  
  
|Function|描述|  
|--------------|--------|  
|[AtlAxAttachControl](../Topic/AtlAxAttachControl.md)|建立主應用程式物件，將它連接至提供的視窗，然後將現有的控制項。|  
|[AtlAxCreateControl](../Topic/AtlAxCreateControl.md)|建立主應用程式物件，將它連接至提供的視窗，然後載入控制項。|  
|[AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)|建立已授權的 ActiveX 控制項，將它初始化，並將它裝載在指定的視窗，類似於 [AtlAxCreateControl](../Topic/AtlAxCreateControl.md)。|  
|[AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)|建立主應用程式物件，將它連接至提供的視窗，然後載入控制項 \(也允許事件接收所設定\)。|  
|[AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)|建立已授權的 ActiveX 控制項，將它初始化，並將它裝載在指定的視窗，類似於 [AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)。|  
|[AtlAxCreateDialog](../Topic/AtlAxCreateDialog.md)|若要從對話方塊資源中的非強制回應對話方塊並傳回視窗控制代碼。|  
|[AtlAxDialogBox](../Topic/AtlAxDialogBox.md)|若要從對話方塊資源的強制回應對話方塊。|  
|[AtlAxGetControl](../Topic/AtlAxGetControl.md)|傳回在視窗中裝載控制項的 **IUnknown** 介面指標。|  
|[AtlAxGetHost](../Topic/AtlAxGetHost.md)|傳回連接的主應用程式物件的 **IUnknown** 介面指標至視窗。|  
|[AtlAxWinInit](../Topic/AtlAxWinInit.md)|初始化控制項裝載程式碼。|  
|[AtlAxWinTerm](../Topic/AtlAxWinTerm.md)|Uninitializes 控制項裝載程式碼。|  
  
 在前三 `HWND` 函式的參數必須是現有的視窗 \(\) 幾乎任何型別。  如果您明確呼叫這三個函式都 \(通常，您不需要\)，請勿將控制代碼已經為裝載的視窗 \(如果您，現有的主應用程式物件將不會釋放\)。  
  
 前七個函式呼叫隱含 [AtlAxWinInit](../Topic/AtlAxWinInit.md) 。  
  
> [!NOTE]
>  控制項裝載 API 以 ATL 的支援的基礎 ActiveX 控制項內含項目。  不過，如果您使用或，以充分利用 ATL 的包裝函式類別，通常沒有必要直接呼叫這些函式。  如需詳細資訊，請參閱 [哪個 ATL 類別有助於 ActiveX 控制項內含項目?](../atl/which-atl-classes-facilitate-activex-control-containment-q.md)。  
  
## 請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)