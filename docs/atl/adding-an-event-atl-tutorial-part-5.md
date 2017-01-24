---
title: "加入事件 (ATL 教學課程，第 5 部分) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入事件 (ATL 教學課程，第 5 部分)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在這個步驟中，您會將 `ClickIn` 和一 `ClickOut` 事件加入至 ATL 控制項。  您將會引發 `ClickIn` 事件，當使用者在多邊形和引發 `ClickOut` 內按一下 ，如果使用者按一下外部。  工作會將事件如下:  
  
-   將 `ClickIn` 和 `ClickOut` 方法  
  
-   產生型別程式庫。  
  
-   介面實作連接點。  
  
## 將 ClickIn 和 ClickOut 方法  
 當您在步驟 2 中的 ATL 控制項，您選擇 \[**連接點**\] 核取方塊。  這會在 Polygon.idl 檔案的 `_IPolyCtlEvents` 介面。  請注意介面名稱是以底線。  這是表示慣例介面是一個內部介面。  因此，可讓您瀏覽 COM 物件的程式可以選擇不要顯示給使用者的介面。  同時也請注意 \[**連接點**\] 的選項會增加在 Polygon.idl 檔的下列這一行表示 `_IPolyCtlEvents` 是預設來源介面:  
  
 `[default, source] dispinterface _IPolyCtlEvents;`  
  
 來源屬性表示控制項是告知來源，如此，便會呼叫在容器的介面。  
  
 現在加入 `ClickIn` ，而且 `_IPolyCtlEvents` 的 `ClickOut` 方法連接。  
  
#### 將 ClickIn 和 ClickOut 方法  
  
1.  在 \[類別檢視\] 中，展開多邊形和 PolygonLib 顯示 \_IPolyCtlEvents。  
  
2.  以滑鼠右鍵按一下 \_IPolyCtlEvents。  在捷徑功能表中按一下 \[加入\]，再按一下 \[加入方法\]。  
  
3.  選取 `void`\[**傳回型別**\] 。  
  
4.  在  方塊中輸入 \[**方法名稱**\] 的 `ClickIn` 。  
  
5.  在 \[**參數屬性**\] 底下，選取  方塊中 \[**在**\] 。  
  
6.  選取 `LONG`\[**參數型別**\] 。  
  
7.  輸入 `x` 做為 \[**參數名稱**\]，然後按一下 \[**新增**\]。  
  
8.  重複步驟 5 到 7， y. \[**參數名稱**\] 的這個。  
  
9. 按一下 \[**下一步**\]。  
  
10. 輸入 `方法 ClickIn` 做為 \[**helpstring**\]。  
  
11. 按一下 \[**完成**\]。  
  
12. 重複上述步驟定義具有相同 `LONG` 參數 `x` 和 `y`，相同的 \[**參數屬性**\] 的 `ClickOut` 方法和相同 `void` 傳回型別。  
  
 檢查 Polygon.idl 檔案來查看程式碼加入至 `_IPolyCtlEvents` 分配介面。  
  
 在您的 Polygon.idl 檔案的 `_IPolyCtlEvents` 分配介面現在應該如下所示:  
  
 [!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/CPP/adding-an-event-atl-tutorial-part-5_1.idl)]  
  
 `ClickIn` 和 `ClickOut` 方法採用按的點的 X 和 Y 座標做為參數。  
  
## 產生型別程式庫。  
 此時會產生型別程式庫，，因為連接點精靈將使用它需要建構一個連接點介面的連接點介面容器控制項會取得資訊。  
  
#### 產生型別程式庫。  
  
1.  重建專案。  
  
     \-或\-  
  
2.  以滑鼠右鍵按一下 \[方案總管\] 中的 Polygon.idl 檔案並按一下 \[**編譯**\] 在捷徑功能表上的 。  
  
 這會建立 Polygon.tlb 檔，為您的型別程式庫。  因為這是二進位檔案，不能直接，檢視或編輯 Polygon.tlb 檔案從 \[方案總管\] 中看不到。  
  
## 介面實作連接點。  
 實作連接點介面的連接點介面容器控制項的。  在 COM 中，事件是透過連接點機制來實作。  若要接收 COM 物件的事件，容器會建立與該連接點的諮詢連接實作的 COM 物件。  由於 COM 物件可以有多個連接點，則 COM 物件也實作連接點容器介面。  透過這個介面，容器可以判斷連接點支援。  
  
 實作連接點的介面呼叫 `IConnectionPoint`和實作連接點容器的介面呼叫 `IConnectionPointContainer`。  
  
 若要協助實作 `IConnectionPoint`，您會使用實作連接點精靈。  這個精靈可藉由讀取您的型別程式庫和實作可引發之事件的每一個函式產生 `IConnectionPoint` 介面。  
  
