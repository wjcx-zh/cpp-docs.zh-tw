---
title: 通用 Windows 應用程式 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ba556ee3803bb00f07032e0589209af2d32addf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591749"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 應用程式 (C++)

通用 Windows 平台 (UWP) 應用程式具體表現一套強調以針對不同裝置上的不同螢幕大小自動調整的內容為主軸的簡單使用者介面的設計原則。 您會在 XAML 標記中建立 UI，並在原生 C++ 中建立程式碼後置。 您也可以建立元件 (DLL)，供其他語言所撰寫的 UWP 應用程式使用。 UWP 應用程式的 API 介面是 Windows 執行階段，這是構造良好的程式庫，提供各種不同的作業系統服務。

> [!TIP]
> 適用於 Windows 10 中，您可以使用傳統型橋接器應用程式轉換器封裝您現有的桌面應用程式透過 Microsoft Store 部署。 如需詳細資訊，請參閱 < [Centennial 專案中使用 Visual c + + Runtime](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project)並[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="uwp-apps-that-use-cwinrt"></a>UWP 應用程式使用 C + + /cli WinRT

C + + /cli WinRT 是新的、 僅限標頭的程式庫為基礎 c + + 語言推演，適用於 Windows 執行階段使用完整標準 c + +，不同於 C + + /CX 實作。 C + + /cli WinRT 不會使用非標準的語法或 Microsoft 語言擴充功能，以及它利用完整的 c + + 編譯器建立高度最佳化的輸出。 如需詳細資訊，請參閱 < [C + + /cli WinRT](/windows/uwp/cpp-and-winrt-apis)。 如需 C + + /cli WinRT 及程式碼快速入門中，請參閱[介紹 C + + /cli WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

## <a name="uwp-apps-that-use-ccx"></a>UWP 應用程式使用 C + + /CX

|||
|-|-|
|[Visual C++ 語言參考 (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|描述 c + + 可精簡 Windows 執行階段 Api，並啟用錯誤處理的例外狀況為基礎的擴充功能組。|
|[建置應用程式和程式庫 (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|說明如何建立可以從 C++/CX 應用程式或元件存取的 DLL 和靜態程式庫。|
|[教學課程： 建立的 UWP"Hello，World"應用程式，在 C + + /CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|逐步解說中，將會介紹基本概念的 UWP 應用程式開發，在 C + + /CX。 |
|[建立 Windows 執行階段元件，在 C + + /CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何建立其他的 UWP 應用程式和元件可以使用的 Dll。|
|[UWP 遊戲程式設計](/windows/uwp/gaming/)|描述如何使用 DirectX 和 C + + /CX，以建立遊戲。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 的 UWP 應用程式

Windows 執行階段 c + + 樣板程式庫提供的 ISO c + + 程式碼可以存取 Windows 執行階段例外狀況的環境中的低階 COM 介面。 在大部分情況下，我們建議您使用 C + + /cli WinRT 或 C + + /CX 而不是 Windows 執行階段 c + + 樣板程式庫，適用於 UWP 應用程式開發。 Windows 執行階段 c + + 樣板程式庫的相關資訊，請參閱[Windows 執行階段 c + + 範本庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另請參閱

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>