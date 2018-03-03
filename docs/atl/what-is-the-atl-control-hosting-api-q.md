---
title: "什麼是 ATL 控制項裝載應用程式開發介面？ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e985ffd3b514feec81f4fee540a95792eb3658e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-the-atl-control-hosting-api"></a>什麼是 ATL 控制項裝載應用程式開發介面？
ATL 的控制項裝載應用程式開發介面是可做為 ActiveX 控制項容器的任何視窗函式的集合。 這些函式可以是靜態或動態連結至您的專案，因為它們都可做為原始碼和 ATL90.dll 所公開。 下表所列出的控制項裝載函式。  
  
|功能|描述|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|建立主機物件，請將它連接至提供的視窗，然後附加現有的控制項。|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|建立主機物件，請將它連接至提供的視窗，然後載入控制項。|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|建立授權的 ActiveX 控制項、 初始化，然後將它裝載於指定的視窗，類似於[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)。|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|建立主機物件、 將它連接至提供的視窗，然後載入控制項 （也可讓事件接收器設定）。|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|建立授權的 ActiveX 控制項、 初始化，然後將它裝載於指定的視窗，類似於[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)。|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|建立從對話方塊資源的非強制回應對話方塊，並傳回視窗控制代碼。|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|建立強制回應對話方塊中，從對話方塊資源。|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|傳回**IUnknown**裝載在視窗中控制項的介面指標。|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|傳回**IUnknown**主機物件的介面指標連接到視窗。|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化的控制項裝載程式碼。|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|未初始化的控制項裝載程式碼。|  
  
 `HWND`中前三個函式的參數必須是現有的視窗 （幾乎） 任何型別。 如果您明確呼叫任何這三個功能 （一般而言，您不需要），不要將控制代碼傳遞給已經做為主機的視窗 （如果您這樣做，現有的主機物件將不會釋放）。  
  
 前七個函式呼叫[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)隱含。  
  
> [!NOTE]
>  控制項裝載應用程式開發介面會形成 ATL 的 ActiveX 控制項內含項目支援的基礎。 不過，通常沒有幾乎不需要直接呼叫這些函式，如果您利用或充分利用 ATL 的包裝函式類別。 如需詳細資訊，請參閱[的 ATL 類別簡化 ActiveX 控制項內含項目](which-atl-classes-facilitate-activex-control-containment-q.md)。  
  
## <a name="see-also"></a>請參閱  
 [控制項內含項目常見問題集](which-atl-classes-facilitate-activex-control-containment-q.md)
