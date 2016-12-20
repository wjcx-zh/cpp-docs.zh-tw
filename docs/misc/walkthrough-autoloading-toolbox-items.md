---
title: "逐步解說：自動載入工具箱項目 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱 [Visual Studio SDK], 使用反映加入控制項"
  - "反映, 工具箱"
ms.assetid: b03c0d62-3be0-475f-b1d9-725dee993ad6
caps.latest.revision: 56
caps.handback.revision: 56
manager: "douge"
---
# 逐步解說：自動載入工具箱項目
這個逐步解說會示範 Managed VSPackage 如何使用反映自動載入自己的組件提供的全部 <xref:System.Drawing.Design.ToolboxItem> 項目。  
  
> [!NOTE]
>  在 \[工具箱\] 加入自訂控制項的建議方式，是使用隨附於 Visual Studio SDK，包含自動載入支援的 \[工具箱控制項\] 範本。 本主題會保留以供回溯相容性、在 \[工具箱\] 加入現有的控制項，以及進階的工具箱開發之用。  
>   
>  如需使用範本建立 \[工具箱\] 控制項的詳細資訊，請參閱[如何：建立使用 Windows Forms 的 \[工具箱\] 控制項](../Topic/How%20to:%20Create%20a%20Toolbox%20Control%20That%20Uses%20Windows%20Forms.md) 和 [建立 WPF 工具箱控制項](../Topic/Creating%20a%20WPF%20Toolbox%20Control.md)。  
  
 本逐步解說會引導您完成下列步驟：  
  
1.  使用 <xref:System.ComponentModel.ToolboxItemAttribute>、<xref:System.Drawing.ToolboxBitmapAttribute> 和 <xref:System.ComponentModel.DisplayNameAttribute>，在 VSPackage 物件中加入並正確登錄所有的 \[工具箱\] 控制項。  
  
2.  建立下列兩個控制項，並將其各自的圖示加入 \[工具箱\] 中：  
  
    -   使用預設的 <xref:System.Drawing.Design.ToolboxItem> 類別加入一個控制項。  
  
    -   使用衍生自 <xref:System.Drawing.Design.ToolboxItem> 類別的自訂類別加入另一個控制項。  
  
3.  如提供具有 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 類別的 <xref:System.Drawing.Design.ToolboxItem> 物件一樣，登錄 VSPackage。  
  
4.  在載入時，使用反映產生 VSPackage 提供的所有 <xref:System.Drawing.Design.ToolboxItem> 物件清單。  
  
5.  建立 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件的處理常式。 這樣可確保正確載入 VSPackage 的 <xref:System.Drawing.Design.ToolboxItem> 物件。  
  
6.  實作 VSPackage 的命令以強制重新初始化 \[工具箱\]。  
  
## 必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[擴充 Visual Studio 概觀](../Topic/Extending%20Visual%20Studio%20Overview.md)。  
  
## Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在 \[新增專案\] 對話方塊的三個不同位置：  
  
1.  位在 Visual Basic 擴充性下。 專案的預設語言為 Visual Basic。  
  
2.  位在 C\# 擴充性下。 專案的預設語言為 C\#。  
  
3.  位在其他專案類型擴充性下。 專案的預設語言為 C\+\+。  
  
## 建立 Managed VSPackage  
  
#### 建立 LoadToolboxMembers VSPackage  
  
1.  建立名為 `LoadToolboxMembers` 的 VSPackage。 如需詳細資訊，請參閱[逐步解說：使用 Visual Studio 封裝範本建立功能表命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
2.  加入功能表命令。  
  
     在 Visual Basic 將命令命名為 `Initialize LoadToolboxMembers VB`，在 Visual C\# 為 `Initialize LoadToolboxMembers CS`。  
  
 如果針對多種語言執行本逐步解說作業，您必須更新專案，以釐清產生的組件。  
  
#### 釐清 Visual Basic 和 Visual C\# Vspackage  
  
1.  針對 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]：  
  
    -   在**方案總管**中，開啟專案屬性並選取 \[應用程式\] 索引標籤。  
  
         將組件名稱變更為 `LoadToolboxMembersVB`，並將預設的命名空間變更為 `Company.LoadToolboxMembersVB`。  
  
