---
title: "擴充功能分析器 | Microsoft Docs"
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
  - "VSPackage, 載入失敗分析器"
ms.assetid: 8d2bcc4e-9feb-45a5-8d8e-470346f0d39e
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# 擴充功能分析器
\[擴充功能分析器\] 可擷取和記錄最常見的擴充功能載入失敗。 \[擴充功能分析器\] 會在自己的工具視窗中執行。 該分析器會回報失敗原因，並建議修正問題的方法。  
  
 您可以從 Visual Studio 組件庫下載 [\[擴充功能分析器\]](http://go.microsoft.com/fwlink/?LinkId=205840)。 \[擴充功能分析器\] 的組件會安裝在 \<*Visual Studio 安裝路徑*\>\\Common7\\IDE\\PrivateAssemblies\\ 中。  
  
## 瀏覽器  
 安裝好 \[擴充功能分析器\] 之後，請在 \[工具\] 功能表上，依序按一下 \[擴充功能分析器\] 和 \[瀏覽器\]。 即會顯示一個視窗，其中列出電腦已註冊的所有擴充功能。 該視窗也會提供 VSIX 檔案、VSPackage、PkgDef 檔案和 MEF 元件的不同索引標籤。 您可以依任何資料行名稱來排序清單。  
  
1.  \[VSIX\] 索引標籤會顯示已安裝的 VSIX 擴充功能資訊。 您可以選取 \[Show System Components\] \(顯示系統元件\) 核取方塊，以納入系統元件。 在這個索引標籤中，您可以巡覽至 VSIX 的記錄檔項目、在 Visual Studio XML 編輯器中開啟 VSIX 資訊清單，並開啟 VSIX 擴充功能所在的安裝資料夾。  
  
2.  \[VSPackage\] 索引標籤會顯示 Visual Studio 中目前已知的 VSPackage 資訊 \(不論是否已載入\)。 這些資訊包括 VSIX 識別項、.pkgdef 檔和 VSPackage 的 GUID。 您可以選取 \[Show System Packages\] \(顯示系統套件\) 核取方塊，以納入系統 VSPackage。 在這個索引標籤中，您可以巡覽至記錄檔項目、查看 \[VSIX\] 索引標籤上列出的 VSIX、查看 \[PkgDef 檔案\] 索引標籤上列出的 .pkgdef 檔，並分析 VSPackage。 \[輸出\] 窗格會顯示分析的結果。  
  
3.  \[PkgDef 檔案\] 索引標籤會顯示 Visual Studio 中已知擴充功能的 .pkgdef 檔案資訊。 這些資訊包括 VSIX 識別項和擴充功能的路徑。 您可以巡覽至記錄檔或 \[VSIX\] 索引標籤，並在編輯器中檢視 .pkgdef 檔。  
  
4.  \[MEF 元件\] 索引標籤會顯示 Visual Studio 中已知的 MEF 元件資訊。 這些資訊包括 VSIX 識別項和擴充功能的安裝路徑。 您可以選取 \[Show System Components\] \(顯示系統元件\) 核取方塊，以納入系統元件。 您也可以巡覽至對應的 VSIX 項目、.pkgdef 檔和擴充功能所在的安裝位置。  
  
> [!WARNING]
>  您可能會收到要求開啟 Fusion 記錄的訊息。 若要這樣做，請指定記錄檔的位置。 您可能需要重新啟動 Visual Studio 的所有執行個體，然後再繼續。  
  
## 記錄檔檢視器  
 如果您執行的專案已開啟記錄功能 \(方法是將 \/log 新增至專案的命令列引數\)，則可以使用**擴充功能記錄檔檢視器**來查看記錄檔訊息。 如需詳細資訊，請參閱[\/Log](../Topic/-Log%20\(devenv.exe\).md)。 \[擴充功能記錄檔檢視器\] 視窗會顯示日期、接聽程式、項目類型 \(訊息類型\)、錯誤類型、類別\/介面資訊，以及記錄檔訊息。 您可以排序和篩選這些資訊。  
  
## 常見的擴充功能載入問題  
 下列為 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 擴充功能載入失敗的一般原因；  
  
-   相依性問題。 擴充功能的部署方式可能導致找不到相依組件。  
  
-   例外狀況。 當載入 VSPackage 時，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 呼叫自己的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 方法。 如果此方法擲回例外狀況，VSPackage 載入就會失敗。 若要排除此問題，最好逐步執行 SetSite 程式碼。  
  
-   註冊不當。 驗證擴充功能是否已妥善簽署，並使用正確的公開金鑰註冊 VSPackage。  
  
## 請參閱  
 [管理 Vspackage](../Topic/Managing%20VSPackages.md)