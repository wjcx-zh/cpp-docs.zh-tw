---
title: MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結
ms.date: 11/19/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: 3f16ea3ad77c676695a9d5ca6e2deb10637de455
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621189"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結

ActiveX 控制項的其中一個更強大的用法是資料系結，可讓控制項的屬性與資料庫中的特定欄位系結。 當使用者修改此系結屬性中的資料時，控制項會通知資料庫，並要求更新記錄欄位。 然後，資料庫會通知控制項要求成功或失敗。

>[!IMPORTANT]
> ActiveX 是不應該用於新開發的舊版技術。 如需取代 ActiveX 之新式技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

本文涵蓋您工作的控制端。 與資料庫進行資料系結互動是控制容器的責任。 您在容器中管理資料庫互動的方式已超出本檔的範圍。 本文的其餘部分將說明如何準備控制項以進行資料系結。

![資料&#45;繫結控制項的概念圖](../mfc/media/vc374v1.gif "資料&#45;繫結控制項的概念圖") <br/>
資料繫結控制項的概念圖

`COleControl`類別提供兩個成員函式，讓資料系結成為簡單的程式來執行。 第一個函式[BoundPropertyRequestEdit](reference/colecontrol-class.md#boundpropertyrequestedit)是用來要求變更屬性值的許可權。 [BoundPropertyChanged](reference/colecontrol-class.md#boundpropertychanged)是第二個函式，會在屬性值成功變更後呼叫。

本文章涵蓋下列主題：

- [建立可系結的內建屬性](#vchowcreatingbindablestockproperty)

- [建立可系結的 Get/Set 方法](#vchowcreatingbindablegetsetmethod)

## <a name="creating-a-bindable-stock-property"></a><a name="vchowcreatingbindablestockproperty"></a>建立可系結的內建屬性

雖然您可能會想要可系結的[get/set 方法](#vchowcreatingbindablegetsetmethod)，但還是可以建立資料系結的庫存屬性。

> [!NOTE]
> 根據預設，庫存屬性具有 `bindable` 和 `requestedit` 屬性。

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>使用加入屬性 Wizard 加入可系結的內建屬性

1. 使用[MFC ActiveX 控制項 Wizard](reference/mfc-activex-control-wizard.md)來開始專案。

1. 以滑鼠右鍵按一下控制項的介面節點。

   這會開啟快捷方式功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入屬性**]。

1. 從 [**屬性名稱**] 下拉式清單中選取其中一個專案。 例如，您可以選取 [**文字**]。

   因為**Text**是內建屬性，所以已檢查可系**結和** **requestedit**屬性。

1. 從 [ **IDL 屬性**] 索引標籤中選取下列核取方塊： **displaybind**和**defaultbind** ，將屬性加入至專案中的屬性定義。IDL 檔案。 這些屬性會讓使用者看見控制項，並讓 stock 屬性成為預設可系結屬性。

此時，您的控制項可以顯示資料來源中的資料，但是使用者將無法更新資料欄位。 如果您想要讓控制項也能夠更新資料，請變更 OnOcmCommand 函式， `OnOcmCommand` [OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md)使其看起來如下：

[!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

您現在可以建立專案，這會註冊控制項。 當您在對話方塊中插入控制項時，將會加入**資料欄位**和**資料來源**屬性，而且您現在可以選取要在控制項中顯示的資料來源和欄位。

## <a name="creating-a-bindable-getset-method"></a><a name="vchowcreatingbindablegetsetmethod"></a>建立可系結的 Get/Set 方法

除了資料系結的 get/set 方法之外，您也可以建立可系結的內建[屬性](#vchowcreatingbindablestockproperty)。

> [!NOTE]
> 此程式假設您有子類別化 Windows 控制項的 ActiveX 控制項專案。

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>若要使用加入屬性 Wizard 來新增可系結的 get/set 方法

1. 載入控制項專案。

1. 在 [**控制項設定**] 頁面上，為控制項的子類別選取視窗類別。 例如，您可能會想要將編輯控制項設為子類別。

1. 載入控制項專案。

1. 以滑鼠右鍵按一下控制項的介面節點。

   這會開啟快捷方式功能表。

1. 從快捷方式功能表按一下 [**新增**]，然後按一下 [**加入屬性**]。

1. 在 [**屬性名稱**] 方塊中輸入屬性名稱。 在 `MyProp` 此範例中使用。

1. 從 [**屬性類型**] 下拉式清單方塊中選取資料類型。 針對此範例，請使用**short** 。

1. 在 [實作類型] **** 中，按一下 [Get/Set 方法] ****。

1. 從 [IDL 屬性] 索引標籤中選取下列核取方塊： [可系結]、[ **requestedit**]、[ **displaybind**] 和 [ **defaultbind** **]，將**屬性加入至專案中的屬性定義。IDL 檔案。 這些屬性會讓使用者看見控制項，並讓 stock 屬性成為預設可系結屬性。

1. 按一下 [完成] 。

1. 修改函式的主體， `SetMyProp` 使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#2](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. 傳遞至和函式的參數 `BoundPropertyChanged` `BoundPropertyRequestEdit` 是屬性的 dispid，這是傳遞給中屬性（property）之 id （）屬性（attribute）的參數（property）。IDL 檔案。

1. 修改[OnOcmCommand](mfc-activex-controls-subclassing-a-windows-control.md)函式，使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#1](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. 修改函式， `OnDraw` 使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#3](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. 在標頭檔的 [public] 區段中，您的控制項類別的標頭檔中，加入下列成員變數的定義（函數）：

   [!code-cpp[NVC_MFC_AxData#4](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. 使下面這一行成為函式中的最後一行 `DoPropExchange` ：

   [!code-cpp[NVC_MFC_AxData#5](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. 修改函式， `OnResetState` 使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#6](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. 修改函式， `GetMyProp` 使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#7](codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

您現在可以建立專案，這會註冊控制項。 當您在對話方塊中插入控制項時，將會加入**資料欄位**和**資料來源**屬性，而且您現在可以選取要在控制項中顯示的資料來源和欄位。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
