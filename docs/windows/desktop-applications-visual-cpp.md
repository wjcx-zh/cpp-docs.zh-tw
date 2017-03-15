---
title: "Windows 傳統型應用程式 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
caps.latest.revision: 17
caps.handback.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Windows 傳統型應用程式 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您想要建立具有以視窗為基礎的使用者介面，而且可在 Windows 桌面上之 Windows XP 到 Windows 10 的各種 Windows 版本中執行的原生傳統型應用程式時，可以建立 Windows 傳統型應用程式。  
  
 *「Windows 傳統型應用程式」*\(Windows Desktop Application，在之前的文件中有時稱為 Win32 應用程式\) 是意指使用訊息迴圈直接處理 Windows 訊息之應用程式的慣用詞彙，這個應用程式並不使用 Microsoft Foundation Classes \(MFC\)、Active Template Library \(ATL\)、.NET Framework 等 Framework 來處理 Windows 訊息。 C\+\+ 的 Windows 傳統型應用程式可以使用 C 執行階段 \(CRT\)、標準範本庫 \(STL\) 類別和函式、COM 物件，以及任何統稱為 Windows 應用程式開發介面的公用 Windows 函式。 如需 C\+\+ 的 Windows 傳統型應用程式簡介，請參閱[學習以 C\+\+ 設計 Windows 程式](http://go.microsoft.com/fwlink/p/?LinkId=262281)。  
  
 Windows 傳統型應用程式是一種建立 Windows 原生傳統型應用程式的方式；另一種方式為 MFC 應用程式。 MFC 是建立含有許多使用者介面控制項或自訂使用者控制項的應用程式 \(特別是企業型應用程式\) 時的預設選項。 MFC 針對序列化、文字操作、列印作業和現代使用者介面項目 \(例如功能區\) 提供便利的協助程式類別。 這些類別不適用於 Windows 傳統型應用程式。  
  
## 相關文章  
  
|標題|描述|  
|--------|--------|  
|[Windows 程式開發](http://go.microsoft.com/fwlink/p/?LinkId=262282)|包含 Windows 應用程式開發介面和 COM 的相關資訊 \(部分 Windows 應用程式開發介面和協力廠商 DLL 會實作為 COM 物件\)。|  
|[Hilo：開發適用於 Windows 7 的 C\+\+ 應用程式](http://go.microsoft.com/fwlink/p/?LinkId=262284)|說明如何建立豐富型用戶端 Windows 傳統型應用程式，這個應用程式會使用 Windows 動畫和 Direct2D 建立浮動切換式 \(Carousel\-based\) 使用者介面。|  
|[主控台應用程式](../windows/console-applications-in-visual-cpp.md)|包含主控台應用程式的相關資訊。 Win32 \(或 Win64\) 主控台應用程式沒有自己的視窗和訊息迴圈。 這會在主控台視窗中執行，而且輸入和輸出都是透過命令列來處理。|  
|[Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md)|說明 Visual Studio 中的 Visual C\+\+ 主要功能，以及 Visual C\+\+ 文件其餘部分的連結。|  
|MSDN 網站上的 [Visual C\+\+ 開發人員中心](http://go.microsoft.com/fwlink/p/?LinkId=252885)|包含與 Windows 傳統型應用程式相關的教學課程、部落格文章和文章。|  
|[如何：在 Windows 桌面應用程式中使用 Windows 10 SDK ](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|包含將您的專案設定為使用 Windows 10 SDK 建置的步驟。|