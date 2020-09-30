---
title: 在應用程式中使用屬性工作表
ms.date: 11/04/2016
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
ms.openlocfilehash: 789764c9af988135219bd710d4f8aec1cda9143a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504648"
---
# <a name="using-property-sheets-in-your-application"></a>在應用程式中使用屬性工作表

若要在您的應用程式中使用屬性工作表，請完成下列步驟：

1. 建立每個屬性頁的對話方塊範本資源。 記住使用者可能在各個頁面間切換，因此盡可能一致地配置每一頁。

   所有頁面的對話方塊範本不一定要有相同的大小。 架構會使用最大頁面的大小來決定對於屬性頁要在屬性工作表中配置多少空間。

   當您建立屬性頁的對話方塊樣板資源時，您必須在對話屬性的屬性工作表中指定下列樣式：

   - 將 [**一般**] 頁面上的 [**標題**] 編輯方塊，設定為您想要在此頁面的索引標籤中顯示的文字。

   - 將 [**樣式**] 頁面上的 [**樣式**] 清單方塊設定為 [**子**系]。

   - 將 [**樣式**] 頁面上的 [**框線**] 清單方塊設定為 [**細**]。

   - 確定已選取 [**樣式**] 頁面上的 [**標題列**] 核取方塊。

   - 確定已選取 [**更多樣式**] 頁面上的 [**已停用**] 核取方塊。

1. 建立對應于每個屬性頁對話方塊範本的 [CPropertyPage](../mfc/reference/cpropertypage-class.md)衍生類別。 請參閱 [加入類別](../ide/adding-a-class-visual-cpp.md)。 選擇 `CPropertyPage` 做為基底類別。

1. 建立成員變數來保存此屬性頁的值。 因為屬性頁是特別的對話方塊，將成員變數加入屬性頁的程序與將成員變數加入對話方塊的程序完全相同。 如需詳細資訊，請參閱 [定義對話方塊控制項的成員變數](../windows/adding-editing-or-deleting-controls.md)。

1. 在原始程式碼中，建立 [CPropertySheet](../mfc/reference/cpropertysheet-class.md) 物件。 通常，您會針對顯示屬性工作表的命令，在處理常式中建構 `CPropertySheet` 物件。 這個物件代表整個屬性工作表。 如果您使用 [DoModal](../mfc/reference/cpropertysheet-class.md#domodal) 函式建立模式屬性工作表，則架構預設會提供三個命令按鈕： [確定]、[取消] 和 [套用]。 此架構不會針對以 [Create](../mfc/reference/cpropertysheet-class.md#create) 函式建立的非強制回應屬性工作表建立任何命令按鈕。 除非您要加入其他控制項 (例如預覽視窗) 或顯示非強制回應屬性工作表，否則不需要從 `CPropertySheet` 衍生類別。 對於非強制回應屬性工作表此步驟是必要的，因為它們不含可以用來關閉屬性工作表的任何預設控制項。

1. 對於要加入至屬性工作表的每個頁面，請執行下列步驟：

   - 為您在這個程序中稍早建立的每個 `CPropertyPage` 衍生類別建構一個物件。

   - 針對每個頁面呼叫 [CPropertySheet：： AddPage](../mfc/reference/cpropertysheet-class.md#addpage) 。

   通常，建立 `CPropertySheet` 的物件也會在這個步驟中建立 `CPropertyPage` 物件。 不過，如果您實作 `CPropertySheet` 衍生類別，您可以在 `CPropertyPage` 物件中內嵌 `CPropertySheet` 物件，以及從 `AddPage` 衍生類別建構函式為每個頁面呼叫 `CPropertySheet`。 `AddPage` 會將 `CPropertyPage` 物件加入至屬性工作表的頁面清單中，但實際上不會建立該頁面的視窗。 因此，不必一直等到建立屬性工作表視窗才呼叫 `AddPage`；您可以從屬性工作表的建構函式呼叫 `AddPage`。

   根據預設，如果屬性工作表所擁有的索引標籤數目比屬性工作表單一列能夠容納的還多，索引標籤就會堆疊在多列當中。 若要停用堆疊，請呼叫 [CPropertySheet：： EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs) ，並將參數設定為 **FALSE**。 在建立屬性工作表時，您必須呼叫 `EnableStackedTabs`。

1. 呼叫 [CPropertySheet：:D omodal](../mfc/reference/cpropertysheet-class.md#domodal) 或 [Create](../mfc/reference/cpropertysheet-class.md#create) 來顯示內容表。 呼叫 `DoModal` 將屬性工作表建立為強制回應對話方塊。 呼叫 **create** ，將屬性工作表建立為非強制回應對話方塊。

1. 在屬性頁和屬性工作表的擁有者之間交換資料。 這會在「 [交換資料](../mfc/exchanging-data.md)」一文中說明。

如需如何使用屬性工作表的範例，請參閱 MFC 一般範例 [PROPDLG](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另請參閱

[屬性工作表](../mfc/property-sheets-mfc.md)
