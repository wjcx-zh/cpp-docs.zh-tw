---
title: 桌面應用程式 （Visual c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9c8180288374711db4e6d866c73a0bc8919caf2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="desktop-applications-visual-c"></a>桌面應用程式 （Visual c + +）
A*桌面應用程式*c + + 中是可以存取一組完整的 Windows 應用程式開發介面，並在視窗或系統主控台中任一個執行的原生應用程式。 在 c + + 桌面應用程式可以執行 Windows XP 到 Windows 10 （但是不再正式支援 Windows XP 和有許多 Windows 應用程式開發介面已引進從那時起）。   桌面應用程式是從通用 Windows 平台 (UWP) 應用程式，可以在執行 Windows 10 的電腦上以及 XBox、 Windows Phone、 Surface Hub 和其他裝置上執行的不同。 如需桌面 vs 的詳細資訊。UWP 應用程式，請參閱[選擇您的技術](https://msdn.microsoft.com/en-us/library/windows/desktop/dn614993\(v=vs.85\).aspx)。  
  
 **術語**  
  
-   A *Win32*應用程式是一種 Windows 桌面應用程式，可讓 c + + 中的使用的原生[Windows C 應用程式開發介面和/或 COM Api](https://msdn.microsoft.com/en-us/library/windows/desktop/ff818516\(v=vs.85\).aspx) CRT 和標準程式庫應用程式開發介面，以及第 3 個合作對象文件庫。 在視窗中執行的 Win32 應用程式需要開發人員明確地搭配 Windows 程序函式內的 Windows 訊息。 雖然名稱的 Win32 應用程式可以編譯為 32 位元 (x86) 或 64 位元 (x64) 二進位。 在 Visual Studio IDE 中的條款 x86 和 Win32 的意義相同。  
  
-   [元件物件模型 (COM)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms694363\(v=vs.85\).aspx)是一種規格，可讓以與彼此通訊的不同語言撰寫的程式。 許多 Windows 元件會實作為 COM 物件，並遵循標準的 COM 規則的物件建立介面探索及物件解構。  使用 c + + 桌面應用程式的 COM 物件是相當簡單，但更進階撰寫您自己的 COM 物件。 [Active Template Library (ATL)](../atl/atl-com-desktop-components.md)提供巨集和 helper 函式可簡化 COM 開發。  
  
-   MFC 應用程式是使用的 Windows 桌面應用程式[Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md)建立使用者介面。 COM 元件，以及 CRT 和標準程式庫 Api，也可以使用 MFC 應用程式。 MFC 提供的視窗訊息迴圈和 Windows 應用程式開發介面的精簡 c + + 物件導向包裝函式。 MFC 是應用程式的預設選擇，特別是企業型應用程式，建立含有許多使用者介面控制項或自訂使用者控制項。 MFC 提供視窗管理、 序列化、 文字操作、 列印、 和現代使用者介面項目，例如功能區的便利的協助程式類別。 若要有效使用 MFC 您應該熟悉 Win32。  
  
-   C + + CLI 應用程式或元件使用 c + + 語法的擴充功能 （如允許 c + + 規格） 來啟用.NET 和原生 C + + 程式碼之間的互動。  C + + /CLI 應用程式可以有原生方式執行的組件以及存取.NET Framework 執行.NET 基底類別庫的組件。 C + + CLI 是慣用的選項，當您需要使用 C# 或 Visual Basic 撰寫的程式碼的原生 c + + 程式碼時。 它主要是供.NET Dll 中，而不是在使用者介面程式碼中使用。 如需詳細資訊，請參閱[.NET 程式設計使用 C + + /CLI （Visual c + +）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。  
  
 C 執行階段 (CRT) 和標準程式庫類別和函式、 COM 物件與公用 Windows 函式，統稱為 Windows API，可以使用任何 c + + 中的桌面應用程式。 如需 C++ 的 Windows 傳統型應用程式簡介，請參閱 [學習以 C++ 設計 Windows 程式](http://go.microsoft.com/fwlink/p/?LinkId=262281)。  
  
## <a name="in-this-section"></a>本節內容  
  
|標題|描述|  
|-----------|-----------------|  
|[主控台應用程式](../windows/console-applications-in-visual-cpp.md)|包含主控台應用程式的相關資訊。 Win32 (或 Win64) 主控台應用程式沒有自己的視窗和訊息迴圈。 這會在主控台視窗中執行，而且輸入和輸出都是透過命令列來處理。|  
|[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)|如何建立在相對於在主控台視窗中執行的桌面應用程式。|  
|[使用 DirectX （c + +） 建立遊戲的資源](../windows/resources-for-creating-a-game-using-directx.md)|C + + 中建立遊戲的內容連結。|  
|[逐步解說： 建立和使用靜態程式庫](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|如何建立.lib 二進位檔案。|  
|[如何：在 Windows 傳統型應用程式中使用 Windows 10 SDK](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含將您的專案設定為使用 Windows 10 SDK 建置的步驟。|  
  
## <a name="related-articles"></a>相關文章  
  
|標題|描述|  
|-----------|-----------------|  
|[Windows 程式開發](http://go.microsoft.com/fwlink/p/?LinkId=262282)|包含 Windows 應用程式開發介面和 COM 的相關資訊 (部分 Windows 應用程式開發介面和協力廠商 DLL 會實作為 COM 物件)。|  
|[Hilo：開發適用於 Windows 7 的 C++ 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=262284)|說明如何建立豐富型用戶端 Windows 傳統型應用程式，這個應用程式會使用 Windows 動畫和 Direct2D 建立浮動切換式 (Carousel-based) 使用者介面。  Windows 7 之後尚未更新為本教學課程，但是它仍然會提供 Win32 程式設計中的完整介紹。|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|說明 Visual Studio 中的 Visual C++ 主要功能，以及 Visual C++ 文件其餘部分的連結。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++](../visual-cpp-in-visual-studio.md)
