---
title: "MFC ActiveX 控制項： 在 ActiveX 控制項中使用圖片 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPPICTUREDISP
dev_langs:
- C++
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a27e5ebb58056dfd14417adea211daf2c6ac2ddf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>MFC ActiveX 控制項：在 ActiveX 控制項中使用圖片
本文說明常見圖片類型和如何在 ActiveX 控制項中實作。 主題包括：  
  
-   [自訂圖片屬性的概觀](#_core_overview_of_custom_picture_properties)  
  
-   [在 ActiveX 控制項中實作自訂圖片屬性](#_core_implementing_a_custom_picture_property_in_your_activex_control)  
  
-   [於控制項專案中加入項目](#_core_additions_to_your_control_project)  
  
##  <a name="_core_overview_of_custom_picture_properties"></a> 自訂圖片屬性的概觀  
 圖片類型在某些 ActiveX 控制項群組中是很常見的一種類型。 圖片類型可以處理中繼檔、點陣圖或圖示，並且讓使用者指定要在 ActiveX 控制項中顯示的圖片。 自訂圖片屬性是以圖片物件和允許控制項使用者存取圖片屬性的 Get/Set 函式來進行實作。 控制項使用者可利用內建圖片屬性頁來存取自訂圖片屬性。  
  
 除了標準圖片類型，尚可使用字型和色彩類型。 如需在 ActiveX 控制項中使用標準 Font 類型的詳細資訊，請參閱 [MFC ActiveX 控制項：使用字型](../mfc/mfc-activex-controls-using-fonts.md)一文。  
  
 ActiveX 控制項類別提供許多您可以用來在控制項內實作圖片屬性的元件。 這些元件包括：  
  
-   [CPictureHolder](../mfc/reference/cpictureholder-class.md) 類別。  
  
     這個類別提供簡易存取圖片物件及自訂圖片屬性所顯示之項目的功能。  
  
-   支援 **LPPICTUREDISP**類型屬性，此由 Get/Set 函式完成實作。  
  
     您可以使用 [類別檢視] 快速加入一個支援圖片類型的自訂屬性或屬性。 如需使用 [類別檢視] 加入 ActiveX 控制項屬性的詳細資訊，請參閱 [MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)一文。  
  
-   操作控制項圖片屬性的屬性頁。  
  
     這個屬性頁是 ActiveX 控制項可以使用的內建屬性頁的一部分。 如需 ActiveX 控制項屬性頁的詳細資訊，請參閱 [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)一文。  
  
##  <a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a> 在 ActiveX 控制項中實作自訂圖片屬性  
 當您完成本章節所列步驟之後，控制項便可以顯示由使用者所選定的圖片。 使用者可以在顯示目前圖片的屬性頁上更改已顯示的圖片，該屬性頁中也有一個瀏覽按鈕，以供使用者選取不同的圖片。  
  
 自訂圖片屬性的實作程序與其他屬性的程序相似，主要差異是在此種自訂屬性必須支援圖片類型。 因為圖片屬性的項目必須由 ActiveX 控制項繪製，因此必須針對屬性進行加入和修改才能完整實作屬性。  
  
 若要實作自訂圖片屬性，您必須執行下列動作：  
  
-   [在控制項專案中加入程式碼](#_core_additions_to_your_control_project)。  
  
     必須加入一個標準圖片屬性頁 ID、一個 `CPictureHolder`類型資料成員，和具 Get/Set 實作之 **LPPICTUREDISP** 類型的自訂屬性。  
  
-   [在控制項類別中修改幾種函式](#_core_modifications_to_your_control_project)。  
  
     這些修改主要是針對負責 ActiveX 控制項繪製的若干函式。  
  
##  <a name="_core_additions_to_your_control_project"></a> 於控制項專案中加入項目  
 若要為標準圖片屬性頁加入屬性頁 ID，請在控制項實作檔 (.CPP) 中的 `BEGIN_PROPPAGEIDS` 巨集之後插入下列這行程式碼：  
  
 [!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]  
  
 您也必須將 `BEGIN_PROPPAGEIDS` 巨集的計數參數設成以 1 遞增。 下面這行程式碼可說明這點：  
  
 [!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]  
  
 若要對控制項類別加入 `CPictureHolder` 資料成員，請在控制項標頭檔 (.H) 裡的控制項類別宣告保護區段中插入下列這行程式碼：  
  
 [!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]  
  
 您不一定要將資料成員命名為 `m_pic`；任何名稱都可以使用。  
  
 接著，加入一個支援圖片類型的自訂屬性：  
  
#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>若要使用 [加入屬性精靈] 來加入自訂圖片屬性  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表選擇 [加入]  ，然後選擇 [加入屬性] 。  
  
5.  在 [屬性名稱]  方塊中，輸入屬性名稱。 為達示範目的，這個程序中將會使用 `ControlPicture` 。  
  
6.  在**屬性型別**方塊中，選取**IPictureDisp\*** 屬性型別。  
  
7.  在 [實作類型] 中，按一下 [Get/Set 方法] 。  
  
8.  為 Get 和 Set 函式輸入唯一名稱，或接受預設名稱 (在這個範例中，會使用預設名稱 `GetControlPicture` 和 `SetControlPicture` )。  
  
9. 按一下 [ **完成**]。  
  
 [加入屬性精靈] 會在控制項標頭檔 (.H) 的分派對應註解之間加入下列這行程式碼：  
  
 [!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]  
  
 除此之外，下列這段程式碼也會插入至控制項實作檔 (.CPP) 的分派對應中：  
  
 [!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]  
  
 [加入屬性精靈] 也會在控制項實作檔中加入下列這兩個 Stub 函式：  
  
 [!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]  
  
> [!NOTE]
>  控制項類別和函式名稱可能會與上述範例不同。  
  
###  <a name="_core_modifications_to_your_control_project"></a> 於控制項專案中修改項目  
 當您已經在控制項專案中加入了必要的項目之後，您需要修改幾種會影響 ActiveX 控制項轉譯的函式。 這些函式，即 `OnResetState`、 `OnDraw`和自訂圖片屬性的 Get/Set 函式位於控制項實作檔中。 請注意，在這個範例中，控制項類別名稱為 `CSampleCtrl`， `CPictureHolder` 資料成員名稱為 `m_pic`，而自訂圖片屬性名稱是 `ControlPicture`。  
  
 在 `OnResetState` 控制項函式中，將下列這行選擇性的程式碼加到 `COleControl::OnResetState`呼叫之後：  
  
 [!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]  
  
 如此便會將控制項圖片設成空白圖片。  
  
 若要適當地繪製圖片，請呼叫在 [控制項函式中的](../mfc/reference/cpictureholder-class.md#render) CPictureHolder::Render `OnDraw` 。 將函式修改成類似下面範例中的函式：  
  
 [!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]  
  
 在控制項自訂圖片屬性的 Get 函式中，加入下列這行程式碼：  
  
 [!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]  
  
 在控制項自訂圖片屬性的 Set 函式中，加入下列這行程式碼：  
  
 [!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]  
  
 圖片屬性必須設定成具有持續性，這樣在設計階段所加入的資料才會於執行階段顯示。 將下列這行程序碼加入 `COleControl`衍生類別的 `DoPropExchange` 函式中：  
  
 [!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]  
  
> [!NOTE]
>  類別和函式名稱可能與上述範例中的不同。  
  
 在您完成修改之後，請重建專案以納入自訂圖片屬性的新功能，並且使用測試容器來測試新屬性。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md) 。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項： 使用字型](../mfc/mfc-activex-controls-using-fonts.md)   
 [MFC ActiveX 控制項：屬性頁](../mfc/mfc-activex-controls-property-pages.md)

