---
title: "轉散發 Visual C++ 檔案 | Microsoft Docs"
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
  - "應用程式部署 [C++], 檔案轉散發"
  - "部署應用程式 [C++], 檔案轉散發"
  - "檔案轉散發 [C++]"
  - "轉散發應用程式 [C++]"
  - "轉散發應用程式 [C++], 關於轉散發應用程式"
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
caps.latest.revision: 50
caps.handback.revision: 48
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 轉散發 Visual C++ 檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您部署應用程式時，您也必須部署必要的支援檔案。  如果其中有任何檔案是由 Microsoft 提供，請檢查您否有權限轉散發。  若要檢閱 Microsoft 軟體授權條款，請參閱 Visual Studio 安裝目錄或 Visual Studio 安裝媒體中的 License.htm。  若要檢視 Visual Studio 特定版本《Microsoft 軟體授權條款》之＜可散發程式碼＞一節所指的「可轉散發 \(REDIST\) 清單」，請參閱 Microsoft 網站上的 [Microsoft Visual Studio 2013 與 Microsoft Visual Studio 2013 SDK 可散發程式碼](http://go.microsoft.com/fwlink/p/?LinkId=313603)。  如需可轉散發檔案的詳細資訊，請參閱[決定要轉散發哪些 DLL](../ide/determining-which-dlls-to-redistribute.md) 和[部署範例](../ide/deployment-examples.md)。  
  
 若要部署可轉散發 Visual C\+\+ 檔案，您可以使用 Visual Studio 隨附的 Visual C\+\+ 可轉散發套件 \(VCRedist\_x86.exe、VCRedist\_x64.exe 或 VCRedist\_arm.exe\)。  您可以在 Visual Studio 安裝目錄 \(位於 Program Files \[\(x86\)\]\\Microsoft Visual Studio *version*\\VC\\redist\\*locale*\\\) 中找到這些檔案。  另一個選項是使用可轉散發合併模組 \(.msm 檔案\)，這些檔案位於 Program Files \[\(x86\)\]\\Common Files\\Merge Modules\\。  您也可以直接安裝「應用程式本機資料夾」中的可轉散發 Visual C\+\+ DLL，此資料夾是包含您的可執行應用程式檔案的資料夾。  對於維護原因，建議您不要使用此安裝位置。  
  
 Visual C\+\+ 可轉散發套件會安裝並註冊所有 Visual C\+\+ 程式庫。  如果使用可轉散發套件，您必須在目標系統上執行該套件並設定為安裝應用程式的必要條件。  建議您使用這些套件進行部署，以便自動更新 Visual C\+\+ 程式庫。  如需如何使用這些套件的範例，請參閱[逐步解說：使用 Visual C\+\+ 可轉散發套件部署 Visual C\+\+ 應用程式](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
 每個「Visual C\+\+ 可轉散發套件」都會檢查電腦上是否有較新的版本存在。  若發現較新的版本，則不會安裝該套件。  從 Visual Studio 2015 開始，可轉散發套件會顯示錯誤訊息，說明安裝程式失敗。  若使用 **\/quiet** 旗標執行套件，則不會顯示錯誤訊息。  不論是哪一種情況，Microsoft 安裝程式都會記錄錯誤，而且錯誤結果會被傳回給呼叫者。  從 Visual Studio 2015 套件開始，您可以檢查登錄值以判斷是否已安裝較新的版本。  目前已安裝的版本是以 REG\_SZ 值儲存在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\[\\Wow6432Node\]\\Microsoft\\DevDiv\\vc\\Servicing\\14.0\\RuntimeMinimum 的 Version 機碼中。  若目前已安裝的版本較新，則您不需要安裝您的可轉散發套件。  
  
 如果您使用的合併模組包含 Visual C\+\+ DLL ，則必須將它包含在您用來部署應用程式的 Windows Installer 套件 \(或類似的安裝套件\) 中。  如需詳細資訊，請參閱[使用合併模組轉散發](../ide/redistributing-components-by-using-merge-modules.md)。  如需範例，請參閱[逐步解說：使用安裝專案部署 Visual C\+\+ 應用程式](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)，其中也會說明如何使用 InstallShield Limited Edition 建立安裝套件。  
  
## 可能的執行階段錯誤  
 如果找不到 Visual C\+\+ 程式庫 DLL，而且 Windows 無法載入它供您的應用程式使用，則可能會出現這個訊息：**這個應用程式無法啟動，因為找不到 MSVCR\<版本號碼\>.dll，重新安裝應用程式可能可以解決這個問題。**  
  
 若要解決這種錯誤，請確定您的應用程式建置程序正確無誤，且已將 Visual C\+\+ 程式庫正確地部署在目標系統上。  如需詳細資訊，請參閱[了解 Visual C\+\+ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[使用合併模組轉散發](../ide/redistributing-components-by-using-merge-modules.md)|描述如何使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 可轉散發合併模組，將 Visual C\+\+ 執行階段程式庫安裝在 %windir%\\system32\\ 資料夾中做為共用的 DLL。|  
|[轉散發 Visual C\+\+ ActiveX 控制項](../ide/redistributing-visual-cpp-activex-controls.md)|描述如何轉散發使用了 ActiveX 控制項的應用程式。|  
|[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)|討論如何轉散發資料存取物件 \(DAO\) 的支援檔案，以及 Microsoft Data Access SDK 中的資料庫技術。|  
|[轉散發 MFC 程式庫](../ide/redistributing-the-mfc-library.md)|描述如何轉散發使用了 MFC 的應用程式。|  
|[轉散發 ATL 應用程式](../ide/redistributing-an-atl-application.md)|描述如何轉散發使用 ATL 的應用程式。  從 Visual Studio 2012 開始，就不需要適用於 aLT 的轉散發程式庫。|  
|[部署範例](../ide/deployment-examples.md)|示範如何部署 Visual C\+\+ 應用程式的範例連結。|  
|[部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)|介紹 Visual C\+\+ 部署概念和技術。|