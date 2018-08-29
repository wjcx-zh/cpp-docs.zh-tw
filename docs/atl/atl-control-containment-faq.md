---
title: ATL 控制項內含項目常見問題集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5de6f53ca03bbab9ca42d4140a3942244db35f7
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131501"
---
# <a name="atl-control-containment-faq"></a>ATL 控制項內含項目常見問題集

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>哪些 ATL 類別可協助 ActiveX 控制項內含項目？
ATL 的控制項裝載程式碼不需要您使用任何 ATL 類別;您可以只建立 **"AtlAxWin80"** 視窗並使用如有必要的控制項裝載 API (如需詳細資訊，請參閱**什麼是 ATL 控制項裝載 API**。 不過，下列類別讓內含項目功能更方便使用。  
  
|類別|描述|  
|-----------|-----------------|  
|[CAxWindow](../atl/reference/caxwindow-class.md)|包裝 **"AtlAxWin80"** 視窗中，提供方法，來建立視窗、 建立控制項和/或附加控制項至視窗，並擷取主機物件上的介面指標。|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|包裝 **"AtlAxWinLic80"** 視窗中，提供方法，來建立視窗、 建立控制項和/或授權的控制項附加至視窗，和擷取主機物件上的介面指標。|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|做為對話方塊資源為基礎的 ActiveX 控制項類別的基底類別。 這類控制項可以包含其他 ActiveX 控制項。|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|做為對話方塊資源為基礎的對話方塊類別的基底類別。 這類對話方塊可以包含 ActiveX 控制項。|  
|[CWindow](../atl/reference/cwindow-class.md)|提供一種方法， [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol)，這會傳回的介面指標上的控制項，指定其裝載視窗的識別碼。 此外，Windows API 的包裝函式會由`CWindow`通常讓視窗管理更容易。|  

## <a name="what-is-the-atl-control-hosting-api"></a>什麼是 ATL 控制項裝載 API？

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
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|傳回**IUnknown**在視窗中裝載之控制項的介面指標。|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|傳回**IUnknown**主機物件的介面指標連接到視窗。|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化的控制項裝載程式碼。|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|未初始化的控制項裝載程式碼。|  
  
 `HWND`中前三個函式的參數必須是現有的視窗 （幾乎） 任何型別。 如果您明確呼叫任何這些三個函式 （一般而言，您就不必），不傳遞至已經做為主機的視窗控制代碼 （如果您這樣做，現有的主物件不會釋放）。  
  
 前七個函式會呼叫[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)隱含。  
  
> [!NOTE]
>  控制項裝載 API 所構成的 ActiveX 控制項內含項目 ATL 的支援的基礎。 不過，通常很少需要直接呼叫這些函式，如果您利用或充分利用 ATL 的包裝函式類別。 如需詳細資訊，請參閱 <<c0> [ 其中 ATL 類別協助 ActiveX 控制項內含項目](which-atl-classes-facilitate-activex-control-containment-q.md)。  

## <a name="what-is-atlaxwin100"></a>什麼是 AtlAxWin100？

`AtlAxWin100` 是可協助提供 ATL 的控制項裝載功能的視窗類別名稱。 當您建立這個類別的執行個體時，視窗程序會自動使用控制項裝載 API 來建立與視窗相關聯的主機物件，並將它與您指定為視窗的標題控制項。 

## <a name="when-do-i-need-to-call-atlaxwininit"></a>何時需要呼叫 AtlAxWinInit？

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)註冊 **"AtlAxWin80"** 視窗類別 （再加上幾個自訂視窗訊息），因此必須呼叫此函式，然後再建立主視窗。 不過，您不一定需要明確地呼叫此函式，因為裝載 Api （和使用它們的類別） 通常為您呼叫此函式。 超過一次呼叫此函式沒有壞處。

## <a name="what-is-a-host-object"></a>什麼是主物件？

主應用程式物件是 COM 物件，表示 ActiveX 控制項容器的 ATL 提供特定的視窗。 主機物件存放至子類別 [容器] 視窗，讓它可以反映至控制項的訊息，它提供必要的容器介面，以供該控制項，它會公開[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)和[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)介面，可讓您設定控制項的環境。  
  
 您可以使用的主物件來設定容器的環境屬性。

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>我是否可以裝載在單一視窗中的多個控制項？

您不可以裝載在單一的 ATL 主視窗中的多個控制項。 每個主機視窗被設計來保存一個控制項 （這可讓簡單的機制來處理訊息反映和控制每個環境的屬性） 一次。 不過，如果您需要使用者看到的單一視窗中的多個控制項時，很容易建立為該視窗的子系的多個主控件 windows。

## <a name="can-i-reuse-a-host-window"></a>可以重複使用主機視窗嗎？

不建議您重複使用的主應用程式視窗。 若要確保您的程式碼的加強，您應該將繫結主應用程式視窗的單一控制項的存留期的存留的期。

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>何時需要呼叫 AtlAxWinTerm？

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)取消註冊 **"AtlAxWin80"** 視窗類別。 您應該呼叫此函式 （如果您不再需要建立主應用程式視窗） 之後所有現有的主控件 windows 皆已終結。 如果您未呼叫此函式，該視窗類別將會取消註冊自動處理序終止時。

## <a name="hosting-activex-controls-using-atl-axhost"></a>使用 ATL AXHost 裝載 ActiveX 控制項

本章節中的範例示範如何建立 AXHost 以及如何裝載使用各種 ATL 函式的 ActiveX 控制項。 它也會示範如何存取 「 控制項 」 和 「 接收事件 (使用[IDispEventImpl](../atl/reference/idispeventimpl-class.md)) 所裝載之控制項中。 此範例裝載在主視窗或子視窗中的行事曆控制項。  
  
 請注意定義`USE_METHOD`符號。 您可以變更此符號介於 1 到 8 之間的值。 符號的值會決定控制項建立的方式：  
  
-   偶數值`USE_METHOD`，若要建立主應用程式子視窗呼叫並將它轉換成控制主機。 奇數的值，程式碼會建立做為主機的子視窗。  
  
-   值`USE_METHOD`介於 1 和 4 中，存取控制項，以及接收事件的呼叫也會建立主應用程式中完成。 介於 5 到 8 之間的值查詢介面的主機，並攔截接收。  
  
 摘要如下：  
  
|USE_METHOD|主機|控制存取和事件接收|示範的函式|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|子視窗|一個步驟|CreateControlLicEx|  
|2|主視窗|一個步驟|AtlAxCreateControlLicEx|  
|3|子視窗|一個步驟|CreateControlEx|  
|4|主視窗|一個步驟|AtlAxCreateControlEx|  
|5|子視窗|多個步驟|CreateControlLic|  
|6|主視窗|多個步驟|AtlAxCreateControlLic|  
|7|子視窗|多個步驟|CreateControl|  
|8|主視窗|多個步驟|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [CAxWindow2T 類別](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic 介面](../atl/reference/iaxwinhostwindowlic-interface.md)