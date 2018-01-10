---
title: "Visual c + + 中的 Dll |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed3679d29b8d181e2cbd9896d0322fea634bfbf0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dlls-in-visual-c"></a>Visual C++ 中的 DLL  
  
在 Windows 中，動態連結程式庫 (DLL) 是一種做為函式和資源的共用程式庫的可執行檔。 動態連結是一項作業系統功能，可讓可執行檔呼叫函式，或使用儲存在個別的檔案資源。 這些函式和資源可以與使用它們的可執行檔分開編譯和部署。 DLL 不是獨立的可執行檔。它會呼叫它的應用程式的內容中執行。 作業系統可以載入 DLL 應用程式的記憶體空間在載入應用程式 (*隱含連結*)，或視需要於執行階段 (*明確連結*)。 DLL 也讓您輕鬆地在可執行檔之間共用函式和資源。 多個應用程式可以同時存取記憶體中單一 DLL 複本的內容。  
  
## <a name="differences-between-dynamic-linking-and-static-linking"></a>動態連結與靜態連結之間的差異  
  
靜態連結會複製所有目的碼的靜態程式庫到可執行檔會在建置時使用它。 動態連結只包含資訊所需的 Windows 執行階段來尋找並載入包含資料項目或函式的 DLL。 當您建立 DLL 時，您也可以建立包含這項資訊匯入程式庫。 當您建置呼叫 DLL 的可執行檔時，連結器會使用匯入程式庫中的已匯出的符號來儲存 Windows 載入器這項資訊。 當載入器載入 DLL 時，DLL 會對應到您的應用程式的記憶體空間。 如果有的話，在 DLL 中函式特殊`DllMain`，呼叫以執行 DLL 需要任何初始設定。  
  
<a name="differences-between-applications-and-dlls"></a>  
  
## <a name="differences-between-applications-and-dlls"></a>應用程式和 Dll 之間的差異  
  
雖然 Dll 和應用程式是兩個可執行檔的模組，但會在數種方式不同。 給使用者，最明顯差異是 Dll 不是可以直接執行的應用程式。 從系統的觀點來看，有兩個應用程式和 Dll 之間的基本差異：  
  
-   應用程式可以有多個執行個體的系統中執行的同時，本身，而 DLL 可以有只有一個執行個體。  
  
-   應用程式可以做為項目堆疊、 執行緒執行、 全域記憶體、 檔案控制代碼和訊息佇列，例如，可以擁有的處理序載入，但 DLL 不能。  
  
<a name="advantages-of-using-dlls"></a>  
  
## <a name="advantages-of-using-dlls"></a>使用 Dll 的優點  
  
動態連結，而不靜態連結的程式碼和資源，可提供許多優點。 當您使用 DLL 時，可以節省記憶體空間，並降少交換。 當多個應用程式可以使用單一 DLL 複本時，您可以節省磁碟空間和下載頻寬。 DLL 可分開部署和更新，這讓您提供售後支援和軟體更新而無須重新建置和提供所有程式碼。 DLL 是提供特定地區設定資源時便利的方式，它可以支援多語言程式，並簡化應用程式國際版本的建立。 明確連結可以讓您的應用程式探索和載入 Dll 在執行階段，例如提供新功能的延伸模組。  
  
動態連結具有下列優點：  
  
-   動態連結時，節省記憶體，並減少交換。 許多處理序可以使用 DLL 同時共用的唯讀狀態的部分記憶體中 DLL 單一複本。 相反地，使用靜態連結程式庫建置每個應用程式具有 Windows 必須載入記憶體的程式庫程式碼的完整複本。  
  
-   動態連結可以節省磁碟空間和頻寬。 許多應用程式可以共用的 DLL 在磁碟上的單一複本。 相反地，每一個使用靜態連結程式庫所建置的應用程式已連結至其可執行檔映像，這會使用更多磁碟空間，並採用更多的頻寬，要傳送的程式庫程式碼。  
  
-   維護安全性修正，升級會更加容易。 當您的應用程式的 DLL 中使用一般函數時，然後只要函式引數和傳回值不會變更，您可以實作錯誤修正及將更新部署至 DLL。 當 Dll 更新時，使用它們的應用程式不需要重新編譯或重新連結，和他們進行部署時，立即使用新的 DLL。 相反地，修正您在靜態連結的物件程式碼需要您重新連結，並重新部署它會使用每個應用程式。  
  
-   您可以提供售後支援使用 Dll。 例如，可以修改顯示驅動程式 DLL 支援應用程式推出時無法使用的顯示。 您可以使用明確連結載入為 Dll，應用程式擴充功能，並加入您的應用程式的新功能，而不需重建或重新部署它。  
  
