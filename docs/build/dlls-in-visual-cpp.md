---
title: 在 Visual Studio 中建立 C/c + + Dll
ms.date: 12/10/2018
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 5bd30c84ba202c3f772ad4451368efde10285e6c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815810"
---
# <a name="create-cc-dlls-in-visual-studio"></a>在 Visual Studio 中建立 C/c + + Dll

在 Windows，動態連結程式庫 (DLL) 會是一種可做為函式和資源的共用程式庫的可執行檔。 動態連結是一項作業系統功能，可讓可執行檔呼叫函式，或使用儲存在個別的檔案中的資源。 這些函式和資源可以與使用它們的可執行檔分開編譯和部署。 DLL 不是獨立的可執行檔;它會呼叫它的應用程式內容中執行。 作業系統可以將 DLL 載入應用程式的記憶體空間在載入應用程式 (*隱含連結*)，或視需要在執行階段 (*明確連結*)。 DLL 也讓您輕鬆地在可執行檔之間共用函式和資源。 多個應用程式可以同時存取記憶體中單一 DLL 複本的內容。

## <a name="differences-between-dynamic-linking-and-static-linking"></a>動態連結與靜態連結之間的差異

靜態連結，會同時在靜態程式庫中所有的物件程式碼複製到會在建置時使用它的可執行檔中。 動態連結包含只將 Windows 執行階段，以找出並載入包含資料項目或函式的 DLL 所需的資訊。 當您建立 DLL 時，您也可以建立包含這項資訊匯入程式庫。 當您建置呼叫 DLL 的可執行檔時，則連結器會使用匯入程式庫中的已匯出的符號來儲存此資訊，Windows 載入器。 當載入器載入 DLL 時，DLL 會對應到您的應用程式的記憶體空間中。 如果有的話，DLL 中函式的特殊`DllMain`，呼叫以執行 DLL 需要任何初始設定。

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>應用程式和 Dll 之間的差異

即使 Dll 和應用程式都是這兩個可執行檔的模組，但會在數種方式不同。 給使用者，最明顯的差異是 Dll 不是可以直接執行的應用程式。 從系統觀點來看，有兩個應用程式和 Dll 之間的基本差異：

- 應用程式可以有多個執行個體的系統中執行的同時，本身，而 DLL 只能有一個執行個體。

- 應用程式可以載入做為處理序可以擁有一個堆疊、 執行、 全域記憶體、 檔案控制代碼和訊息佇列的執行緒等項目，但 DLL 不能。

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>使用 Dll 的優點

動態連結，而不靜態連結至程式碼和資源，可提供許多優點。 當您使用 DLL 時，可以節省記憶體空間，並降少交換。 當多個應用程式可以使用單一 DLL 複本時，您可以節省磁碟空間和下載頻寬。 DLL 可分開部署和更新，這讓您提供售後支援和軟體更新而無須重新建置和提供所有程式碼。 DLL 是提供特定地區設定資源時便利的方式，它可以支援多語言程式，並簡化應用程式國際版本的建立。 明確連結，可以讓您的應用程式，來探索及載入的 Dll 在執行階段，例如提供新功能的延伸模組。

動態連結具有下列優點：

- 動態連結時，節省記憶體，並減少交換。 許多程序可以使用 DLL，同時共用一份在記憶體中 DLL 的唯讀部分。 相反地，使用靜態連結程式庫建置的每個應用程式具有 Windows 必須載入記憶體的程式庫程式碼的完整複本。

- 動態連結可節省磁碟空間和頻寬。 許多應用程式可以共用磁碟上的 DLL 單一的複本。 相反地，使用靜態連結程式庫所建置的每個應用程式已連結至其可執行檔映像，其使用更多磁碟空間，並採用更多的頻寬，將程式庫程式碼。

