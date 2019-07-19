---
title: 在 Visual Studio 中C++建立 C/dll
ms.date: 07/18/2019
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 9f5b34fda8a429f8e55631e1e0125ed6f79d5bae
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341078"
---
# <a name="create-cc-dlls-in-visual-studio"></a>在 Visual Studio 中C++建立 C/dll

在 Windows 中, 動態連結程式庫 (DLL) 是一種可執行檔, 作為函式和資源的共用程式庫。 動態連結是一種作業系統功能, 可以讓可執行檔呼叫函式, 或使用儲存在另一個檔案中的資源。 這些函式和資源可以與使用它們的可執行檔分開編譯和部署。 DLL 不是獨立的可執行檔;它會在呼叫它的應用程式內容中執行。 作業系統可以在載入應用程式 (*隱含連結*) 時, 或視需要在執行時間 (*明確連結*) 將 DLL 載入應用程式的記憶體空間。 DLL 也讓您輕鬆地在可執行檔之間共用函式和資源。 多個應用程式可以同時存取記憶體中單一 DLL 複本的內容。

## <a name="differences-between-dynamic-linking-and-static-linking"></a>動態連結與靜態連結之間的差異

靜態連結會將靜態程式庫中的所有物件程式碼複製到在建立時使用它的可執行檔。 動態連結只包含 Windows 在執行時間所需的資訊, 以找出並載入包含資料項目或函數的 DLL。 當您建立 DLL 時, 也會建立包含此資訊的匯入程式庫。 當您建立呼叫 DLL 的可執行檔時, 連結器會使用匯入程式庫中的已匯出符號來儲存此 Windows 載入程式的資訊。 當載入器載入 DLL 時, DLL 會對應至應用程式的記憶體空間。 如果存在, 則會呼叫 dll `DllMain`中的特殊函式, 以執行 dll 所需的任何初始化。

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>應用程式和 Dll 之間的差異

雖然 Dll 和應用程式都是可執行檔模組, 但它們的差異有好幾種。 對使用者來說, 最明顯的差異在於 Dll 不是可以直接執行的應用程式。 從系統的觀點來看, 應用程式和 Dll 之間有兩個基本差異:

- 應用程式可以有多個本身的實例同時在系統中執行, 而 DLL 只能有一個實例。

- 應用程式可以載入為可擁有堆疊、執行執行緒、全域記憶體、檔案控制代碼和訊息佇列等專案的進程, 但 DLL 則不能。

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>使用 Dll 的優點

對程式碼和資源的動態連結, 與靜態連結相比, 提供了數個優點:

- 動態連結可節省記憶體並減少交換。 許多進程可以同時使用 DLL, 在記憶體中共用 DLL 唯讀部分的單一複本。 相反地, 使用靜態程式庫建立的每個應用程式都有一個完整的程式庫程式碼複本, Windows 必須載入記憶體中。

- 動態連結可節省磁碟空間和頻寬。 許多應用程式都可以在磁片上共用一個 DLL 複本。 相反地, 使用靜態程式庫建立的每個應用程式都有連結到其可執行映射的程式庫程式碼, 其使用更多的磁碟空間, 而且需要更多頻寬來傳送。

- 維護、安全性修正和升級會變得更容易。 當您的應用程式使用 DLL 中的通用函式時, 只要函式引數和傳回值沒有變更, 您就可以執行 bug 修正, 並將更新部署至 DLL。 當 Dll 更新時, 使用它們的應用程式不需要重新編譯或重新連結, 而是在部署時立即使用新的 DLL。 相反地, 您在靜態連結的物件程式碼中所做的修正, 會要求您重新連結和重新部署使用它的每個應用程式。

- 您可以使用 Dll 來提供上市後的支援。 例如, 您可以修改顯示驅動程式 DLL, 以支援在出貨時無法使用的顯示。

- 您可以在執行時間使用明確連結來探索和載入 DLL, 例如應用程式延伸模組, 可將新功能新增至您的應用程式, 而不需要重建或重新部署。

- 動態連結可讓您更輕鬆地支援以不同程式設計語言撰寫的應用程式。 只要程式遵循函式的呼叫慣例, 以不同程式設計語言撰寫的程式就可以呼叫相同的 DLL 函式。 程式和 DLL 函式必須以下列方式相容: 函式預期其引數會推送至堆疊的順序、函式或應用程式是否負責清除堆疊, 以及是否有任何引數傳入暫存器。

