---
title: "逐步解說：發行 Web 控制項專案範本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "範本, Web 控制項"
  - "Web 控制項範本"
ms.assetid: b56490f8-38bd-4220-a17e-5ebb30d3ac78
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# 逐步解說：發行 Web 控制項專案範本
您可以建立 Web 控制項專案範本，以作為其他 Web 控制項專案的基礎。 您也可以將範本當做 VSIX 擴充功能來散發。  
  
 若要散發 VSIX 擴充功能，建議您將其加入 Visual Studio 組件庫網站，因為開發人員可以使用 \[擴充管理員\] 瀏覽是否有新的和更新的擴充功能。 您也可以散發擴充功能，方法是將它放置在另一部伺服器上，或者將它燒錄到 CD 或其他媒體上。  
  
 本逐步解說是兩個相關逐步解說的其中一個，說明如何建立 Web 控制項專案範本，然後再散發範本。 另一個逐步解說 [逐步解說: 發行 Visual Studio 擴充功能](../Topic/Walkthrough:%20Publishing%20a%20Visual%20Studio%20Extension.md)，說明如何建立及散發 Web 控制項。  
  
 本逐步解說包含下列各節：  
  
-   在 VSIX 擴充功能中建立 Web 控制項專案範本  
  
-   將範本發行至 Visual Studio 組件庫  
  
-   從 Visual Studio 組件庫安裝範本  
  
-   測試已安裝的範本  
  
-   將偵錯動作精靈加入範本中  
  
## 必要條件  
 若要完成本逐步解說，您必須了解 Web 控制項，並了解如何建立專案、設定專案屬性及使用 Visual Studio 實驗執行個體。 Visual Studio 和 Visual Studio SDK 必須安裝在電腦上。 在開始進行本逐步解說之前，您必須完成[逐步解說: 發行 Visual Studio 擴充功能](../Topic/Walkthrough:%20Publishing%20a%20Visual%20Studio%20Extension.md)。  
  
## 在 VSIX 擴充功能中建立 Web 控制項專案範本  
 若要建立 Web 控制項專案範本，請先建立 Web 控制項專案。 針對本逐步解說，請以您在[逐步解說: 發行 Visual Studio 擴充功能](../Topic/Walkthrough:%20Publishing%20a%20Visual%20Studio%20Extension.md)中建立的 ColorTextControl Web 控制項專案開始著手。  
  
 在將專案範本發行至 Visual Studio 組件庫之前，請使用 \[匯出範本為 VSIX 精靈\] 將範本匯出為 VSIX 擴充功能，然後提供圖示以協助在 \[擴充管理員\] 中識別，並提供影像來說明其用途。  
  
#### 準備要散發的 Web 控制項專案  
  
1.  在 Visual Studio 中開啟 MyWebControls 專案。  
  
2.  使用 \[擴充管理員\] 從 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkId=194329) 網站下載 \[匯出範本精靈\]。  
  
     安裝精靈之後，當開啟專案時，\[檔案\] 功能表中會出現 \[匯出範本為 VSIX\]。  
  
3.  按一下 \[檔案\] 功能表上的 \[匯出範本為 VSIX\]。  
  
     ![File menu Export Project as VSIX](../misc/media/pcwc_exportasvsix.png "PCWC\_ExportAsVsix")  
  
4.  在 \[選擇範本類型\] 頁面上，選取 \[專案範本\]，然後選取 MyWebControls.csproj。 按 \[下一步\]。  
  
     ![選擇專案範本](../misc/media/pcwc_choosetemplate.png "PCWC\_ChooseTemplate")  
  
5.  在 \[選取範本選項\] 頁面上，將 \[範本名稱\] 設定為 `Extensibility Color Text Web Toolbox Control`，並將 \[範本描述\] 設定為 `Color text web control project that produces a VSIX extension.`  
  
6.  按一下 \[圖示影像\] 方塊旁的 \[瀏覽\]。 在 \[檔案名稱\] 方塊中，輸入 `*.*`。 找出 Color.bmp，然後按一下 \[開啟\]。  
  
7.  按一下 \[預覽影像\] 方塊旁的 \[瀏覽\]。 在 \[檔案名稱\] 方塊中，輸入 `*.*`。 找出 ScreenShot.bmp，然後按一下 \[開啟\]。 按 \[下一步\]。  
  
     ![選取範本選項](../misc/media/pcwc_selecttemplateoptions2.png "PCWC\_SelectTemplateOptions2")  
  
8.  在 \[選取 VSIX 選項\] 頁面上，將 \[產品名稱\] 變更為 `Extensibility Color Text Web Control Template`。  
  
