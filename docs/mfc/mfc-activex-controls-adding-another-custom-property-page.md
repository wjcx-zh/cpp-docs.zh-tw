---
title: MFC ActiveX 控制項：加入另一個自訂屬性頁
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 02c87c2c5283b7293c2a7ab028ec9a2abbba2b33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364745"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC ActiveX 控制項：加入另一個自訂屬性頁

有時,ActiveX 控件的屬性將超過一個屬性頁上的合理擬合屬性。 在這種情況下,您可以將屬性頁添加到 ActiveX 控制件以顯示這些屬性。

本文討論將新屬性頁添加到已具有至少一個屬性頁的 ActiveX 控制項。 有關新增股票屬性頁(字型、圖片或顏色)的詳細資訊,請參閱文章[MFC ActiveX 控制件:使用股票屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)。

以下過程使用由 ActiveX 控制嚮導創建的範例 ActiveX 控制框架。 因此,類名稱和標識符是此示例所獨有的。

有關在 ActiveX 控制件中使用屬性頁的詳細資訊,請參閱以下文章:

- [MFC ActiveX 控制項：屬性頁](../mfc/mfc-activex-controls-property-pages.md)

- [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  強烈建議新屬性頁符合 ActiveX 控制件屬性頁的大小標準。 庫存圖片和顏色屬性頁測量 250x62 對話方塊單元 (DLU)。 標準字體屬性頁為 250x110 DLL。 ActiveX 控制項精靈建立的預設屬性頁使用 250x62 DLU 標準。

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>將新屬性頁樣本插入到項目中

1. 打開控件專案后,在專案工作區中打開資源視圖。

1. 右鍵按下「資源檢視」以打開快捷功能表,然後單擊「**添加資源**」。

1. 展開**對話框**節點,然後選擇**IDD_OLE_PROPPAGE_SMALL**。

1. 按下 **「新建**」以將資源添加到專案中。

1. 選擇新的屬性頁範本以刷新**屬性**視窗(在**資源檢視中**)。

1. 輸入**ID**屬性的新值。 此範例使用**IDD_PROPPAGE_NEWPAGE**。

1. 按一下工具列的 [儲存] **** 。

### <a name="to-associate-the-new-template-with-a-class"></a>將新樣本與類關聯

1. 打開類視圖。

1. 在「類視圖」中右鍵單擊以打開快捷功能表。

1. 在快捷選單中,按一下「**添加**」,然後單擊「**添加類**」。

   這將打開[「添加類」](../ide/add-class-dialog-box.md)對話方塊。

1. 按兩下**MFC 類**範本。

1. 在[MFC 類嚮導](../mfc/reference/mfc-add-class-wizard.md)中的 **「類名稱**」框中,鍵入新對話方塊類的名稱。 (在此範例中,.) `CAddtlPropPage`

1. 如果要更改檔名,請按下「**更改**」。 鍵入實現和標頭檔的名稱,或接受預設名稱。

1. 在 **「基本類別」** 框`COlePropertyPage`中, 選擇 。

1. 在 **「對話框 ID」** 框中, 選擇**IDD_PROPPAGE_NEWPAGE**。

1. 按下 **「完成」** 以建立類。

要允許控制的使用者存取此新屬性頁,請對控制項的屬性頁 IDs 巨集部份(位於控制項來實檔中)進行以下變更:

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

請注意,必須將BEGIN_PROPPAGEIDS宏的第二個參數(屬性頁計數)從 1 增加到 2。

還必須修改控制項實現檔 (。CPP 檔以包括標頭 (。H) 新屬性頁類的檔。

下一步是創建兩個新的字串資源,為新屬性頁提供類型名稱和標題。

#### <a name="to-add-new-string-resources-to-a-property-page"></a>新增屬性頁加入新字串資源

1. 打開控制專案后,打開資源檢視。

1. 按兩下**字串表**資料夾,然後按兩下要向其添加字串的現有字串元表資源。

   這將在視窗中打開字串表。

1. 選擇字串表末尾的空白行,鍵入字串的文本或標題:例如,"其他屬性頁"。

   這將打開顯示標題和**ID**框**的****字串屬性**頁面。 **標題盒**包含您鍵入的字串。

1. 在**ID**盒中,選擇或鍵入字串的 ID。 完成後按 Enter。

   此示例對新屬性頁的類型名稱使用**IDS_SAMPLE_ADDPAGE。**

1. 使用**IDS_SAMPLE_ADDPPG_CAPTION**對 ID 和標題的「其他屬性頁」 重複步驟 3 和 4。

1. 在。新屬性頁類別的 CPP 檔(在此範例`CAddtlPropPage`中)`CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry`修改, 以便 IDS_SAMPLE_ADDPAGE由[AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass)傳遞,如以下範例所示:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. 修改`CAddtlPropPage`的 建構函數,以便IDS_SAMPLE_ADDPPG_CAPTION`COlePropertyPage`傳遞給 建構函數,如下所示:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

進行必要的修改後,將重建專案並使用測試容器來測試新的屬性頁。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md) 。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)
