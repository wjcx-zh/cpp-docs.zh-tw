---
title: "開發 Visual C++ 的 IDE 和工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "Visual C++, 開發工具"
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 開發 Visual C++ 的 IDE 和工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C++ 是 Visual Studio 整合式開發環境 (IDE) 的一部分，與其他語言共用許多相同的視窗和工具。 其中許多視窗和工具會在 MSDN Library 的 **Visual Studio IDE**底下提供說明，包括方案總管 [](../Topic/Visual%20Studio%20IDE.md)、程式碼編輯器和偵錯工具。 這些共用工具或視窗針對 C++ 所提供的功能集，通常會與針對 .NET 語言或 Javascript 所提供的功能集稍有不同。 有些視窗或工具只有 Visual Studio Pro 或 Visual Studio Enterprise 才會提供。 本主題從 Visual C++ 的觀點來介紹 Visual Studio IDE，並提供與 Visual C++ 相關的其他主題連結。  
  
 除了 Visual Studio IDE 中的共用工具之外，Visual C++ 還有數個專門用來開發機器碼的工具。 本文也會列出這些工具。 如需各版 Visual Studio 中的可用工具清單，請參閱 [Visual C++ Tools and Templates in Visual Studio Editions](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)。  
  
## <a name="creating-a-solution-and-projects"></a>建立方案和專案  
 您可以在所有 Visual C++ 版本中，將可執行檔 (例如 .exe、.dll 或 .lib) 的原始程式碼和相關檔案，組織成一個專案。 專案包含一個 XML 格式的專案檔 (.vcxproj)，其指定編譯程式所需的所有檔案和資源，並包含其他組態設定，例如目標平台 (x86、x64 或 ARM)，以及您要建置程式的發行版本或偵錯版本。 專案 (一個或多個) 包含在 *「方案」*(solution) 中；例如，方案可能包含數個 Win32 DLL 專案，以及使用這些 DLL 的一個 Win32 主控台應用程式。 當您建置專案時，MSBuild 引擎會使用專案檔，並產生可執行檔及 (或) 您已指定的其他任何自訂輸出。  
  
 **專案範本**  
  
 Visual C++ 隨附數個專案範本，其中包含各種基本程式類型所需的起始程式碼和設定。 您一開始通常會選擇 **檔案 &#124;新的專案** 從專案範本建立專案，然後將新的原始程式檔加入至該專案，或開始撰寫程式碼提供的檔案。 如需 C++ 專案和專案精靈的特定資訊，請參閱 [Creating and Managing Visual C++ Projects](../ide/creating-and-managing-visual-cpp-projects.md)。  
  
 **應用程式精靈**  
  
 Visual C++ 提供針對某些專案類型的精靈。 該精靈可引導您逐步完成建立新專案的程序。 這對具有許多選項和設定的專案類型會很有幫助。 如需詳細資訊，請參閱 [Creating Desktop Projects By Using Application Wizards](../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
## <a name="creating-user-interfaces-with-designers"></a>使用設計工具建立使用者介面  
 如果您的程式具有使用者介面，首要工作之一就是將按鈕、清單方塊等控制項填入其中。 Visual Studio 包含針對 C++ 應用程式之各種類別的視覺化設計介面和工具箱。 不論您建立的應用程式類型為何，基本概念都一樣：您會將控制項從工具箱視窗，拖曳至設計介面的所需位置。 Visual Studio 會在背景產生正常運作所需的資源和程式碼。  
  
 如需設計通用 Windows 平台應用程式的使用者介面的詳細資訊，請參閱  [設計和 UI](https://developer.microsoft.com/en-us/windows/design)。  
  
 如需建立 MFC 應用程式之使用者介面的詳細資訊，請參閱 [MFC Desktop Applications](../mfc/mfc-desktop-applications.md)。 Win32 Windows 程式的相關資訊，請參閱 [Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)。  
  
 如需使用 C++/CLI 建立 Windows Form 應用程式的相關資訊，請參閱 [使用 .NET Framework 建立 Windows Form 應用程式 (C++)](http://msdn.microsoft.com/zh-tw/8e007885-6c8b-4fb2-a41d-91febd114a9b)。  
  
## <a name="writing-and-editing-code"></a>撰寫和編輯程式碼  
 **語意的顏色標示**  
  
 建立專案之後，所有專案檔會都會顯示在方案總管視窗中。 當您按一下方案總管中的 .h 或 .cpp 檔案時，會在程式碼編輯器中開啟檔案。 程式碼編輯器是 C++ 原始程式碼特有的文書處理器。 它以顏色標示語言關鍵字、方法和變數名稱，以及程式碼的其他項目，以便您更容易閱讀和了解程式碼。  
  
 **Intellisense**  
  
 程式碼編輯器也支援數項功能，這些功能統稱為 Intellisense。 您可以將滑鼠指標停留在某個方法上方，以查看該方法的一些基本說明。 輸入類別的變數名稱以及 . 或 -> 之後，該類別的執行個體成員清單隨即出現。 如果您輸入類別名稱，再輸入 ::，則會出現靜態成員清單。 當您開始輸入類別或方法名稱時，程式碼編輯器會提供完成陳述式的建議。 如需詳細資訊，請參閱 [Using IntelliSense](../Topic/Using%20IntelliSense.md)。  
  
 **程式碼片段**  
  
 您可以使用 Intellisense 程式碼片段，只要輸入一個快速鍵，就能產生常用或複雜的程式碼建構。 如需詳細資訊，請參閱 [Code Snippets](../Topic/Code%20Snippets.md)。  
  
## <a name="navigating-code"></a>巡覽程式碼  
 您可以透過 [檢視] 功能表存取許多視窗和工具，以巡覽程式碼檔案。 如需這些視窗的詳細資訊，請參閱 [Viewing the Structure of Code](../Topic/Viewing%20the%20Structure%20of%20Code.md)。  
  
 **方案總管]**  
  
 您可以在所有 Visual Studio 版本中，使用方案總管窗格來巡覽專案中的檔案。 請展開 .h 或 .cpp 檔案圖示，以檢視檔案中的類別。 然後展開類別，以查看其成員。 按兩下其中一個成員，即可巡覽至檔案中該成員的定義或實作。  
  
 **類別檢視] 和 [程式碼定義視窗**  
  
 您可以使用 [類別檢視] 窗格來查看所有檔案的命名空間和類別，包括部分類別。 您可以展開每個命名空間或類別，以查看其成員，然後按兩下成員，以巡覽至原始程式檔中的該位置。 如果您開啟 [程式碼定義視窗]，您可以檢視在 [類別檢視] 中所選擇之類型的定義或實作。  
  
 **物件瀏覽器**  
  
 您可以使用 [物件瀏覽器] 來瀏覽 Windows 執行階段元件 (.winmd 檔案)、.NET 組件和 COM 類型程式庫中的類型資訊。 它不適用於 Win32 DLL。  
  
 **移至定義/宣告**  
  
 在任何應用程式開發介面名稱或成員變數上按 F12 鍵，即可移至其定義。 如果定義是在 .winmd 檔案中 (若為 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 應用程式)，則會在 [物件瀏覽器] 中顯示類型資訊。 您也可以在變數或類型名稱上按一下滑鼠右鍵，然後從操作功能表選擇選項，來移至定義或移至宣告。  
  
 **尋找所有參考**  
  
 在原始程式碼檔案中，將滑鼠游標停留在類型、方法或變數名稱上方並按一下滑鼠右鍵，然後選擇 [尋找所有參考]，即可傳回檔案、專案或方案中使用該類型的每個位置清單。 [尋找所有參考] 是智慧型功能，只會傳回完全相同之變數的執行個體，包括其他在不同範圍中有相同名稱的變數。  
  
 **架構總管和相依性圖形 （旗鑑版）**  
  
 您可以使用架構總管來檢視程式碼中各種項目之間的關聯性。 如需詳細資訊，請參閱 [使用架構總管尋找程式碼](http://msdn.microsoft.com/zh-tw/b1707926-ef73-47f9-92cd-e00d0fac7e76)。 使用相依性圖形可檢視相依性關聯性。 如需詳細資訊，請參閱 [How to: Generate Dependency Graphs for C and C++ Code](http://msdn.microsoft.com/zh-tw/3bd5cf9f-62f6-41d0-9f35-d4b2637cba3c)。  
  
## <a name="adding-and-editing-resources"></a>加入和編輯資源  
 「資源」一詞在 Visual Studio 桌面專案的內容中，可以是對話方塊、圖示、可當地語系化的字串、啟動顯示畫面、資料庫連接字串，或任何您想要包含在可執行檔中的任意資料。  
  
 如需加入和編輯原生桌面 C++ 專案中資源的詳細資訊，請參閱 [Working with Resource Files](../mfc/working-with-resource-files.md)。  
  
## <a name="building-compiling-and-linking"></a>建置 (編譯和連結)  
 按下 **Ctrl + Shift + B** 可編譯及連結專案。 Visual Studio 會使用 [MSBuild](MSBuild1.md) 來建立可執行程式碼。 您可以設定在一般建置選項 **工具與 #124;選項與 #124;專案和方案** 而且您可以設定在特定專案的屬性 **專案 &#124;屬性**。 組建錯誤和警告會報告錯誤清單 (**Ctrl +\\, ，E**)。 有時還會在 [輸出] 視窗 (**Alt + 2**) 中顯示其他資訊。 如需詳細資訊，請參閱  [使用專案屬性](../ide/working-with-project-properties.md) 和 [Visual Studio 中建置 c + + 專案](../ide/building-cpp-projects-in-visual-studio.md)。  
  
 您也可以直接從命令列使用 Visual C++ 編譯器 (cl.exe)，以及其他許多與建置相關的獨立工具，例如 NMAKE 和 LIB。 如需詳細資訊，請參閱 [Building on the Command Line](../build/building-on-the-command-line.md) 和 [C/C++ Building Reference](../build/reference/c-cpp-building-reference.md)。  
  
## <a name="testing"></a>測試  
 Visual Studio 包含同時適用於原生 C++ 和 C++/CLI 的單元測試架構。 如需詳細資訊，請參閱 [使用單元測試驗證程式碼](../Topic/Unit%20Test%20Your%20Code.md) 和 [使用適用於 C++ 的 Microsoft 單元測試架構撰寫適用於 C/C++ 的單元測試](../Topic/Writing%20Unit%20tests%20for%20C-C++%20with%20the%20Microsoft%20Unit%20Testing%20Framework%20for%20C++.md)。  
  
## <a name="debugging"></a>偵錯  
 您可以在專案組態設定為 [偵錯] 時，按 F5 鍵來偵錯程式。 在偵錯期間，您可以按 F9 鍵設定中斷點、按 F10 鍵逐步執行程式碼、檢視指定變數或暫存器的值，甚至在某些情況下，您還可以在程式碼中進行變更並繼續偵錯，而不需要重新編譯。 如需詳細資訊，請參閱 [Debugging in Visual Studio](../Topic/Debugging%20in%20Visual%20Studio.md)。  
  
## <a name="deploying-completed-applications"></a>部署完成的應用程式  
 您將部署 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 客戶透過 Windows 市集透過 **專案 &#124;存放區** 功能表選項。 CRT 的部署會在背景自動處理。 如需詳細資訊，請參閱 [銷售應用程式](http://go.microsoft.com/fwlink/p/?LinkId=262280)。  
  
 當您將原生 C++ 桌面應用程式部署至另一部電腦時，您必須安裝該應用程式本身及其相依的所有程式庫檔案。 隨應用程式一起部署 Visual C++ 執行階段的方式有三種：集中部署、本機部署或靜態連結。 如需詳細資訊，請參閱 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)。  
  
 如需有關部署 C + + /cli 程式，請參閱 [開發人員部署手冊](../Topic/.NET%20Framework%20Deployment%20Guide%20for%20Developers.md),，  
  
## <a name="other-tools"></a>其他工具  
  
## <a name="related-articles"></a>相關文章  
  
|||  
|-|-|  
|[Visual c + + 工具和 Visual Studio 版本中的範本](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)|顯示各版 Visual Studio 中的可用功能。|  
|[Visual c + + 導覽](http://msdn.microsoft.com/zh-tw/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)|提供 Visual Studio 開發環境概觀，以及您可以建立的 C++ 應用程式類型。|  
|[建立和管理 Visual c + + 專案](../ide/creating-and-managing-visual-cpp-projects.md)|提供 Visual Studio 中的 C++ 專案概觀，以及說明如何建立和管理這些專案的其他文章連結。|  
|[建置 C/c + + 程式](../build/building-c-cpp-programs.md)|說明如何建置 C++ 專案。|  
|[部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)|提供 C++ 應用程式的部署概觀，以及詳細說明部署的其他文章連結。|  
|[移植和升級程式](http://msdn.microsoft.com/zh-tw/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)|提供說明如何開啟使用舊版 Visual Studio 所建立之 C++ 應用程式，以及如何開啟使用 Visual Studio 以外工具所建立之應用程式的文章連結。|  
|||  
|[Visual C++](../top/visual-cpp-in-visual-studio-2015.md)|說明 Visual Studio 中的 Visual C++ 主要功能，以及 Visual C++ 文件其餘部分的連結。|