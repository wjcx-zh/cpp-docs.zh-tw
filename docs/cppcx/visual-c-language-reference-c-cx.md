---
title: C + +/CX 語言參考
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: f28270ace3965a3cf89e250a873af14e48390708
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507422"
---
# <a name="ccx-language-reference"></a>C + +/CX 語言參考

C + +/CX 是一組 c + + 語言的延伸模組，可讓您在盡可能接近新式 c + + 的用法中建立 Windows 應用程式和 Windows 執行階段元件。 您可以使用 c + +/CX，以原生程式碼撰寫 Windows 應用程式和元件，輕鬆地與 Visual c #、Visual Basic 和 JavaScript 互動，以及支援 Windows 執行階段的其他語言。 在需要直接存取原始 COM 介面或非例外狀況程式碼的罕見情況下，您可以使用 [Windows 執行階段 C++ 範本庫 (WRL) ](./wrl/windows-runtime-cpp-template-library-wrl.md)。

> [!NOTE]
> **/WinRT 是C++/cx 的建議替代方式。 [ C++ ](/windows/uwp/cpp-and-winrt-apis/index)** 這是新的標準 c + + 17 語言投影，適用于 Windows 執行階段 Api，從1803版開始，最新的 Windows 10 SDK 提供。 C + +/WinRT 完全在標頭檔中執行，其設計目的是要讓您能夠取得新式 Windows API 的第一級存取權。
>
> 使用 c + +/WinRT，您可以使用任何符合標準的 c + + 17 編譯器來取用及撰寫 Windows 執行階段 Api。 C + +/WinRT 的執行效能通常會比 Windows 執行階段的任何其他語言選項更好，並產生較小的二進位檔。 我們將繼續支援 C++/CX 和 WRL，但強烈建議讓新的應用程式使用 C++/WinRT。 如需詳細資訊，請參閱 [c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/index)。

您可以使用 c + +/CX 建立：

- C + + 通用 Windows 平臺 (UWP) 應用程式，這些應用程式使用 XAML 定義使用者介面及使用原生堆疊。 如需詳細資訊，請參閱 [在 c + + 中建立 "hello world" 應用程式 (UWP) ](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

- 以 JavaScript 為基礎的 Windows 應用程式可以使用的 c + + Windows 執行階段元件。 如需詳細資訊，請參閱 [在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

- Windows DirectX 遊戲與細膩圖像處理應用程式。 如需詳細資訊，請參閱 [使用 DirectX 建立簡單的 UWP 遊戲](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game)。

## <a name="related-articles"></a>相關文章

| 連結 | 描述 |
|--|--|
| [快速參考](../cppcx/quick-reference-c-cx.md) | C + +/CX。的關鍵字和運算子資料表 |
| [型別系統](../cppcx/type-system-c-cx.md) | 描述基本 c + +/CX 類型和程式設計結構，以及如何利用 c + +/CX 來取用和建立 Windows 執行階段類型。 |
| [建置應用程式和程式庫](../cppcx/building-apps-and-libraries-c-cx.md) | 討論如何使用 IDE 來建立應用程式，以及連結至靜態程式庫和 Dll。 |
| [與其他語言交互操作](../cppcx/interoperating-with-other-languages-c-cx.md) | 討論使用 c + +/CX 撰寫的元件如何與使用 JavaScript 撰寫的元件、任何 managed 語言或 Windows 執行階段 C++ 範本庫搭配使用。 |
| [執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md) | 討論如何為您建立的元件指定執行緒與封送處理行為。 |
| [命名空間參考](../cppcx/namespaces-reference-c-cx.md) | 預設命名空間、Platform 命名空間、Platform::Collections 及相關命名空間的參考文件。 |
| [通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) | 列出 Windows 執行階段應用程式中不可用的 CRT 函式。 |
| [開始使用 Windows 10 應用程式](/windows/uwp/get-started/) | 提供 Windows 10 應用程式的高階指引以及詳細資訊連結。 |
| [C + +/CX 第0部分 \[ \] ：簡介](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/CX 第1部分 \[ \] ：簡單類別](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/CX 第2部分 \[ \] ：磨損頭銜的類型](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/CX 第3部分 \[ \] ：在結構下](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/CX 第4部，共 \[ n 個 \] ：靜態成員函式](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)| C + +/CX。的簡介 blog 系列 |