2.  針對 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]：  
  
    1.  在**方案總管**中，開啟專案屬性並選取 \[應用程式\] 索引標籤。  
  
         將組件名稱變更為 `LoadToolboxMembersCS`，並將預設的命名空間變更為 `Company.LoadToolboxMembersCS`。  
  
    2.  在程式碼編輯器中開啟 LoadToolboxMembersPackage 類別。  
  
         若要使用重構工具重新命名現有的命名空間，請以滑鼠右鍵按一下現有的命名空間名稱 `LoadToolboxMembers`，然後指向 \[重構\]，然後按一下 \[重新命名\]。 將名稱變更為 `LoadToolboxMembersCS`。  
  
3.  儲存所有變更。  
  
#### 加入支援的參考  
  
1.  在 LoadToolboxMembers 專案中，加入 <xref:System.Drawing.Design?displayProperty=fullName> .NET Framework 元件的參考，如下所示。  
  
    1.  在**方案總管**中，以滑鼠右鍵按一下 \[LoadToolboxMembers\] 專案，然後按一下 \[加入\] 和 \[參考\]。  
  
    2.  在 \[參考\] 對話方塊的 \[.NET\] 索引標籤上，按兩下 \[System.Drawing.Design\]。  
  
2.  如為 Visual Basic，請將下列命名空間加入專案的匯入命名空間清單中：  
  
    -   Company.LoadToolboxMembersVB  
  
    -   系統  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
#### 測試產生的程式碼  
  
1.  在 Visual Studio 實驗登錄區中編譯並啟動 VSPackage。  
  
2.  在 \[工具\] 功能表上，按一下 \[初始化 LoadToolboxMembers VB\] 或 \[初始化 LoadToolboxMembers CS\]。  
  
     這樣會開啟訊息方塊，包含的文字指出已呼叫過封裝的功能表項目處理常式。  
  
3.  關閉 [!INCLUDE[vs_current_short](../misc/includes/vs_current_short_md.md)] 的實驗版本。  
  
## 建立 \[工具箱\] 控制項  
 在本節中，您要建立並登錄使用者控制項 `Control1`，宣告相關聯的預設 \[工具箱\] 項目。 如需如何撰寫 Windows Forms 控制項和 <xref:System.Drawing.Design.ToolboxItem> 類別的詳細資訊，請參閱[在設計階段開發 Windows Form 控制項](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)。  
  
#### 建立和預設 ToolboxItem 一起使用的 \[工具箱\] 控制項  
  
