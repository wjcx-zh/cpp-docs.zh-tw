---
title: 通用 Windows 應用程式 (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: landing-page
ms.openlocfilehash: 6c2bf7e44e3f1cb2c73ccaaed4363e34cbd7f0c9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218374"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 應用程式 (C++)

通用 Windows 平臺 (UWP) 是適用于 Windows 的現代化程式設計介面。 您可以使用 UWP 撰寫應用程式或元件一次, 並將它部署在任何 Windows 10 裝置上。 您可以在中C++撰寫元件, 並以任何其他 UWP 相容語言撰寫的應用程式可以使用它。

大部分 UWP 檔位於 Windows 內容樹狀結構的[通用 Windows 平臺檔](/windows/uwp/)。 您可以在這裡找到開始教學課程及參考檔。 

針對新的 UWP 應用程式和元件, 我們建議您使用[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), 這是一種新的 standard c + + 17 語言投影, 適用于 Windows 執行階段 api。 C++從1803版開始, Windows 10 SDK 中提供了/WinRT。 C++/WinRT 完全實作為標頭檔, 其設計目的是為您提供現代化 Windows API 的第一級存取權。 與C++/cx 執行不同。 C++/WinRT 不會使用非標準語法或 Microsoft 語言延伸模組, 而且它會充分利用C++編譯器來建立高度優化的輸出。 如需詳細資訊, 請參閱[ C++/WinRT 簡介](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

您可以使用傳統型橋接器應用程式轉換器來封裝現有的桌面應用程式, 以透過 Microsoft Store 進行部署。 如需詳細資訊, 請參閱在 Centennial 專案和[桌面橋接器](/windows/uwp/porting/desktop-to-uwp-root)[中C++使用 Visual Runtime](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) 。

## <a name="uwp-apps-that-use-ccx"></a>使用C++/CX 的 UWP 應用程式

|||
|-|-|
|[Visual C++ 語言參考 (C++/CX)](visual-c-language-reference-c-cx.md)|描述一組擴充功能, 可C++簡化 Windows 執行階段 api 的耗用量, 並啟用以例外狀況為基礎的錯誤處理。|
|[建置應用程式和程式庫 (C++/CX)](building-apps-and-libraries-c-cx.md)|說明如何建立可以從 C++/CX 應用程式或元件存取的 DLL 和靜態程式庫。|
|[教學課程：在/Cx 中C++建立 UWP "Hello, World" 應用程式](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|介紹/Cx。中C++UWP 應用程式開發基本概念的逐步解說 |
|[在/Cx 中C++建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何建立其他 UWP 應用程式和元件可以使用的 Dll。|
|[UWP 遊戲程式設計](/windows/uwp/gaming/)|說明如何使用 DirectX 和C++/cx 來建立遊戲。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 執行階段C++範本庫 (WRL) 的 UWP 應用程式

Windows 執行階段C++樣板程式庫提供的低層級 COM 介面, ISO C++程式碼可以在無例外狀況的環境中存取 Windows 執行階段。 在大部分情況下, 建議您使用/WinRT 或C++ C++/cx, 而不要使用 Windows 執行階段C++的範本庫來進行 UWP 應用程式開發。 如需 Windows 執行階段C++範本庫的相關資訊, 請參閱[Windows 執行階段C++範本庫 (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[使用 C++ 進行 Windows 程式設計的概觀](../windows/overview-of-windows-programming-in-cpp.md)<br/>