---
title: MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結
ms.date: 09/12/2018
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
ms.openlocfilehash: 54cfbc6d31c0c86163400df691dec47e0c093d36
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603654"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結

ActiveX 控制項的功能更強大的用途之一是資料繫結，可讓資料庫中的特定欄位繫結控制項的屬性。 當使用者修改這個繫結的屬性中的資料時，控制會通知資料庫和要求，更新資料錄的欄位。 然後資料庫就會通知控制的成功或失敗的要求。

>[!IMPORTANT]
> ActiveX 是舊版的技術，不應用於新的開發。 如需有關取代 ActiveX 的現代技術的詳細資訊，請參閱[ActiveX 控制項](activex-controls.md)。

本文章涵蓋您的工作的控制項部分。 實作與資料庫的資料繫結互動是控制項容器的責任。 您在容器中管理的資料庫互動的方式已超出本文件的範圍。 本文的其餘部分會說明如何準備資料繫結的控制項。

![資料的概念圖&#45;繫結控制項](../mfc/media/vc374v1.gif "vc374v1")的資料繫結控制項的概念圖

`COleControl`類別提供兩個成員函式，讓資料繫結來實作簡單的程序。 第一個函式中， [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit)，用來要求權限可變更屬性值。 [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged)，第二個函式，呼叫後已成功變更屬性值。

本文章涵蓋下列主題：

- [建立可繫結的內建屬性](#vchowcreatingbindablestockproperty)

- [建立可繫結的 Get/Set 方法](#vchowcreatingbindablegetsetmethod)

##  <a name="vchowcreatingbindablestockproperty"></a> 建立可繫結的內建屬性

您可建立資料繫結的內建屬性，雖然很有可能會想[可繫結的 get/set 方法](#vchowcreatingbindablegetsetmethod)。

> [!NOTE]
>  內建屬性具有`bindable`和`requestedit`預設屬性。

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>若要新增的可繫結的內建屬性，使用 加入屬性精靈

1. 開始專案，使用[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)。

1. 以滑鼠右鍵按一下您的控制項的介面節點。

   這會開啟快顯功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

1. 選取其中一個項目**屬性名稱**下拉式清單。 例如，您可以選取**文字**。

   因為**文字**已內建的屬性，**可繫結**並**requestedit**屬性已經過檢查。

1. 選取下列核取方塊，從**IDL 屬性**索引標籤： **displaybind**並**defaultbind**將屬性新增至專案中的屬性定義。IDL 檔案。 這些屬性讓使用者可看見控制項，且必須內建屬性的預設可繫結屬性。

此時，您的控制項可以顯示資料來源的資料，但使用者將無法更新資料欄位。 如果您想您也可以更新資料、 變更的控制項`OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)看起來像這樣的函式：

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

您現在可以建置專案，將會註冊該控制項。 當您在對話方塊中，插入控制項**資料欄位**並**資料來源**將已加入的屬性，而且您現在可以選取資料來源，以及要在控制項中顯示的欄位。

##  <a name="vchowcreatingbindablegetsetmethod"></a> 建立可繫結的 Get/Set 方法

除了資料繫結至的 get/set 方法，您也可以建立[可繫結的內建屬性](#vchowcreatingbindablestockproperty)。

> [!NOTE]
>  此程序假設您有專案子類別化 Windows 控制項的 ActiveX 控制項。

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>若要加入使用 [新增屬性精靈] 可繫結的 get/set 方法

1. 載入控制項專案。

1. 在 **控制設定**頁面上，選取 子類別化控制項的視窗類別。 比方說，您可能想要子類別化編輯控制項。

1. 載入控制項專案。

1. 以滑鼠右鍵按一下您的控制項的介面節點。

   這會開啟快顯功能表。

1. 從快顯功能表中，按一下**新增**，然後按一下**加入屬性**。

1. 輸入中的屬性名稱**屬性名稱** 方塊中。 使用`MyProp`此範例中。

1. 選取資料類型從**屬性的型別**下拉式清單方塊。 使用**簡短**此範例中。

1. 在 [實作類型] 中，按一下 [Get/Set 方法] 。

9. 從 [IDL 屬性] 索引標籤中選取下列核取方塊：**可繫結**， **requestedit**， **displaybind**，以及**defaultbind**新增要在專案的屬性定義的屬性。IDL 檔案。 這些屬性讓使用者可看見控制項，且必須內建屬性的預設可繫結屬性。

10. 按一下 [ **完成**]。

11. 修改主體`SetMyProp`函式，使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

12. 將參數傳遞給`BoundPropertyChanged`和`BoundPropertyRequestEdit`函式是屬性，亦即參數傳遞至 id （） 屬性中之屬性的 dispid。IDL 檔案。

13. 修改[OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函式，如此它包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

14. 修改`OnDraw`函式，使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

15. 若要標頭檔的標頭檔，針對您的控制項類別的 public 區段，新增下列定義 （建構函式） 的成員變數：

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

16. 讓下面這行中的最後一行`DoPropExchange`函式：

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

17. 修改`OnResetState`函式，使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

18. 修改`GetMyProp`函式，使其包含下列程式碼：

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

您現在可以建置專案，將會註冊該控制項。 當您在對話方塊中，插入控制項**資料欄位**並**資料來源**將已加入的屬性，而且您現在可以選取資料來源，以及要在控制項中顯示的欄位。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

