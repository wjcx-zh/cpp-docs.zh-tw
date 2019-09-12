---
title: MFC ActiveX 控制項：新增另一個自訂屬性頁
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 09d85d69efc4c6cf0bf253099bae78c1e570f8a5
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907384"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC ActiveX 控制項：新增另一個自訂屬性頁

ActiveX 控制項偶爾會有比一個屬性頁更適合的屬性。 在此情況下，您可以將屬性頁新增至 ActiveX 控制項，以顯示這些屬性。

本文討論如何將新的屬性頁新增至已有至少一個屬性頁的 ActiveX 控制項。 如需有關加入內建屬性頁（字型、圖片或色彩）的詳細資訊，請[參閱 MFC ActiveX 控制項一文：使用內建屬性](../mfc/mfc-activex-controls-using-stock-property-pages.md)頁。

下列程式會使用 ActiveX Control Wizard 所建立的範例 ActiveX 控制項架構。 因此，此範例中的類別名稱和識別碼是唯一的。

如需在 ActiveX 控制項中使用屬性頁的詳細資訊，請參閱下列文章：

- [MFC ActiveX 控制項：屬性頁](../mfc/mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  強烈建議新的屬性頁符合 ActiveX 控制項屬性頁的大小標準。 [股票圖片] 和 [色彩] 屬性頁會測量250x62 對話方塊單位（DLU）。 標準字型屬性頁是 250x110 Dlu。 ActiveX 控制項嚮導所建立的預設屬性頁會使用 250x62 DLU 標準。

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>若要將新的屬性頁範本插入至您的專案

1. 在開啟控制項專案時，開啟 [專案] 工作區中的資源檢視。

1. 在資源檢視上按一下滑鼠右鍵，以開啟快捷方式功能表，然後按一下 [**新增資源**]。

1. 展開對話方塊節點，然後選取 [ **IDD_OLE_PROPPAGE_SMALL** **]** 。

1. 按一下 [**新增**] 將資源新增至您的專案。

1. 選取 [新增屬性頁] 範本，以重新整理 [**屬性**] 視窗（**資源檢視**中）。

1. 為 [**識別碼**] 屬性輸入新的值。 這個範例會使用**IDD_PROPPAGE_NEWPAGE**。

1. 按一下工具列上的 [**儲存**]。

### <a name="to-associate-the-new-template-with-a-class"></a>若要將新範本與類別產生關聯

1. 開啟類別檢視。

1. 在類別檢視上按一下滑鼠右鍵，以開啟快捷方式功能表。

1. 從捷徑功能表按一下 [新增]，然後按一下 [加入類別]。

   這會開啟 [[新增類別](../ide/add-class-dialog-box.md)] 對話方塊。

1. 按兩下 [ **MFC 類別**] 範本。

1. 在 [ [MFC 類別] Wizard](../mfc/reference/mfc-add-class-wizard.md)的 [**類別名稱**] 方塊中，輸入新對話方塊類別的名稱。 （在此範例`CAddtlPropPage`中為）。

1. 如果您想要變更檔案名，請按一下 [**變更**]。 輸入您的執行和標頭檔的名稱，或接受預設名稱。

1. 在 [**基底類別**] 方塊`COlePropertyPage`中，選取。

1. 在 [**對話方塊識別碼]** 方塊中，選取 [ **IDD_PROPPAGE_NEWPAGE**]。

9. 按一下 **[完成]** 以建立類別。

若要讓控制項的使用者能夠存取這個新的屬性頁，請對控制項的屬性頁 Id 宏區段（位於控制項執行檔案）進行下列變更：

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

請注意，您必須將 BEGIN_PROPPAGEIDS 宏的第二個參數（屬性頁計數）從1增加至2。

您也必須修改控制項執行檔（）。CPP）檔案，以包含標頭（。H）檔案（新的屬性頁類別）。

下一個步驟牽涉到建立兩個新的字串資源，以提供新屬性頁的類型名稱和標題。

#### <a name="to-add-new-string-resources-to-a-property-page"></a>若要將新的字串資源加入至屬性頁

1. 在開啟控制項專案的情況下，開啟資源檢視。

1. 按兩下 [**字串資料表**] 資料夾，然後按兩下您要加入字串的現有字串資料表資源。

   這會在視窗中開啟字串資料表。

1. 選取字串資料表結尾的空白行，然後輸入字串的文字或標題，例如「其他屬性頁」。

   這會開啟顯示 [**標題**] 和 [ **ID** ] 方塊的 [**字串屬性**] 頁面。 [**標題**] 方塊包含您輸入的字串。

1. 在 [**識別碼**] 方塊中，選取或輸入字串的識別碼。 當您完成時，請按 Enter 鍵。

   這個範例會使用**IDS_SAMPLE_ADDPAGE**做為新屬性頁的類型名稱。

1. 針對識別碼使用**IDS_SAMPLE_ADDPPG_CAPTION**重複步驟3和4，並針對標題重複 [其他屬性頁]。

1. 在。新屬性頁類別的 CPP 檔案（在此範例`CAddtlPropPage`中為）會`CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry`修改，以便由[AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass)傳遞 IDS_SAMPLE_ADDPAGE，如下列範例所示：

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. 修改的`CAddtlPropPage`函式，以便將 IDS_SAMPLE_ADDPPG_CAPTION 傳遞給此`COlePropertyPage`函式，如下所示：

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

進行必要的修改之後，請重建您的專案，並使用測試容器來測試新的屬性頁。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md) 。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
