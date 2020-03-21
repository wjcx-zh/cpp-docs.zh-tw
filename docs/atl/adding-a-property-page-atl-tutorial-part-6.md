---
title: 加入屬性頁 (ATL 教學課程，第 6 部分)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: 467ae19c372e24b2d368002cb83367b7087136fd
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078775"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>加入屬性頁 (ATL 教學課程，第 6 部分)

> [!NOTE]
> Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

屬性頁會實作為個別的 COM 物件，以便在需要時能夠共用它們。 在此步驟中，您將執行下列工作來將屬性頁加入至控制項：

- 建立屬性頁資源

- 加入程式碼來建立及管理屬性頁

- 將屬性頁加入至控制項

## <a name="creating-the-property-page-resource"></a>建立屬性頁資源

若要將屬性頁加入至控制項，請使用 ATL 屬性頁範本。

### <a name="to-add-a-property-page"></a>加入屬性頁

1. 在 [方案總管] 中，以滑鼠右鍵按一下 `Polygon`。

1. 在捷徑功能表上，按一下 [加入] > [新增項目]。

1. 從範本清單中，選取[ATL] > [ATL 屬性頁]，然後按一下 [加入]。

1. 當 [ATL 屬性頁精靈] 出現時，輸入 *PolyProp* 作為**簡短**名稱。

1. 按一下 [字串] 以開啟 [字串] 頁面，然後輸入**多邊形(&P)** 作為**標題**。

   屬性頁的**標題**為出現在該頁面的索引標籤中的字串。 **文件字串**是屬性框架用來放入狀態列或工具提示的描述。 請注意，標準屬性框架目前不會使用這個字串，因此，您可以使其保留預設內容。 您目前將不會產生**說明檔**，因此，請刪除該文字方塊中的項目。

1. 按一下 [完成]，即會建立屬性頁物件。

隨即建立下列三個檔案：

|檔案|描述|
|----------|-----------------|
|PolyProp.h|包含 C++ 類別 `CPolyProp`，其會實作屬性頁。|
|PolyProp.cpp|包括 PolyProp.h 檔案。|
|PolyProp.rgs|註冊屬性頁物件的登錄指令碼。|

此外，也會進行下列程式碼變更：

- 將新的屬性頁加入至 Polygon.cpp 中的物件項目對應。

- 將 `PolyProp` 類別加入至 Polygon.idl 檔案。

- 將新的登錄指令檔 PolyProp.rgs 加入至專案資源。

- 將對話方塊範本加入至屬性頁的專案資源。

- 將您指定的屬性字串加入至資源字串資料表。

現在加入您希望出現在屬性頁上的欄位。

### <a name="to-add-fields-to-the-property-page"></a>將欄位加入至屬性頁

1. 在 [方案總管] 中，按兩下 Polygon.rc 資源檔。 這將會開啟 [資源檢視]。

1. 在 [資源檢視] 中，展開 `Dialog` 節點，然後按兩下 `IDD_POLYPROP`。 請注意，除了告訴您在此處插入您的控制項的標籤外，出現的對話方塊會是空的。

1. 選取該標籤，然後透過更改 [屬性]`Sides:` **視窗中的**標題**文字，來變更它以標明** 。

1. 調整標籤方塊的大小，以使其符合文字的大小。

1. 將**編輯控制項**從**工具箱**拖曳到標籤右邊。

1. 最後，使用 [屬性] 視窗來將編輯控制項的`IDC_SIDES`識別碼**變更為** 。

這樣即可完成建立屬性頁資源的流程。

## <a name="adding-code-to-create-and-manage-the-property-page"></a>加入程式碼來建立及管理屬性頁

既然您已建立屬性頁資源，您現在需要撰寫實作程式碼。

首先，在按下 [套用]`CPolyProp`**按鈕時，啟用** 類別以在物件中設定邊數。

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>修改 Apply 函式以設定邊數

1. 使用下列程式碼來取代 PolyProp.h 中的 `Apply` 函式：

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

屬性頁一次可附加一個以上的用戶端，因此，`Apply` 函式會進行迴圈循環，並使用擷取自編輯方塊的值來呼叫每個用戶端上的 `put_Sides`。 您正在使用 [CComQIPtr](../atl/reference/ccomqiptr-class.md) 類別，其會在每個物件上執行 `QueryInterface`，以從 `IPolyCtl` 介面 (儲存於 `IUnknown` 陣列) 中取得`m_ppUnk` 介面。

