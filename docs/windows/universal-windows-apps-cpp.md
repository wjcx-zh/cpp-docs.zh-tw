---
title: "通用 Windows 應用程式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 656c8ac642ae9c8a6a76e1ed52ca014b5515e65f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="universal-windows-apps-c"></a>通用 Windows 應用程式 (C++)
通用 Windows 平台 (UWP) 應用程式具體表現一組設計原則，以強調為主的不同裝置上的不同螢幕大小自動調整的內容的簡單使用者介面。 您會在 XAML 標記中建立 UI，並在原生 C++ 中建立程式碼後置。 您也可以建立元件 (DLL)，供其他語言所撰寫的 UWP 應用程式使用。 用於 UWP 應用程式開發介面是 Windows 執行階段，這是構造良好的程式庫提供各種不同的作業系統服務。  

> [!TIP]  
> 適用於 Windows 10 中，您可以使用桌面應用程式轉換工具來封裝您現有的桌面應用程式以透過 Windows 市集的部署。 如需詳細資訊，請參閱 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) (在 Centennial 專案中使用 Visual C++ 執行階段) 和[使用傳統型橋接器將您的傳統型應用程式移轉至通用 Windows 平台 (UWP)](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)。
  
  
## <a name="uwp-apps-that-use-ccx"></a>使用 C++/CX 的 UWP 應用程式  
  
|||  
|-|-|  
|[Visual C++ 語言參考 (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|描述一組擴充功能，簡化 c + + 使用的 Windows 執行階段 Api，並啟用根據例外狀況的錯誤處理。|  
|[建置應用程式和程式庫 (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|說明如何建立可以從 C++/CX 應用程式或元件存取的 DLL 和靜態程式庫。|  
|[教學課程：使用 C++ 建立您的第一個 Windows 市集應用程式](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|此逐步解說介紹 c + + 通用 Windows 平台應用程式開發的基本概念。 (尚未更新有關在 Windows 10 上開發 UWP 的資訊)。|  
|[在 C++ 中建立 Windows 執行階段元件](https://docs.microsoft.com/en-us/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何建立其他的通用 Windows 平台應用程式和元件可以使用的 Dll。|  
|[開發遊戲](https://docs.microsoft.com/en-us/windows/uwp/gaming/)|說明如何使用 DirectX 和 C++ 來建立遊戲。|  
  
## <a name="universal-windows-platform-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 執行階段 c + + 樣板程式庫 (WRL) 的通用 Windows 平台應用程式 
 Windows 執行階段 c + + 樣板程式庫提供的 ISO c + + 程式碼可以存取的無例外狀況的環境中的 Windows 執行階段的低階 COM 介面。 在大部分情況下，我們建議您使用 C + + /CX 而不是 Windows 執行階段 c + + 樣板程式庫，針對通用 Windows 平台應用程式開發。 Windows 執行階段 c + + 樣板程式庫的相關資訊，請參閱[Windows 執行階段 c + + 樣板程式庫 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++](../visual-cpp-in-visual-studio.md)

