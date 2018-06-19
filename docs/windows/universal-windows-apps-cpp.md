---
title: 通用 Windows 應用程式 （c + +） |Microsoft 文件
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
ms.openlocfilehash: 9914e9ac83efcc43ef120259254b65ef4f1e0ee9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891119"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 應用程式 (C++)

通用 Windows 平台 (UWP) 應用程式具體表現一組設計原則，以強調為主的不同裝置上的不同螢幕大小自動調整的內容的簡單使用者介面。 您會在 XAML 標記中建立 UI，並在原生 C++ 中建立程式碼後置。 您也可以建立元件 (DLL)，供其他語言所撰寫的 UWP 應用程式使用。 用於 UWP 應用程式開發介面是 Windows 執行階段，這是構造良好的程式庫提供各種不同的作業系統服務。

> [!TIP]  
> 適用於 Windows 10 中，您可以使用橋接器桌面應用程式轉換工具來封裝您現有的桌面應用程式以透過 Microsoft 市集部署。 如需詳細資訊，請參閱[Centennial 專案中使用 Visual c + + Runtime](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project)和[桌面橋接器](/windows/uwp/porting/desktop-to-uwp-root)。

## <a name="uwp-apps-that-use-cwinrt"></a>UWP 應用程式使用 C + + WinRT

C + + WinRT 是新的且僅限標頭的程式庫為基礎 c + + 語言投射為 Windows 執行階段使用完全標準 c + +，不同於 C + + /CX 實作。 C + + WinRT 不會使用非標準的語法或 Microsoft 語言擴充功能，也可以利用完整的 c + + 編譯器建立獲得高度最佳化的輸出。 如需詳細資訊，請參閱[C + + WinRT](/windows/uwp/cpp-and-winrt-apis)。 如需 C + + WinRT 及程式碼快速入門中，請參閱[簡介使用 C + + WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

## <a name="uwp-apps-that-use-ccx"></a>UWP 應用程式使用 C + + /CX

|||
|-|-|
|[Visual C++ 語言參考 (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|描述一組擴充功能，簡化 c + + 使用的 Windows 執行階段 Api，並啟用根據例外狀況的錯誤處理。|
|[建置應用程式和程式庫 (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|說明如何建立可以從 C++/CX 應用程式或元件存取的 DLL 和靜態程式庫。|
|[教學課程： 建立 UWP"Hello，World"應用程式，在 C + + /CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|逐步解說介紹基本概念的 UWP 應用程式開發，在 C + + /CX。 |
|[建立 Windows 執行階段元件，在 C + + /CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何建立其他的 UWP 應用程式和元件可以使用的 Dll。|
|[UWP 遊戲程式設計](/windows/uwp/gaming/)|描述如何使用 DirectX 和 C + + /CX 建立遊戲。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 的 UWP 應用程式

Windows 執行階段 c + + 樣板程式庫提供的 ISO c + + 程式碼可以存取的無例外狀況的環境中的 Windows 執行階段的低階 COM 介面。 在大部分情況下，我們建議您使用 C + + WinRT 或 C + + /CX 而不是 Windows 執行階段 c + + 樣板程式庫開發 UWP 應用程式。 Windows 執行階段 c + + 樣板程式庫的相關資訊，請參閱[Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>另請參閱

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>
