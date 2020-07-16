---
title: C + +/CX 語言參考
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: 4f3816280630a6a061eb037a33367ef4e9d90375
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403851"
---
# <a name="ccx-language-reference"></a>C + +/CX 語言參考

C + +/CX 是 c + + 語言的一組延伸模組，可讓您在盡可能接近現代 c + + 的用法中建立 Windows 應用程式和 Windows 執行階段元件。 使用 c + +/CX 以機器碼撰寫 Windows 應用程式和元件，輕鬆地與 Visual c #、Visual Basic 和 JavaScript 互動，以及其他支援 Windows 執行階段的語言。 在需要直接存取原始 COM 介面或非例外狀況程式碼的罕見情況下，您可以使用[Windows 執行階段 c + + Template Library （WRL）](../windows/windows-runtime-cpp-template-library-wrl.md)。

> [!NOTE]
> **/WinRT 是C++/cx 的建議替代方式。 [ C++ ](/windows/uwp/cpp-and-winrt-apis/index)** 這是新的 standard c + + 17 語言投影，適用于從1803版起的最新 Windows 10 SDK 中提供的 Windows 執行階段 Api。 C + +/WinRT 完全實作為標頭檔，並設計來提供您對新式 Windows API 的第一級存取。
>
> 使用 c + +/WinRT，您可以使用任何符合標準的 c + + 17 編譯器來取用和撰寫 Windows 執行階段 Api。 C + +/WinRT 的執行效能通常較佳，而且會產生比 Windows 執行階段的任何其他語言選項更小的二進位檔。 我們將繼續支援 C++/CX 和 WRL，但強烈建議讓新的應用程式使用 C++/WinRT。 如需詳細資訊，請參閱[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/index)。

藉由使用 c + +/CX，您可以建立：

- 使用 XAML 定義使用者介面及使用原生堆疊的 c + + 通用 Windows 平臺（UWP）應用程式。 如需詳細資訊，請參閱[在 c + + 中建立 "hello world" 應用程式（UWP）](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

- 以 JavaScript 為基礎的 Windows 應用程式可使用的 c + + Windows 執行階段元件。 如需詳細資訊，請參閱 [在 C++ 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

- Windows DirectX 遊戲與細膩圖像處理應用程式。 如需詳細資訊，請參閱[使用 DirectX 建立簡單的 UWP 遊戲](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game)。

## <a name="related-articles"></a>相關文章

| 連結 | 描述 |
|--|--|
| [快速參考](../cppcx/quick-reference-c-cx.md) | C + +/CX。關鍵字和運算子的表格 |
| [型別系統](../cppcx/type-system-c-cx.md) | 描述基本 c + +/CX 類型和程式設計結構，以及如何利用 c + +/CX 來取用和建立 Windows 執行階段類型。 |
| [建置應用程式和程式庫](../cppcx/building-apps-and-libraries-c-cx.md) | 討論如何使用 IDE 來建立應用程式，以及連結至靜態程式庫和 Dll。 |
| [與其他語言交互操作](../cppcx/interoperating-with-other-languages-c-cx.md) | 討論使用 c + +/CX 撰寫的元件如何與以 JavaScript、任何 managed 語言或 Windows 執行階段 c + + 範本庫撰寫的元件搭配使用。 |
| [執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md) | 討論如何為您建立的元件指定執行緒與封送處理行為。 |
| [命名空間參考](../cppcx/namespaces-reference-c-cx.md) | 預設命名空間、Platform 命名空間、Platform::Collections 及相關命名空間的參考文件。 |
| [通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) | 列出 Windows 執行階段應用程式中不可用的 CRT 函式。 |
| [開始使用 Windows 10 應用程式](/windows/uwp/get-started/) | 提供 Windows 10 應用程式的高階指引以及詳細資訊連結。 |
| [C + +/CX 第0部分 \[ n \] ：簡介](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/CX 第1部分，共 \[ n 個 \] ：簡單類別](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/CX 第二部分，共 \[ n 個 \] ：磨損的類型](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/CX 第3部，共 \[ n 個 \] ：建築之下](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/CX 第4部分，共 \[ n 個 \] ：靜態成員函式](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)| C + +/CX。簡介的 blog 系列 |
