---
title: "Visual C++ 中的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "DLL [C++]"
  - "DLL [C++], 關於 DLL"
  - "動態連結 [C++]"
  - "可執行檔 [C++]"
  - "連結 [C++], 動態和靜態的比較"
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Visual C++ 中的 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

動態連結程式庫 \(DLL\) 是做為函式和資源之共用程式庫的可執行檔。  動態連結可讓可執行檔呼叫函式，或使用儲存在另一個檔案中的資源。  這些函式和資源可以與使用它們的可執行檔分開編譯和部署。  作業系統可以在載入可執行檔時將 DLL 載入到可執行檔的記憶體空間，或視需要在執行階段載入 DLL。  DLL 也讓您輕鬆地在可執行檔之間共用函式和資源。  多個應用程式可以同時存取記憶體中單一 DLL 複本的內容。  
  
 靜態連結會將 .lib 檔案中的所有目的碼複製成可執行檔。  動態連結只包含在執行階段找出並載入包含資料項目或函式的 DLL 所需的資訊。  當您建立 DLL 時，您也會建立包含這項資訊的 .lib 檔。  當您建置呼叫 DLL 的可執行檔時，連結器會使用 .lib 檔中的已匯出符號來儲存載入器的此項資訊。  當載入器載入 DLL 時，DLL 會對應到可執行檔的記憶體空間。  DLL 中的特殊函式 `DllMain` 會呼叫來執行 DLL 需要的任何初始化。  
  
 不使用靜態連結而改用動態連結可提供許多優點。  當您使用 DLL 時，可以節省記憶體空間，並降少交換。  當多個應用程式可以使用單一 DLL 複本時，您可以節省磁碟空間和下載頻寬。  DLL 可分開部署和更新，這讓您提供售後支援和軟體更新而無須重新建置和提供所有程式碼。  DLL 是提供特定地區設定資源時便利的方式，它可以支援多語言程式，並簡化應用程式國際版本的建立。  
  
 下列主題會提供 DLL 程式設計的詳細資訊。  
  
## 本章節內容  
 [逐步解說：建立和使用動態連結程式庫 \(C\+\+\)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
 描述如何使用 Visual Studio 來建立並使用 DLL。  
  
 [應用程式和 DLL 之間的差異](../build/differences-between-applications-and-dlls.md)  
 說明應用程式和 DLL 之間的基本差異。  
  
 [使用 DLL 的優點](../build/advantages-of-using-dlls.md)  
 說明動態連結的優點。  
  
 [DLL 的種類](../build/kinds-of-dlls.md)  
 提供關於各種不同可建置 DLL 的資訊。  
  
 [DLL 常見問題集](../build/dll-frequently-asked-questions.md)  
 提供 DLL 常見問題的解答。  
  
 [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)  
 說明 DLL 的明確和隱含連結方式。  
  
 [初始化 DLL](../build/initializing-a-dll.md)  
 討論必須在載入 DLL 時執行的初始化程式碼 \(例如，配置記憶體\)。  
  
 [執行階段程式庫行為](../build/run-time-library-behavior.md)  
 說明執行階段程式庫如何執行 DLL 啟動程序。  
  
 [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
 討論使用 **LoadLibrary** 和 `AfxLoadLibrary` 在執行階段明確地連結到 DLL 的方式。  
  
 [GetProcAddress](../build/getprocaddress.md)  
 討論使用 **GetProcAddress** 取得 DLL 中匯出函式 \(Exported Function\) 的位址。  
  
 [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
 討論在不再需要 DLL 模組時使用 **FreeLibrary** 和 `AfxFreeLibrary` 的方式。  
  
 [Windows 用來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
 說明 Windows 作業系統在系統上找出 DLL 時所用的搜尋路徑。  
  
 [動態連結至 MFC 之標準 DLL 的模組狀態](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
 說明動態連結至 MFC 的標準 DLL 之模組狀態。  
  
 [擴充 DLL](../build/extension-dlls-overview.md)  
 說明實作衍生自現有 MFC 程式庫類別的重複使用類別的 DLL。  
  
 [建立僅含資源的 DLL](../build/creating-a-resource-only-dll.md)  
 說明僅含資源 DLL，這種 DLL 只會包含資源，例如，圖示、點陣圖、字串和對話方塊。  
  
 [MFC 應用程式中的當地語系化資源：附屬 DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)  
 提供對附屬 DLL 的增強支援，這項功能可協助建立當地語系化成多國語言的應用程式。  
  
 [匯入和匯出](../build/importing-and-exporting.md)  
 說明將公用 \(Public\) 符號匯入應用程式，或是從 DLL 匯出函式的方法。  
  
 [Active 技術和 DLL](../build/active-technology-and-dlls.md)  
 讓物件伺服程式可以於 DLL 內實作。  
  
 [DLL 中的 Automation](../build/automation-in-a-dll.md)  
 說明 MFC DLL 精靈提供的 Automation 選項。  
  
 [MFC DLL 命名慣例](../build/naming-conventions-for-mfc-dlls.md)  
 討論包含在 MFC 的 DLL 和程式庫如何遵守結構化的命名慣例。  
  
 [從 Visual Basic 應用程式呼叫 DLL 函式](../build/calling-dll-functions-from-visual-basic-applications.md)  
 說明從 Visual Basic 應用程式呼叫 DLL 函式的方式。  
  
## 相關章節  
 [將 MFC 當成 DLL 的一部分來使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
 說明標準 DLL，可以讓您將 MFC 程式庫當成 Windows 動態連結程式庫來使用。  
  
 [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
 說明如何以 MFC 應用程式和擴充 DLL 使用 MFCxx.dll 和 MFCxxD.dll \(其中 x 是指 MFC 版本號碼\) 共用的動態連結程式庫。  
  
 [\(NOTINBUILD\)Visual C\+\+ Programming Methodologies](http://msdn.microsoft.com/zh-tw/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 提供主題連結，這些主題將描述 Visual C\+\+ 程式庫的概念性資訊，以及討論各種程式碼撰寫技術和技巧。