9. 您可以視需要變更 \[公司名稱\]、\[版本\]、\[授權\] 和 \[快速入門指南 URL\]。  
  
10. 清除 \[自動將範本匯入 Visual Studio\] 選項。 按一下 \[完成\]。  
  
     ![取消核取自動匯入範本](../misc/media/pcwc_.png "PCWC\_")  
  
     在 Windows 檔案總管的 ..\\My Documents\\Visual Studio *\<版本\>*\\My Exported Templates\\ 資料夾中，會列出 Extensibility Color Text Web Control Template.vsix。  
  
## 將範本發行至 Visual Studio 組件庫  
 專案範本現在已準備好要發行至 Visual Studio 組件庫。  
  
#### 將範本發行至 Visual Studio 組件庫  
  
1.  在網頁瀏覽器中，開啟 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkId=194329)網站。  
  
2.  按一下右上角的 \[登入\]。  
  
3.  使用您的 Microsoft 帳戶登入。 如果您沒有 Microsoft 帳戶，可以在這裡建立一個帳戶。  
  
4.  按一下 \[上傳\]。  
  
5.  在 \[步驟 1：擴充功能類型\] 中，選取 \[專案或項目範本\]，然後按一下 \[下一步\]。  
  
6.  在 \[步驟 2：上傳\]，按一下 \[瀏覽\]。 在 \\My Exported Templates\\ 資料夾中，選取 Extensibility Color Text Web Control Template.vsix。 按 \[下一步\]。  
  
7.  在 \[步驟 3：基本資訊\] 中，會顯示來自 \[匯出範本為 VSIX 精靈\] 的資訊。  
  
8.  將 \[分類\] 設定為 `ASP.NET`，並將 \[標記\] 設定為 `toolbox, web control, templates`。  
  
9. 閱讀並同意發佈協議 \(Contribution Agreement\)，然後在方塊中輸入所顯示的文字。  
  
10. 按一下 \[建立發佈\]，然後按一下 \[發行\]。  
  
11. 在 Visual Studio 組件庫中搜尋 Extensibility Color Text Web Control Template。 範本清單應該會出現。  
  
     ![新的 Web 控制項範本清單](../misc/media/pcwc_templatelisting.png "PCWC\_TemplateListing")  
  
## 從 Visual Studio 組件庫安裝範本  
 發行 Web 控制項專案範本之後，請在 Visual Studio 中進行安裝及測試。  
  
#### 在 Visual Studio 中安裝 Web 控制項專案範本  
  
1.  在 Visual Studio 的 \[工具\] 功能表上，按一下 \[擴充管理員\]。  
  
2.  按一下 \[線上組件庫\]，然後搜尋 Extensibility Color Text Web Control Template。 範本清單應該會出現。  
  
3.  按一下 \[**下載**\]。 下載擴充功能之後，按一下 \[安裝\]。  
  
## 測試已安裝的範本  
 現在，您可以使用 Extensibility Color Text Web Control 專案範本建立自訂 Web 控制項。 您不需要手動建立每個控制項。 本節說明如何使用範本來建立 BlueColorTextControl Web 控制項。  
  
#### 建立以範本為基礎的 Web 控制項  
  
1.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  按一下左窗格中的 \[線上範本\]，展開 \[範本\]，然後按一下 \[ASP.NET\]。 按一下中間窗格中的 \[Extensibility Color Text Web Control Template\]。  
  
     ![Select the extensibility color text web template](../misc/media/pcwc_newprojecttemplate.png "PCWC\_NewProjectTemplate")  
  
3.  將 \[名稱\] 設定為 `MoreWebControls`。 按一下 \[**確定**\]。  
  
4.  在**方案總管**中，將 ColorTextControl.cs 重新命名為 BlueColorTextControl.cs。  
  
5.  按兩下 BlueColorTextControl.cs 在編輯器中加以開啟。  
  
6.  在 `ToolboxData` 屬性中，將出現的兩個 `ColorTextControl` 取代為 `BlueColorTextControl`。  
  
     這些值會指定在設計階段將控制項從 \[工具箱\] 拖曳至網頁時，針對該控制項所產生的開頭和結束標記。  這些標記必須符合控制項類別的名稱，也就是出現在 \[工具箱\] 中的控制項名稱。  
  
     控制項類別原始程式碼的開頭現在應該類似下列程式碼。  
  
    ```  
    namespace MoreWebControls { [DefaultProperty("Text")] [ToolboxData("<{0}:BlueColorTextControl runat=server> </{0}:BlueColorTextControl>")] [ProvideToolboxControl("MoreWebControls", false)] public class BlueColorTextControl : WebControl {  
  
    ```  
  
