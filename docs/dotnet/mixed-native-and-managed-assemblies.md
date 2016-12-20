---
title: "混合 (原生和 Managed) 組件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 編譯器選項 [C++], 混合的組件"
  - "組件 [C++], 混合"
  - "Interop [C++], 混合的組件"
  - "互通性 [C++], 混合的組件"
  - "Managed 程式碼 [C++], 互通性"
  - "混合的組件 [C++]"
  - "混合的組件 [C++], 關於混合的組件"
  - "混合的 DLL 載入 [C++]"
  - "機器碼 [C++], .NET 互通性"
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 混合 (原生和 Managed) 組件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

混合組件可以同時包含 Unmanaged 機器指令和 MSIL 指令。  這樣會讓混合組件可以呼叫 .NET 元件或由 .NET 元件呼叫，同時保留和完全 Unmanaged 元件的相容性。  開發人員可以利用混合組件，同時使用 Managed 和 Unmanaged 功能撰寫應用程式。  這使得混合組件很適合用於將現有的 Visual C\+\+ 應用程式移轉至 .NET 平台。  
  
 例如，使用 **\/clr** 編譯器參數只重新編譯一個模組，就可以將完全由 Unmanaged 函式組成的現有應用程式帶到 .NET 平台。  然後此模組就可以使用 .NET 功能，而且仍相容於應用程式的其餘部分。  如此，應用程式就可以採用一部分接著一部分的漸進方式轉換至 .NET 平台。  甚至可以在相同檔案內，以一個函式接著一個函式的方式決定要進行 Managed 或 Unmanaged 編譯 \(Compilation\) \(請參閱 [managed、unmanaged](../preprocessor/managed-unmanaged.md)\)。  
  
 Visual C\+\+ 支援產生下列三種獨特型別的 Managed 組件：混合的、純綷的和可驗證的。  後兩者會於[純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)中討論。  
  
## 本章節內容  
 [如何：移轉至 \/clr](../dotnet/how-to-migrate-to-clr.md)  
 描述在應用程式中引入或升級 .NET 功能的建議步驟。  
  
 [如何：使用 \/clr 編譯 MFC 和 ATL 程式碼](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)  
 討論如何編譯現有的 MFC 和 ATL 程式，使其以 Common Language Runtime 為目標。  
  
 [混合組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)  
 描述「載入器鎖定」的問題和解決方案。  
  
 [混合組件的程式庫支援](../dotnet/library-support-for-mixed-assemblies.md)  
 討論如何在 **\/clr** 編譯中使用原生程式庫。  
  
 [效能考量](../dotnet/performance-considerations-for-interop-cpp.md)  
 描述混合組件和資料封送處理 \(Marshaling\) 的效能含意。  
  
 [應用程式定義域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)  
 討論應用程式定義域的 Visual C\+\+ 支援。  
  
 [Double Thunking](../dotnet/double-thunking-cpp.md)  
 討論 Managed 函式之原生進入點 \(Entry Point\) 的效能含意。  
  
 [當使用以 \/clr 建置的 COM 物件時防止 CLR 關閉之例外狀況](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)  
 討論如何確保適當地關閉 Managed 應用程式，此應用程式會使用以 **\/clr** 編譯的 COM 物件。  
  
 [如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式](../dotnet/create-a-partially-trusted-application.md)  
 討論如何藉由移除 msvcm90.dll 的相依性，以建立使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 的部分信任 Common Language Runtime 應用程式。  
  
 如需混合組件程式碼撰寫方針的詳細資訊，請參閱 MSDN 文章 \< Managed 與 Unmanaged 程式碼互通性概觀 [http:\/\/msdn.microsoft.com\/netframework\/default.aspx?pull\=\/library\/dndotnet\/html\/manunmancode.asp](http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp)\>。  
  
## 請參閱  
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)