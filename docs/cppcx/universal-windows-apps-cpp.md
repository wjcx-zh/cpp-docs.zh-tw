---
title: 通用 Windows 應用程式 (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.openlocfilehash: fbd5366ee52dfe32baef9458a82c16914666699e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58783999"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 應用程式 (C++)

通用 Windows 平台 (UWP) 是 Windows 的現代程式設計介面。 使用 UWP 撰寫的應用程式或元件一次，並將它部署在任何 Windows 10 裝置。 您可以撰寫元件C++和任何其他的 UWP 相容語言撰寫的應用程式可以使用它。

大部分的 UWP 文件是在 Windows 內容在樹狀目錄[通用 Windows 平台的文件](/windows/uwp/)。 您會在這裡找到開始教學課程也做為參考文件。 

新的 UWP 應用程式和元件，我們建議您使用[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)，新標準 C + + 17 語言推演，適用於 Windows 執行階段 Api。 C++/ 在 Windows 10 SDK 版本 1803年之後推出 WinRT。 C++/ WinRT 完全在標頭檔中實作，而且是為您提供第一級存取新式 Windows api。 不同於C++/CX 實作。 C++/ WinRT 不會使用非標準的語法或 Microsoft 語言擴充功能，以及它完整利用C++編譯器建立高度最佳化的輸出。 如需詳細資訊，請參閱 <<c0> [ 簡介C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。</c0>

您可以使用傳統型橋接器應用程式轉換器封裝您現有的桌面應用程式透過 Microsoft Store 部署。 如需詳細資訊，請參閱 <<c0> [ 視覺化使用C++在 Centennial 專案中的執行階段](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project)並[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。</c0>

## <a name="uwp-apps-that-use-ccx"></a>UWP 應用程式使用C++/CX

|||
|-|-|
|[Visual C++ 語言參考 (C++/CX)](visual-c-language-reference-c-cx.md)|描述一組簡化的延伸模組的C++的 Windows 執行階段 Api 和例外狀況為基礎的啟用錯誤處理的耗用量。|
|[建置應用程式和程式庫 (C++/CX)](building-apps-and-libraries-c-cx.md)|說明如何建立可以從 C++/CX 應用程式或元件存取的 DLL 和靜態程式庫。|
|[教學課程：建立的 UWP"Hello，World"應用程式，在C++/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|逐步解說中，將會介紹開發 UWP 應用程式的基本概念C++/CX。 |
|[建立 Windows 執行階段元件中的C++/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何建立其他的 UWP 應用程式和元件可以使用的 Dll。|
|[UWP 遊戲程式設計](/windows/uwp/gaming/)|描述如何使用 DirectX 和C++來建立遊戲的 /CX。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 執行階段的 UWP 應用程式C++範本庫 (WRL)

Windows 執行階段C++範本程式庫會提供低階 COM 介面的 isoC++程式碼可以存取 Windows 執行階段例外狀況的環境中。 在大部分情況下，我們建議您使用C++/WinRT 或C++而不是 Windows 執行階段 /CXC++適用於 UWP 應用程式開發的範本程式庫。 如需 Windows 執行階段的詳細資訊C++樣板程式庫，請參閱[Windows 執行階段C++範本程式庫 (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[使用 C++ 進行 Windows 程式設計的概觀](../windows/overview-of-windows-programming-in-cpp.md)<br/>