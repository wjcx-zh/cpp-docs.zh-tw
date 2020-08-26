---
title: 通用 Windows 應用程式 (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: 45d02a5ab923ee46da97d78a1e5ceb2f4313352a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841670"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 應用程式 (C++)

通用 Windows 平臺 (UWP) 是適用于 Windows 的新式程式設計介面。 您可以使用 UWP 來撰寫應用程式或元件一次，並將它部署到任何 Windows 10 裝置上。 您可以使用 c + + 撰寫元件，並以任何其他 UWP 相容語言撰寫的應用程式都可以使用它。

大部分的 UWP 檔是在 Windows 內容樹狀結構的 [通用 Windows 平臺檔](/windows/uwp/)中。 您將在這裡找到教學課程及參考檔。

針對新的 UWP 應用程式和元件，建議您使用 [c + +/WinRT](/windows/uwp/cpp-and-winrt-apis/)，這是 Windows 執行階段 api 的新 Standard c + + 17 語言投影。 從1803版開始，Windows 10 SDK 提供 c + +/WinRT。 C + +/WinRT 完全在標頭檔中執行，其設計目的是要提供您最新的 Windows API 的第一級存取。 不同于 c + +/CX 的執行，c + +/WinRT 不會使用非標準語法或 Microsoft 語言延伸模組，並充分利用 c + + 編譯器來建立高度優化的輸出。 如需詳細資訊，請參閱 [c + +/WinRT 簡介](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

您可以使用傳統型橋接器應用程式轉換器來封裝您現有的桌面應用程式，以透過 Microsoft Store 進行部署。 如需詳細資訊，請參閱 [在 Centennial 專案中使用 Visual C++ 運行](https://devblogs.microsoft.com/cppblog/using-visual-c-runtime-in-centennial-project/) 時間和 [傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="uwp-apps-that-use-ccx"></a>使用 c + +/CX 的 UWP 應用程式

[C + +/CX 語言參考](visual-c-language-reference-c-cx.md)\
描述可簡化 c + + 取用 Windows 執行階段 Api 的擴充功能集，並啟用以例外狀況為基礎的錯誤處理。

[建立應用程式和程式庫 (c + +/CX) ](building-apps-and-libraries-c-cx.md)\
說明如何建立可以從 C++/CX 應用程式或元件存取的 DLL 和靜態程式庫。

[教學課程：在 c + +/CX 中建立 UWP "Hello，World" 應用程式](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)\
介紹如何在 c + +/CX。中進行 UWP 應用程式開發的基本概念的逐步解說

[在 c + +/CX 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)\
說明如何建立其他 UWP 應用程式和元件可以使用的 Dll。

[UWP 遊戲程式設計](/windows/uwp/gaming/)\
說明如何使用 DirectX 和 c + +/CX 來建立遊戲。

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 執行階段 C++ 範本庫 (WRL 的 UWP 應用程式) 

Windows 執行階段 C++ 範本庫提供低層級的 COM 介面，ISO c + + 程式碼可以在無例外狀況的環境中存取 Windows 執行階段。 在大部分情況下，建議您使用 c + +/WinRT 或 c + +/CX，而不是使用 UWP 應用程式開發的 Windows 執行階段 C++ 範本庫。 如需 Windows 執行階段 C++ 範本庫的詳細資訊，請參閱 [Windows 執行階段 C++ 範本庫 (WRL) ](wrl/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[C + + 中的 Windows 程式設計簡介](../windows/overview-of-windows-programming-in-cpp.md)<br/>
