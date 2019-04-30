---
title: Visual C++ 語言參考 (C++/CX)
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: ce0272499b653b9077a891e39e9b29797e7e051d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384942"
---
# <a name="visual-c-language-reference-ccx"></a>Visual C++ 語言參考 (C++/CX)

C++/CX 是一組延伸模組的C++可建立 Windows 應用程式和 Windows 執行階段元件是盡可能接近現代的慣用語的語言C++。 使用C++撰寫 Windows 應用程式和元件以原生程式碼，輕鬆地 /CX 互動視覺效果C#，Visual Basic 和 JavaScript，以及其他支援 Windows 執行階段的語言。 在罕見情況下需要直接存取原始 COM 介面，或使用非例外狀況的程式碼，您可以使用[Windows 執行階段C++範本程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。

> [!NOTE]
> **[C++/ WinRT](/windows/uwp/cpp-and-winrt-apis/index)是建議的替代做法，以C++/CX**。 它是新的標準 C + + 17 語言推演，適用於 Windows 執行階段 Api，可在最新的 Windows 10 SDK，從 1803年版開始。 C++/ WinRT 是完全在標頭檔中實作，並設計為您提供第一級存取新式 Windows api。
>
> 使用C++/WinRT，您可以使用及撰寫 Windows 執行階段 Api 使用任何符合標準的 C + + 17 編譯器。 C++/ WinRT 通常會執行得更好，並產生較小的二進位檔，比 Windows 執行階段的其他語言選項。 我們會繼續支援C++/CX 和 WRL，但強烈建議使用新的應用程式C++/WinRT。 如需詳細資訊，請參閱 < [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index)。

使用C++//CX 中，您可以建立：

- C++通用 Windows 平台 (UWP) 應用程式使用 XAML 定義使用者介面，並使用原生堆疊。 如需詳細資訊，請參閱 <<c0> [ 建立"hello world"應用程式中的C++(UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。</c0>

- C++可供 JavaScript 型 Windows 應用程式的 Windows 執行階段元件。 如需詳細資訊，請參閱 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

- Windows DirectX 遊戲與細膩圖像處理應用程式。 如需詳細資訊，請參閱 <<c0> [ 建立簡單的 UWP 遊戲搭配 DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game)。

## <a name="related-articles"></a>相關文章

|||
|-|-|
|[快速參考](../cppcx/quick-reference-c-cx.md)|關鍵字和運算子的資料表C++/CX。|
|[類型系統](../cppcx/type-system-c-cx.md)|描述基本C++/CX 類型和程式設計建構，以及如何運用C++/CX 來使用及建立 Windows 執行階段類型。|
|[建置應用程式和程式庫](../cppcx/building-apps-and-libraries-c-cx.md)|討論如何使用 IDE 來建置應用程式，並連結至靜態程式庫和 Dll。|
|[與其他語言交互操作](../cppcx/interoperating-with-other-languages-c-cx.md)|討論如何使用所撰寫的元件C++/CX 可用以 JavaScript 撰寫的元件，任何 managed 語言或 Windows 執行階段C++範本程式庫。|
|[執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)|討論如何為您建立的元件指定執行緒與封送處理行為。|
|[命名空間參考](../cppcx/namespaces-reference-c-cx.md)|預設命名空間、Platform 命名空間、Platform::Collections 及相關命名空間的參考文件。|
|[通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|列出 Windows 執行階段應用程式中不可用的 CRT 函式。|
|[Windows 10 應用程式的操作指南](https://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|提供 Windows 10 應用程式的高階指引以及詳細資訊連結。|
|[C++/CX 第 0 部分\[n\]:簡介](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX 第 1 部分\[n\]:簡單的類別](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX 第 2 部分\[n\]:戴帽子的](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX 第 3 部分\[n\]:在建構](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX 第 4 部分\[n\]:靜態成員函式](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|簡介 VisualC++上的部落格系列C++/CX。|
