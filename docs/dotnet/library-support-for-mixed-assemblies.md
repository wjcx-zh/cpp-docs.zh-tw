---
title: "混合組件的程式庫支援 | Microsoft Docs"
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
helpviewer_keywords: 
  - "程式庫 [C++], 混合的組件"
  - "混合的組件 [C++], 程式庫支援"
  - "msvcm90[d].dll"
  - "msvcmrt[d].lib"
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 混合組件的程式庫支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於搭配 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 編譯的應用程式，Visual C\+\+ 支援使用 Standard C\+\+ 程式庫、通用執行階段程式庫 \(CRT\)、ATL 和 MFC。  這讓使用這些程式庫的現有應用程式也能使用 .NET Framework 功能。  
  
 這項支援也提供了新的 DLL 和匯入程式庫，如下：  
  
-   如果您使用 \/clr 編譯，則是 Msvcmrt\[d\].lib。  混合組件會連結至這個匯入程式庫。  
  
-   如果是搭配 \/clr:pure 編譯，則是 Msvcm90\[d\].dll 和 Msvcurt\[d\].lib。  DLL 是提供 Managed C 執行階段 \(CRT\) 支援的混合組件，並且是屬於安裝在全域組件快取 \(GAC\) 中 Managed 組件的一部分。  純組件會連結至這個匯入程式庫，最後會繫結至 Msvcm90.dll。  
  
 這項支援會提供數種相關的優點：  
  
-   混合和純程式碼都能使用 CRT 和 Standard C\+\+ 程式庫。  所提供的 CRT 和 Standard C\+\+ 程式庫不是可驗證的。最終，呼叫仍會傳送到與您在使用機器碼時相同的 CRT 和 Standard C\+\+ 程式庫。  
  
-   在純影像和混合影像中正確的共同例外狀況處理 \(Exception Handling\)。  
  
-   在純影像和混合影像中 C\+\+ 變數的靜態初始化。  
  
-   支援在 Managed 程式碼中的 per\-AppDomain 和 per\-process 變數。  
  
-   解析套用至 Visual C\+\+ .NET 和 Visual C\+\+ .NET 2003 中的混合 DLL 的載入器鎖定問題。  
  
 此外，這項支援表示出下列限制：  
  
-   只支援 CRT DLL 模型 \(以 \/clr 或 \/clr:pure 編譯的程式碼都適用\)。  
  
-   如果純物件和混合物件是使用 Visual C\+\+ 程式庫，您就無法在單一影像中混用這些物件 \(因為在純影像中所有物件都必須是純粹的\)。  如果這樣做，會得到連結階段錯誤。  
  
 您應該更新 Common Language Runtime \(CLR\) 為最新版本，因為 CLR 不保證能和先前的版本共用。  使用這些變更所建置的程式碼，將不會在 CLR 1.x 版上執行。  
  
## 請參閱  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)