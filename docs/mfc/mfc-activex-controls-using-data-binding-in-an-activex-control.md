---
title: MFC ActiveX 控制項： 在 ActiveX 控制項中使用資料繫結 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab5195cc2381e515688182ad73452b07afd06b98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353269"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結
ActiveX 控制項的功能更強大的用途是資料繫結，可讓資料庫中的特定欄位繫結控制項的屬性。 當使用者修改此繫結屬性中的資料時，控制項告知的資料庫和要求更新資料錄欄位。 然後資料庫就會通知控制項的成功或失敗的要求。  
  
 本文涵蓋將您的工作的控制項部分。 實作與資料庫的資料繫結互動是控制項容器的責任。 如何在容器中管理的資料庫互動是超出範圍的這份文件。 本文的其餘部分說明如何準備資料繫結的控制項。  
  
 ![資料的概念圖&#45;繫結控制項](../mfc/media/vc374v1.gif "vc374v1")  
資料繫結控制項的概念圖  
  
 `COleControl`類別提供兩個成員函式可讓資料繫結簡單的程序來實作。 第一個函式， [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit)，用來要求權限才能變更屬性值。 [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged)，第二個函式，屬性值已成功變更之後呼叫。  
  
 本文涵蓋下列主題：  
  
-   [建立可繫結的內建屬性](#vchowcreatingbindablestockproperty)  
  
-   [建立可繫結的 Get/Set 方法](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a> 建立可繫結的內建屬性  
 它可建立資料繫結的內建屬性，雖然可能會想[可繫結的 get/set 方法](#vchowcreatingbindablegetsetmethod)。  
  
> [!NOTE]
>  內建屬性有**可繫結**和**requestedit**預設屬性。  
  
#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>若要加入的繫結的內建屬性，使用 加入屬性精靈  
  
1.  開始專案使用[MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)。  
  
2.  以滑鼠右鍵按一下控制項的介面節點。  
  
     這會開啟快顯功能表。  
  
3.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
4.  選取其中一個項目從**屬性名稱**下拉式清單。 例如，您可以選取**文字**。  
  
     因為**文字**已內建屬性，**可繫結**和**requestedit**屬性已經過檢查。  
  
5.  選取下列核取方塊，從**IDL 屬性** 索引標籤： **displaybind**和**defaultbind**來屬性加入至專案的屬性定義。IDL 檔案。 這些屬性讓控制項顯示給使用者，且必須內建屬性的預設可繫結屬性。  
  
 此時，您的控制項可以顯示資料來源的資料，但使用者無法更新資料欄位。 如果您想要也能夠更新資料、 變更您控制`OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函式來看起來像這樣：  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 您現在可以建置專案，將會登錄此控制項。 當您在對話方塊中，插入控制項**資料欄位**和**資料來源**屬性將會被加入和您現在可以選取資料來源和控制項中顯示的欄位。  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a> 建立可繫結的 Get/Set 方法  
 除了資料繫結至的 get/set 方法，您也可以建立[可繫結的內建屬性](#vchowcreatingbindablestockproperty)。  
  
> [!NOTE]
>  此程序假設您有 ActiveX 控制項專案的 Windows 控制項的子類別。  
  
#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>若要加入使用 [加入屬性精靈] 可繫結的 get/set 方法  
  
1.  載入控制項專案。  
  
2.  在**控制設定**頁面上，選取 子類別化控制項的視窗類別。 例如，您可能要子類別化編輯控制項。  
  
3.  載入控制項專案。  
  
4.  以滑鼠右鍵按一下控制項的介面節點。  
  
     這會開啟快顯功能表。  
  
5.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
6.  輸入中的屬性名稱**屬性名稱**方塊。 使用`MyProp`此範例中。  
  
7.  選取資料類型從**屬性型別**下拉式清單方塊。 使用**簡短**此範例中。  
  
8.  在 [實作類型] 中，按一下 [Get/Set 方法] 。  
  
9. 從 [IDL 屬性] 索引標籤中選取下列核取方塊：**可繫結**， **requestedit**， **displaybind**，和**defaultbind**新增要在專案的屬性定義的屬性。IDL 檔案。 這些屬性讓控制項顯示給使用者，且必須內建屬性的預設可繫結屬性。  
  
10. 按一下 [ **完成**]。  
  
11. 修改主體`SetMyProp`函式，使其包含下列程式碼：  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. 參數傳遞至`BoundPropertyChanged`和`BoundPropertyRequestEdit`函式是屬性，這是傳遞至 id （） 屬性中屬性的參數的 dispid。IDL 檔案。  
  
13. 修改[OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)函式，如此它包含下列程式碼：  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. 修改`OnDraw`函式，使其包含下列程式碼：  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. 若要公開的標頭檔的控制項類別的標頭檔區段中，加入成員變數的下列定義 （建構函式）：  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. 進行下列行中的最後一行`DoPropExchange`函式：  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. 修改`OnResetState`函式，使其包含下列程式碼：  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. 修改`GetMyProp`函式，使其包含下列程式碼：  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 您現在可以建置專案，將會登錄此控制項。 當您在對話方塊中，插入控制項**資料欄位**和**資料來源**屬性將會被加入和您現在可以選取資料來源和控制項中顯示的欄位。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   