#### 使用實作連接點精靈  
  
1.  在 \[類別檢視\] 中，以滑鼠右鍵按一下控制項的實作類別 `CPolyCtl`。  
  
2.  在捷徑功能表上，按一下 \[**新增**\]，然後按一下 \[**加入連接點**\]。  
  
3.  選取 `_IPolyCtlEvents` 從 \[**來源介面**\] 清單並按兩下將它加入 \[**實作連接點。**\] 資料行。  按一下 \[**完成**\]。  連接點的 Proxy 類別，產生在這種情況下， `CProxy_IPolyCtlEvents`。  
  
 如果您在 \[方案總管\] 中查看產生的 \_IPolyCtlEvents\_CP.h 檔案，您會看到它具有從 `IConnectionPointImpl`取得呼叫 `CProxy_IPolyCtlEvents` 的類別。  \_IPolyCtlEvents\_CP.h 也定義了這兩個方法 `Fire_ClickIn` 和 `Fire_ClickOut`，會使用兩個同等的參數。  例如，當您想要引發從您的控制項時，會發生事件並呼叫這些方法。  
  
 精靈也會加入 `CProxy_PolyEvents` 和 `IConnectionPointContainerImpl` 至控制項的多重繼承清單。  升級精靈會將適當的項目也會公開了 `IConnectionPointContainer` 至 COM 對應。  
  
 您完成實作程式碼支援事件。  現在，加入一些程式碼來逢其餘時引發事件。  當使用者按一下控制項中，以滑鼠左鍵請記住，您 `ClickIn``ClickOut` 引發或事件。  若要知道使用者何時按一下按鈕，請將 `WM_LBUTTONDOWN` 訊息的處理常式。  
  
#### 將 WM\_LBUTTONDOWN 訊息處理常式  
  
1.  在 \[類別檢視\] 中，以滑鼠右鍵按一下 CPolyCtl 類別並按一下 \[**屬性**\] 在捷徑功能表上的 。  
  
2.  在 \[**屬性**\] 視窗，請按一下 \[**訊息**\] 圖示然後按一下清單中的 `WM_LBUTTONDOWN` 左邊。  
  
3.  從顯示的  下拉式清單中，按一下 \[**\<Add\> OnLButtonDown**\]。  `OnLButtonDown` 處理常式宣告加入至 PolyCtl.h，，處理常式實作會加入至 PolyCtl.cpp。  
  
 接下來，修改這個處理常式。  
  
#### 修改 OnLButtonDown 方法  
  
1.  將包含在 PolyCtl.cpp 的 `OnLButtonDown` 方法的程式碼 \(刪除精靈中的任何程式碼\)，讓它看起來像這樣:  
  
     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/CPP/adding-an-event-atl-tutorial-part-5_2.cpp)]  
  
 這個程式碼使用在 `OnDraw` 函式計算的點會偵測具有呼叫的使用者用滑鼠按一下 \[ `PtInRegion`的區域。  
  
 `uMsg` 參數已處理的 Windows 訊息的 ID。  這可讓您設定處理訊息的範圍的函式。  `wParam` 和 `lParam` 參數已處理訊息的標準值。  bHandled 的參數可讓您指定是否函式處理該訊息。  根據預設，這個值設定為 `TRUE` 指出函式處理該訊息，不過，您也可以將其設定為 `FALSE`。  這會導致 ATL 繼續搜尋其他訊息處理常式 \(Message Handler\) 函式會傳送訊息。  
  
## 建置和測試控制項  
 現在請試用您的事件。  建立控制項並重新啟動 ActiveX 控制項測試容器。  此時，檢視事件記錄視窗。  若要將事件加入至 \[輸出\] 視窗中，按一下  功能表上的 \[**選項**\]\[**記錄**\] 並選取 \[**輸出視窗中的記錄**\]。  按一下插入這個控制項與嘗試在視窗中。  請注意 `ClickIn` 引發，如果您在已填滿的多邊形內，按一下 ，然後 `ClickOut` 引發，當您按一下外部時。  
  
 接下來，您會將  屬性頁。  
  
 [回到步驟 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [在 &#91;步驟 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## 請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)