---
title: 加入屬性頁 (ATL 教學課程，第 6 部分) |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf7f0383697fbc1e23e179936a2616d1d236b5f2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361586"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>加入屬性頁 (ATL 教學課程，第 6 部分)
屬性頁會實作為個別的 COM 物件，讓他們所需進行共用。 在此步驟中，您將進行下列工作，以加入至控制項的屬性頁：  
  
-   建立屬性頁資源  
  
-   加入程式碼，來建立和管理 屬性頁  
  
-   控制項中加入屬性頁  
  
## <a name="creating-the-property-page-resource"></a>建立屬性頁資源  
 若要加入您的控制項屬性頁，請使用 ATL 加入類別精靈。  
  
#### <a name="to-add-a-property-page"></a>若要加入屬性頁  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下多邊形。  
  
2.  在捷徑功能表，按一下 **新增**，然後按一下 **加入類別**。  
  
3.  從範本清單中，選取**ATL 屬性頁**按一下**新增**。  
  
4.  ATL 屬性頁精靈出現時，請輸入`PolyProp`為**簡短**名稱。  
  
5.  按一下**字串**開啟**字串**頁面上，輸入 **& 多邊形**為**標題**。  
  
     **標題**屬性的頁面會出現在該頁面的索引標籤的字串。 **文件字串**是暫停狀態列或工具提示中使用屬性框架的描述。 請注意，標準屬性畫面格目前不會使用這個字串，所以您可以將它與預設內容。 您將不會產生**說明檔**目前，所以刪除該文字方塊中的項目。  
  
6.  按一下**完成**，就會建立屬性頁物件。  
  
 會建立下列三個檔案：  
  
|檔案|描述|  
|----------|-----------------|  
|PolyProp.h|包含 c + + 類別`CPolyProp`，它會實作的屬性頁。|  
|PolyProp.cpp|包含 PolyProp.h 檔案。|  
|PolyProp.rgs|註冊屬性頁物件登錄指令碼。|  
  
 下列程式碼變更也進行：  
  
-   物件項目對應 Polygon.cpp 中會加入新的屬性頁。  
  
-   `PolyProp`類別新增至 Polygon.idl 檔案。  
  
-   新的登錄指令碼檔 PolyProp.rgs 隨即加入至專案資源。  
  
-   對話方塊範本會加入至專案資源的屬性頁。  
  
-   您指定的屬性字串會新增至資源字串資料表。  
  
 現在加入您想要顯示在 [屬性] 頁面上的欄位。  
  
#### <a name="to-add-fields-to-the-property-page"></a>將欄位加入至屬性頁  
  
1.  在 [方案總管] 中，按兩下 Polygon.rc 資源檔。 這會開啟 資源檢視。  
  
2.  在資源檢視中，展開 [對話方塊] 節點，然後按兩下 IDD_POLYPROP。 請注意，出現的對話方塊是空的除了會告訴您插入您的控制項的標籤。  
  
3.  選取該標籤，並將它變更為讀取`Sides:`藉由改變**標題**中的文字**屬性**視窗。  
  
4.  調整 [標籤] 方塊的大小，使其符合文字的大小。  
  
5.  編輯控制項從工具箱拖曳至右邊的標籤。  
  
6.  最後，變更**識別碼**編輯控制項的`IDC_SIDES`使用 [屬性] 視窗。  
  
 如此即完成建立屬性頁資源的程序。  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>加入程式碼，來建立和管理 屬性頁  
 既然您已經建立的屬性頁面的資源，您需要撰寫實作程式碼。  
  
 首先，啟用`CPolyProp`類別來設定在物件中的邊數時**套用**按下按鍵時。  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>若要修改設定的側邊數目套用函式  
  