- 維護安全性問題修正，並可以更輕鬆地升級。 當您的應用程式會使用常見的函式在 DLL 中時，然後只要函式引數和傳回值不會變更，您可以實作錯誤修正並部署更新 dll。 更新 Dll 時, 使用它們的應用程式不需要重新編譯或重新連結，和他們進行部署時，立即使用新的 DLL。 相較之下，您在靜態連結的物件程式碼中進行的修正程式會要求您重新連結並重新部署會使用它的每個應用程式。

- 您可以提供售後支援使用 Dll。 比方說，可以修改顯示驅動程式 DLL，以支援應用程式推出時無法使用的顯示。 您可以使用 載入應用程式延伸模組 Dll，為 明確連結，並加入您的應用程式中的新功能，而不需要重建或重新部署它。

- 動態連結可讓您更輕鬆地支援以不同的程式設計語言撰寫的應用程式。 以不同的程式設計語言撰寫的程式可以呼叫相同的 DLL 函式，只要程式遵循函式的呼叫慣例。 程式和 DLL 函式必須以下列方式相容： 函式預期的引數推送至堆疊，函式或應用程式是否負責清除堆疊，以及是否有任何引數的順序暫存器中傳遞。

- 動態連結提供擴充 MFC 程式庫類別機制。 您可以從現有的 MFC 類別衍生的類別，並將它們放在使用 MFC 擴充 DLL 中，MFC 應用程式。

- 動態連結更輕鬆建立應用程式的國際版本。 將地區設定特有的資源放在 DLL 中，很容易建立國際版本的應用程式。 而不是傳送應用程式的許多當地語系化的版本，您可以將字串和每種語言的映像放在不同的資源 DLL，然後您的應用程式可以載入適當的資源，在執行階段該地區設定。

使用 Dll 的潛在缺點是應用程式不是自封式;這取決於個別的 DLL 模組，您必須部署，或您自己驗證為您安裝的一部分存在。

## <a name="more-information-on-how-to-create-and-use-dlls"></a>如何建立和使用 Dll 的詳細資訊

下列主題提供有關的詳細的資訊，Visual c + + dll 的程式設計。

[逐步解說：建立和使用動態連結程式庫 (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
描述如何使用 Visual Studio 來建立並使用 DLL。

[DLL 的種類](kinds-of-dlls.md)<br/>
提供關於各種不同可建置 DLL 的資訊。

[DLL 常見問題集](dll-frequently-asked-questions.md)<br/>
提供 DLL 常見問題的解答。

[將可執行檔連結至 DLL](linking-an-executable-to-a-dll.md)<br/>
說明 DLL 的明確和隱含連結方式。

[初始化 DLL](run-time-library-behavior.md#initializing-a-dll)<br/>
討論您的 DLL 載入時必須執行的 DLL 初始化程式碼。

[DLL 和 Visual C++ 執行階段程式庫行為](run-time-library-behavior.md)<br/>
說明執行階段程式庫如何執行 DLL 啟動程序。

[LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)<br/>
討論如何使用**LoadLibrary**和`AfxLoadLibrary`明確地連結至 DLL，以在執行階段。

[GetProcAddress](getprocaddress.md)<br/>
討論如何使用**GetProcAddress**取得 DLL 中匯出的函式的位址。

[FreeLibrary 和 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)<br/>
討論如何使用**FreeLibrary**和`AfxFreeLibrary`不再需要 DLL 模組時。

[動態連結程式庫搜尋順序](/windows/desktop/Dlls/dynamic-link-library-search-order)<br/>
說明 Windows 作業系統在系統上找出 DLL 時所用的搜尋路徑。

[動態連結至 MFC 之 MFC DLL 的模組狀態](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)<br/>
描述的一般 MFC DLL 動態連結至 MFC 的模組狀態。

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

[將 MFC 當成 DLL 的一部分使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)<br/>
說明標準 MFC Dll，可讓您使用 MFC 程式庫當成 Windows 動態連結程式庫。

[MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)<br/>
描述如何使用 MFCxx.dll 和 MFCxxD.dll （其中 x 是 MFC 版本號碼） 共用動態連結程式庫與 MFC 應用程式和 MFC 擴充 Dll。
