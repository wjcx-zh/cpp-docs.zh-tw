---
title: ATL 控制項內含項目常見問題集
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 693617589f157d352972485396777cec587a5b8f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352696"
---
# <a name="atl-control-containment-faq"></a>ATL 控制項內含項目常見問題集

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>哪些 ATL 類別可協助 ActiveX 控制項內含項目？

ATL 的控制項裝載程式碼不會要求您使用任何 ATL 類別;您可以直接建立「 **AtlAxWin80** 」視窗，並視需要使用控制項裝載 API (如需詳細資訊，請參閱 **什麼是 ATL 控制項裝載 api**。 但是，下列類別讓內含專案功能更容易使用。

|類別|說明|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|包裝 **"AtlAxWin80"** 視窗，提供建立視窗、建立控制項及/或將控制項附加至視窗，以及在主機物件上取得介面指標的方法。|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|包裝 **"AtlAxWinLic80"** 視窗，提供建立視窗、建立控制項及/或將授權的控制項附加至視窗，以及在主機物件上取得介面指標的方法。|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|作為根據對話方塊資源的 ActiveX 控制項類別的基類。 這類控制項可以包含其他 ActiveX 控制項。|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|作為根據對話方塊資源之對話方塊類別的基類。 這類對話方塊可包含 ActiveX 控制項。|
|[CWindow](../atl/reference/cwindow-class.md)|提供方法 [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol)，這個方法會傳回控制項上的介面指標，並指定其主機視窗的識別碼。 此外，公開的 Windows API 包裝函式 `CWindow` 通常讓視窗管理更容易。|

## <a name="what-is-the-atl-control-hosting-api"></a>什麼是 ATL 控制項裝載 API？

ATL 的控制項裝載 API 是一組函式，可讓任何視窗作為 ActiveX 控制項容器。 這些函式可以靜態或動態方式連結至您的專案，因為它們是以原始程式碼的形式提供，而且是由 ATL90.dll 所公開。 下表列出控制項裝載函數。

|函式|說明|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|建立主機物件、將它連接到提供的視窗，然後附加現有的控制項。|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|建立主機物件、將它連接到提供的視窗，然後載入控制項。|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載于指定的視窗中，類似于 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)。|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|建立主機物件、將它連接到提供的視窗，然後載入控制項 (也允許設定) 的事件接收器。|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|建立授權的 ActiveX 控制項、將它初始化，然後將它裝載于指定的視窗中，類似于 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)。|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|從對話方塊資源建立非強制回應對話方塊，並傳回視窗控制碼。|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|從對話方塊資源建立強制回應對話方塊。|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|傳回裝載于視窗中之控制項的 **IUnknown** 介面指標。|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|傳回連接至視窗之主機物件的 **IUnknown** 介面指標。|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化控制項裝載程式碼。|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|取消初始化控制項裝載程式碼。|

`HWND`前三個函式中的參數必須是 (幾乎) 任何類型的現有視窗。 如果您明確地呼叫這三個函式中的任一個 (通常不需要) ，也不需要將控制碼傳遞至已作為主控制項的視窗 (如果這樣做，就不會) 釋放現有的主物件。

前七個函式會以隱含方式呼叫 [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) 。

> [!NOTE]
> 控制項裝載 API 形成 ATL 對 ActiveX 控制項內含專案的支援基礎。 但是，如果您利用或充分利用 ATL 的包裝函式類別，通常不需要直接呼叫這些函式。 如需詳細資訊，請參閱 [哪些 ATL 類別可加速 ActiveX 控制項](#which-atl-classes-facilitate-activex-control-containment)內含專案。

## <a name="what-is-atlaxwin100"></a>什麼是 AtlAxWin100？

`AtlAxWin100` 是視窗類別的名稱，可協助提供 ATL 的控制項裝載功能。 當您建立這個類別的實例時，視窗程式會自動使用控制項裝載 API 來建立與視窗相關聯的主控制項物件，並使用您指定為視窗標題的控制項載入它。

## <a name="when-do-i-need-to-call-atlaxwininit"></a>何時需要呼叫 AtlAxWinInit？

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) 會註冊 **"AtlAxWin80"** 視窗類別 (加上幾個自訂視窗訊息) 因此，必須先呼叫此函式，然後再嘗試建立主視窗。 不過，您不一定需要明確地呼叫此函式，因為裝載 Api (和使用它們的類別) 通常會為您呼叫此函式。 呼叫此函式不會有一次以上的傷害。

## <a name="what-is-a-host-object"></a>什麼是主物件？

主物件是 COM 物件，代表特定視窗的 ATL 所提供的 ActiveX 控制項容器。 主機物件會將容器視窗子類別化，讓它能夠反映控制項的訊息，它會提供控制項所要使用的必要容器介面，並公開 [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) 和 [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) 介面，讓您設定控制項的環境。

您可以使用主機物件來設定容器的環境屬性。

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>我可以在單一視窗中裝載多個控制項嗎？

在單一 ATL 主控制項視窗中不能裝載多個控制項。 每個主控制項視窗的設計是一次只保留一個控制項 (如此一來，就能使用簡單的機制來處理訊息反映和個別控制的環境屬性) 。 但是，如果您需要使用者在單一視窗中查看多個控制項，請將多個主視窗建立為該視窗的子系，是很簡單的事。

## <a name="can-i-reuse-a-host-window"></a>我可以重複使用主機視窗嗎？

不建議您重複使用主機視窗。 為了確保程式碼的穩定性，您應該將主機視窗的存留期與單一控制項的存留期系結。

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>何時需要呼叫 AtlAxWinTerm？

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) 會取消註冊 **"AtlAxWin80"** 視窗類別。 如果您不再需要在所有現有的主機視窗終結之後建立主機視窗) ，您應該呼叫此函式 (。 如果您未呼叫此函式，則會在進程終止時自動取消註冊視窗類別。

## <a name="hosting-activex-controls-using-atl-axhost"></a>使用 ATL AXHost 裝載 ActiveX 控制項

本章節中的範例說明如何建立 AXHost，以及如何使用各種 ATL 函數來裝載 ActiveX 控制項。 它也會示範如何使用 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) 從裝載的控制項存取控制項和接收事件 (。 此範例會在主視窗或子視窗中裝載行事曆控制項。

請注意符號的定義 `USE_METHOD` 。 您可以變更此符號的值，以便在1和8之間變化。 符號的值會決定要如何建立控制項：

- 針對的偶數值 `USE_METHOD` ，建立主機子類別的呼叫會將視窗子類別化，並將它轉換成控制項主控制項。 若為奇數值，程式碼會建立做為主機的子視窗。

- `USE_METHOD`若為介於1和4之間的值，則會在也會建立主控制項的呼叫中完成對控制項和事件接收的存取。 介於5和8之間的值會查詢介面的主機，並連結接收器。

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

[控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T 類別](../atl/reference/caxwindow2t-class.md)<br/>
[IAxWinHostWindowLic 介面](../atl/reference/iaxwinhostwindowlic-interface.md)
