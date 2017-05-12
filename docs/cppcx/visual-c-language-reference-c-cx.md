---
title: "Visual C++ 語言參考 (C++-CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
caps.latest.revision: 27
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 27
---
# Visual C++ 語言參考 (C++-CX)
[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 是一組可讓您使用盡可能接近現代 C\+\+ 的慣用語來建立 Windows 應用程式與 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 元件的 C\+\+ 語言擴充功能。 您可以使用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]，透過容易與 Visual C\#、Visual Basic、JavaScript 與其他支援 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 的語言互動的原生程式碼，撰寫 Windows 應用程式與元件。 針對少數需要直接存取原始 COM 介面或使用非例外狀況程式碼的情況，您可以使用 [Windows Runtime C\+\+ Template Library \(WRL\)](~/windows/windows-runtime-cpp-template-library-wrl.md)。  
  
 新的模型代表 Windows 上新一代的原生 C\+\+ 程式設計。 您可以使用此模型建立：  
  
-   可使用 XAML 定義使用者介面及使用原生堆疊的 C\+\+ Windows 應用程式。 如需詳細資訊，請參閱[在 C\+\+ 中建立 "hello world" 應用程式 \(Windows 10\)](http://msdn.microsoft.com/library/windows/apps/dn996906.aspx)。  
  
-   可供 JavaScript 型 Windows 應用程式使用的 C\+\+ [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 元件。 如需詳細資訊，請參閱[在 C\+\+ 中建立 Windows 執行階段元件](http://msdn.microsoft.com/library/hh441569.aspx)[在 C\+\+ 中建立 Windows 執行階段元件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)。  
  
-   Windows DirectX 遊戲與細膩圖像處理應用程式。 如需詳細資訊，請參閱[使用 DirectX 來建立簡單的通用 Windows 平台 \(UWP\) 遊戲](http://msdn.microsoft.com/library/windows/apps/xaml/mt210793.aspx)。  
  
## 相關文章  
  
|||  
|-|-|  
|[快速參考](../cppcx/quick-reference-c-cx.md)|[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 關鍵字和運算子的表格。|  
|[類型系統](../cppcx/type-system-c-cx.md)|說明基本 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 型别與程式設計建構，以及如何運用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 來使用及建立 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]型别。|  
|[建置應用程式和程式庫](../cppcx/building-apps-and-libraries-c-cx.md)|討論如何使用 IDE 建置應用程式以及連結至靜態程式庫與 DLL。|  
|[與其他語言間的互通性](../cppcx/interoperating-with-other-languages-c-cx.md)|討論使用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 撰寫的元件如何與使用 JavaScript 撰寫的元件、任何 Managed 語言或 [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)] 搭配使用。|  
|[執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)|討論如何為您建立的元件指定執行緒與封送處理行為。|  
|[命名空間參考](../cppcx/namespaces-reference-c-cx.md)|預設命名空間、Platform 命名空間、Platform::Collections 及相關命名空間的參考文件。|  
|[通用 Windows 平台應用程式不支援 CRT 函式](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|列出 Windows 執行階段應用程式中不可用的 CRT 函式。|  
|[Windows 10 應用程式的操作指南](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|提供 Windows 10 應用程式的高階指引以及詳細資訊連結。|  
  
1.  [C\+\+\/CX \[n\] 的第 0 部分：簡介](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
2.  [C\+\+\/CX \[n\] 的第 0 部分：簡介](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
3.  [C\+\+\/CX \[n\] 的第 2 部分：戴帽子的類別](http://blogs.msdn.com/b/vcblog/archive/2012/09/17/cxxcxpart02typesthatwearhats.aspx)  
  
4.  [C\+\+\/CX \[n\] 的第 3 部分：建構中](http://blogs.msdn.com/b/vcblog/archive/2012/10/05/cxxcxpart03underconstruction.aspx)  
  
5.  [C\+\+\/CX \[n\] 的第 4 部分：靜態成員函式](http://blogs.msdn.com/b/vcblog/archive/2012/10/19/cxxcxpart04staticmemberfunctions.aspx)