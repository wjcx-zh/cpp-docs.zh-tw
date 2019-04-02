---
title: 通用 Windows 應用程式 (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.openlocfilehash: fbd5366ee52dfe32baef9458a82c16914666699e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58783999"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 應用程式 (C++)

通用 Windows 平台 (UWP) 是 Windows 的現代程式設計介面。 使用 UWP 撰寫的應用程式或元件一次，並將它部署在任何 Windows 10 裝置。 您可以在 c + + 撰寫的元件，並以任何其他的 UWP 相容語言撰寫的應用程式可以使用它。

大部分的 UWP 文件是在 Windows 內容在樹狀目錄[通用 Windows 平台的文件](/windows/uwp/)。 您會在這裡找到開始教學課程也做為參考文件。 

新的 UWP 應用程式和元件，我們建議您使用[C + + /cli WinRT](/windows/uwp/cpp-and-winrt-apis/)，新標準 C + + 17 語言推演，適用於 Windows 執行階段 Api。 C + + /cli WinRT 位於 Windows 10 SDK 從 1803年版開始。 C + + /cli WinRT 完全在標頭檔中實作，旨在提供您的第一級存取新式 Windows api。 不同於 C + + /CX 實作。 C + + /cli WinRT 不會使用非標準的語法或 Microsoft 語言擴充功能，以及它利用完整的 c + + 編譯器建立高度最佳化的輸出。 如需詳細資訊，請參閱 <<c0> [ 介紹 C + + /cli WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

您可以使用傳統型橋接器應用程式轉換器封裝您現有的桌面應用程式透過 Microsoft Store 部署。 如需詳細資訊，請參閱 < [Centennial 專案中使用 Visual c + + Runtime](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project)並[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="uwp-apps-that-use-ccx"></a>UWP 應用程式使用 C + + /CX

|||
|-|-|
|[Visual C++ 語言參考 (C++/CX)](visual-c-language-reference-c-cx.md)|描述 c + + 可精簡 Windows 執行階段 Api，並啟用錯誤處理的例外狀況為基礎的擴充功能組。|
|[建置應用程式和程式庫 (C++/CX)](building-apps-and-libraries-c-cx.md)|說明如何建立可以從 C++/CX 應用程式或元件存取的 DLL 和靜態程式庫。|
|[教學課程：建立的 UWP"Hello，World"應用程式，在 C + + /CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|逐步解說中，將會介紹基本概念的 UWP 應用程式開發，在 C + + /CX。 |
|[建立 Windows 執行階段元件，在 C + + /CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何建立其他的 UWP 應用程式和元件可以使用的 Dll。|
|[UWP 遊戲程式設計](/windows/uwp/gaming/)|描述如何使用 DirectX 和 C + + /CX，以建立遊戲。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 的 UWP 應用程式

Windows 執行階段 c + + 樣板程式庫提供的 ISO c + + 程式碼可以存取 Windows 執行階段例外狀況的環境中的低階 COM 介面。 在大部分情況下，我們建議您使用 C + + /cli WinRT 或 C + + /CX 而不是 Windows 執行階段 c + + 樣板程式庫，適用於 UWP 應用程式開發。 Windows 執行階段 c + + 樣板程式庫的相關資訊，請參閱[Windows 執行階段 c + + 範本庫 (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中的 c + +](../overview/visual-cpp-in-visual-studio.md)<br/>
[使用 C++ 進行 Windows 程式設計的概觀](../windows/overview-of-windows-programming-in-cpp.md)<br/>