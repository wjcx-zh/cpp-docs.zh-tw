---
title: "純粹的和可驗證的程式碼 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7bcaabb9f0a696a5eb7b01c4bd78757681e4e6a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pure-and-verifiable-code-ccli"></a>純粹的和可驗證的程式碼 (C++/CLI)
對於.NET 程式設計，Visual c + + 支援三種不同類型的元件和應用程式建立： 混合的、 純粹的和可驗證。 這三個都是透過[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項。  
  
## <a name="remarks"></a>備註  
 如需可驗證的組件的詳細資訊，請參閱：  
  
-   [混合的、純粹的和可驗證的功能比較 (C++/CLI)](../dotnet/mixed-pure-and-verifiable-feature-comparison-cpp-cli.md)  
  
-   [如何： 移轉至 /clr: pure (C + + /CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [如何：建立可驗證的 C++ 專案 (C++/CLI)](../dotnet/how-to-create-verifiable-cpp-projects-cpp-cli.md)  
  
-   [如何： 移轉至 /clr: safe (C + + /CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)  
  
-   [使用可驗證的組件搭配 SQL Server (C++/CLI)](../dotnet/using-verifiable-assemblies-with-sql-server-cpp-cli.md)  
  
-   [安全性最佳做法](../security/security-best-practices-for-cpp.md)  
  
-   [將專案從混合模式轉換為純中繼語言](../dotnet/converting-projects-from-mixed-mode-to-pure-intermediate-language.md)  
  
## <a name="mixed-clr"></a>混合 (/ clr)  
 混合的組件 (以編譯**/clr**)、 包含 unmanaged 和 managed 組件，讓它們使用.NET 功能，但仍然包含 unmanaged 程式碼。 這可讓應用程式和元件更新，而不需要重寫整個專案中使用.NET 功能。 使用 Visual c + + 混合這種方式中的 managed 和 unmanaged 程式碼會呼叫 c + + Interop。 如需詳細資訊，請參閱[混合 （原生和 Managed） 組件](../dotnet/mixed-native-and-managed-assemblies.md)和[原生和.NET 互通性](../dotnet/native-and-dotnet-interoperability.md)。  
  
## <a name="pure-clrpure"></a>純 (/ /clr: pure)  
 純粹組件 (以編譯**/clr: pure**) 可以包含這兩個原生與 managed 資料類型，但只有 managed 函式。 混合的組件，例如純組件可讓透過 P/Invoke 的原生 dll interop (請參閱[c + + （DllImport 屬性） 中使用明確 PInvoke](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md))，但是不使用 c + + Interop 功能。 此外，純粹組件無法匯出因為純組件使用中的進入點是可從原生函式呼叫的函式[__clrcall](../cpp/clrcall.md)呼叫慣例。  
  
### <a name="advantages-of-clrpure"></a>優點 /clr: pure  
  
-   較佳的效能： 純粹組件只包含 MSIL，因為沒有原生函式，並因此的 managed/unmanaged 轉換所需。 （透過 P/Invoke 的函式呼叫是此規則的例外狀況）。  
  
-   AppDomain 感知： Managed 函式和 CLR 資料型別存在於`Application Domains`，這會影響其可視性和存取範圍。 純粹組件是否為網域感知 (__declspec ([appdomain](../cpp/appdomain.md)) 會針對每種類型隱含)，存取其類型和功能的其他.NET 元件會更方便且更安全。 如此一來，純粹組件與混合的組件比其他.NET 元件相互操作更輕鬆地所示。  
  
-   非磁碟載入： 純粹組件可以載入記憶體中，即使資料流處理。 這是不可或缺的預存程序為使用.NET 組件。 這不同於混合的組件，因為相依於 Windows 載入機制，必須存在於磁碟才能執行。  
  
-   反映： 它不可能對混合的可執行檔、 其反映純粹組件可提供完整的反映支援而。 如需詳細資訊，請參閱[反映 (C + + /CLI)](../dotnet/reflection-cpp-cli.md)。  
  
-   主機可： 純粹組件只包含 MSIL，因為它們的行為更如預期般和以彈性的方式與 CLR 混合組件時應用程式中使用該主機並修改其預設行為。  
  
### <a name="limitations-of-clrpure"></a>限制的 /clr: pure  
 本節涵蓋的功能目前不支援**/clr: pure**。  
  
-   純粹組件無法由 unmanaged 函式呼叫。 因此純粹組件無法實作 COM 介面或公開原生的回呼。 純粹組件無法匯出透過 __declspec （dllexport） 函式或。DEF 檔案。 此外，宣告的函式與\__clrcall 慣例無法透過匯入\__declspec(dllimport)。 原生模組中的函式可以呼叫從純的組件，但純粹組件無法顯示原生呼叫的函式，如此一來公開純的組件中的功能必須透過在混合的組件中的 managed 函式來完成。 請參閱[How to： 移轉至 /clr: pure (C + + CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)如需詳細資訊。  
  
-   ATL 和 MFC 程式庫不會受到純模式編譯 Visual c + + 中。  
  
-   Visual C++ 連結器不接受以純 .netmodule 做為輸入。 不過，連結器中，接受純.obj 檔案，而且.obj 檔中包含的 netmodule 中所包含的超集。 請參閱[.netmodule 檔作為連結器輸入](../build/reference/netmodule-files-as-linker-input.md)如需詳細資訊。  
  
-   不支援編譯器 COM 支援 (#import)，因為這可能會引入 unmanaged 純組件的指示。  
  
-   浮點數的對齊和例外狀況處理的選項不是可調整的純粹組件。 如此一來，您無法使用有。 這會轉譯一些標頭檔，例如 fpieee.h，相容以 /clr: pure。  
  
-   在 PSDK GetLastError 函式可提供未定義的行為，以編譯時**/clr: pure**。  
  
## <a name="verifiable-clrsafe"></a>驗證 (/: safe)  
 **/Clr: safe**編譯器選項會產生可驗證的組件，例如所撰寫的 Visual Basic 和 C# 中，可讓 common language runtime (CLR)，以確保程式碼沒有違反目前需求不符合安全性設定。 例如，如果安全性設定禁止寫入至磁碟元件，CLR 可以判斷可驗證的元件是否符合此準則，再執行任何程式碼。 沒有可驗證的組件的 CRT 支援。 （CRT 支援是可透過純的 MSIL 版本的 C 執行階段程式庫的純粹組件）。  
  
 可驗證的組件會提供這些優點純粹的和混合的組件：  
  
-   增強的安全性。  
  
-   某些情況下需要它 （例如，SQL 元件）。  
  
-   元件和可驗證的應用程式，逐漸將需要未來的 Windows 版本。  
  
 一個缺點是沒有提供 c + + interop 功能。 可驗證的組件不能包含任何 unmanaged 函式或原生資料類型，即使它們並未參考的 managed 程式碼。  
  
 使用的"safe"這個字，儘管編譯應用程式與**/clr: safe**並不表示沒有錯誤，它只代表 CLR，可以在執行階段驗證的安全性設定。  
  
 組件不論類型為何，從 managed 組件對原生 Dll，透過 P/Invoke 的呼叫將會編譯，但可能無法在執行階段視安全性設定而定。  
  
> [!NOTE]
>  一個程式碼撰寫的狀況，將會通過編譯器，但會導致無法驗證的組件： 呼叫虛擬函式，透過使用範圍解析運算子的物件執行個體。  例如：`MyObj -> A::VirtualFunction();`。  
  
## <a name="see-also"></a>請參閱  
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)