---
title: "決定要轉散發哪些 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
  - "應用程式部署 [C++], DLL 轉散發"
  - "相依性 [C++], 應用程式部署和"
  - "部署應用程式 [C++], DLL 轉散發"
  - "DLL [C++], 轉散發"
  - "轉散發 DLL"
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 決定要轉散發哪些 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建置的應用程式時，如果該應用程式使用 Visual Studio 所提供的 Dll，則應用程式使用者的電腦上也必須要有這些 Dll，應用程式才能執行。  因為大部分的使用者可能未安裝 Visual Studio，因此您必須為他們提供這些 Dll。  Visual Studio 可讓這些 Dll 成為您能夠包含在應用程式安裝程式中的可轉散發程式庫。  
  
 可轉散發 Dll 隨附於 Visual Studio 的安裝中。  根據預設，它們會安裝在 Program Files \(x86\)\\Microsoft Visual Studio version\\VC\\Redist 資料夾中。  為了使其更容易包含在您的安裝程式中，您也可從 Microsoft 下載中心取得獨立的可轉散發套件。  這些是會將可轉散發檔案安裝在使用者電腦上的可執行檔。  可轉散發套件的版本必須符合用來建立應用程式的 Visual Studio 工具組版本。  若要尋找相符的可轉散發套件，請在 [Microsoft 下載中心](http://go.microsoft.com/fwlink/p/?LinkId=158431)中搜尋「Visual C\+\+ 可轉散發套件」。  
  
 若要判斷必須隨應用程式一起轉散發的 DLL，請收集應用程式所依賴的 DLL 並做成一份清單。  收集這份清單的其中一個方法是執行 Dependency Walker \(depends.exe\)，如[了解 Visual C\+\+ 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)所說明。  
  
 取得相依性清單後，請將它與 Microsoft Visual Studio 安裝目錄中任何 Redist.txt 檔案的清單比較，或是與您的 Visual Studio 版本的《Microsoft 軟體授權條款》＜可散發程式碼＞一節所指之可轉散發 DLL 的「可轉散發 \(REDIST\) 清單」進行比較。  Visual Studio 2013 的清單可透過網路從 [Microsoft Visual Studio 2013 和 Microsoft Visual Studio 2013 SDK 的可散發程式碼](http://go.microsoft.com/fwlink/p/?LinkId=313603)取得。  並不是 Visual Studio 中包含的檔案都可讓您轉散發；您只能轉散發 Redist.txt 或線上「REDIST 清單」中指定的檔案。 您不能轉散發偵錯版本的應用程式以及各種 Visual C\+\+ 偵錯 DLL。  如需詳細資訊，請參閱[選擇部署方法](../ide/choosing-a-deployment-method.md)。  
  
 下表描述您的應用程式可能依賴的部分 Visual C\+\+ DLL。  
  
|Visual C\+\+ 程式庫|描述|適用於|  
|----------------------|--------|---------|  
|msvcr*version*.dll|機器碼的 C 執行階段程式庫 \(CRT\)。|使用 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)的應用程式。|  
|msvcp*version*.dll|機器碼的 Standard C\+\+ 程式庫。|使用 [Standard C\+\+ 程式庫](../standard-library/cpp-standard-library-reference.md)的應用程式。|  
|mfc*version*.dll|Microsoft Foundation Class \(MFC\) 程式庫。|使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)的應用程式。|  
|mfc*version*u.dll|具有 Unicode 支援的 MFC 程式庫。|使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)並需要 Unicode 支援的應用程式。|  
|mfcmifc80.dll|MFC Managed 介面程式庫。|搭配使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)與 [Windows Form 控制項](../Topic/Windows%20Forms%20Controls.md)的應用程式。|  
|mfcm*version*.dll|MFC Managed 程式庫。|搭配使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)與 [Windows Form 控制項](../Topic/Windows%20Forms%20Controls.md)的應用程式。|  
|mfcm*version*u.dll|具有 Unicode 支援的 MFC Managed 程式庫。|搭配使用 [MFC 程式庫](../mfc/mfc-desktop-applications.md)與 [Windows Form 控制項](../Topic/Windows%20Forms%20Controls.md)的應用程式需要 Unicode 支援。|  
  
> [!NOTE]
>  您不再需要以個別 DLL 的形式轉散發 Active Template Library。  其功能已移至標頭和靜態程式庫。  
  
 如需如何隨應用程式一起轉散發這些 DLL 的詳細資訊，請參閱[轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)。  如需範例，請參閱[部署範例](../ide/deployment-examples.md)。  
  
 一般而言，您並不需要轉散發系統 Dll，因為它們是作業系統的一部分。  但是，還是有一些例外情形，例如當應用程式會在數個版本的 Microsoft 作業系統上執行時。  在此情況下，請務必閱讀對應的授權條款。  另外，請嘗試透過 Windows Update、Service Pack 或 Microsoft 提供的可轉散發套件，將系統 DLL 升級。  您可以在 [Microsoft 支援](http://support.microsoft.com/)網站或 [Microsoft 下載中心](http://go.microsoft.com/fwlink/p/?LinkId=158431)上搜尋，以找出可用的套件。  
  
## 請參閱  
 [選擇部署方法](../ide/choosing-a-deployment-method.md)   
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)