1.  取代`Apply`PolyProp.h 中以下列程式碼的函式：  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 屬性頁可以有一個以上的用戶端一次附加所以`Apply`函式執行迴圈周圍，並呼叫`put_Sides`值的每個用戶端上擷取的編輯方塊中。 您使用[CComQIPtr](../atl/reference/ccomqiptr-class.md)類別，會執行`QueryInterface`來取得每個物件上`IPolyCtl`介面從**IUnknown**介面 (儲存在`m_ppUnk`陣列)。  
  
 程式碼現在會檢查該設定`Sides`實際運作的屬性。 如果失敗，程式碼會顯示訊息方塊顯示錯誤詳細資料，從**IErrorInfo**介面。 通常，容器會要求的物件**ISupportErrorInfo**介面並呼叫`InterfaceSupportsErrorInfo`第一個，以判斷物件是否支援設定資訊時發生錯誤。 您可以略過這項工作。  
  
 [CComPtr](../atl/reference/ccomptr-class.md)可協助您藉由自動處理 參考計數，因此您不需要呼叫`Release`介面上。 `CComBSTR` 可協助您與`BSTR`處理，因此您不需要執行最終`SysFreeString`呼叫。 也使用其中一種不同的字串轉換類別，讓您可以轉換`BSTR`視 (這就是為什麼`USES_CONVERSION`巨集是在函式的開頭)。  
  
 您也需要設定屬性頁的記錄變更旗標，指出**套用**按鈕應會啟用。 使用者變更中的值時，發生這種的情況**邊**編輯方塊。  
  
#### <a name="to-handle-the-apply-button"></a>若要處理套用按鈕  
  
1.  在 類別檢視中，於 CPolyProp 上按一下滑鼠右鍵，然後按一下**屬性**快顯功能表。  
  
2.  在 [屬性] 視窗中，按一下**事件**圖示。  
  
3.  展開`IDC_SIDES`節點事件清單中。  
  
4.  選取`EN_CHANGE`，並從右邊下拉式功能表按一下**\<新增 > OnEnChangeSides**。 `OnEnChangeSides`處理常式宣告將會加入至 Polyprop.h 和 Polyprop.cpp 的處理常式實作。  
  
 接下來，您將修改此處理常式。  
  
#### <a name="to-modify-the-onenchangesides-method"></a>若要修改 OnEnChangeSides 方法  
  
1.  下列程式碼加入至 Polyprop.cpp 中`OnEnChangeSides`（刪除精靈將放入那里任何程式碼） 的方法：  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides` 時將會呼叫**WM_COMMAND**訊息傳送時附有**EN_CHANGE**通知`IDC_SIDES`控制項。 `OnEnChangeSides` 然後呼叫`SetDirty`並傳遞`TRUE`是表示此屬性現在已損毀頁面和**套用**按鈕應會啟用。  
  
## <a name="adding-the-property-page-to-the-control"></a>控制項中加入屬性頁  
 ATL 加入類別精靈和 ATL 屬性頁精靈不要將屬性頁到您的控制項為您自動執行，因為專案中可能有多個控制項。 您必須將項目加入至控制項的屬性對應。  
  
#### <a name="to-add-the-property-page"></a>若要加入屬性頁  
  
1.  開啟 PolyCtl.h 並新增這行的屬性對應：  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 控制項的屬性對應現在看起來像這樣：  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 您可以加入`PROP_PAGE`巨集的屬性頁面，但是如果您使用 clsid`PROP_ENTRY`巨集所示，`Sides`儲存控制項時，也會儲存屬性值。  
  
 巨集的三個參數是屬性的 DISPID 和其上已有此屬性的屬性頁 CLSID 的屬性描述。 如果，例如 Visual Basic 中載入控制項，並在設計階段設定的邊數，這非常有用。 因為儲存邊數，當您重新載入您的 Visual Basic 專案，將會還原邊數。  
  
## <a name="building-and-testing-the-control"></a>建置和測試控制項  
 立即建立該控制項，並將它插入 ActiveX 控制項測試容器。 測試容器中上**編輯**功能表上，按一下  **PolyCtl 類別物件**。 屬性頁隨即出現。按一下**多邊形** 索引標籤。  
  
 **套用**一開始會停用按鈕。 開始輸入中的值**邊**方塊和**套用**按鈕會變成啟用狀態。 當您完成輸入值之後，按一下**套用** 按鈕。 控制項的顯示變更，而**套用**按鈕再次停用。 請嘗試輸入無效的值。 您會看到訊息方塊包含錯誤描述，您從設定`put_Sides`函式。  
  
 接下來，您會將您在網頁上的控制項。  
  
 [步驟 5 至](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [至步驟 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)

