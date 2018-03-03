---
title: "加入事件 (ATL 教學課程，第 5 部分) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c42befe57bdc7a01da31bd6c4e010458e1d3ba7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>加入事件 (ATL 教學課程，第 5 部分)
在此步驟中，您將加入`ClickIn`和`ClickOut`ATL 控制項的事件。 您將會引發`ClickIn`如果使用者在多邊形和引發事件`ClickOut`外部使用者。 要加入事件的工作如下所示：  
  
-   加入`ClickIn`和`ClickOut`方法  
  
-   產生類型程式庫  
  
-   實作連接點介面  
  
## <a name="adding-the-clickin-and-clickout-methods"></a>加入 ClickIn 和 ClickOut 方法  
 當您在步驟 2 中建立 ATL 控制項時，您選取**連接點**核取方塊。 這會建立`_IPolyCtlEvents`Polygon.idl 檔案中的介面。 請注意，介面名稱以底線開頭。 這是表示此介面是內部介面慣例。 因此，讓您瀏覽 COM 物件的程式可以選擇不顯示使用者介面。 也請注意，選取**連接點**表示 Polygon.idl 檔案中加入下列這一行`_IPolyCtlEvents`是預設來源介面：  
  
 `[default, source] dispinterface _IPolyCtlEvents;`  
  
 來源屬性表示控制項來源的通知，因此它會在容器上呼叫這個介面。  
  
 現在，加入`ClickIn`和`ClickOut`方法`_IPolyCtlEvents`介面。  
  
#### <a name="to-add-the-clickin-and-clickout-methods"></a>若要加入的 ClickIn 和 ClickOut 方法  
  
1.  類別檢視 中展開多邊形和 PolygonLib 顯示 _IPolyCtlEvents。  
  
2.  以滑鼠右鍵按一下 _IPolyCtlEvents。 在捷徑功能表，按一下 **新增**，然後按一下 **加入方法**。  
  
3.  選取**傳回型別**的`void`。  
  
4.  輸入`ClickIn`中**方法名稱**方塊。  
  
5.  在下**參數屬性**，選取**中**方塊。  
  
6.  選取**參數型別**的`LONG`。  
  
7.  型別`x`為**參數名稱**，然後按一下**新增**。  
  
8.  重複步驟 5 到 7，這次**參數名稱**的`y`。  
  
9. 按 [ **下一步**]。  
  
10. 型別`method ClickIn`為**helpstring**。  
  
11. 按一下 [ **完成**]。  
  
12. 重複上述步驟，以定義`ClickOut`方法具有相同`LONG`參數`x`和`y`，相同**參數屬性**和相同`void`傳回型別。  
  
 檢查 Polygon.idl 檔，請參閱程式碼已加入至`_IPolyCtlEvents`分配介面。  
  
 `_IPolyCtlEvents` Polygon.idl 檔案中的分配介面現在看起來應該像這樣：  
  
 [!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_1.idl)]  
  
 `ClickIn`和`ClickOut`方法接受 x 和 y 座標的按下點，做為參數。  
  
## <a name="generating-the-type-library"></a>產生類型程式庫  
 此時，產生類型程式庫，因為連接點精靈會使用它來取得所建構的連接點介面和連接點容器介面控制項所需的資訊。  
  
#### <a name="to-generate-the-type-library"></a>若要產生類型程式庫  
  
1.  重建專案。  
  
     -或-  
  
2.  以滑鼠右鍵按一下方案總管 中的 Polygon.idl 檔，然後按一下**編譯**快顯功能表。  
  
 這會建立 Polygon.tlb 檔案，也就是類型程式庫。 Polygon.tlb 檔案不可見方案總管 中，因為它是二進位檔案，無法檢視或直接編輯。  
  
## <a name="implementing-the-connection-point-interfaces"></a>實作連接點介面  
 實作連接點介面和連接點容器控制項的介面。 在 COM 中，透過連接點的機制中實作事件。 若要接收事件，從 COM 物件，容器會建立諮詢連接的 COM 物件實作連接點。 COM 物件可以有多個連接點，因為 COM 物件也會實作連接點容器介面。 透過這個介面，容器就可以判斷哪一個連接點支援。  
  
 實作連接點的介面稱為`IConnectionPoint`，並實作連接點容器的介面稱為`IConnectionPointContainer`。  
  
 若要協助實作`IConnectionPoint`，您將使用實作連接點精靈。 這個精靈會產生`IConnectionPoint`讀取類型程式庫，並實作每個事件都可以引發的函式的介面。  
  
