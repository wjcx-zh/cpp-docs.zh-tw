---
title: "逐步解說：使用自動化呼叫 Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "逐步解說 [Visual Studio SDK], 使用自動化呼叫"
ms.assetid: ca4dab48-632c-4c2a-8c84-57c027e37987
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# 逐步解說：使用自動化呼叫 Visual Studio SDK
此逐步解說說明如何建立使用 Visual Studio 服務的 Visual Studio 增益集。 您所建立的增益集會取得服務提供者，並使用它來取得服務。 若要取得任何提供的 Visual Studio 服務，您可以使用這項相同的技術。 如需服務和服務提供者的詳細資訊，請參閱 [使用並提供服務](../Topic/Using%20and%20Providing%20Services.md)。 下列程序示範如何建立增益集，然後從增益集取得服務。  
  
## 建立增益集  
 在本節中，您會使用 Visual Studio 增益集專案範本來建立 Visual Studio 增益集。  
  
#### 建立增益集  
  
1.  建立新的 Visual Studio 專案 \(\[檔案\/新增\/專案\]\)。  
  
2.  在 \[新增專案\] 對話方塊的左窗格中，展開 \[其他專案類型\] 節點，然後按一下 \[擴充性\] 節點。 選取 \[Visual Studio 增益集\]。  
  
3.  建立名稱為 `Addin` 的新增益集專案。  
  
     在 \[[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 增益集精靈\] 中，按一下 \[下一步\]。  
  
4.  在 \[選取程式語言\] 頁面上，選取 \[使用 Visual C\# 建立增益集\] 或 \[使用 Visual Basic 建立增益集\]。  
  
5.  在 \[選擇主應用程式\] 頁面上，選取 \[Microsoft Visual Studio \<版本\>\]。  
  
6.  在 \[輸入名稱和描述\] 頁面上，於 \[名稱\] 方塊中輸入 `MyAddin`，並於 \[描述\] 方塊中輸入 `MyAddin Walkthrough`。  
  
7.  在 \[選擇增益集選項\] 頁面上，於 \[您要建立增益集的命令列 UI 嗎?\] 下選取 \[工具\] 功能表項目的選項。 清除其他核取方塊。  
  
8.  接受所有其他預設值。  
  
9. 建置方案，並確認方案編譯無誤。  
  
## 從增益集取得服務  
 下列步驟會引導您從增益集取得服務。  
  
#### 取得服務  
  
1.  開啟 Connect.cs 或 Connect.vb 檔案，並將這些行加入 `using` \(C\#\) 或 `Imports` \(Visual Basic\) 陳述式：  
  
     [!code-cs[VSSDKAddin#1](../misc/codesnippet/CSharp/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_1.cs)]
     [!code-vb[VSSDKAddin#1](../misc/codesnippet/VisualBasic/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_1.vb)]  
  
2.  在**方案總管**中，於專案節點上按一下滑鼠右鍵，然後加入這些 .NET 參考。  
  
    ```  
    Microsoft.VisualStudio.OLE.Interop Microsoft.VisualStudio.Shell.Interop  
    ```  
  
3.  將下列幾行的程式碼加入 `Exec` 方法的 `if(commandName == "Addin.Connect.Addin")` 或 `If commandName = "Addin.Connect.Addin" Then` 子句中：  
  
     [!code-cs[VSSDKAddin#2](../misc/codesnippet/CSharp/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_2.cs)]
     [!code-vb[VSSDKAddin#2](../misc/codesnippet/VisualBasic/walkthrough-calling-into-the-visual-studio-sdk-by-using-automation_2.vb)]  
  
     這個程式碼會將目前應用程式物件 \(類型 `DTE2`\) 轉換為 `IOleServiceProvider`，然後呼叫 `QueryService` 以取得 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服務。 這個服務提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面。 執行增益集時，<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> 方法會顯示訊息方塊。  
  
4.  按 F5 鍵，以偵錯模式建置和啟動增益集專案。  
  
     這會啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的另一個執行個體。  
  
5.  在新的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 執行個體中，按一下 \[工具\] 功能表上的 \[增益集\]。 訊息方塊會顯示下列訊息：  
  
    ```  
    MyAddin Inside Addin.Connect  
    ```  
  
## 請參閱  
 [如何：停用和移除增益集](../Topic/How%20to:%20Deactivate%20and%20Remove%20an%20Add-In.md)