---
title: 什麼是 ATL 控制項裝載 API？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc85c7ca47d5d1226ffc3089e01c0755ef6c6ac
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850549"
---
# <a name="what-is-the-atl-control-hosting-api"></a>什麼是 ATL 控制項裝載 API？
ATL 的控制項裝載 API 是可做為 ActiveX 控制項容器的任何視窗的函式集。 這些函式可以是靜態或動態連結至您的專案，因為它們都可以以原始程式碼和 ATL90.dll 所公開。 下表詳列的控制項裝載函式。  
  
|功能|描述|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|建立主應用程式物件、 將它連線到提供的視窗中，則會附加現有的控制項。|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|建立主應用程式物件、 將它連線到提供的視窗，然後載入控制項。|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|建立授權的 ActiveX 控制項，它初始化，並將它裝載於指定的視窗，類似於[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)。|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|建立主應用程式物件、 將它連線到提供的視窗，然後載入控制項 （也可讓事件接收器設定）。|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|建立授權的 ActiveX 控制項，它初始化，並將它裝載於指定的視窗，類似於[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)。|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|從對話方塊資源會建立非強制回應對話方塊，並傳回視窗控制代碼。|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|建立強制回應對話方塊中，從對話方塊資源。|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|傳回`IUnknown`在視窗中裝載之控制項的介面指標。|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|傳回`IUnknown`主機物件的介面指標連接到視窗。|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化的控制項裝載程式碼。|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|未初始化的控制項裝載程式碼。|  
  
 `HWND`中前三個函式的參數必須是現有的視窗 （幾乎） 任何型別。 如果您明確呼叫任何這些三個函式 （一般而言，您就不必），不傳遞至已經做為主機的視窗控制代碼 （如果您這樣做，現有的主物件不會釋放）。  
  
 前七個函式會呼叫[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)隱含。  
  
> [!NOTE]
>  控制項裝載 API 所構成的 ActiveX 控制項內含項目 ATL 的支援的基礎。 不過，通常很少需要直接呼叫這些函式，如果您利用或充分利用 ATL 的包裝函式類別。 如需詳細資訊，請參閱 <<c0> [ 其中 ATL 類別協助 ActiveX 控制項內含項目](which-atl-classes-facilitate-activex-control-containment-q.md)。  
  
## <a name="see-also"></a>另請參閱  
 [控制項內含項目常見問題集](which-atl-classes-facilitate-activex-control-containment-q.md)