-   動態連結可讓您更輕鬆地支援以不同的程式設計語言撰寫的應用程式。 以不同的程式設計語言撰寫的程式可以呼叫相同的 DLL 函式，只要程式遵循函式的呼叫慣例。 程式和 DLL 函式必須以下列方式相容： 中的函式預期的引數推送至堆疊、 函式或應用程式是負責清除堆疊，以及是否有任何引數的順序暫存器中傳遞。  
  
-   動態連結提供擴充 MFC 程式庫類別機制。 您可以從現有的 MFC 類別衍生類別，並將它們放在使用 MFC 擴充 DLL 中的 MFC 應用程式。  
  
-   動態連結簡化國際版本的應用程式的建立。 藉由將地區設定專屬的資源放在 DLL 中，很容易建立國際版本的應用程式。 而不是傳送應用程式的許多當地語系化的版本，您可以將字串和每一種語言的映像放在不同的資源 DLL，，然後您的應用程式可以載入的執行階段地區設定適當的資源。   
  
 使用 Dll 的潛在缺點是應用程式不是各自獨立。這取決於個別的 DLL 模組，您必須部署，或您自己驗證為您安裝的一部分存在。  
  
  
## <a name="more-information-on-how-to-create-and-use-dlls"></a>如何建立和使用 Dll 的詳細資訊  
  
下列主題提供有關的詳細的資訊，Visual c + + 程式 dll。  
  
 [逐步解說：建立和使用動態連結程式庫 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
 描述如何使用 Visual Studio 來建立並使用 DLL。  
  
 [DLL 的種類](../build/kinds-of-dlls.md)  
 提供關於各種不同可建置 DLL 的資訊。  
  
 [DLL 常見問題集](../build/dll-frequently-asked-questions.md)  
 提供 DLL 常見問題的解答。  
  
 [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)  
 說明 DLL 的明確和隱含連結方式。  
  
 [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
 討論的初始化程式碼必須載入 DLL 時執行。  
  
 [DLL 和 Visual C++ 執行階段程式庫行為](../build/run-time-library-behavior.md)  
 說明執行階段程式庫如何執行 DLL 啟動程序。  
  
 [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
 討論如何使用**LoadLibrary**和`AfxLoadLibrary`明確地連結到在執行階段 DLL。  
  
 [GetProcAddress](../build/getprocaddress.md)  
 討論如何使用**GetProcAddress**取得 DLL 中匯出函式的位址。  
  
 [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
 討論如何使用**FreeLibrary**和`AfxFreeLibrary`不再需要 DLL 模組時。  
  
 [Windows 用來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
 說明 Windows 作業系統在系統上找出 DLL 時所用的搜尋路徑。  
  
 [動態連結至 MFC 之 MFC DLL 的模組狀態](../build/module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)  
 描述的一般 MFC DLL 動態連結至 MFC 的模組狀態。  
  
 [MFC 延伸模組 DLL](../build/extension-dlls-overview.md)  
 說明實作衍生自現有 MFC 程式庫類別的重複使用類別的 DLL。  
  
 [建立僅含資源的 DLL](../build/creating-a-resource-only-dll.md)  
 說明僅含資源 DLL，這種 DLL 只會包含資源，例如，圖示、點陣圖、字串和對話方塊。  
  
 [MFC 應用程式中的當地語系化資源：附屬 DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)  
 提供對附屬 DLL 的增強支援，這項功能可協助建立當地語系化成多國語言的應用程式。  
  
 [匯入和匯出](../build/importing-and-exporting.md)  
 說明將公用 (Public) 符號匯入應用程式，或是從 DLL 匯出函式的方法。  
  
 [Active 技術和 DLL](../build/active-technology-and-dlls.md)  
 讓物件伺服程式可以於 DLL 內實作。  
  
 [DLL 中的 Automation](../build/automation-in-a-dll.md)  
 說明 MFC DLL 精靈提供的 Automation 選項。  
  
 [MFC DLL 命名慣例](../build/naming-conventions-for-mfc-dlls.md)  
 討論包含在 MFC 的 DLL 和程式庫如何遵守結構化的命名慣例。  
  
 [從 Visual Basic 應用程式呼叫 DLL 函式](../build/calling-dll-functions-from-visual-basic-applications.md)  
 說明從 Visual Basic 應用程式呼叫 DLL 函式的方式。  
  
## <a name="related-sections"></a>相關章節  
  
 [將 MFC 當成 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)  
 說明標準的 MFC Dll，可讓您使用 MFC 程式庫當成 Windows 動態連結程式庫。  
  
 [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
 說明如何使用 MFCxx.dll 和 mfcxxd.dll （其中 x 是 MFC 版本號碼） 指共用 MFC 應用程式與 MFC 擴充 Dll 的動態連結程式庫。  
