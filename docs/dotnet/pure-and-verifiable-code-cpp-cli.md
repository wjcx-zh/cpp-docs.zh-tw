---
title: "純粹的和可驗證的程式碼 (C++/CLI) | Microsoft Docs"
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
  - ".NET Framework [C++], 純粹的和可驗證的程式碼"
  - "/clr 編譯器選項 [C++], 混合的組件"
  - "/clr 編譯器選項 [C++], 純粹組件"
  - "/clr 編譯器選項 [C++], 可驗證的組件"
  - "組件 [C++], 混合程式碼"
  - "組件 [C++], 純程式碼"
  - "組件 [C++], 可驗證的程式碼"
  - "混合的組件 [C++]"
  - "混合的組件 [C++], 關於混合的組件"
  - "純的 MSIL [C++]"
  - "純的 MSIL [C++], 關於純程式碼"
  - "可驗證的組件 [C++]"
  - "可驗證的組件 [C++], 關於可驗證的組件"
  - "可驗證的類型安全程式碼 [C++]"
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 純粹的和可驗證的程式碼 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於 .NET 程式設計，Visual C\+\+ 支援建立三種不同類型的元件和應用程式：混合的、純粹的和可驗證的。  這三種都是透過 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項提供使用。  
  
## 備註  
 如需可驗證組件的詳細資訊，請參閱：  
  
-   [混合的、純粹的和可驗證的功能比較](../dotnet/mixed-pure-and-verifiable-feature-comparison-cpp-cli.md)  
  
