---
title: 通用 Windows 應用程式 (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: 25b89d2d9cb99e05145e60f9c9b1a6324fbbeb39
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404596"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 應用程式 (C++)

通用 Windows 平臺（UWP）是適用于 Windows 的現代化程式設計介面。 您可以使用 UWP 撰寫應用程式或元件一次，並將它部署在任何 Windows 10 裝置上。 您可以使用 c + + 撰寫元件，而以任何其他 UWP 相容語言撰寫的應用程式則可以使用它。

大部分 UWP 檔位於 Windows 內容樹狀結構的[通用 Windows 平臺檔](/windows/uwp/)。 您可以在這裡找到開始教學課程及參考檔。

針對新的 UWP 應用程式和元件，建議您使用[c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/)，這是適用于 Windows 執行階段 api 的新 Standard c + + 17 語言投影。 從1803版開始，Windows 10 SDK 中提供 c + +/WinRT。 C + +/WinRT 完全實作為標頭檔，其設計目的是為您提供現代化 Windows API 的第一級存取。 不同于 c + +/CX 執行，c + +/WinRT 不會使用非標準語法或 Microsoft 語言延伸模組，而且它會充分利用 c + + 編譯器來建立高度優化的輸出。 如需詳細資訊，請參閱[c + + 簡介/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

您可以使用傳統型橋接器應用程式轉換器來封裝現有的桌面應用程式，以透過 Microsoft Store 進行部署。 如需詳細資訊，請參閱在 Centennial 專案和[桌面橋接器](/windows/uwp/porting/desktop-to-uwp-root)[中使用 Visual C++ 運行](https://devblogs.microsoft.com/cppblog/using-visual-c-runtime-in-centennial-project/)時間。

## <a name="uwp-apps-that-use-ccx"></a>使用 c + +/CX 的 UWP 應用程式

|||
|-|-|
|[C++/CX 語言參考](visual-c-language-reference-c-cx.md)|描述一組擴充功能，可簡化 Windows 執行階段 Api 的 c + + 耗用量，並啟用以例外狀況為基礎的錯誤處理。|
|[建立應用程式和程式庫（c + +/CX）](building-apps-and-libraries-c-cx.md)|說明如何建立可以從 C++/CX 應用程式或元件存取的 DLL 和靜態程式庫。|
|[教學課程：在 c + +/CX 中建立 UWP "Hello，World" 應用程式](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|介紹在 c + +/CX。中 UWP 應用程式開發基本概念的逐步解說 |
|[在 c + +/CX 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何建立其他 UWP 應用程式和元件可以使用的 Dll。|
|[UWP 遊戲程式設計](/windows/uwp/gaming/)|說明如何使用 DirectX 和 c + +/CX 來建立遊戲。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 執行階段 c + + 範本庫（WRL）的 UWP 應用程式

Windows 執行階段 c + + 範本程式庫提供低層級 COM 介面，ISO c + + 程式碼可以透過這些介面，在無例外狀況的環境中存取 Windows 執行階段。 在大部分情況下，建議您使用 c + +/WinRT 或 c + +/CX，而不要使用適用于 UWP 應用程式開發的 Windows 執行階段 c + + 範本庫。 如需 Windows 執行階段 c + + 範本程式庫的相關資訊，請參閱[Windows 執行階段 c + + 範本庫（WRL）](wrl/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[C + + 的 Windows 程式設計總覽](../windows/overview-of-windows-programming-in-cpp.md)<br/>
