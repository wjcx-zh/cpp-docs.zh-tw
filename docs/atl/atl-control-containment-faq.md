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
ms.openlocfilehash: 36ff3381447b46b28908522d65be9f34fe23addf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317392"
---
# <a name="atl-control-containment-faq"></a>ATL 控制項內含項目常見問題集

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>哪些 ATL 類別可協助 ActiveX 控制項內含項目？

ATL 的控制託管代碼不要求您使用任何 ATL 類;您可以簡單地創建一個 **「AtlAxWin80」** 視窗,並在必要時使用控制託管 API(有關詳細資訊,請參閱**什麼是 ATL 控制託管 API。** 但是,以下類使包含功能更易於使用。

|類別|描述|
|-----------|-----------------|
|[薩克斯視窗](../atl/reference/caxwindow-class.md)|包裝 **「AtlAxWin80」** 視窗,提供建立視窗、創建控制項和/或將控制件附加到視窗以及檢索主機物件上的介面指標的方法。|
|[薩克斯視窗2T](../atl/reference/caxwindow2t-class.md)|包裝 **「AtlAxWinLic80」** 視窗,提供建立視窗、創建控制項和/或將許可控制項附加到視窗以及檢索主機物件上的介面指標的方法。|
|[CCom 複合控制](../atl/reference/ccomcompositecontrol-class.md)|充當基於對話方塊資源的 ActiveX 控制項類別的基類。 此類控件可以包含其他 ActiveX 控制件。|
|[CAx 對話](../atl/reference/caxdialogimpl-class.md)|充當基於對話框資源的對話框類的基類。 此類對話框可以包含 ActiveX 控制件。|
|[CWindow](../atl/reference/cwindow-class.md)|提供一種方法[GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol),該方法將在控件上返回介面指標,給定其主機視窗的 ID。 此外,通常通過打開的`CWindow`Windows API 包裝器使視窗管理更加容易。|

## <a name="what-is-the-atl-control-hosting-api"></a>什麼是 ATL 控制項裝載 API？

ATL 的控制宿主 API 是允許任何視窗充當 ActiveX 控制容器的功能集。 這些函數可以靜態或動態地連結到您的專案中,因為它們可作為原始程式碼提供,並由 ATL90.dll 公開。 下表列出了控制託管功能。

|函式|描述|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|建立主機物件,將其連接到提供的視窗,然後附加現有控制項。|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|建立主機物件,將其連接到提供的視窗,然後載入控制項。|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|建立授權的 ActiveX 控制檔,初始化它,並將其託管在指定的視窗中,類似於[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)。|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|創建主機物件,將其連接到提供的視窗,然後載入控制項(還允許設置事件接收器)。|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|建立授權的 ActiveX 控制檔,初始化它,並將其託管在指定的視窗中,類似於[AtlAxCreateControllic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)。|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|從對話框資源建立無模式對話框並返回視窗句柄。|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|從對話框資源創建模式對話方塊。|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|返回託管在視窗中的控制項的**I 未知**介面指標。|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|返回連接到視窗的主機物件的**I 未知**介面指標。|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|初始化控制項託管代碼。|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|取消初始化控制項託管代碼。|

前`HWND`三個函數中的參數必須是(幾乎)任何類型的現有視窗。 如果顯式調用這三個函數中的任何一個(通常,您不必這樣做),則不要將句柄傳遞給已充當主機的視窗(如果這樣做,則不會釋放現有主機物件)。

前七個函數隱式調用[AtlAxWininit。](reference/composite-control-global-functions.md#atlaxwininit)

> [!NOTE]
> 控制託管 API 構成了 ATL 支援 ActiveX 控制遏制的基礎。 但是,如果您利用或充分利用 ATL 的包裝類,通常不需要直接調用這些函數。 有關詳細資訊,請參閱哪些[ATL 類有助於 ActiveX 控制遏制](which-atl-classes-facilitate-activex-control-containment-q.md)。

## <a name="what-is-atlaxwin100"></a>什麼是 AtlAxWin100？

`AtlAxWin100`是有助於提供 ATL 控制託管功能的視窗類的名稱。 創建此類的實例時,視窗過程將自動使用控制項宿主 API 創建與視窗關聯的主機物件,並使用指定為視窗標題的控制項載入該物件。

## <a name="when-do-i-need-to-call-atlaxwininit"></a>何時需要呼叫 AtlAxWinInit？

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)註冊 **「AtlAxWin80」** 視窗類(加上幾個自定義視窗訊息),因此在嘗試創建主機視窗之前必須調用此函數。 但是,您並不總是需要顯式調用此函數,因為託管 API(以及使用它們的類)通常為您調用此函數。 多次調用此函數沒有壞處。

## <a name="what-is-a-host-object"></a>什麼是主物件？

主機物件是表示 ATL 為特定視窗提供的 ActiveX 控制容器的 COM 物件。 主機物件對容器視窗進行子類化,以便它可以向控件反映消息,它提供了控制項使用的必要容器介面,並公開[IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md)和[IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md)介面,以允許您配置控制項的環境。

可以使用主機物件設置容器的環境屬性。

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>我可以在單一視窗中裝載多個控制項嗎？

不可能在單個 ATL 主機視窗中承載多個控制項。 每個主機視窗都設計為一次完全保留一個控制項(這允許一個簡單的機制來處理消息反射和每個控制項的環境屬性)。 但是,如果需要使用者在單個視窗中看到多個控制項,則創建多個主機視窗作為該視窗的子級是件簡單的事情。

## <a name="can-i-reuse-a-host-window"></a>我可以重複使用主機視窗嗎？

不建議您重複使用主機視窗。 為了確保代碼的魯棒性,應將主機視窗的存留期與單個控制項的存留期綁定。

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>何時需要呼叫 AtlAxWinTerm？

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)取消註冊 **「AtlAxWin80」** 視窗類。 在銷毀所有現有主機視窗后,應調用此函數(如果不再需要創建主機視窗)。 如果不調用此函數,則進程終止時將自動取消註冊視窗類。

## <a name="hosting-activex-controls-using-atl-axhost"></a>使用 ATL AXHost 裝載 ActiveX 控制項

本節中的範例展示如何建立 AXHost 以及如何使用各種 ATL 函數託管 ActiveX 控制件。 它還演示如何從託管的控制項存取控制件和接收器事件(使用[IDispEventImpl)。](../atl/reference/idispeventimpl-class.md) 該示例在主視窗中或子視窗中承載"日曆"控制件。

請注意符號的定義`USE_METHOD`。 您可以更改此符號的值,以介於 1 和 8 之間。 符號的值決定如何建立控制項:

- 對於 偶數`USE_METHOD`值 ,創建主機子類的調用將視窗轉換為控制項主機。 對於奇數值,代碼將創建充當主機的子視窗。

- 對於`USE_METHOD`介於 1 和 4 之間的值,在同時創建主機的調用中完成對事件的控制和下沉的訪問。 值介於 5 和 8 之間,查詢主機的介面並掛接接收器。

摘要如下：

|USE_METHOD|Host|控制存取和事件下沉|簡報功能|
|-----------------|----------|--------------------------------------|---------------------------|
|1|子視窗|一步|建立控制|
|2|主視窗|一步|AtlAxCreateControlLicEx|
|3|子視窗|一步|建立控制Ex|
|4|主視窗|一步|AtlAxCreateControlEx|
|5|子視窗|多個步驟|建立控制|
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
[IAxwinHost 視窗介面](../atl/reference/iaxwinhostwindowlic-interface.md)