1.  在**方案總管**中，將 <xref:System.Windows.Forms.UserControl> 物件加入 LoadToolboxMembers 專案中，如下所示：  
  
    1.  在**方案總管**中，以滑鼠右鍵按一下 \[LoadToolboxMembers\] 專案，指向 \[加入\]，然後按一下 \[使用者控制項\]。  
  
    2.  在 \[加入新項目\] 對話方塊中，將 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 的名稱變更為 `Control1.vb` 或 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 的名稱變更為 `Control1.cs`。  
  
         如需如何在專案中加入新項目的詳細資訊，請參閱 [NIB: 如何：加入新的專案項目](http://msdn.microsoft.com/zh-tw/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。  
  
     新的控制項會在 \[設計\] 檢視中開啟。  
  
2.  從 \[工具箱\] 將 \[按鈕\] 控制項 \(位於 \[通用控制項\] 分類\) 拖曳至設計工具。  
  
3.  按兩下您剛才建立的按鈕。 這樣會產生該按鈕 <xref:System.Windows.Forms.Control.Click> 事件的事件處理常式。 使用下列程式碼更新事件處理常式：  
  
     [!code-cs[LoadToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_1.cs)]
     [!code-vb[LoadToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_1.vb)]  
  
4.  修改控制項的建構函式，在呼叫 `InitializeComponent` 方法之後設定按鈕文字：  
  
     [!code-cs[LoadToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_2.cs)]
     [!code-vb[LoadToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_2.vb)]  
  
5.  將屬性加入檔案中，讓 VSPackage 查詢已提供的 <xref:System.Drawing.Design.ToolboxItem> 類別：  
  
     [!code-cs[LoadToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_3.cs)]
     [!code-vb[LoadToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_3.vb)]  
  
6.  儲存檔案。  
  
 在以下的程序中，您要建立並登錄第二個使用者控制項 `Control2`，和相關聯的自訂 \[工具箱\] 項目，衍生自 <xref:System.Drawing.Design.ToolboxItem> 類別的 `Control2_ToolboxItem`。  
  
#### 建立 \[工具箱\] 控制項以使用自訂的 ToolboxItem 衍生類別  
  
1.  建立名為 `Control2` 的第二個使用者控制項。 按兩下表單顯示程式碼檔案。  
  
2.  將 `System.Drawing.Design` 和 `System.Globalization` 加入類別所使用的命名空間中。  
  
     [!code-cs[LoadToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_4.cs)]
     [!code-vb[LoadToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_4.vb)]  
  
3.  加入按鈕和按鈕 Click 事件處理常式，然後像更新第一個控制項那樣更新控制項的建構函式。  
  
4.  將 <xref:System.ComponentModel.DisplayNameAttribute>、<xref:System.ComponentModel.DescriptionAttribute>、<xref:System.ComponentModel.ToolboxItemAttribute> 和 <xref:System.Drawing.ToolboxBitmapAttribute> 屬性加入檔案中。  
  
     這些屬性會讓 VSPackage 查詢 <xref:System.Drawing.Design.ToolboxItem> 類別。  
  
     如需如何撰寫自訂 <xref:System.Drawing.Design.ToolboxItem> 物件的詳細資訊和範例，請參閱 <xref:System.Drawing.Design.ToolboxItem> 參考頁面的討論。  
  
     加上前面的變更，您的第二個控制項類別應該類似下列程式碼。 在下一個步驟之前，符號 `Control2_ToolboxMenu` 都尚未定義。  
  
     [!code-cs[LoadToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_5.cs)]
     [!code-vb[LoadToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_5.vb)]  
  
5.  建立一個名為 `Control2_ToolboxItem` 的類別。 這個 <xref:System.Drawing.Design.ToolboxItem> 是為第二個控制項所建構，加入 \[工具箱\] 中。 類別必須套用 `SerializableAttribute`。  
  
     [!code-cs[LoadToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_6.cs)]
     [!code-vb[LoadToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_6.vb)]  
  
6.  儲存檔案。  
  
## 內嵌點陣圖圖示  
 之前使用的 <xref:System.Drawing.ToolboxBitmapAttribute> 兩個執行個體，指出專案使用下列圖示代表兩個控制項：  
  
-   位於命名空間的 `Control1.bmp` 包含了第一個控制項。  
  
-   位於命名空間的 `Control2.bmp` 包含了第二個控制項。  
  
#### 內嵌 ToolboxItem 點陣圖圖示  
  
1.  在專案中加入兩個新的點陣圖，如下所示。  
  
    1.  以滑鼠右鍵按一下 `LoadToolboxMembers` 專案。  
  
    2.  指向 \[加入\]，然後按一下 \[新增項目\]。  
  
    3.  在 \[加入新項目\] 對話方塊中，選取 \[點陣圖檔\]，並將檔案命名為 `Control1.bmp`。  
  
    4.  對第二個點陣圖重複這些步驟，並將它命名為 `Control2.bmp`。  
  
         這樣會在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 點陣圖編輯器中開啟每個點陣圖。  
  
2.  設定每個圖示的大小為 16 x 16，如下所示。  
  
    1.  在 \[檢視\] 功能表中，按一下每個點陣圖的 \[屬性視窗\]。  
  
    2.  在 \[屬性\] 視窗中，將 \[高度\] 和 \[寬度\] 設為 16。  
  
3.  使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的點陣圖編輯器建立每個圖示的影像。  
  
4.  在**方案總管**中，按一下每個點陣圖檔案，然後在 \[屬性\] 視窗中，將 \[建置動作\] 屬性設為 \[內嵌資源\]。  
  
5.  儲存所有開啟的檔案。  
  
## 修改 VSPackage 實作  
 必須修改 VSPackage 的預設實作才能執行下列動作：  
  
-   登錄支援以成為 \[工具箱\] 項目提供者。  
  
-   取得 VSPackage 支援的 <xref:System.Drawing.Design.ToolboxItem> 物件清單。  
  
-   處理 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件時，在 \[工具箱\][!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中載入 <xref:System.Drawing.Design.ToolboxItem> 物件。  
  
 下個程序會說明如何修改封裝的實作。  
  
#### 將封裝實作修改成 VSPackage 的 \[工具箱\] 項目提供者  
  
1.  在程式碼編輯器中開啟 LoadToolboxMembersPackage.cs 或 LoadToolboxMembersPackage.vb 檔案。  
  
2.  修改 `LoadToolboxMembersPackage` 類別的宣告，也就是解決方案中 <xref:Microsoft.VisualStudio.Shell.Package> 類別的實作，如下所示。  
  
    1.  將下列命名空間指示詞加入 `LoadToolboxMembersPackage` 類別檔案中。  
  
         [!code-cs[LoadToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_7.cs)]
         [!code-vb[LoadToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_7.vb)]  
  
    2.  加入 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 的執行個體，將 VSPackage 登錄為 <xref:System.Drawing.Design.ToolboxItem> 類別。  
  
        > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 的唯一引數是 VSPackage 提供的 <xref:System.Drawing.Design.ToolboxItem> 版本。 您可以藉由變更此值，強制 IDE 載入 VSPackage，即使它有稍早快取的 <xref:System.Drawing.Design.ToolboxItem> 類別版本。  
  
    3.  將下列兩個新的 `private` 欄位加入 `LoadToolboxMembersPackage` 類別中：  
  
         名為 `ToolboxItemList` 的 <xref:System.Collections.ArrayList> 成員，保存 `LoadToolboxMembersPackage` 類別管理的 <xref:System.Drawing.Design.ToolboxItem> 物件清單。  
  
         名為 `CategoryTab` 的 <xref:System.String>，包含 \[工具箱\] 分類或索引標籤，用來保存 `LoadToolboxMembersPackage` 類別管理的 <xref:System.Drawing.Design.ToolboxItem> 物件。  
  
     這項修改結果類似下列程式碼：  
  
     [!code-cs[LoadToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_8.cs)]
     [!code-vb[LoadToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_8.vb)]  
  
3.  展開要修改的封裝成員區域，修改 `Initialize` 方法來執行下列動作：  
  
    -   如為 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]，訂閱 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件。  
  
    -   呼叫 `CreateItemList` 方法來填滿 <xref:System.Collections.ArrayList> 物件 `ToolboxItemList`。`ToolboxItemList` 會包含 `LoadToolboxMembersPackage` 管理的所有工具箱項目清單。  
  
     [!code-cs[LoadToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_9.cs)]
     [!code-vb[LoadToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_9.vb)]  
  
4.  加入兩個方法，`CreateItemList` 和 `CreateToolboxItem`，使用中繼資料建構 `LoadToolboxMembers` 組件中可用的 <xref:System.Drawing.Design.ToolboxItem> 物件執行個體，如下所示：  
  
     [!code-cs[LoadToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_10.cs)]
     [!code-vb[LoadToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_10.vb)]  
  
5.  實作 `OnRefreshToolbox` 方法處理 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件。  
  
     `OnRefreshToolbox` 方法使用 `LoadToolboxMembersPackage` 類別之 `ToolboxItemList` 成員包含的 <xref:System.Drawing.Design.ToolboxItem> 物件清單。 它也會執行下列操作：  
  
    -   移除 \[工具箱\] 分類中所有由變數 `CategoryTab` 定義的 <xref:System.Drawing.Design.ToolboxItem> 物件。  
  
    -   將 `ToolboxItemList` 列出的所有 <xref:System.Drawing.Design.ToolboxItem> 物件的新執行個體加入 VSProject 的分類索引標籤。  
  
    -   將 \[工具箱\] 使用中索引標籤設為 VSProject 的分類索引標籤。  
  
     [!code-cs[LoadToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_11.cs)]
     [!code-vb[LoadToolboxMembers#11](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_11.vb)]  
  
    > [!NOTE]
    >  您可以開發一個機制，測試 VSPackage 或項目的版本，只有在 VSPackage 版本已變更或 <xref:System.Drawing.Design.ToolboxItem> 版本已變更時才更新，當做練習。  
  
## 初始化 \[工具箱\]  
  
#### 實作命令以初始化 \[工具箱\]  
  
-   變更功能表項目命令處理常式方法 `MenuItemCallBack`，如下所示。  
  
    1.  使用下列程式碼取代現有的 `MenuItemCallBack` 實作：  
  
         [!code-cs[LoadToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-autoloading-toolbox-items_12.cs)]
         [!code-vb[LoadToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-autoloading-toolbox-items_12.vb)]  
  
## 建置和執行解決方案  
 您可以使用在實驗登錄區中執行的 Visual Studio 執行個體，演練本逐步解說的產品。  
  
#### 演練本逐步解說  
  
1.  在 Visual Studio 中，按一下 \[建置\] 功能表上的 \[重建方案\]。  
  
2.  按 F5，在實驗登錄區中啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的第二個執行個體。  
  
     如需如何使用實驗登錄區的詳細資訊，請參閱[實驗執行個體](../Topic/The%20Experimental%20Instance.md)。  
  
3.  按一下 \[工具\] 功能表。  
  
     名為 \[初始化 LoadToolboxMembers VB\] 或 \[初始化 LoadToolboxMembers CS\] 的命令會出現在功能表上方，具有數字 1 的圖示。  
  
4.  建立新的 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] Windows Forms 應用程式。  
  
     應該會出現 <xref:System.Windows.Forms.Form> 型的設計工具。  
  
5.  將 \[工具箱\] 的 \[LoadToolboxMembers 逐步解說 VB\] 或 \[LoadToolboxMembers 逐步解說 CS\] 分類中的新控制項的其中一個或兩個都拖曳到設計工具的表單中。  
  
    > [!NOTE]
    >  如果 \[工具箱\] 未顯示，請按一下 \[檢視\] 功能表的 \[工具箱\]。 如果 \[工具箱\] 中未出現 VSPackage 的分類索引標籤，請按一下 \[工具\] 功能表上的 \[初始化 LoadToolboxMembers VB\] 或 \[初始化 LoadToolboxMembers CS\]，重新初始化 \[工具箱\]。  
  
6.  按一下 \[建置\] 功能表的 \[重建方案\]，建置 Windows 應用程式。  
  
7.  按一下 \[偵錯\] 功能表上的 \[開始\] 或 \[開始偵錯\]，執行應用程式。  
  
8.  在應用程式執行時，按一下您在應用程式加入的其中一個控制項。  
  
     訊息方塊隨即出現，並顯示 `"Hello world from Company.LoadToolboxMembers.Control1"` 或  `"Hello world from Company.LoadToolboxMembers.Control2"`。  
  
## 分析實作  
  
### 建立工具箱控制項  
 當方法 `CreateItemList` 向 `Assembly` 查詢可用的 \[工具箱\] 控制項時，它會使用指派給 `Control1` 和 `Control2` 的屬性。  
  
-   <xref:System.ComponentModel.ToolboxItemAttribute> 會執行下列兩個函式：  
  
    -   將 <xref:System.ComponentModel.ToolboxItemAttribute> 指派給 `Control1` 和 `Control2`，表示每一個都是 \[工具箱\] 控制項。  
  
    -   當控制項加入 \[工具箱\] 中時，<xref:System.ComponentModel.ToolboxItemAttribute> 建構函式的引數會指出是使用預設的 <xref:System.Drawing.Design.ToolboxItem>，還是使用衍生自 <xref:System.Drawing.Design.ToolboxItem> 的自訂類別。  
  
         指派給 `Control1` 的 <xref:System.ComponentModel.ToolboxItemAttribute> 的執行個體，是使用 `true` 的引數所建立，它在加入 \[工具箱\] 中時，會指出使用預設的 <xref:System.Drawing.Design.ToolboxItem> 類別。  
  
         指派給 `Control2` 的 <xref:System.ComponentModel.ToolboxItemAttribute> 的執行個體，是使用衍生自 <xref:System.Drawing.Design.ToolboxItem> \(`Control2_ToolboxItem`\) 的類別 <xref:System.Type> 所建立。  
  
-   <xref:System.Drawing.ToolboxBitmapAttribute> 類別會指定環境使用的點陣圖來識別控制項。  
  
     將 \[建置動作\] 屬性設為 \[內嵌資源\] 在組件中內嵌點陣圖，將點陣圖放在組件的命名空間中。 因此，`Control1.bmp` 可以稱為 `Company.LoadToolboxMembers.Control1.bmp`。  
  
     <xref:System.Drawing.ToolboxBitmapAttribute> 支援把這個完整路徑當做引數的建構函式。 例如，使用 `[ToolboxBitmap("Company.LoadToolboxMembers.Control1.bmp")]` 可以把 <xref:System.Drawing.ToolboxBitmapAttribute> 類別套用至 `Control1`。  
  
     為支援彈性，本逐步解說會使用把 <xref:System.Type> 類別當做 <xref:System.Drawing.ToolboxBitmapAttribute> 建構函式第一個引數的建構函式。 用來識別點陣圖檔案的命名空間取自 <xref:System.Type>，會插入在點陣圖基底名稱的前面。  
  
     因為實作 <xref:Microsoft.VisualStudio.Shell.Package> \(`LoadToolboxMembers`\) 的 <xref:System.Type> 物件位於 `Company.LoadToolboxMembers` 命名空間，所以 `[ToolboxBitmap(typeof(Control1), "Control1.bmp")]` 相當於 `[ToolboxBitmap("Company.LoadToolboxMembers.Control1.bmp")]`。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> 指定 \[工具箱\] 的控制項名稱。  
  
### 登錄 \[工具箱\] 控制項提供者  
 將 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 類別套用到實作 <xref:Microsoft.VisualStudio.Shell.Package> 的類別會影響產生的 VSPackage 登錄設定。 如需 <xref:System.Drawing.Design.ToolboxItem> 提供者的登錄設定詳細資訊，請參閱[註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)。  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 環境使用 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 建構函式的版本引數，管理向 \[工具箱\] 提供項目的 VSPackages 快取。 在載入 VSPackage 提供 \[工具箱\] 項目之後，在提供者的登錄版本變更前，會一直使用 VSPackage 的快取版本。 因此，如果您想要在建置後修改這個逐步解說的產品，請務必變更套用至 `AddToolboxItem` 之 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 建構函式的版本引數。 例如，`[ProvideToolboxItems(1)]` 應該變更為 `[ProvideToolboxItems(2)]`。 若未變更版本，則 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 環境不會載入任何已完成的修改。  
  
 在本逐步解說中，VSPackage 被設定成只提供支援預設剪貼簿格式的 \[工具箱\] 控制項。 如需預設剪貼簿格式的清單，請參閱[擴充工具箱](../misc/extending-the-toolbox.md)。 如果您想要支援其他的剪貼簿格式，或決定不支援預設格式，請將屬性 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> 套用至 `LoadToolboxMembersPackage` 類別。 如需登錄 \[工具箱\] 控制項提供者的詳細資訊，請參閱[進階工具箱控制項開發](../misc/advanced-toolbox-control-development.md)。  
  
### 將控制項加入 \[工具箱\] 中  
 `CreateItemList` 中的功能會模擬 <xref:System.Drawing.Design.ToolboxService.System%23Drawing%23Design%23IToolboxService%23GetToolboxItems%2A> 提供的功能。  
  
 `CreateItemList` 方法只會檢查實作 <xref:System.ComponentModel.IComponent> 介面的非抽象 <xref:System.Type> 物件。  
  
## 後續步驟  
 使用 <xref:System.Drawing.Design.ToolboxService.System%23Drawing%23Design%23IToolboxService%23GetToolboxItems%2A> 而不使用 `CreateItemList`，會讓這個逐步解說的產品更穩固。  
  
 您也可以修改 `CreateItemList`，使用 <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> 將控制項載入以 `LoadToolboxMembers` 組件的內嵌文字清單為基礎的 \[工具箱\] 中。  
  
## 請參閱  
 [擴充工具箱](../misc/extending-the-toolbox.md)   
 [註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)   
 [進階工具箱控制項開發](../misc/advanced-toolbox-control-development.md)   
 [工具箱逐步解說](../misc/toolbox-walkthroughs.md)