7.  在 `get` 方法中，將 `color:green` 變更為 `color:blue`。  
  
    ```  
    get { String s = (String)ViewState["Text"]; return "<span style='color:blue'>" + s + "</span>"; }  
    ```  
  
     這會將 span 標記中的文字變更為藍色。  
  
8.  建置 MoreWebControls 專案。  
  
## 測試新的 Web 控制項  
 現在，您可以測試 \[工具箱\] 中是否有新的 Web 控制項可用。 不過，即使開啟 MoreWebControls 專案，按 F5 鍵仍無法啟動用以測試控制項的 Visual Studio 實驗執行個體。 這是因為專案是以 Extensibility Color Text Web Control Template 為基礎，但尚未針對此範本設定偵錯動作。 \(下一節說明如何將設定偵錯動作的精靈加入範本中\)。 目前若要測試控制項，請使用下列步驟：  
  
#### 測試新的 Web 控制項  
  
1.  若要開啟 Visual Studio 的實驗執行個體，請啟動實驗執行個體。  
  
    1.  在 [!INCLUDE[win7](../build/includes/win7_md.md)] 中，使用 \[開始\] 功能表 \(\[開始\]\/\[所有程式\]\/\[Microsoft Visual Studio \<版本\> SDK\]\/\[工具\]\/\[啟動 Microsoft Visual Studio \<版本\> 的實驗執行個體\]\)。  
  
    2.  在 [!INCLUDE[win81](../misc/includes/win81_md.md)] 的 \[開始\] 畫面中，輸入 \[啟動 Microsoft Visual Studio \<版本\> 的實驗執行個體\]。  
  
2.  建立 Web 應用程式專案。  
  
3.  在專案中，開啟 default.aspx。 確定顯示 \[原始碼\] 檢視。  
  
4.  在 \[工具箱\] 的 \[MoreWebControls\] 分類中，應該會顯示 **BlueColorTextControl**。  
  
     ![MoreWebControls BlueColorTextControl](../misc/media/pcwc_toolbox2.png "PCWC\_Toolbox2")  
  
5.  將 BlueColorTextControl 拖曳至網頁之 `body` 標記中的某個位置。  
  
6.  在 `ColorTextControl` 標記中加入 `Text` 屬性，並將其值設為 `Think Blue!`。 結果標記應類似如下。  
  
    ```  
    <cc1:BlueColorTextControl ID="BlueColorTextControl1" Text="Think Blue!" runat="server" />  
  
    ```  
  
7.  按 F5 鍵啟動 ASP.NET 程式開發伺服器。  
  
     BlueColorTextControl 的顯示畫面應類似下圖。  
  
     ![BlueColorTextControl 呈現 Think Blue](../misc/media/pcwc_thinkblue.png "PCWC\_ThinkBlue")  
  
8.  關閉 ASP.NET 程式開發伺服器。  
  
9. 關閉 Visual Studio 的實驗執行個體。  
  
## 將偵錯動作精靈加入範本中  
 如上節所述，如果在開啟 MoreWebControls 專案時按 F5 鍵，將不會開啟 Visual Studio 的實驗執行個體， 而是會顯示這則訊息：「無法直接啟動輸出類型為類別庫的專案」。 當實驗執行個體的位置對專案而言是未知時，就會發生這種情況。 不過，您可以允許範本判斷實驗執行個體在目標電腦上的位置，並設定適當的偵錯動作。 之後，電腦上所有以該範本為基礎的專案都會如預期般回應 F5。  
  
 Visual Studio SDK 隨附的每個擴充性專案範本都會包含一個精靈，該精靈會在安裝期間執行、在目標電腦上尋找實驗執行個體，然後設定偵錯動作。 您可以建立自己的精靈來執行這項作業，而且您可以在所散發的每個範本中包含這個精靈。  
  
 若要將 \[偵錯動作精靈\] 加入 Extensibility Color Text Web Control Template 中，您必須刪除範本的第一個版本、將精靈加入其中，然後再重新建立範本。  
  
#### 刪除範本的第一個版本  
  
1.  在 Visual Studio 組件庫網站左上角，按一下 \[我的發佈\]。 \[Extensibility Color Text Web Control Template\] 清單隨即出現。  
  
2.  若要從 Visual Studio 組件庫中永久移除專案範本，請按一下 \[刪除\]。  
  
3.  在 Visual Studio 的 \[工具\] 功能表上，按一下 \[擴充管理員\]。  
  
4.  選取 \[Extensibility Color Text Web Control Template\]，然後按一下 \[解除安裝\]。  
  
