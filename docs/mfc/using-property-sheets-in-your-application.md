---
title: "應用程式中使用屬性工作表 |Microsoft 文件"
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
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4247a40fa364774674c1c79845625df51ecd34ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-property-sheets-in-your-application"></a>在應用程式中使用屬性工作表
若要在您的應用程式中使用屬性工作表，請完成下列步驟：  
  
1.  建立每個屬性頁的對話方塊範本資源。 記住使用者可能在各個頁面間切換，因此盡可能一致地配置每一頁。  
  
     所有頁面的對話方塊範本不一定要有相同的大小。 架構會使用最大頁面的大小來決定對於屬性頁要在屬性工作表中配置多少空間。  
  
     當您建立屬性頁的對話方塊樣板資源時，您必須在對話屬性的屬性工作表中指定下列樣式：  
  
    -   設定**標題**編輯方塊**一般**頁面以您想要在此頁面的索引標籤中顯示的文字。  
  
    -   設定**樣式**清單方塊上的**樣式**頁面，即可**子**。  
  
    -   設定**框線**清單方塊上的**樣式**頁面，即可**細**。  
  
    -   請確認**標題列** 核取方塊**樣式**頁面中選取。  
  
    -   請確認**已停用** 核取方塊**其他樣式**頁面中選取。  
  
2.  建立[CPropertyPage](../mfc/reference/cpropertypage-class.md)-衍生的類別對應至每個屬性頁對話方塊範本。 請參閱[將類別加入](../ide/adding-a-class-visual-cpp.md)。 選擇 `CPropertyPage` 做為基底類別。  
  
3.  建立成員變數來保存此屬性頁的值。 因為屬性頁是特別的對話方塊，將成員變數加入屬性頁的程序與將成員變數加入對話方塊的程序完全相同。 如需詳細資訊，請參閱[定義對話方塊控制項的成員變數](../windows/defining-member-variables-for-dialog-controls.md)。  
  
4.  建構[CPropertySheet](../mfc/reference/cpropertysheet-class.md)在原始程式碼中的物件。 通常，您會針對顯示屬性工作表的命令，在處理常式中建構 `CPropertySheet` 物件。 這個物件代表整個屬性工作表。 如果您要建立強制回應屬性工作表與[DoModal](../mfc/reference/cpropertysheet-class.md#domodal)函式，此架構，依預設提供三個命令按鈕: [確定]、 [取消] 和 [套用]。 架構會建立沒有命令按鈕，以建立非強制回應屬性工作表的[建立](../mfc/reference/cpropertysheet-class.md#create)函式。 除非您要加入其他控制項 (例如預覽視窗) 或顯示非強制回應屬性工作表，否則不需要從 `CPropertySheet` 衍生類別。 對於非強制回應屬性工作表此步驟是必要的，因為它們不含可以用來關閉屬性工作表的任何預設控制項。  
  
5.  對於要加入至屬性工作表的每個頁面，請執行下列步驟：  
  
    -   為您在這個程序中稍早建立的每個 `CPropertyPage` 衍生類別建構一個物件。  
  
    -   呼叫[cpropertysheet:: Addpage](../mfc/reference/cpropertysheet-class.md#addpage)為每一頁。  
  
     通常，建立 `CPropertySheet` 的物件也會在這個步驟中建立 `CPropertyPage` 物件。 不過，如果您實作 `CPropertySheet` 衍生類別，您可以在 `CPropertyPage` 物件中內嵌 `CPropertySheet` 物件，以及從 `AddPage` 衍生類別建構函式為每個頁面呼叫 `CPropertySheet`。 `AddPage` 會將 `CPropertyPage` 物件加入至屬性工作表的頁面清單中，但實際上不會建立該頁面的視窗。 因此，不必一直等到建立屬性工作表視窗才呼叫 `AddPage`；您可以從屬性工作表的建構函式呼叫 `AddPage`。  
  
     根據預設，如果屬性工作表所擁有的索引標籤數目比屬性工作表單一列能夠容納的還多，索引標籤就會堆疊在多列當中。 若要停用 「 堆疊 」，請呼叫[cpropertysheet:: Enablestackedtabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs)參數設為**FALSE**。 在建立屬性工作表時，您必須呼叫 `EnableStackedTabs`。  
  
6.  呼叫[cpropertysheet:: Setwizardmode](../mfc/reference/cpropertysheet-class.md#domodal)或[建立](../mfc/reference/cpropertysheet-class.md#create)顯示屬性工作表。 呼叫 `DoModal` 將屬性工作表建立為強制回應對話方塊。 呼叫**建立**屬性工作表建立為非強制回應對話方塊。  
  
7.  在屬性頁和屬性工作表的擁有者之間交換資料。 說明文章中[交換資料](../mfc/exchanging-data.md)。  
  
 如需如何使用屬性工作表的範例，請參閱 MFC 一般範例[PROPDLG](../visual-cpp-samples.md)。  
  
## <a name="see-also"></a>請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)

