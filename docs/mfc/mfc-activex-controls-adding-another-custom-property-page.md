---
title: MFC ActiveX 控制項：加入另一個自訂屬性頁
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: a749c5d8d676ac85c3c2085eb041328aff599ab8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508882"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC ActiveX 控制項：加入另一個自訂屬性頁

ActiveX 控制項有時候會有比可合理容納在一個屬性頁更多的屬性。 在此情況下，您可以將屬性頁加入至 ActiveX 控制項，以顯示這些屬性。

本文討論如何將新的屬性頁新增至已至少有一個屬性頁的 ActiveX 控制項。 如需有關加入內建屬性頁 (字型、圖片或色彩) 的詳細資訊，請參閱 [MFC ActiveX 控制項：使用內建屬性頁](mfc-activex-controls-using-stock-property-pages.md)一文。

下列程式使用 ActiveX Control Wizard 所建立的範例 ActiveX 控制項架構。 因此，類別名稱和識別碼在此範例中是唯一的。

如需在 ActiveX 控制項中使用屬性頁的詳細資訊，請參閱下列文章：

- [MFC ActiveX 控制項：屬性頁](mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控制項：使用內建屬性頁](mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  強烈建議新的屬性頁遵守 ActiveX 控制項屬性頁的大小標準。 [股票圖片] 和 [色彩] 屬性頁會測量250x62 對話單位 (DLU) 。 標準字型屬性頁是 250x110 Dlu。 ActiveX Control Wizard 所建立的預設屬性頁面會使用 250x62 DLU 標準。

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>在專案中插入新的屬性頁範本

1. 開啟您的控制項專案，開啟 [專案] 工作區中的資源檢視。

1. 以滑鼠右鍵按一下資源檢視開啟快捷方式功能表，然後按一下 [ **加入資源**]。

1. 展開對話方塊節點，然後選取 [ **IDD_OLE_PROPPAGE_SMALL** **]** 。

1. 按一下 [ **新增** ]，將資源新增至您的專案。

1. 選取新的屬性頁範本，以重新整理**資源檢視**) 中的 [**屬性**] 視窗 (。

1. 輸入 **ID** 屬性的新值。 這個範例會使用 **IDD_PROPPAGE_NEWPAGE**。

1. 按一下工具列的 [儲存]  。

### <a name="to-associate-the-new-template-with-a-class"></a>若要建立新範本與類別的關聯

1. 開啟類別檢視。

1. 以滑鼠右鍵按一下類別檢視開啟快捷方式功能表。

1. 從快捷方式功能表按一下 [ **加入** ]，然後按一下 [ **加入類別**]。

   這會開啟 [ [加入類別](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) ] 對話方塊。

1. 按兩下 [ **MFC 類別** ] 範本。

1. 在 [ [MFC 類別 Wizard]](reference/mfc-add-class-wizard.md)的 [**類別名稱**] 方塊中，輸入新對話方塊類別的名稱。 在此範例中 (， `CAddtlPropPage` ) 。

1. 如果您想要變更檔案名，請按一下 [ **變更**]。 輸入您的實值和標頭檔名稱，或接受預設名稱。

1. 在 [ **基類** ] 對話方塊中，選取 `COlePropertyPage` 。

1. 在 [ **對話方塊識別碼]** 方塊中，選取 [ **IDD_PROPPAGE_NEWPAGE**]。

1. 按一下 **[完成]** 以建立類別。

若要允許控制項的使用者存取這個新的屬性頁面，請對控制項的 [屬性頁識別碼宏] 區段進行下列變更， (位於控制項執行檔) ：

[!code-cpp[NVC_MFC_AxUI#32](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

請注意，您必須增加 BEGIN_PROPPAGEIDS 宏的第二個參數， (屬性頁計數) 從1到2。

您也必須修改控制項執行檔 (。.CPP) 檔案，以包含 ( 的標頭。H) 新屬性頁類別的檔案。

下一步是要建立兩個新的字串資源，以提供新屬性頁的類型名稱和標題。

#### <a name="to-add-new-string-resources-to-a-property-page"></a>將新字串資源加入至屬性頁

1. 當您的控制項專案開啟時，開啟資源檢視。

1. 按兩下 [ **字串資料表** ] 資料夾，然後按兩下您要加入字串的現有字串資料表資源。

   這會在視窗中開啟字串資料表。

1. 選取字串資料表結尾的空白行，然後輸入字串的文字（或標題）：例如「其他屬性頁」。

   這會開啟顯示**標題**和**識別碼**方塊的**字串屬性**頁面。 [ **標題** ] 方塊包含您所輸入的字串。

1. 在 [ **識別碼** ] 方塊中，選取或輸入字串的識別碼。 當您完成時，請按 Enter 鍵。

   這個範例會使用 **IDS_SAMPLE_ADDPAGE** 作為新屬性頁的型別名稱。

1. 使用 ID 的 **IDS_SAMPLE_ADDPPG_CAPTION** 重複步驟3和4，並使用標題的 [其他屬性頁面]。

1. 在。新屬性頁類別的 CPP 檔 (在此範例中， `CAddtlPropPage`) 修改， `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` 以便透過 [AfxOleRegisterPropertyPageClass](reference/registering-ole-controls.md#afxoleregisterpropertypageclass)傳遞 IDS_SAMPLE_ADDPAGE，如下列範例所示：

   [!code-cpp[NVC_MFC_AxUI#33](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. 修改的函式， `CAddtlPropPage` 以便將 IDS_SAMPLE_ADDPPG_CAPTION 傳遞至函式，如下所示 `COlePropertyPage` ：

   [!code-cpp[NVC_MFC_AxUI#34](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

進行必要的修改之後，請重建您的專案，並使用測試容器來測試新的屬性頁。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](testing-properties-and-events-with-test-container.md) 。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)
