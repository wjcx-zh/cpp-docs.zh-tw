---
title: "MFC ActiveX 控制項：加入另一個自訂屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 屬性頁"
  - "自訂屬性頁"
  - "MFC ActiveX 控制項 [C++], 屬性頁"
  - "屬性頁 [C++], MFC ActiveX 控制項"
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：加入另一個自訂屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有時候， ActiveX 控制項比對屬性頁將具有多個屬性可以合法相容。  在這種情況下，您可以將屬性頁加入至 ActiveX 控制項顯示這些屬性。  
  
 至少已有一個屬性頁的本文討論加入新的屬性頁加入至 ActiveX 控制項。  如需將內建屬性頁的詳細資訊 \(字型、圖片、色彩\)，請參閱本文件的 [MFC ActiveX 控制項:使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)。  
  
 下列程序使用 ActiveX 控制項精靈建立的範例 ActiveX 控制項框架。  因此，類別名稱和識別項對這個範例是唯一的。  
  
 如需使用屬性頁的詳細資訊在 ActiveX 控制項，請參閱下列文件:  
  
-   [MFC ActiveX 控制項:屬性頁](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [MFC ActiveX 控制項:使用內建屬性頁](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
    > [!NOTE]
    >  強烈建議新屬性頁遵守 ActiveX 控制項屬性頁的大小準則。  內建圖片和色彩屬性頁測量 250x62 對話方塊單位 \(\)。  標準字型屬性頁是 250x110 DLU。  ActiveX 控制項精靈建立的預設屬性頁使用 250x62 DLU 標準。  
  
### 要插入新的屬性呼叫範本至專案  
  
1.  開啟您的專案，請在專案工作區開啟資源檢視。  
  
2.  以滑鼠右鍵按一下在資源檢視中開啟捷徑功能表並按一下 \[**加入資源**\]。  
  
3.  展開 **Dialog** 節點，並選取 **IDD\_OLE\_PROPPAGE\_SMALL**。  
  
4.  按一下 `New` 將資源加入至您的專案。  
  
5.  選取新的屬性頁範本重新整理屬性視窗。  
  
6.  輸入 **ID** 屬性的新值。  這個範例使用 **IDD\_PROPPAGE\_NEWPAGE**。  
  
7.  按一下工具列上的 \[**儲存**\]。  
  
### 與新範本與類別  
  
1.  開啟類別檢視。  
  
2.  以滑鼠右鍵按一下在類別檢視中開啟捷徑功能表。  
  
3.  在捷徑功能表中，按一下 \[加入\] 後再按一下 \[加入類別\]。  
  
     這樣會開啟 [加入類別](../ide/add-class-dialog-box.md) 對話方塊。  
  
4.  按兩下 **MFC Class** 範本。  
  
5.  在 [MFC 類別精靈](../mfc/reference/mfc-add-class-wizard.md)上的 \[**類別名稱**\] 方塊中，輸入新對話方塊類別。\(在本例中， `CAddtlPropPage`\)。  
  
6.  如果您要變更檔案名稱，請按一下 **Change**。  輸入名稱以您的實作和標頭檔或接受預設名稱。  
  
7.  在 **Base Class** 方塊中，選取 `COlePropertyPage`。  
  
8.  在 **Dialog ID** 方塊中，選取 **IDD\_PROPPAGE\_NEWPAGE**。  
  
9. 按一下建立類別的 **Finish** 。  
  
 若要允許對這個新的屬性頁中控制項的使用者存取，對控制項的屬性頁 ID 巨集部分進行下列變更 \(位於控制項實作檔\):  
  
 [!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]  
  
 請注意您必須將 `BEGIN_PROPPAGEIDS` 巨集 \(屬性頁面計數\) 從 1 到 2. 的第二個參數。  
  
 您也必須修改控制項實作檔 \(.CPP\) 檔案包含標頭 \(。H\) 新屬性頁類別的檔案。  
  
 下一個步驟包括建立為新的屬性頁會提供型別名稱和標題的兩個新的字串資源。  
  
#### 將新的屬性頁的字串資源  
  
1.  開啟您的專案中，開啟資源檢視。  
  
2.  按兩下 **String Table** 資料夾然後按兩下您要加入資料的現有的字串資料表資源。  
  
     這會在視窗的字串資料表。  
  
3.  選取空白行在字串資料表結尾並輸入文字或標題，字串:例如， 「其他屬性頁」。  
  
     這會開啟以顯示 **Caption** 和 **ID** 方塊 **String Properties** 的頁面。  **Caption** 方塊會包含您輸入的字串。  
  
4.  在 **ID** 方塊中，選取或輸入字串的 ID。  當您完成時，請按 ENTER。  
  
     這個範例會為新的屬性頁的型別名稱使用 **IDS\_SAMPLE\_ADDPAGE** 。  
  
5.  重複使用 **IDS\_SAMPLE\_ADDPPG\_CAPTION** 的步驟 3 和步驟 4 ID 和其他屬性頁的」的標題。  
  
6.  在新的屬性頁類別 .CPP 檔案 \(在此範例中， `CAddtlPropPage`\) 修改 `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` ，以便 IDS\_SAMPLE\_ADDPAGE 透過 [AfxOleRegisterPropertyPageClass](../Topic/AfxOleRegisterPropertyPageClass.md)，如下列範例所示:  
  
     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]  
  
7.  如下所示修改 `CAddtlPropPage` 建構函式，以便 **IDS\_SAMPLE\_ADDPPG\_CAPTION** 傳遞給 `COlePropertyPage` 建構函式，如下所示:  
  
     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]  
  
 在您進行必要的修改重建專案並使用測試容器測試新屬性頁之後。  如需存取測試容器的詳細資訊，請參閱[用測試容器測試屬性和事件](../mfc/testing-properties-and-events-with-test-container.md)。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)