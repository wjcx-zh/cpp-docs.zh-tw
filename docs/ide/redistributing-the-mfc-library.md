---
title: "轉散發 MFC 程式庫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "MFC, 轉散發"
  - "轉散發 MFC 程式庫"
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
caps.latest.revision: 32
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 轉散發 MFC 程式庫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您將應用程式動態連結至 MFC 程式庫，則必須轉散發 Msvcr100.dll，因為所有 MFC DLL 都使用 C 執行階段程式庫 \(CRT\) 的共用版本。  您也必須轉散發 Mfc100u.dll 或 Mfc100.dll。  
  
 如果您將應用程式靜態連結至 MFC \(也就是說，如果您在 \[**屬性頁**\] 對話方塊的 \[**一般**\] 索引標籤上指定了 \[**使用 MFC 的靜態程式庫**\]\)，則不需要轉散發 Mfc100u.dll 或 Mfc100.dll。  不過，雖然在測試和內部部署應用程式時使用靜態連結沒問題，但仍不建議用它來轉散發 MFC。  如需部署 Visual C\+\+ 程式庫之建議策略的詳細資訊，請參閱[選擇部署方法](../ide/choosing-a-deployment-method.md)。  
  
 如果您的應用程式使用了實作 WebBrowser 控制項的 MFC 類別 \(例如，[CHtmlView 類別](../mfc/reference/chtmlview-class.md)或 [CHtmlEditView Class](../mfc/reference/chtmleditview-class.md)\)，則建議您也安裝最新版的 Microsoft Internet Explorer，讓目標電腦具有最新的通用控制項檔案 \(至少需要 Internet Explorer 4.0\)。如需如何安裝 Internet Explorer 元件的詳細資訊，請參閱 Microsoft 技術支援網站上的＜文件 185375：如何建立 Internet Explorer 的單一 EXE 安裝＞\(機器譯文\)。  
  
 如果您的應用程式使用 MFC 資料庫類別 \(例如 [CRecordset Class](../mfc/reference/crecordset-class.md)和 [CRecordView Class](../mfc/reference/crecordview-class.md)\)，則您必須轉散發應用程式所使用的 ODBC 和任何 ODBC 驅動程式。  如需詳細資訊，請參閱[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)。  
  
 如果您的 MFC 應用程式會使用 Windows Form 控制項，您就必須隨同應用程式一併轉散發 mfcmifc80.dll。  這個 DLL 是以強式名稱簽署的 .NET 組件，可以在應用程式的本機資料夾中隨著應用程式轉散發，或是透過[Gacutil.exe \(Global Assembly Cache Tool\)](../Topic/Gacutil.exe%20\(Global%20Assembly%20Cache%20Tool\).md) 部署到「全域組件快取」\(GAC\)。  
  
 如果您要轉散發 MFC DLL，請確認所轉散發的是零售版本，而非偵錯版本。  DLL 的偵錯版本無法轉散發。  偵錯版本的 MFC DLL 名稱結尾會有個 "d"，例如 Mfc100d.dll。  
  
 如果您要修改 MFC 來源，然後重新建置 MFC DLL，則必須重新命名修改過的 MFC DLL，這樣才不會和 Visual Studio 包含的 MFC DLL 發生衝突。  建議您不要重新建置或重新命名 MFC DLL。  如需詳細資訊，請參閱 MFC 技術提示 33。  
  
 您可以使用 VCRedist\_*architecture*.exe\(隨 Visual Studio 一起安裝的合併模組\)，或在應用程式所在的資料夾中部署 MFC DLL，藉此重新分配 MFC。  如需如何轉散發 MFC 的詳細資訊，請參閱[轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
## 當地語系化 MFC 元件的安裝  
 如果您決定要安裝 MFC 當地語系化 DLL 來當地語系化您的應用程式，則必須使用可轉散發合併檔案 \(.msm\)。  例如，如果您要在 x86 電腦上當地語系化應用程式，就必須將 Microsoft\_VC100\_MFCLOC\_x86.msm 合併到適用於 x86 電腦的安裝套件。  
  
 可轉散發的 .msm 檔案包含可用於當地語系化的 DLL。  每種支援的語言各有一個 DLL。  安裝程序會將這些 DLL 安裝在目標電腦的 %windir%\\system32\\ 資料夾中。  
  
 如需如何當地語系化 MFC 應用程式的詳細資訊，請參閱 [TN057：MFC 元件的當地語系化](../mfc/tn057-localization-of-mfc-components.md)，以及 Microsoft 支援網站上的[文件 208983：如何使用 MFC LOC DLL](http://go.microsoft.com/fwlink/?LinkId=198025)。  
  
 您可以將 MFC DLL 部署至應用程式本機資料夾，以轉散發 MFC 當地語系化 DLL。  如需如何轉散發 Visual C\+\+ 程式庫的詳細資訊，請參閱[轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)。  
  
## 請參閱  
 [轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)