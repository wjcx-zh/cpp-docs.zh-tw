---
title: "連結器屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.RegisterOutput"
  - "VC.Project.VCLinkerTool.IgnoreImportLibrary"
  - "VC.Project.VCLinkerTool.UseLibraryDependencyInputs"
  - "VC.Project.VCLinkerTool.LinkLibraryDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "個別使用者重新導向"
  - "連結器屬性頁"
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 連結器屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題會討論 \[**一般**\] 連結器屬性頁上的下列屬性：  
  
 **忽略匯入程式庫**  
 指示連結器不要嘗試將這個組建產生的任何 .lib 輸出連結至任何相依專案 \(Dependent Project\)。  這讓專案系統能夠處理在建置時不產生 .lib 檔的 .dll 檔。  如果專案相依於產生 DLL 的其他專案，專案系統便會自動連結該子專案所產生的 .lib 檔。  這對產生 COM DLL 或僅限資源 DLL 的專案來說是不需要的，因為這些 DLL 並沒有任何有意義的匯出。  如果 DLL 沒有匯出，則連結器不會產生 .lib 檔。  如果磁碟中沒有匯出 .lib 檔且專案系統指示連結器連結這個 \(遺漏\) DLL，連結將會失敗。  
  
 使用 \[忽略匯入程式庫\] 來解決這個問題。  當設定為 `Yes` 時，專案系統將會忽略該 .lib 檔案是否存在，讓相依於這個專案的任何專案都不會與不存在的 .lib 檔案連結。  
  
 若要以程式設計的方式存取這個屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。  
  
 **註冊輸出**  
 執行 regsvr32.exe \/s $\(TargetPath\)，只對 .dll 專案有效。  .exe 專案會忽略這個屬性。  如果您要登錄 .exe 輸出，請在組態上設定建置後事件來進行登錄 .exe 檔所需的自訂登錄。  
  
 若要以程式設計的方式存取這個屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。  
  
 **個別使用者重新導向**  
 習慣上，[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的註冊是在 HKEY\_CLASSES\_ROOT \(HKCR\) 中進行的。  在 [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)] 中，若要存取 HKCR，您必須以更高階的權限模式來執行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  開發人員不會永遠都要以更高階的權限模式來執行，不過依然需要進行註冊。  個別使用者重新導向讓您能夠不需要以這個模式執行即可註冊。  
  
 個別使用者重新導向將會強制對 HKCR 的所有寫入，都重新導向到 HKEY\_CURRENT\_USER \(HKCU\)。  如果關閉個別使用者重新導向，便可能會在程式嘗試寫入 HKCR 時造成[專案建置錯誤 PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md)。  
  
 **連結程式庫相依性**  
 提供您 .lib 檔的連結選項，這個檔是由相依專案所產生。  一般而言，您會想要在 .lib 檔案中連結。  
  
 您可以提供檔案名稱和相對路徑以指定 .obj 檔案，例如 **..\\..\\MyLibProject\\MyObjFile.obj**。  如果 .obj 檔案的原始程式碼 \#includes 先行編譯標頭，例如 pch.h， pch.obj 檔案位於資料夾相同為 **MyObjFile.obj** ，那麼您也必須加入 **pch.obj** 指定為其他相依性。  
  
 **使用程式庫相依性輸入**  
 在大型的專案中，當相依專案產生 .lib 檔時，會停用累加連結。  如果有許多相依專案產生 .lib 檔案，則建立應用程式可能需要花費很久的時間。  當這個屬性設定為 `Yes` 時，專案系統便會在 .obj 檔中，為相依專案所產生的 .lib 檔進行連結，並進而啟用累加連結。  
  
 如需如何存取 \[**一般**\] 連結器屬性頁的詳細資訊，請參閱 [HOW TO：使用屬性頁指定專案屬性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
## 請參閱  
 [VC\+\+ Directories, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/zh-tw/e027448b-c811-4c3d-8531-4325ad3f6e02)   
 [屬性頁](../ide/property-pages-visual-cpp.md)