程式碼現在會檢查 `Sides` 屬性實際運作的設定。 如果失敗，程式碼就會顯示一個訊息方塊，其中顯示來自 `IErrorInfo` 介面的錯誤詳細資料。 通常，容器會要求 `ISupportErrorInfo` 介面的物件，並先呼叫 `InterfaceSupportsErrorInfo` 來判斷該物件是否支援設定錯誤資訊。 您可以略過此工作。

[CComPtr](../atl/reference/ccomptr-class.md) 會透過自動處理參考計數來協助您，因此，您不需要在介面上呼叫 `Release`。 `CComBSTR` 會使用 BSTR 處理來協助您，因此，您不需要執行最後一個 `SysFreeString` 呼叫。 您也會使用各種不同字串轉換類別的其中一種，因此，可視需要轉換 BSTR (這就是為什麼 USES_CONVERSION 巨集會在函式開頭)。

您也需要設定屬性頁的記錄變更旗標，以指出應啟用 [套用] 按鈕。 當使用者變更 [側邊] 編輯方塊中的值時，就會發生此情況。

### <a name="to-handle-the-apply-button"></a>處理套用按鈕

1. 在 [類別檢視] 中，以滑鼠右鍵按一下 `CPolyProp`，然後按一下捷徑功能表上的 [屬性]。

1. 在 [屬性] 視窗中，按一下 [事件] 圖示。

1. 在事件清單中展開 `IDC_SIDES` 節點。

1. 選取 `EN_CHANGE`，然後從右側的下拉式功能表中，按一下 [**新增> OnEnChangeSides]\<** 。 `OnEnChangeSides` 處理常式宣告將加入至 Polyprop.h，並將處理常式實作加入至 Polyprop.cpp。

接下來，您將修改此處理常式。

### <a name="to-modify-the-onenchangesides-method"></a>修改 OnEnChangeSides 方法

1. 將 Polyprop.cpp 中的下列程式碼加入至 `OnEnChangeSides` 方法 (刪除精靈放入在那裡的任何程式碼)：

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

針對 `OnEnChangeSides` 控制項使用 `WM_COMMAND` 通知傳送 `EN_CHANGE` 訊息時，將會呼叫 `IDC_SIDES`。 `OnEnChangeSides` 接著會呼叫 `SetDirty` 並傳遞 TRUE，以指出屬性頁現在已進行記錄變更且應啟用 [套用] 按鈕。

## <a name="adding-the-property-page-to-the-control"></a>將屬性頁加入至控制項

ATL 屬性頁範本和精靈不會自動將屬性頁加入至您的控制項，因為您的專案中可能有多個控制項。 您必須將項目加入至控制項的屬性對應。

### <a name="to-add-the-property-page"></a>加入屬性頁

1. 開啟 PolyCtl.h，並將下列數行加入至屬性對應：

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

控制項的屬性對應現在看起來像這樣：

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

您可以使用屬性頁的 CLSID 來加入 `PROP_PAGE` 巨集，但若您使用 `PROP_ENTRY` 巨集 (如同所示)，則在儲存控制項時，也會儲存 `Sides` 屬性值。

巨集的三個參數為屬性描述、屬性的 DISPID，以及其上有屬性的屬性頁 CLSID。 例如，如果您將控制項載入至 Visual Basic 並在設計階段設定邊數，則這非常有用。 由於會儲存邊數，因此，當您重新載入 Visual Basic 專案，將會還原邊數。

## <a name="building-and-testing-the-control"></a>建置和測試控制項

立即建置該控制項，並將它插入至 ActiveX 控制項測試容器。 在 [測試容器] 的 [編輯] 功能表上，按一下 [PolyCtl 類別物件]。 屬性頁隨即顯示，其中含有您加入的資訊。

一開始會停用 [套用] 按鈕。 開始在 [側邊] 方塊中輸入值，而 [套用] 按鈕將會變成啟用狀態。 當您完成輸入值之後，按一下 [套用] 按鈕。 控制項會顯示變更，並再次停用 [套用] 按鈕。 請嘗試輸入無效的值。 您將會看到一個訊息方塊，其中包含您從 `put_Sides` 函式設定的錯誤描述。

接下來，您要將控制項放在網頁上。

[回到步驟 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [前往步驟 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>另請參閱

[教學課程](../atl/active-template-library-atl-tutorial.md)