#### <a name="to-use-the-implement-connection-point-wizard"></a>若要使用實作連接點精靈  
  
1.  在 類別檢視，以滑鼠右鍵按一下控制項的實作類別`CPolyCtl`。  
  
2.  在捷徑功能表，按一下 **新增**，然後按一下 **加入連接點**。  
  
3.  選取`_IPolyCtlEvents`從**來源介面**清單，然後按兩下以將它加入至**實作連接點**資料行。 按一下 [ **完成**]。 連接點的 proxy 類別，將會產生在此情況下， `CProxy_IPolyCtlEvents`。  
  
 如果您看一下產生的 _IPolyCtlEvents_CP.h 檔案，在 [方案總管] 中，您會看到它有一種類別稱為`CProxy_IPolyCtlEvents`衍生自`IConnectionPointImpl`。 _IPolyCtlEvents_CP.h 也可以定義兩個方法`Fire_ClickIn`和`Fire_ClickOut`，這需要兩個座標的參數。 當您想要引發的事件，從您的控制項時，您可以呼叫這些方法。  
  
 精靈也加入`CProxy_PolyEvents`和`IConnectionPointContainerImpl`至控制項的多個繼承的清單。 精靈也公開`IConnectionPointContainer`讓您藉由新增適當的項目到 COM 對應。  
  
 您已完成實作支援事件的程式碼。 現在，加入一些程式碼以在適當時間引發事件。 請記住，您要引發`ClickIn`或`ClickOut`時使用者按下滑鼠左的按鈕控制項中的事件。 若要了解，當使用者按一下按鈕，加入的處理常式`WM_LBUTTONDOWN`訊息。  
  
#### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>若要加入 WM_LBUTTONDOWN 訊息的處理常式  
  
1.  在 類別檢視中，於 CPolyCtl 類別上按一下滑鼠右鍵，然後按一下**屬性**快顯功能表。  
  
2.  在**屬性**視窗中，按一下 **訊息**圖示，然後按一下`WM_LBUTTONDOWN`從左側清單。  
  
3.  從出現的下拉式清單中，按一下  **\<新增 > OnLButtonDown**。 `OnLButtonDown` PolyCtl.h，將會加入處理常式宣告和 PolyCtl.cpp 將會加入處理常式實作。  
  
 接下來，修改此處理常式。  
  
#### <a name="to-modify-the-onlbuttondown-method"></a>若要修改 OnLButtonDown 方法  
  
1.  變更程式碼所組成， `OnLButtonDown` PolyCtl.cpp （刪除精靈所放置的任何程式碼） 中的方法，讓它看起來像這樣：  
  
     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]  
  
 這點的使用中的計算的程式碼會讓`OnDraw`函式來建立偵測到使用者的滑鼠點按的呼叫與區域`PtInRegion`。  
  
 `uMsg`參數是要處理視窗訊息的識別碼。 這可讓您擁有一個函式，會處理一個範圍的訊息。 `wParam`和`lParam`參數是要處理訊息的標準值。 參數 bHandled 可讓您指定函式或不處理訊息。 根據預設，此值設定為`TRUE`，表示函式會處理訊息，但是您可以將它設定為`FALSE`。 這會導致 ATL 繼續尋找來傳送訊息給另一個訊息處理常式函式。  
  
## <a name="building-and-testing-the-control"></a>建置和測試控制項  
 現在，請測試您的事件。 建置控制項，然後重新啟動 ActiveX 控制項測試容器。 此時，請檢視 [事件記錄檔] 視窗。 若要將事件傳送至 [輸出] 視窗中，按一下**記錄**從**選項**功能表，然後選取**記錄到輸出視窗**。 插入控制項並嘗試按一下視窗中。 請注意，`ClickIn`若之內填滿的多邊形，請按一下引發和`ClickOut`外部按一下時引發。  
  
 接下來，您會加入屬性頁。  
  
 [步驟 4 至](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)&#124;[至步驟 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="see-also"></a>請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)

