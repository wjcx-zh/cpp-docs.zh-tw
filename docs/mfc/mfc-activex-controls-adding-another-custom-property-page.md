---
title: MFC ActiveX 控制項： 加入另一個自訂屬性頁 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a0e8713bc228e65cb06e58d7ccb5389f7366e76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350777"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>MFC ActiveX 控制項：加入另一個自訂屬性頁
有時候，ActiveX 控制項將會有更多超過可合理地容納在單一的屬性頁面上的屬性。 在此情況下，您可以將屬性頁加入 ActiveX 控制項以顯示這些屬性。  
  
 這篇文章討論已經有一個以上的屬性頁的 ActiveX 控制項中加入新的屬性頁。 如需有關加入內建屬性頁 （字型、 圖片或色彩），請參閱文章[MFC ActiveX 控制項： 使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)。  
  
 下列程序會使用 ActiveX 控制項精靈所建立的範例 ActiveX 控制項架構。 因此，類別名稱和識別碼是此範例中唯一的。  
  
 如需在 ActiveX 控制項中使用屬性頁的詳細資訊，請參閱下列文章：  
  
-   [MFC ActiveX 控制項：屬性頁](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [MFC ActiveX 控制項：使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
    > [!NOTE]
    >  強烈建議新屬性頁應遵守標準的 ActiveX 控制項屬性頁的大小。 內建的圖片及色彩屬性頁面，量值為 250 x 62 對話方塊單位 (DLU)。 標準的字型屬性頁是 250 x 110 Dlu。 ActiveX 控制項精靈所建立的預設屬性頁會使用的 250 x 62 DLU 標準。  
  
### <a name="to-insert-a-new-property-page-template-into-your-project"></a>您的專案中插入新的屬性頁範本  
  
1.  控制項專案開啟時，請在 [專案] 工作區中開啟資源檢視。  
  
2.  若要開啟捷徑功能表，然後按一下資源檢視中以滑鼠右鍵按一下**加入資源**。  
  
3.  展開**對話方塊**節點，然後選取**IDD_OLE_PROPPAGE_SMALL**。  
  
4.  按一下`New`，將資源加入至您的專案。  
  
5.  選取新的屬性頁面範本，若要重新整理 [屬性] 視窗。  
  
6.  輸入新值**識別碼**屬性。 這個範例會使用**IDD_PROPPAGE_NEWPAGE**。  
  
7.  按一下**儲存**工具列上。  
  
### <a name="to-associate-the-new-template-with-a-class"></a>若要將新的範本關聯的類別  
  
1.  開啟 [類別檢視]。  
  
2.  在 類別檢視，開啟捷徑功能表上按一下滑鼠右鍵。  
  
3.  從捷徑功能表，按一下 **新增**，然後按一下 **加入類別**。  
  
     這會開啟[加入類別](../ide/add-class-dialog-box.md) 對話方塊。  
  
4.  按兩下**MFC 類別**範本。  
  
5.  在**類別名稱**方塊中[MFC 類別精靈](../mfc/reference/mfc-add-class-wizard.md)，輸入新的對話方塊類別的名稱。 (在此範例中， `CAddtlPropPage`。)  
  
6.  如果您想要變更檔案名稱，按一下**變更**。 輸入您的實作和標頭檔的名稱或接受預設名稱。  
  
7.  在**基底類別**方塊中，選取`COlePropertyPage`。  
  
8.  在**對話方塊 ID**方塊中，選取**IDD_PROPPAGE_NEWPAGE**。  
  
9. 按一下**完成**建立類別。  
  
 若要允許控制項使用者存取這個新的屬性頁面，對控制項的屬性頁 Id 巨集區段 （位於控制項實作檔） 中的下列變更：  
  
 [!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]  
  
 請注意，您必須增加第二個參數`BEGIN_PROPPAGEIDS`為 2 的巨集 （屬性頁面計數） 1。  
  
 您也必須修改控制項實作檔 (。要包含的標頭的 CPP) 檔案 (。H） 檔案的新屬性頁類別。  
  
 下一個步驟建立兩個新的字串資源將會為新的屬性頁提供型別名稱和標題。  
  
#### <a name="to-add-new-string-resources-to-a-property-page"></a>若要加入新的字串資源的屬性頁  
  
1.  開啟您控制專案，開啟 [資源檢視]。  
  
2.  按兩下**字串資料表**資料夾，然後按兩下現有的字串資料表的資源您要新增的字串。  
  
     這是在視窗中開啟字串資料表。  
  
3.  選取空白的行結尾的字串資料表，然後輸入文字或標題的字串： 例如，其他屬性頁面。 」  
  
     這會開啟**字串屬性**頁面顯示**標題**和**識別碼**方塊。 **標題**方塊包含您所輸入的字串。  
  
4.  在**識別碼**方塊中，選取或輸入字串的 ID。 當您完成時，請按下 Enter。  
  
     這個範例會使用**IDS_SAMPLE_ADDPAGE**針對新的屬性頁的型別名稱。  
  
5.  重複步驟 3 和 4 使用**IDS_SAMPLE_ADDPPG_CAPTION**識別碼和 「 其他屬性頁 」 標題。  
  
6.  在中。您新的屬性頁類別 CPP 檔案 (在此範例中， `CAddtlPropPage`) 修改`CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry`以便 IDS_SAMPLE_ADDPAGE 傳[AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass)，如下列範例所示：  
  
     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]  
  
7.  修改的建構函式`CAddtlPropPage`以便**IDS_SAMPLE_ADDPPG_CAPTION**傳遞至`COlePropertyPage`建構函式，如下所示：  
  
     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]  
  
 之後您已進行必要的修改重建您的專案，使用測試容器測試新的屬性頁。 如需測試容器存取方法的詳細資訊，請參閱 [以測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md) 。  
  
## <a name="see-also"></a>另請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)

