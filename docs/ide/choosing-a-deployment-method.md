---
title: "選擇部署方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式部署 [C++], 方法"
  - "部署應用程式 [C++], 方法"
  - "DLL [C++], 轉散發"
  - "動態連結 [C++]"
  - "程式庫 [C++], 應用程式部署問題"
  - "資訊清單 [C++]"
  - "轉散發 DLL"
  - "並存組件 [C++]"
  - "靜態連結 [C++]"
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
caps.latest.revision: 35
caps.handback.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 選擇部署方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除非您的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 應用程式是獨立的，而且可以利用複製命令進行部署，否則建議您使用 Windows Installer 進行部署。  Windows Installer 支援安裝、修復或解除安裝，同時也支援不可部分完成更新應用程式檔案、相依性和登錄項目。  
  
> [!NOTE]
>  雖然可以在 Visual Studio 中利用 [ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md) 方法部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 原生應用程式，但必須執行額外的步驟。  如需詳細資訊，請參閱 [Visual C\+\+ 應用程式的 ClickOnce 部署](../ide/clickonce-deployment-for-visual-cpp-applications.md)。  
  
## Visual C\+\+ 程式庫是共用 DLL  
 由於 Visual Studio 安裝程式會將 Visual C\+\+ 程式庫安裝在 %windir%\\system32\\ 目錄中，當您開發與這些程式庫相依的 Visual C\+\+ 應用程式時，該應用程式會如預期執行。  不過，若要在可能沒有安裝 Visual Studio 的電腦上部署該應用程式，建議您先確定已將程式庫和應用程式一併安裝在那些電腦中。  
  
## 轉散發 Visual C\+\+ 程式庫  
 在您的部署中，您可以轉散發具有轉散發授權的任何 Visual C\+\+ 程式庫版本。  部署方法有三種：  
  
-   使用可轉散發套件集中部署，這會將 Visual C\+\+ 程式庫安裝在 %windir%\\system32\\ 中做為共用的 DLL \(必須要有系統管理員權限才能安裝至此資料夾\)。在目標電腦上安裝應用程式之前，您可以建立會執行可轉散發套件的指令碼或安裝程式。  可轉散發套件適用於 x86、x64 和 ARM 平台 \(VCRedist\_x86.exe、VCRedist\_x64.exe 或 VCRedist\_arm.exe\)。  Visual Studio 將這些套件包含在 %ProgramFiles\(x86\)%\\Microsoft Visual Studio `version`\\VC\\Redist\\`locale ID`\\ 中。  您也可以從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkId=132793)下載檔案 \(在 \[下載中心\] 中搜尋與您的應用程式相符的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 可轉散發套件 *Visual Studio version and update*。  例如，若您使用 Visual Studio 2012 Update 4 建置應用程式，請搜尋「Visual C\+\+ 可轉散發套件 2012 Update 4」\)。如需關於如何使用可轉散發套件的資訊，請參閱[逐步解說：使用 Visual C\+\+ 可轉散發套件部署 Visual C\+\+ 應用程式](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
-   使用合併模組進行集中部署時，每一個模組各會將一個特定的 Visual C\+\+ 程式庫安裝在 %windir%\\system32\\ 中做為共用的 DLL \(必須要有系統管理員權限才能安裝至此資料夾\)。合併模組會變成應用程式 .msi 安裝程式檔案的一部分。  Visual C\+\+ 可轉散發合併模組包含在 Visual Studio 的 \\Program Files \(x86\)\\Common Files\\Merge Modules\\ 中。  如需詳細資訊，請參閱[使用合併模組轉散發](../ide/redistributing-components-by-using-merge-modules.md)。  
  
-   本機部署，使用此方法時，您可以從 Visual Studio 安裝複製特定的 Visual C\+\+ DLL \(通常位於 \\Program Files \(x86\)\\Microsoft Visual Studio `version`\\VC\\Redist\\`platform`\\`library`\\\)，再將這些 DLL 安裝在目標電腦上應用程式可執行檔所在的相同資料夾中。  您可以使用此部署方法讓不具系統管理員權限的使用者進行安裝，也可以用於安裝可透過網路共用執行的應用程式。  
  
 若部署使用可轉散發合併模組，但由不具系統管理員權限的使用者執行安裝，則不會安裝 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLL，應用程式也不會執行。  此外，以合併模組建置 \(允許個別使用者安裝\) 的應用程式安裝程式會將程式庫安裝在共用位置，此位置會影響系統的所有使用者。  您可以使用本機部署將必要的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] DLL 安裝在特定使用者的應用程式目錄中，而不會影響其他使用者，也不需要具備系統管理員權限。  由於這可能會產生服務性問題，我們不建議本機部署 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 可轉散發 DLL。  
  
 不正確的 Visual C\+\+ 程式庫部署方式可能會在執行相依的應用程式時發生執行階段錯誤。  當作業系統載入應用程式時，會按照 [LoadLibraryEx](http://go.microsoft.com/fwlink/?LinkId=132792) 中所述的搜尋順序進行。  
  
## 動態連結比靜態連結適合  
 建議您避免轉散發 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 程式庫時使用靜態連結。  靜態連結幾乎無法大幅改善應用程式效能，卻會提高服務代價。  例如，請考慮靜態連結至已更新安全性增強之程式庫的應用程式，除非重新編譯並重新部署，否則該應用程式不會因此受益。  相反地，我們建議您將應用程式動態連結至相依的程式庫，以便在部署時更新這些程式庫。  
  
## 請參閱  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Not in Build: Choosing a Deployment Strategy](http://msdn.microsoft.com/zh-tw/ecd632d8-063c-4028-b785-81bba045107b)   
 [Windows Installer Deployment Overview](http://msdn.microsoft.com/zh-tw/3ce4610a-b54f-404e-b650-42f4a55dfc3b)   
 [ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)   
 [部署範例](../ide/deployment-examples.md)