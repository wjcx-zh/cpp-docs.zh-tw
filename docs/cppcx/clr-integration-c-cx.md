---
title: "CLR 整合 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 10
---
# CLR 整合 (C++/CX)
某些 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 類型接收了 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 的特殊處理，所用語言以通用語言執行平台 \(CLR\) 為基礎。 這篇文章討論一種語言的數個類型如何對應到另一種語言。 例如，CLR 將 Windows.Foundation.IVector 對應到 System.Collections.IList、將 Windows.Foundation.IMap 對應到 System.Collections.IDictionary 等等。 同樣地，[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 會特別對應諸如 Platform::Delegate 和 Platform::String 這樣的類型。  
  
## 將 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 對應到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 當 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 讀取 Windows 中繼資料 \(.winmd\) 檔案時，編譯器會自動將常見的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 命名空間和類型對應到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 命名空間和類型。 例如，數值 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 類型 `UInt32` 會自動對應到 `default::uint32`。  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 將數個其他 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 類型對應到 **Platform** 命名空間。 例如 **Windows::Foundation** HSTRING 控制代碼，代表唯讀的 Unicode 文字字串，會對應到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] `Platform::String` 類別。 當 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 作業傳回錯誤 HRESULT 時，它會對應到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] `Platform::Exception`。 如需詳細資訊，請參閱[Built\-in Types](http://msdn.microsoft.com/zh-tw/acc196fd-09da-4882-b554-6c94685ec75f)。  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 也會對應 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 命名空間中的某些類型，以增強類型的功能。 針對這些類型，[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 提供了對 C\+\+ 而言特有，但類型的標準 .winmd 檔案不提供的協助程式建構函式和方法。  
  
 下列清單顯示支援新建構函式和 Helper 方法的值結構。 如果之前撰寫的程式碼使用結構初始設定清單，請變更為使用新加入的建構函式。  
  
 **Windows::Foundation**  
  
-   點  
  
-   Rect  
  
-   大小  
  
 **Windows::UI**  
  
-   色彩  
  
 **Windows::UI::Xaml**  
  
-   CornerRadius  
  
-   持續期間  
  
-   GridLength  
  
-   Thickness  
  
 **Windows::UI::Xaml::Interop**  
  
1.  TypeName  
  
 **Windows::UI::Xaml::Media**  
  
-   矩陣  
  
 **Windows::UI::Xaml::Media::Animation**  
  
-   KeyTime  
  
-   RepeatBehavior  
  
 **Windows::UI::Xaml::Media::Media3D**  
  
-   Matrix3D  
  
## 將 CLR 對應到 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 當 Visual C\+\+ 或 C\# 編譯器讀取 .winmd 檔案時，它們會自動將中繼資料檔案中的某些類型對應到適當的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 或 CLR 類型。 例如，在 CLR 中，IVector\<T\> 介面會對應到 IList\<T\>。 但在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中，IVector\<T\> 介面不會對應到另一種類型。  
  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中的 IReference\<T\> 對應到 .NET 的 Nullable\<T\>。  
  
## 請參閱  
 [與其他語言間的互通性](../cppcx/interoperating-with-other-languages-c-cx.md)