-   [如何：移轉至 \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [如何：建立可驗證的 C\+\+ 專案](../dotnet/how-to-create-verifiable-cpp-projects-cpp-cli.md)  
  
-   [如何：移轉至 \/clr:safe](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)  
  
-   [‏使用可驗證的組件搭配 SQL Server](../dotnet/using-verifiable-assemblies-with-sql-server-cpp-cli.md)  
  
-   [安全性最佳作法](../top/security-best-practices-for-cpp.md)  
  
-   [將專案從混合模式轉換為純中繼語言](../dotnet/converting-projects-from-mixed-mode-to-pure-intermediate-language.md)  
  
## 混合 \(\/clr\)  
 混合組件 \(使用 **\/clr** 編譯\) 包含 Unmanaged 和 Managed 組件 \(Part\)，讓它們可以使用 .NET 功能，但是仍會包含 Unmanaged 程式碼。  這讓應用程式和元件可以進行更新以使用 .NET 功能，而不需要重新撰寫整個專案。  用這種方式使用 Visual C\+\+ 混合 Managed 和 Unmanaged 程式碼，稱為 C\+\+ Interop。  如需詳細資訊，請參閱[混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)與[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)。  
  
## 純粹 \(\/clr:pure\)  
 純粹組件 \(使用 **\/clr:pure** 編譯\) 可能同時包含原生和 Managed 資料型別，但是只能包含 Managed 函式。  如同混合組件，純粹組件允許透過 P\/Invoke 與原生 DLL 進行 Interop \(請參閱[在 C\+\+ 中使用明確的 PInvoke \(DllImport 屬性\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)\)，但 C\+\+ Interop 功能無法使用。  此外，純粹組件無法匯出可從原生函式呼叫的函式，因為純粹組件中的進入點 \(Entry Point\) 使用 [\_\_clrcall](../cpp/clrcall.md) 呼叫慣例 \(Calling Convention\)。  
  
### \/clr:pure 的優點  
  
-   較佳的效能：因為純粹組件只包含 MSIL，所以沒有原生函式，因此不需要 Managed\/Unmanaged 轉換 \(透過 P\/Invoke 進行的函式呼叫即為這個規則的例外狀況\)。  
  
-   AppDomain 感知：Managed 函式和 CLR 資料型別存在於`Application Domains`內部，應用程式定義域會影響它們的可視性和存取範圍。  純粹組件可感知定義域 \(每個型別都暗示有 \_\_declspec\([appdomain](../cpp/appdomain.md)\)\)，所以從其他 .NET 元件存取它們的型別和功能變得更容易也更安全。  因此，純粹組件會比混合組件更容易與其他 .NET 元件相互溝通。  
  
-   非磁片載入：純粹組件能夠 In\-Memory 載入，甚至可以經過資料流處理。  這對於將 .NET 組件當做預存程序 \(Stored Procedure\) 使用而言非常重要。  這與混合組件不同，混合組件由於對 Windows 載入機制具有相依性，因此必須存在於磁碟上才能執行。  
  
-   反映：在混合可執行檔無法反映，不過，純粹組件提供完整的反映 \(Reflection\) 支援。  如需詳細資訊，請參閱[反映](../dotnet/reflection-cpp-cli.md)。  
  
-   裝載可控制性：因為純粹組件只包含 MSIL，所以在裝載 CLR 和修改其預設行為的應用程式中使用時，它的行為會比混合組件更可預測且更有彈性。  
  
### \/clr:pure 的限制  
 本章節涵蓋 **\/clr:pure** 目前未支援的功能內容。  
  
-   純粹組件無法由 Unmanaged 函式呼叫。  因此，純粹組件無法實作 COM 介面或公開 \(Expose\) 原生回呼 \(Callback\)。  純粹組件無法透過 \_\_declspec\(dllexport\) 或 .DEF 檔匯出函式。  此外，以 \_\_clrcall 慣例宣告的函式無法透過 \_\_declspec\(dllimport\) 匯入。  原生模組中的函式可以從純粹組件呼叫，但純粹組件無法公開可原生呼叫的函式，所以公開純粹組件中的功能必須透過混合組件中的 Managed 函式來執行。  如需詳細資訊，請參閱[如何：移轉至 \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)。  
  
-   Visual C\+\+ 中的純模式編譯不支援 ATL 和 MFC 庫。  
  
-   Visual C\+\+ 連結器 \(Linker\) 不接受pure .netmodules 做為輸入。  但是，連結器會接受純粹的 .obj 檔，並且 .obj 檔包含 netmodule 中所含資訊的超集。  如需詳細資訊，請參閱[.netmodule 檔做為連結器輸入](../build/reference/netmodule-files-as-linker-input.md)。  
  
-   編譯器 COM 支援 \(\#import\) 不受支援，因為這會將 Unmanaged 指令引入純粹模組。  
  
-   純粹組件的對齊和例外狀況處理浮點選項無法調整。  因此，\_\_declspec\(align\) 無法使用。  這使得有些標頭檔 \(Header File\)，例如 fpieee.h，與 \/clr:pure 不相容。  
  
-   使用 **\/clr:pure** 進行編譯時，PSDK 中的 GetLastError 函式可以提供未定義的行為。  
  
## 可驗證的 \(\/clr:safe\)  
 **\/clr:safe** 編譯器選項會產生可驗證的組件，例如，以 Visual Basic 和 C\# 撰寫的可驗證組件，以及符合可讓 Common Language Runtime \(CLR\) 保證程式碼未違反目前安全性設定之需求的可驗證組件。  例如，如果安全性設定禁止元件寫入磁碟，則 CLR 可以在執行任何程式碼之前，判斷可驗證的元件是否符合這項標準。  可驗證的組件沒有 CRT 支援 \(CRT 支援可以透過 C 執行階段程式庫的純 MSIL 版本，供純粹組件使用\)。  
  
 可驗證的組件提供下列純粹組件和混合組件的優點：  
  
-   增強的安全性。  
  
-   有些情況必須用到它 \(例如 SQL 元件\)。  
  
-   以後的 Windows 版本會逐漸要求元件和應用程式必須是可驗證的。  
  
 一個缺點是 C\+\+ Interop 功能無法使用。  可驗證的組件不能包含任何 Unmanaged 函式或原生資料型別，甚至是未由 Managed 程式碼參考的也不行。  
  
 儘管使用「安全」這個字眼，使用 **\/clr:safe** 編譯應用程式並不表示沒有錯誤，只代表 CLR 可以在執行階段驗證安全性設定。  
  
 無論組件型別為何，透過 P\/Invoke 從 Managed 組件對原生 DLL 所做的呼叫都會進行編譯，但視安全性設定而定，呼叫可能在執行階段失敗。  
  
> [!NOTE]
>  有一個程式碼案例會通過編譯器，但將會產生無法驗證的組件：使用範圍解析 \(Scope Resolution\) 運算子透過物件執行個體呼叫虛擬函式 \(Virtual Function\)。例如：`MyObj -> A::VirtualFunction();`。  
  
## 請參閱  
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)