5.  關閉 \[擴充管理員\]。  
  
6.  關閉 MoreWebControls 方案。  
  
7.  關閉 Visual Studio。  
  
8.  刪除 MoreWebControls 方案資料夾。  
  
9. 若要完成解除安裝程序，請重新啟動 Visual Studio。  
  
 \[偵錯動作精靈\] 必須有 `Microsoft.VisualStudio.TemplateWizard.IWizard` 的公用實作，而且必須使用強式組件名稱進行簽署。  
  
#### 建立偵錯動作精靈  
  
1.  在 \[新增專案\] 對話方塊中，建立 **Visual C\#**、**Windows**、**類別庫**專案，然後將其命名為 `MyWizard`。  
  
2.  在新專案中，將 class1.cs 重新命名為 MyWizard.cs。  
  
3.  以下列程式碼取代 MyWizard.cs 的內容。  
  
    ```  
    using System; using System.Collections.Generic; using System.Linq; using System.Text; using Microsoft.VisualStudio.TemplateWizard; using System.Globalization; using EnvDTE; namespace MyWizard { public class MyWizard : IWizard { public void BeforeOpeningFile(ProjectItem projectItem) { } public void ProjectFinishedGenerating(Project project) { foreach (Configuration config in project.ConfigurationManager) { //Set up the debug options to run "devenv /rootsuffix Exp"; config.Properties.Item("StartAction").Value = 1; //Get the full path to devenv.exe through DTE.FullName config.Properties.Item("StartProgram").Value = project.DTE.FullName; config.Properties.Item("StartArguments").Value = "/rootsuffix Exp"; } } public void ProjectItemFinishedGenerating(ProjectItem projectItem) { } public void RunFinished() { } public void RunStarted(object automationObject, Dictionary<string, string> replacementsDictionary, WizardRunKind runKind, object[] customParams) { } public bool ShouldAddProjectItem(string filePath) { return true; } } }  
  
    ```  
  
4.  將下列參考加入專案中。 如果有多個選項，請選取路徑為 [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)] 的參考。  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
5.  以滑鼠右鍵按一下 MyWizard 專案，然後按一下 \[屬性\]。 在 \[簽署\] 索引標籤上，選取 \[簽署組件\] 選項。  
  
6.  在 \[選擇強式名稱金鑰檔\] 清單中，選取 \[\<新增…\>\]。 \[建立強式名稱金鑰\] 對話方塊隨即顯示。  
  
7.  將 \[金鑰檔名稱\] 設定為 `key.snk`，然後清除 \[以密碼保護我的金鑰檔\] 選項。  
  
     ![指定金鑰檔](../misc/media/pcwc_strongname.png "PCWC\_StrongName")  
  
8.  按一下 \[確定\] 將 key.snk 加入專案中。  
  
9. 將 MyWizard 專案建置為發行組建。 現在可以開始使用精靈。  
  
10. 關閉 MyWizard 方案。  
  
#### 納入精靈並重新建立範本  
  
1.  遵循先前章節＜在 VSIX 擴充功能中建立 Web 控制項專案範本＞中的步驟，但進行下列新增和變更：  
  
    -   您不需要重新下載 \[匯出範本為 VSIX 精靈\]。  
  
    -   在 \[匯出範本為 VSIX 精靈\] 之 \[選取 VSIX 選項\] 頁面的 \[精靈\] 方塊中，瀏覽至您在先前步驟中建立的 \\bin\\Release\\MyWizard.dll 檔案並加以選取。  
  
         ![指定精靈組件](../misc/media/pcwc_wizardassembly.png "PCWC\_WizardAssembly")  
  
    -   當系統提示您覆寫現有的 VSIX 擴充功能輸出檔時，按一下 \[是\]。  
  
2.  當您到達＜測試新的 Web 控制項＞一節時，請按 F5 鍵。 Visual Studio 的實驗執行個體應該會啟動。  
  
## 後續步驟  
 本逐步解說已說明如何使用 \[匯出範本為 VSIX 精靈\] 來建立及散發專案範本。 如果您需要專案範本的更多控制權 \(例如，若要選擇出現在 \[新增專案\] 對話方塊中的圖示\)，您必須明確地建立專案範本並將其包裝在 VSIX 擴充功能中。 如需詳細資訊，請參閱 Visual Studio 部落格網站上的[建立及共用專案和項目範本](http://go.microsoft.com/fwlink/?LinkId=194551)。  
  
## 請參閱  
 [傳送 Visual Studio 擴充功能](../Topic/Shipping%20Visual%20Studio%20Extensions.md)