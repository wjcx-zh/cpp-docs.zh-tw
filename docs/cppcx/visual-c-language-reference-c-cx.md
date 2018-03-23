---
title: Visual c + + 語言參考 (C + + /CX) |Microsoft 文件
ms.custom: ''
ms.date: 09/15/2017
ms.technology: cpp-windows
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
caps.latest.revision: ''
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9cca27f54816c3727762eebba5a9af5246ed173
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="visual-c-language-reference-ccx"></a>Visual C++ 語言參考 (C++/CX)

C + + /CX 是一組可讓建立 Windows 應用程式，以及在盡可能現代 c + + 慣用語中的 Windows 執行階段元件的 c + + 語言擴充功能。 使用 C + + /CX 中與 Visual C#、 Visual Basic 和 JavaScript，輕鬆地互動的原生程式碼和其他語言支援 Windows 執行階段撰寫 Windows 應用程式和元件。 在少數的情況需要直接存取原始 COM 介面或使用非例外狀況的程式碼，您可以使用[Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。

> [!NOTE]
> C + + WinRT 做為新的標準 C + + 17 語言預估的 Windows 執行階段 Api。 使用最新的 Windows 10 SDK 版本 1803年開始。 C + + WinRT 是完全在標頭檔中實作及設計來提供您具有第一級的存取權的現代 Windows api。

> 使用 C + + WinRT，您可以使用及撰寫 Windows 執行階段 Api 使用任何符合標準的 C + + 17 編譯器。 C + + WinRT 通常更好，而且會產生較小的二進位檔，比為 Windows 執行階段的其他語言選項。 我們將繼續支援 C + + /CX 和 WRL，但強烈建議您，新的應用程式使用 C + + WinRT。 如需詳細資訊，請參閱[C + + WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index)。


使用 C + + /CX 中，您可以建立：

- C + + 通用 Windows 平台 (UWP) 應用程式可使用 XAML 定義使用者介面，並且使用原生堆疊。 如需詳細資訊，請參閱[建立"hello world"應用程式在 c + + (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

- 可供 JavaScript 型 Windows 應用程式的 c + + Windows 執行階段元件。 如需詳細資訊，請參閱[c + + 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。

- Windows DirectX 遊戲與細膩圖像處理應用程式。 如需詳細資訊，請參閱[使用 DirectX 建立簡單的 UWP 遊戲](/windows/uwp/gaming/tutorial--create-your-first-metro-style-directx-game)。

## <a name="related-articles"></a>相關文章

|||
|-|-|
|[快速參考](../cppcx/quick-reference-c-cx.md)|資料表的關鍵字和運算子 C + + /CX。|
|[類型系統](../cppcx/type-system-c-cx.md)|說明基本的 C + + /CX 類型與程式設計建構，以及如何使用 C + + /CX 來使用及建立 Windows 執行階段類型。|
|[建置應用程式和程式庫](../cppcx/building-apps-and-libraries-c-cx.md)|討論如何使用 IDE 建置應用程式以及連結至靜態程式庫與 DLL。|
|[與其他語言間的互通性](../cppcx/interoperating-with-other-languages-c-cx.md)|討論如何元件的寫法是使用 C + + /CX 可用以 JavaScript 撰寫的元件、 任何 managed 語言或[!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)]。|
|[執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)|討論如何為您建立的元件指定執行緒與封送處理行為。|
|[命名空間參考](../cppcx/namespaces-reference-c-cx.md)|預設命名空間、Platform 命名空間、Platform::Collections 及相關命名空間的參考文件。|
|[通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|列出 Windows 執行階段應用程式中不可用的 CRT 函式。|
|[Windows 10 應用程式的操作指南](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|提供 Windows 10 應用程式的高階指引以及詳細資訊連結。|
|[C + + /CX 第 0 部分\[n\]： 簡介](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C + + /CX 第 1 部分\[n\]： 簡單的類別](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + + /CX 第 2 部分的\[n\]： 戴帽子的類別](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + + /CX 第 3 部分\[n\]： 建構中](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C + + /CX 第 4 部分\[n\]： 靜態成員函式](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|簡介 Visual c + + 部落格系列上 C + + /CX。|
