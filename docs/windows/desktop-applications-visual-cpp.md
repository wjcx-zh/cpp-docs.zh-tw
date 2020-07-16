---
title: 傳統型應用程式 (Visual C++)
ms.date: 07/28/2019
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.topic: overview
ms.openlocfilehash: f8e3dd386aee835ff383ba7567a5c320f206476e
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404957"
---
# <a name="desktop-applications-visual-c"></a>傳統型應用程式 (Visual C++)

C + + 中的*桌面應用程式*是原生應用程式，可以存取一組完整的 Windows api，並在視窗或系統主控台中執行。 C + + 中的桌面應用程式可以透過 Windows 10 在 Windows XP 上執行（雖然 Windows XP 已不再正式支援，而且有許多自之後引進的 Windows Api）。

桌面應用程式與通用 Windows 平臺（UWP）應用程式不同，它可以在執行 Windows 10 的電腦上，也可在 XBox、Windows Phone、Surface Hub 和其他裝置上執行。 如需有關桌面與 UWP 應用程式的詳細資訊，請參閱[選擇您的技術](/windows/win32/choose-your-technology)。

## <a name="desktop-bridge"></a>傳統型橋接器

在 Windows 10 中，您可以將現有的桌面應用程式或 COM 物件封裝為 UWP 應用程式，並新增 UWP 功能（例如觸控），或從新式 Windows API 集合呼叫 Api。 您也可以在 Visual Studio 中將 UWP 應用程式新增至桌面解決方案，並將其封裝在單一套件中，然後使用 Windows Api 在兩者之間進行通訊。

在 Visual Studio 2017 15.4 版和更新版本中，您可以建立 Windows 應用程式套件專案，以大幅簡化封裝現有桌面應用程式的工作。 有一些限制適用于您的桌面應用程式所使用的登錄呼叫或 Api，但在許多情況下，您可以建立替代的程式碼路徑，以在應用程式套件中執行時達到類似的功能。 如需詳細資訊，請參閱[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="terminology"></a>詞彙

- *Win32*應用程式是 c + + 中的 Windows 桌面應用程式，可利用原生的[Windows C api 和/或 COM Api](/windows/win32/apiindex/windows-api-list) CRT 和標準程式庫 api，以及協力廠商程式庫。 在視窗中執行的 Win32 應用程式需要開發人員在 Windows 程式函式內明確地處理 Windows 訊息。 無論名稱是什麼，Win32 應用程式都可以編譯為32位（x86）或64位（x64）二進位檔。 在 Visual Studio IDE 中，x86 和 Win32 這兩者都是同義。

- [元件物件模型（COM）](/windows/win32/com/the-component-object-model)是一種規格，可讓以不同語言撰寫的程式彼此通訊。 許多 Windows 元件會實作為 COM 物件，並遵循標準 COM 規則來建立物件、介面探索和物件銷毀。  從 c + + 桌面應用程式使用 COM 物件相當簡單，但撰寫自己的 COM 物件更為先進。 [Active Template Library （ATL）](../atl/atl-com-desktop-components.md)提供宏和 helper 函式，可簡化 COM 開發工作。

- MFC 應用程式是一種 Windows 桌面應用程式，它會使用[Microsoft Foundation 類別](../mfc/mfc-desktop-applications.md)來建立使用者介面。 MFC 應用程式也可以使用 COM 元件以及 CRT 和標準程式庫 Api。 MFC 透過視窗訊息迴圈和 Windows Api 提供瘦 c + + 物件導向包裝函式。 MFC 是具有大量使用者介面控制項或自訂使用者控制項的應用程式（尤其是企業類型應用程式）的預設選擇。 MFC 提供便利的 helper 類別來進行視窗管理、序列化、文字操作、列印和新式使用者介面專案（例如功能區）。 若要有效使用 MFC，您應該熟悉 Win32。

- C + +/CLI 應用程式或元件會使用 c + + 語法的延伸模組（如 c + + 標準所允許）來啟用 .NET 和原生 C + + 程式碼之間的互動。  C + +/CLI 應用程式可以具有原生執行的元件，以及在 .NET Framework 上執行且可存取 .NET 基類庫的元件。 當您有原生 c + + 程式碼需要使用以 c # 或 Visual Basic 撰寫的程式碼時，c + +/CLI 是慣用的選項。 它適用于 .NET Dll，而不是在使用者介面程式碼中使用。 如需詳細資訊，請參閱[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

C + + 中的任何桌面應用程式都可以使用 C 執行時間（CRT）和標準程式庫類別和函式、COM 物件和公用 Windows 函式，統稱為 Windows API。 如需 c + + 中的 Windows 桌面應用程式簡介，請參閱[開始使用 Win32 和 c + +](/windows/win32/LearnWin32/learn-to-program-for-windows)。

## <a name="in-this-section"></a>本節內容

|Title|描述|
|-----------|-----------------|
|[以 C++ 撰寫的 Windows 傳統型應用程式](console-applications-in-visual-cpp.md)|包含主控台應用程式的相關資訊。 Win32 (或 Win64) 主控台應用程式沒有自己的視窗和訊息迴圈。 這會在主控台視窗中執行，而且輸入和輸出都是透過命令列來處理。|
|[逐步解說：建立 Windows 傳統型應用程式 (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|建立簡單的 Windows 桌面應用程式。|
|[建立空的 Windows 傳統型應用程式](creating-an-empty-windows-desktop-application.md)|如何建立沒有預設檔案的 Windows 桌面專案。|
|[將檔案加入空的 Win32 應用程式](adding-files-to-an-empty-win32-applications.md)|如何將檔案新增至空白專案。|
|[使用資源檔](working-with-resource-files.md)|如何將影像、圖示、字串資料表和其他資源新增至桌面應用程式。|
|[用於使用 DirectX 建立遊戲的資源 (C++)](resources-for-creating-a-game-using-directx.md)|以 c + + 建立遊戲之內容的連結。|
|[逐步解說：建立和使用靜態程式庫](walkthrough-creating-and-using-a-static-library-cpp.md)|如何建立 .lib 二進位檔案。|
|[如何：在 Windows 桌面應用程式中使用 Windows 10 SDK](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含將您的專案設定為使用 Windows 10 SDK 建置的步驟。|

## <a name="related-articles"></a>相關文章

|Title|描述|
|-----------|-----------------|
|[Windows 程式開發](/windows/win32/index)|包含 Windows 應用程式開發介面和 COM 的相關資訊 (部分 Windows 應用程式開發介面和協力廠商 DLL 會實作為 COM 物件)。|
|[Hilo：開發適用於 Windows 7 的 C++ 應用程式](/previous-versions/msdn10/ff708696(v=msdn.10))|說明如何建立豐富型用戶端 Windows 傳統型應用程式，這個應用程式會使用 Windows 動畫和 Direct2D 建立浮動切換式 (Carousel-based) 使用者介面。  本教學課程在 Windows 7 之後尚未更新，但仍然提供 Win32 程式設計的完整介紹。|
|[C + + 的 Windows 程式設計總覽](overview-of-windows-programming-in-cpp.md)|說明 c + + 中 Windows 桌面程式設計的主要功能。|

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)
