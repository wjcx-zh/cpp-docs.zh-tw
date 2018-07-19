---
title: 加入屬性頁 (ATL 教學課程，第 6 部分) |Microsoft Docs
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
ms.openlocfilehash: 32b89b36318800ff35bc78fee35f094f75bdf36e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848687"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>加入屬性頁 (ATL 教學課程，第 6 部分)
屬性頁會實作為個別的 COM 物件，讓他們所需進行共用。 在此步驟中，您會執行下列工作，以加入至控制項的屬性頁：  
  
-   建立屬性頁資源  
  
-   加入程式碼來建立和管理 [屬性] 頁面  
  
-   將 屬性頁加入至控制項  
  
## <a name="creating-the-property-page-resource"></a>建立屬性頁資源  
 若要加入您的控制項屬性頁，請使用 ATL 加入類別精靈。  
  
#### <a name="to-add-a-property-page"></a>若要加入屬性頁  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下多邊形。  
  
2.  在捷徑功能表，按一下 **新增**，然後按一下**加入類別**。  
  
3.  從範本清單中，選取**ATL 屬性頁**然後按一下**新增**。  
  
4.  ATL 屬性頁精靈出現時，輸入*PolyProp*作為**簡短**名稱。  
  
5.  按一下 **字串**來開啟**字串**頁面，然後輸入 **& 多邊形**作為**標題**。  
  
     **Title**屬性的頁面會顯示在該頁面的索引標籤中的字串。 **文件字串**是屬性框架使用將放在狀態列或工具提示中的描述。 請注意，標準屬性框架目前不使用這個字串，因此您可以將它與預設內容。 您將不會產生**說明檔**目前，所以刪除該文字 方塊中的項目。  
  
6.  按一下 **完成**，就會建立屬性頁物件。  
  
 會建立下列三個檔案：  
  
|檔案|描述|  
|----------|-----------------|  
|PolyProp.h|包含 c + + 類別`CPolyProp`，它會實作的屬性頁。|  
|PolyProp.cpp|包括 PolyProp.h 檔案。|  
|PolyProp.rgs|註冊屬性頁物件登錄指令碼。|  
  
 下列程式碼變更也進行：  
  
-   新的 [屬性] 頁面會新增至 Polygon.cpp 中的物件項目對應。  
  
-   `PolyProp`類別新增至 Polygon.idl 檔案。  
  
-   新的登錄指令碼檔案 PolyProp.rgs 新增至專案資源。  
  
-   對話方塊範本會新增至專案資源屬性頁。  
  
-   您指定的屬性字串會新增至資源字串資料表中。  
  
 現在加入您想要出現在 [屬性] 頁面上的欄位。  
  
#### <a name="to-add-fields-to-the-property-page"></a>若要將欄位加入至屬性頁  
  
1.  在 [方案總管] 中，按兩下 Polygon.rc 資源檔。 這會開啟資源檢視。  
  
2.  在 [資源] 檢視中，展開 [對話方塊] 節點，然後按兩下 IDD_POLYPROP。 請注意出現的對話方塊是空的除了會告訴您插入您的控制項的標籤。  
  
3.  選取該標籤，然後將它變更為讀取`Sides:`更改**標題**中的文字**屬性**視窗。  
  
4.  調整 [標籤] 方塊的大小使其符合文字的大小。  
  
5.  編輯控制項從工具箱拖曳至右邊的標籤。  
  
6.  最後，變更**識別碼**的編輯控制項以`IDC_SIDES`使用 [屬性] 視窗。  
  
 如此即完成建立屬性頁資源的程序。  
  
## <a name="adding-code-to-create-and-manage-the-property-page"></a>加入程式碼來建立和管理 [屬性] 頁面  
 既然您已建立的屬性頁面的資源，您需要撰寫實作程式碼。  
  
 首先，讓`CPolyProp`類別來設定邊數在您的物件時**套用**按下按鈕時。  
  
#### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>若要修改設定邊數套用函式  
  
