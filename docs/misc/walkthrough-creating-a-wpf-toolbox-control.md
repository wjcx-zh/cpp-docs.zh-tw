---
title: "逐步解說：建立 WPF 工具箱控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱"
  - "wpf"
ms.assetid: 8223c06e-f327-4778-8709-e0cc7eae2c78
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# 逐步解說：建立 WPF 工具箱控制項
隨附於 Visual Studio SDK 的 WPF 工具箱控制項範本，可讓您建立在安裝擴充功能時會自動加入 \[工具箱\] 的 Windows Presentation Foundation \(WPF\) 控制項。 本逐步解說會示範如何使用範本建立可散發給其他使用者的計數器控制項。  
  
## 必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../Topic/Visual%20Studio%20SDK.md)。  
  
## 在 Visual Studio 中尋找 WPF 工具箱控制項範本  
 \[WPF 工具箱控制項\] 範本位於 \[新增專案\] 對話方塊中，\[已安裝的範本\] 下的這些位置：  
  
-   **Visual Basic** 為 \[擴充性\]。 專案語言為 Visual Basic。  
  
-   **Visual C\#** 為 \[擴充性\]。 專案語言為 C\#。  
  
## 建立 WPF 工具箱控制項專案  
 \[WPF 工具箱控制項\] 範本會建立未定義的使用者控制項，並提供將控制項加入 \[工具箱\] 的所有必要功能。  
  
#### 若要建立專案  
  
1.  按一下 \[**檔案**\] 功能表上的 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[新增專案\] 對話方塊的 \[已安裝的範本\] 下，按一下您慣用的程式設計語言節點，然後選取 \[擴充性\]。 在專案類型清單中選取 \[WPF 工具箱控制項\]。  
  
3.  在 \[名稱\] 方塊中，輸入專案要使用的名稱。 \(這個逐步解說使用的名稱為 `Counter`。\) 按一下 \[**確定**\]。  
  
     這會建立一個解決方案，包含使用者控制項、將控制項放在 \[工具箱\] 的屬性，和用於部署的 VSIX 資訊清單。 \[名稱\] 方塊會設定解決方案和命名空間的名稱，但它不會設定控制項的名稱，因為它會出現在 \[工具箱\] 中。 稍後在本逐步解說中您會設定這些內容。  
  
### 建置控制項的使用者介面  
 `Counter` 控制項需要三個子控制項：顯示文字和目前計數的兩個 <xref:System.Windows.Controls.Label> 控制項，以及將計數重設為 0 的 <xref:System.Windows.Controls.Button> 控制項。 不需要其他子控制項，因為主控應用程式會以程式設計的方式遞增計數器。  
  
##### 建置使用者介面  
  
1.  在**方案總管**中按兩下 \[ToolboxControl.cs\] 在設計工具中開啟它。  
  
     設計工具會顯示包含了 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.Controls.Grid> 控制項。  
  
2.  選取 <xref:System.Windows.Controls.Grid> 控制項，然後按一下出現在格線上方和左側的藍色長條，將它分割成兩列和兩行。  
  
3.  從 \[工具箱\] 將 <xref:System.Windows.Controls.Label> 控制項拖曳到方格頂端列的每個資料格中。  
  
     此時，您可以在方格上排列項目，設定控制項的配置。 或者，您可以直接編輯 Extensible Application Markup Language \(XAML\)，讓控制項配合文字動態調整大小。  
  
4.  在 \[XAML\] 窗格中，將 `RowDefinition` 項目的高度項目和 `ColumnDefinition` 項目的寬度設為 `"auto"`。  
  
