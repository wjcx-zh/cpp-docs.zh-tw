---
title: "逐步解說：使用自動化來擴充 Managed VSPackage | Microsoft Docs"
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
  - "Managed VSPackage, 使用自動化來擴充"
  - "自動化 [Visual Studio SDK], 逐步解說"
  - "自動化 [Visual Studio SDK], Managed VSPackage"
ms.assetid: 7fd2000b-8ec3-4d83-b169-d38008fb57ee
caps.latest.revision: 35
caps.handback.revision: 35
manager: "douge"
---
# 逐步解說：使用自動化來擴充 Managed VSPackage
此逐步解說將說明如何使用自動化來建立 Managed VSPackage，操作 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\)。 您建立範例 Managed VSPackage，然後在產生的 VSPackage 中使用自動化方法，在 \[輸出\] 視窗顯示 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 屬性。  
  
## 必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../Topic/Visual%20Studio%20SDK.md)。  
  
## Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在 \[新增專案\] 對話方塊的三個不同位置：  
  
1.  位在 Visual Basic 擴充性下。 專案的預設語言為 Visual Basic。  
  
2.  位在 C\# 擴充性下。 專案的預設語言為 C\#。  
  
3.  位在其他專案類型擴充性下。 專案的預設語言為 C\+\+。  
  
### 建立 Managed VSPackage  
  
1.  建立名為 `Auto` 的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Package 專案。  
  
     如需如何建立 Managed VSPackage 的詳細資訊，請參閱[逐步解說：使用 Visual Studio 封裝範本建立功能表命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
2.  在 \[選取程式設計語言\] 頁面上，將語言設為 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]。  
  
3.  保留 \[基本 VSPackage 資訊\] 頁面中的預設值。  
  
4.  在 \[選取 VSPackage 選項\] 頁面上，選取 \[功能表命令\] 核取方塊。  
  
5.  在 \[命令選項\] 頁面上，將 \[命令名稱\] 變更為 `Auto`。  
  
6.  按一下 \[完成\] 按鈕。  
  
     範本會產生名為 Auto 的 Managed 專案。  
  
7.  建置方案，並確認方案編譯無誤。  
  
### 呼叫 Automation 模型  
  
1.  在**方案總管**中，以滑鼠右鍵按一下 Auto 專案節點，然後按一下 \[加入\]、\[參考\]。  
  
2.  在 \[參考\] 對話方塊的 \[.NET\] 索引標籤，按兩下 \[EnvDTE\]。  
  
     這會加入 EnvDTE 自動化命名空間的參考。  
  
3.  在 AutoPackage 檔案中，加入下列命名空間參考。  
  
     [!code-cs[VSSDKAuto#1](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_1.cs)]
     [!code-vb[VSSDKAuto#1](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_1.vb)]  
  
4.  在 AutoPackage 檔案中，將 `MenuItemCallback` 方法的主體取代為下列程式碼行：  
  
     [!code-cs[VSSDKAuto#2](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_2.cs)]
     [!code-vb[VSSDKAuto#2](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_2.vb)]  
  
 此程式碼會呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 以取得 <xref:EnvDTE.DTE> 自動化物件，代表 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE。`MenuItemCallback` 中的自動化程式碼會在 \[輸出\] 視窗中建立名為 **Test** 的新窗格。[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 名稱和版本接著會寫入新的 \[輸出\] 窗格。  
  
1.  按 F5 鍵，以偵錯模式建置和啟動 Auto 專案。  
  
     這會啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 實驗組建 \([!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Exp\)。  
  
    > [!NOTE]
    >  兩個版本的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 會在此時開啟。  
  
2.  在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Exp 的 \[工具\] 功能表上，按一下 \[Auto\]。  
  
     名為 **Test** 的新窗格會在 \[輸出\] 視窗中開啟，並顯示如下：  
  
    ```  
    Name is Microsoft Visual Studio Version is x.xx  
    ```  
  
     其中 x.xx 是最新的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本號碼。  
  
     如需自動化範例的詳細資訊，請參閱 [Visual Studio 的自動化範例](http://www.microsoft.com/downloads/details.aspx?familyid=3ff9c915-30e5-430e-95b3-621dccd25150&displaylang=en)。  
  
## 請參閱  
 [擴充 Visual Studio 環境](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)