1.  取代`Apply`PolyProp.h 中的函式，以下列程式碼：  
  
     [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]  
  
 屬性頁可以有一個以上的用戶端一次連結，因此`Apply`函式的迴圈循環，並呼叫`put_Sides`具有值的每個用戶端上從 編輯方塊。 您使用[CComQIPtr](../atl/reference/ccomqiptr-class.md)類別，它會執行`QueryInterface`以取得每個物件上`IPolyCtl`從介面`IUnknown`介面 (儲存在`m_ppUnk`陣列)。  
  
 程式碼現在會檢查該設定`Sides`實際運作的屬性。 如果失敗，程式碼會顯示訊息方塊顯示錯誤詳細資料，從`IErrorInfo`介面。 通常，容器會要求的物件`ISupportErrorInfo`介面，並呼叫`InterfaceSupportsErrorInfo`第一，若要判斷物件是否支援設定資訊時發生錯誤。 您可以略過這項工作。  
  
 [CComPtr](../atl/reference/ccomptr-class.md)可協助您藉由自動處理參考計數，因此您不需要呼叫`Release`介面上。 `CComBSTR` 可協助您進行 BSTR 處理，因此您不需要執行最後`SysFreeString`呼叫。 您也使用其中一個不同的字串轉換類別，因此必要 （這就是為什麼 USES_CONVERSION 巨集是函式的開頭） 時，您可以將轉換的 BSTR。  
  
 您也需要設定屬性頁的 變更旗標，指出**套用**按鈕應會啟用。 當使用者變更中的值時，發生這種的情況**邊**編輯方塊。  
  
#### <a name="to-handle-the-apply-button"></a>處理套用按鈕  
  
1.  在 類別 檢視中，於 CPolyProp 上按一下滑鼠右鍵，然後按一下 **屬性**快顯功能表。  
  
2.  在 [屬性] 視窗中，按一下**事件**圖示。  
  
3.  展開`IDC_SIDES`節點事件清單中。  
  
4.  選取  `EN_CHANGE`，然後從右側下拉式選單，按一下  **\<新增 > OnEnChangeSides**。 `OnEnChangeSides`處理常式宣告將會新增至 Polyprop.h 和 Polyprop.cpp 的處理常式實作。  
  
 接下來，您將修改這個處理常式。  
  
#### <a name="to-modify-the-onenchangesides-method"></a>若要修改 OnEnChangeSides 方法  
  
1.  下列程式碼增益集至 Polyprop.cpp `OnEnChangeSides` （刪除其中的精靈將放入那里任何程式碼） 的方法：  
  
     [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]  
  
 `OnEnChangeSides` WM_COMMAND 訊息傳送與 EN_CHANGE 通知時，將會呼叫`IDC_SIDES`控制項。 `OnEnChangeSides` 然後呼叫`SetDirty`，並將傳遞 TRUE 表示 [屬性] 頁面現在已變更而**套用**按鈕應會啟用。  
  
## <a name="adding-the-property-page-to-the-control"></a>將 屬性頁加入至控制項  
 ATL 新增類別精靈] 及 [ATL 屬性頁精靈不要將屬性頁到您的控制項為您自動執行，因為您的專案中可能有多個控制項。 您必須將項目加入至控制項的屬性對應。  
  
#### <a name="to-add-the-property-page"></a>若要加入屬性頁  
  
1.  開啟 PolyCtl.h，並將這一行加入至屬性對應：  
  
     [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]  
  
 控制項的屬性對應現在看起來像這樣：  
  
 [!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]  
  
 您可以新增 PROP_PAGE 巨集的屬性頁面，但是如果如所示，使用巨集 PROP_ENTRY clsid`Sides`儲存控制項時，也會儲存屬性值。  
  
 巨集的三個參數是屬性的 DISPID，在其上具有屬性的屬性頁 CLSID 的屬性描述。 如果，比方說，載入 Visual Basic 中的控制項，而且在設計階段設定邊數，這非常有用。 因為儲存邊數時，當您重新載入 Visual Basic 專案，將會還原邊數。  
  
## <a name="building-and-testing-the-control"></a>建置和測試控制項  
 立即建立該控制項，並將它插入 ActiveX 控制項測試容器。 在測試容器中，在**編輯**功能表上，按一下**PolyCtl 類別物件**。 [屬性] 頁面隨即出現;按一下 [**多邊形**] 索引標籤。  
  
 **套用**一開始會停用按鈕。 開始輸入中的值**邊** 方塊中，**套用**按鈕會變成啟用狀態。 您完成輸入值之後，請按一下**套用** 按鈕。 控制項顯示中有所變更，而**套用**按鈕再次停用。 請嘗試輸入無效的值。 您會看到包含您從設定的錯誤描述的訊息方塊`put_Sides`函式。  
  
 接下來，您會將您在網頁上的控制項。  
  
 [回到步驟 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [至步驟 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)