- 動態連結提供了擴充 MFC 程式庫類別的機制。 您可以從現有的 MFC 類別衍生類別, 並將它們放在 MFC 延伸 DLL 中, 以供 MFC 應用程式使用。

- 動態連結可讓您更輕鬆地建立應用程式的國際版本。 Dll 是提供地區設定特定資源的便利方式, 可讓您更輕鬆地建立應用程式的國際版本。 您可以將每個語言的字串和影像放在個別的資源 DLL 中, 而不是運送應用程式的許多當地語系化版本, 然後您的應用程式就可以在執行時間載入該地區設定的適當資源。

使用 Dll 的可能缺點是應用程式不是獨立的,這取決於是否存在個別的 DLL 模組, 您必須在安裝過程中自行部署或驗證。

## <a name="more-information-on-how-to-create-and-use-dlls"></a>有關如何建立和使用 Dll 的詳細資訊

下列主題提供有關如何在 Visual Studio 中建立 C/C++ dll 的詳細資訊。

[逐步解說：建立和使用動態連結程式庫 (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
描述如何使用 Visual Studio 來建立並使用 DLL。

[DLL 的種類](kinds-of-dlls.md)<br/>
提供關於各種不同可建置 DLL 的資訊。

[DLL 的常見問題](dll-frequently-asked-questions.md)<br/>
提供 DLL 常見問題的解答。

[將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md)<br/>
說明 DLL 的明確和隱含連結方式。

[初始化 DLL](run-time-library-behavior.md#initializing-a-dll)<br/>
討論當您的 DLL 載入時, 必須執行的 DLL 初始化程式碼。

[DLL 和 Visual C++ 執行階段程式庫行為](run-time-library-behavior.md)<br/>
說明執行階段程式庫如何執行 DLL 啟動程序。

[LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)<br/>
討論如何  在運行`AfxLoadLibrary`時間使用 LoadLibrary 和明確連結到 DLL。

[GetProcAddress](getprocaddress.md)<br/>
討論如何使用**GetProcAddress**取得 DLL 中匯出函式的位址。

[FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)<br/>
討論使用**FreeLibrary** , `AfxFreeLibrary`以及不再需要 DLL 模組的時機。

[動態連結程式庫搜尋順序](/windows/desktop/Dlls/dynamic-link-library-search-order)<br/>
說明 Windows 作業系統在系統上找出 DLL 時所用的搜尋路徑。

[動態連結至 MFC 之 MFC DLL 的模組狀態](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)<br/>
描述動態連結至 MFC 之一般 MFC DLL 的模組狀態。

[MFC 延伸模組 DLL](extension-dlls-overview.md)<br/>
說明實作衍生自現有 MFC 程式庫類別的重複使用類別的 DLL。

[建立僅含資源的 DLL](creating-a-resource-only-dll.md)<br/>
說明僅含資源 DLL，這種 DLL 只會包含資源，例如，圖示、點陣圖、字串和對話方塊。

[MFC 應用程式中的當地語系化資源：附屬 DLL](localized-resources-in-mfc-applications-satellite-dlls.md)<br/>
提供對附屬 DLL 的增強支援，這項功能可協助建立當地語系化成多國語言的應用程式。

[匯入和匯出](importing-and-exporting.md)<br/>
說明將公用 (Public) 符號匯入應用程式，或是從 DLL 匯出函式的方法。

[Active 技術和 DLL](active-technology-and-dlls.md)<br/>
讓物件伺服程式可以於 DLL 內實作。

[DLL 中的 Automation](automation-in-a-dll.md)<br/>
說明 MFC DLL 精靈提供的 Automation 選項。

[MFC DLL 命名慣例](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)<br/>
討論包含在 MFC 的 DLL 和程式庫如何遵守結構化的命名慣例。

[從 Visual Basic 應用程式呼叫 DLL 函式](calling-dll-functions-from-visual-basic-applications.md)<br/>
說明從 Visual Basic 應用程式呼叫 DLL 函式的方式。

## <a name="related-sections"></a>相關章節

[將 MFC 當做 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)<br/>
描述一般 MFC Dll, 可讓您使用 MFC 程式庫做為 Windows 動態連結程式庫的一部分。

[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)<br/>
描述如何搭配 MFC 應用程式和 MFC 延伸 Dll, 使用 MFCxx 和 MFCxxD (其中 x 是 MFC 版本號碼) 共用動態連結程式庫。