5.  依下例編輯按鈕和兩個標籤的標記。  
  
     [!code-xml[ToolboxControlWPF#11](../misc/codesnippet/Xaml/walkthrough-creating-a-wpf-toolbox-control_1.xaml)]  
  
     `Grid.Row` 和 `Grid.Column` 屬性設定項目在方格上的位置。 按鈕上的 `Grid.ColumnSpan` 屬性讓第一欄可隨按鈕寬度自由調整大小。  
  
     標籤的 `Content` 屬性會使用 `{Binding}` 語法繫結稍後在本逐步解說中要定義的屬性。  
  
### 編碼使用者控制項  
 `Counter` 控制項會公開遞增計數器的方法、計數器每次遞增所引發的事件、`Reset` 按鈕、儲存目前計數的三個屬性、顯示文字，以及要顯示或隱藏 `Reset` 按鈕。`ProvideTolboxControl` 屬性會決定 \[工具箱\] 顯示 `Counter` 控制項的位置。  
  
 您可以使用撰寫 Windows Forms 控制項的方式來撰寫這個控制項，亦即使用事件處理常式和公用方法來設定標籤的內容。 不過，在 WPF 中您可以設定控制項的資料內容，以便可以直接繫結 XAML 項目屬性和程式碼的屬性。 這個模型也提供隔開核心功能和控制項使用者介面 \(UI\) 的抽象層。  
  
 本逐步解說會示範如何建立資料模型類別，然後再繫結控制項的資料內容和資料模型。  
  
##### 建立資料模型  
  
1.  按兩下按鈕開啟程式碼視窗。  
  
2.  在檔案頂端加入 <xref:System.ComponentModel> 命名空間的 `using` 指示詞。  
  
3.  在產生的類別之後，建立公用類別以定義資料內容。  
  
     [!code-cs[ToolboxControlWPF#01](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_2.cs)]  
  
     這個類別會實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，讓 XAML 項目繫結至已定義的屬性。  
  
4.  以滑鼠右鍵按一下 <xref:System.ComponentModel.INotifyPropertyChanged> 介面宣告，按一下 \[實作介面\]，然後按一下 \[實作介面\]。  
  
     Visual Studio 會宣告 `PropertyChanged` 事件。  
  
5.  宣告事件之後，建立下列的私用方法以引發此事件。  
  
     [!code-cs[ToolboxControlWPF#02](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_3.cs)]  
  
6.  建立下列私用欄位和公用屬性，在控制項中保留兩個標籤值。  
  
     [!code-cs[ToolboxControlWPF#03](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_4.cs)]  
  
     引發 `PropertyChanged` 事件會導致 XAML 繫結更新繫結控制項的內容。 將屬性設定為 `public` 可讓設計工具使用它們，但其他程式若不繫結到此資料內容就無法使用。  
  
 既然您已建立了資料模型，就可以實作控制項的程式碼後置功能。  
  
##### 實作控制項  
  
1.  在實作控制項之部分類別的定義上，以滑鼠右鍵按一下類別名稱，再依序按一下 \[重構\] 和 \[重新命名\]，然後將類別名稱變更成 `Counter`。 這是安裝擴充功能時顯示在 \[工具箱\] 的名稱。  
  
2.  在類別定義正上方的 `ProvideToolboxControl` 屬性宣告中，將第一個參數的值從 `"Counter"` 變更為 `"General"`。 這會設定主控 \[工具箱\] 控制項的項目群組名稱。  
  
     下列範例會顯示 `ProvideToolboxControl` 屬性和調整過的類別定義。  
  
     [!code-cs[ToolboxControlWPF#04](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_5.cs)]  
  
3.  建立私用欄位保存控制項的資料內容，然後在建構函式中將資料內容指派給 `MyDataModel` 類別，如下例所示。  
  
     [!code-cs[ToolboxControlWPF#05](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_6.cs)]  
  
4.  建立下列公用屬性，以鏡像資料內容的 `Text` 和 `Count` 屬性。  
  
     [!code-cs[ToolboxControlWPF#06](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_7.cs)]  
  
     這些屬性讓凡是包含此控制項的所有應用程式都能使用來自資料內容的內容。  
  
5.  建立下列遞增計數器的公用方法，以及通知主控應用程式的事件。  
  
     [!code-cs[ToolboxControlWPF#07](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_8.cs)]  
  
6.  實作 `Reset` 按鈕的 Click 處理常式，如下所示。  
  
     [!code-cs[ToolboxControlWPF#08](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_9.cs)]  
  
7.  加入下列公用屬性，以顯示或隱藏 `Reset` 按鈕。  
  
     [!code-cs[ToolboxControlWPF#09](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_10.cs)]  
  
## 測試控制項  
 若要測試 \[工具箱\] 控制項，請先在開發環境中測試，然後在主控應用程式中測試。  
  
#### 測試控制項  
  
1.  按 F5。  
  
     這會建置專案，並開啟已安裝控制項之 Visual Studio 的第二個執行個體。  
  
2.  在 Visual Studio 的新執行個體中建立 WPF 應用程式專案。  
  
3.  在**方案總管**中按兩下 \[MainPage.xaml\]，在設計工具中開啟它。  
  
4.  從 \[工具箱\] 的 \[一般\] 區段，將 \[計數器\] 控制項拖曳至表單，然後選取它。  
  
     \[屬性\] 視窗應該會顯示 `Text` 和 `ShowReset` 屬性，以及繼承自 <xref:System.Windows.Controls.UserControl> 的其他屬性。`Count` 屬性是唯讀的，所以不應該出現。  
  
5.  變更 `Text` 屬性的值。  
  
     設計工具中顯示的標籤文字應該要變更。  
  
6.  將 `ShowReset` 屬性設為 `Hidden`，然後再設回 `Visible`。  
  
     控制項上的 `Reset` 按鈕應該消失後再出現。  
  
7.  將 <xref:System.Windows.Controls.Button> 控制項拖曳至表單，將它的 `Content``` 屬性設為 `Test`，然後按兩下按鈕以在程式碼檢視中開啟其 Click 處理常式。  
  
8.  實作 Click 處理常式以呼叫控制項的 `Increment` 方法。  
  
     [!code-cs[ToolboxControlWPF#21](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_11.cs)]  
  
9. 在建構函式中呼叫 `InitializeComponent` 之後，輸入 `counter1.Implemented +=`，再按兩下 TAB 鍵，產生 `Counter.Incremented` 事件的處理常式。  
  
10. 實作新的處理常式，如下例所示。  
  
     [!code-cs[ToolboxControlWPF#22](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_12.cs)]  
  
11. 按 F5。  
  
     應該會開啟 WPF 應用程式。  
  
12. 按一下 \[測試\]。  
  
     計數器應該會遞增，然後按鈕應該會慢慢淡出。  
  
13. 再按四下 \[測試\]。  
  
     計數器應該遞增，而按鈕應該繼續淡出直到消失為止。 如果在按鈕原先的位置繼續按，計數器應該繼續遞增。  
  
14. 按一下 \[重設\]。  
  
     計數器應該重設為 **0**。  
  
## 後續步驟  
 當您建置 \[工具箱\] 控制項時，Visual Studio 會在專案的 \\bin\\debug\\ 資料夾中建立名為 *ProjectName*.vsix 的檔案。 您可以將 .vsix 檔案上傳到到網路或網站以部署控制項。 當使用者開啟 .vsix 檔案時，控制項就會安裝及加入 Visual Studio 的 \[工具箱\] 中。 或者，如果您將 .vsix 檔上傳至 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站，使用者就可以瀏覽 \[擴充管理員\] 尋找它。  
  
## 請參閱  
 [擴充工具箱](../misc/extending-the-toolbox.md)   
 [建立 Windows Form 工具箱控制項](../Topic/Creating%20a%20Windows%20Forms%20Toolbox%20Control.md)   
 [擴充 Visual Studio 的其他部分](../Topic/Extending%20Other%20Parts%20of%20Visual%20Studio.md)   
 [使用 WPF 設計工具的控制項](http://msdn.microsoft.com/zh-tw/c6235492-b10d-4c3c-ba67-6b6a545faee1)   
 [控制項撰寫概觀](../Topic/Control%20Authoring%20Overview.md)