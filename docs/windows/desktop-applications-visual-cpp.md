---
title: 桌面應用程式 （Visual c + +）
ms.date: 11/04/2016
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.openlocfilehash: 78f50948e96ede8c15e0ac89a591197722dd5b1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584024"
---
# <a name="desktop-applications-visual-c"></a>桌面應用程式 （Visual c + +）

A*桌面應用程式*c + + 中是可以存取 Windows Api 和系統主控台或視窗中的任一個執行一組完整的原生應用程式。 （雖然不會再正式支援的 Windows XP，而且有許多從那時起已引進的 Windows Api），可以在 Windows XP 到 Windows 10 上執行 c + + 的桌面應用程式。

桌面應用程式有所區別的通用 Windows 平台 (UWP) 應用程式，可在執行 Windows 10 電腦上以及 XBox、 Windows Phone、 Surface Hub 和其他裝置上執行。 如需桌面的 vs 的詳細資訊。UWP 應用程式，請參閱[選擇您的技術](https://msdn.microsoft.com/library/windows/desktop/dn614993)。

### <a name="desktop-bridge"></a>傳統型橋接器

在 Windows 10 中，您可以封裝您現有的桌面應用程式或為 UWP 應用程式的 COM 物件和新增 UWP 的功能，例如觸控，或從最新的 Windows API 集呼叫 Api。 您也可以新增至桌面的方案在 Visual Studio 中，並將它們在單一封裝，並使用 Windows Api 來彼此之間通訊的封裝中的 UWP 應用程式。

在 Visual Studio 2017 15.4 版和更新版本，您可以建立 Windows 應用程式封裝專案，大幅簡化封裝現有傳統型應用程式的工作。 有一些限制相對於呼叫哪些登錄或桌面應用程式的 Api 使用，但在許多情況下，您可以建立替代的程式碼路徑，以達到類似的功能，在執行中應用程式套件時。 如需詳細資訊，請參閱[傳統型橋接器](/windows-uwp/porting/desktop-to-uwp-root)。

### <a name="terminology"></a>用語

- A *Win32*應用程式是 Windows 桌面應用程式，可讓 c + + 中的使用原生[Windows C Api 及/或 COM Api](https://msdn.microsoft.com/library/windows/desktop/ff818516) CRT 和標準程式庫 Api，以及第 3 個廠商程式庫。 在視窗中執行的 Win32 應用程式會要求開發人員明確地使用 Windows 程序函式內的 Windows 訊息。 名稱，即使 Win32 應用程式可以編譯為 32 位元 (x86) 或 64 位元 (x64) 二進位。 在 Visual Studio IDE 中，Win32 與條款 x86 的意義相同。

- [元件物件模型 (COM)](/windows/desktop/com/the-component-object-model)是一種規格，可讓以與彼此進行通訊的不同語言撰寫的程式。 許多 Windows 元件會實作為 COM 物件，並遵循標準的 COM 規則，以便建立物件，探索和物件解構的介面。  使用來自 c + + 的桌面應用程式的 COM 物件方法很簡單，但更進階撰寫您自己的 COM 物件。 [Active Template Library (ATL)](../atl/atl-com-desktop-components.md)提供巨集和簡化 COM 開發的協助程式函式。

- MFC 應用程式是使用 Windows 桌面應用程式[Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md)來建立使用者介面。 COM 元件，以及 CRT 和標準程式庫 Api，也可以使用 MFC 應用程式。 MFC 提供的視窗訊息迴圈和 Windows Api 的精簡型 c + + 物件導向包裝函式。 MFC 是應用程式的預設選擇，特別是企業型應用程式 — 具有大量使用者介面控制項或自訂使用者控制項。 MFC 視窗管理、 序列化、 文字操作、 列印及現代化使用者介面項目，例如提供便利的協助程式類別。 若要有效使用 MFC 您應該熟悉 Win32。

- C + + /cli 應用程式或元件使用 c + + 語法延伸模組 （如 c + + 規格所允許的） 來啟用.NET 和原生 C + + 程式碼之間的互動。  C + + /cli 應用程式可以有原生方式執行的組件和.NET Framework 執行使用.NET 基底類別庫的組件。 C + + /cli CLI 是慣用的選項，就需要使用以 C# 或 Visual Basic 撰寫的程式碼的原生 c + + 程式碼。 它主要是用於使用.NET Dll 中，而不是在使用者介面程式碼。 如需詳細資訊，請參閱 < [.NET 程式設計使用 C + + /cli （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

C 執行階段 (CRT) 和標準程式庫的類別和函式、 COM 物件與公用 Windows 函式，統稱為 Windows API，可以使用任何 c + + 的桌面應用程式。 如需 C++ 的 Windows 傳統型應用程式簡介，請參閱 [學習以 C++ 設計 Windows 程式](http://go.microsoft.com/fwlink/p/?LinkId=262281)。

## <a name="in-this-section"></a>本節內容

|標題|描述|
|-----------|-----------------|
|[主控台應用程式](../windows/console-applications-in-visual-cpp.md)|包含主控台應用程式的相關資訊。 Win32 (或 Win64) 主控台應用程式沒有自己的視窗和訊息迴圈。 這會在主控台視窗中執行，而且輸入和輸出都是透過命令列來處理。|
|[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)|如何建立執行 windows，而不是在主控台中的傳統型應用程式。|
|[使用 DirectX （c + +） 建立遊戲的資源](../windows/resources-for-creating-a-game-using-directx.md)|C + + 中建立遊戲的內容連結。|
|[逐步解說： 建立和使用靜態程式庫](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|如何建立.lib 二進位檔案。|
|[如何：在 Windows 傳統型應用程式中使用 Windows 10 SDK](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含將您的專案設定為使用 Windows 10 SDK 建置的步驟。|

## <a name="related-articles"></a>相關文章

|標題|描述|
|-----------|-----------------|
|[Windows 程式開發](http://go.microsoft.com/fwlink/p/?LinkId=262282)|包含 Windows 應用程式開發介面和 COM 的相關資訊 (部分 Windows 應用程式開發介面和協力廠商 DLL 會實作為 COM 物件)。|
|[Hilo：開發適用於 Windows 7 的 C++ 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=262284)|說明如何建立豐富型用戶端 Windows 傳統型應用程式，這個應用程式會使用 Windows 動畫和 Direct2D 建立浮動切換式 (Carousel-based) 使用者介面。  本教學課程尚未更新 Windows 7 之後，但仍會提供 Win32 程式設計的完整介紹。|
|[Visual C++](../visual-cpp-in-visual-studio.md)|說明 Visual Studio 中的 Visual C++ 主要功能，以及 Visual C++ 文件其餘部分的連結。|

## <a name="see-also"></a>另請參閱

[Visual C++](../visual-cpp-in-visual-studio.md)