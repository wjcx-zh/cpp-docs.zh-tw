---
title: "如何：移轉至 /clr:pure (C++/CLI) | Microsoft Docs"
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
  - "/clr 編譯器選項 [C++], 移轉至 /clr:pure"
  - "移轉 [C++], 純的 MSIL"
  - "純的 MSIL [C++], 移植至"
ms.assetid: 5ffb1184-2095-4ade-84aa-4fa6324bc764
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：移轉至 /clr:pure (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題會討論使用 **\/clr:pure** \(如需詳細資訊，請參閱 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)\) 移轉至純 MSIL 時可能會發生的問題。  且會假設要移轉的程式碼目前使用 **\/clr** 選項編譯為混合的組件 \(Assembly\)，因為從 Unmanaged 程式碼到純 MSIL 的移轉路徑並不是直接的路徑。  對於 Unmanaged 程式碼，請在嘗試移轉至純 MSIL 之前先參閱 [如何：移轉至 \/clr](../dotnet/how-to-migrate-to-clr.md)。  
  
## 基本變更  
 純 MSIL 由 MSIL 指令組成，所以包含無法以 MSIL 表示之函式的程式碼會無法編譯。  這包括使用 [\_\_clrcall](../cpp/clrcall.md) 以外的呼叫慣例所定義的函式 \(在純 MSIL 元件中可以叫用非 \_\_clrcall 的函式，但是無法定義此種函式\)。  
  
 若要確保沒有執行階段的錯誤，您應該啟用 C4412 警告。  將 `#pragma warning (default : 4412)` 加入至每個使用 **\/clr:pure** 編譯並在 IJW \(**\/clr\)** 或原生 \(Native\) 程式碼之間傳遞 C\+\+ 型別的編譯單位 \(Compiland\)，啟用 C4412。  如需詳細資訊，請參閱[編譯器警告 \(層級 2\) C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)。  
  
## 架構上的考量  
 一些在[純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)中列出的純 MSIL 組件的限制，和應用程式設計以及移轉策略有很大的關係。  最值得注意的是，純 MSIL 組件與混合的組件不一樣，對於 Unmanaged 模組沒有完整的相容性。  
  
 純 MSIL 組件可以呼叫 Unmanaged 函式，但是無法被 Unmanaged 函式呼叫。  因此，純 MSIL 對於使用 Unmanaged 函式的用戶端程式碼而言是較佳的選擇，而比較不適合由 Unmanaged 函式所使用的伺服器端程式碼。  如果 Unmanaged 函式要使用純 MSIL 組件中包含的功能，則必須使用混合的組件做為介面層。  
  
 使用 ATL 或 MFC 的應用程式不適合移轉到純 MSIL，因為在這個發行版本中不支援這些程式庫。  同樣地，[!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 包含無法在 **\/clr:pure** 下編譯的標頭檔 \(Header File\)  
  
 雖然純 MSIL 組件可以呼叫 Unmanaged 函式，但是這個能力僅限於簡單的 C\-Style 函式。  更複雜之 Unmanaged API 的使用，就會需要以 COM 介面的方式公開 \(Expose\) Unmanaged 功能，或是使用混合的組件，做為 MSIL 和 Unmanaged 元件之間的介面。  使用混合的組件層，是使用會取用回呼 \(Callback\) 函式之 Unmanaged 函式的唯一方法，因為純組件無法提供原生可呼叫的函式做為回呼。  
  
## 應用程式定義域和呼叫慣例  
 雖然純 MSIL 組件可以使用 Unmanaged 功能，但是函式和靜態資料會以不同方式進行處理。  在純組件中，函式會以 [\_\_clrcall](../cpp/clrcall.md) 呼叫慣例實作，而靜態資料會針對每個應用程式定義域儲存一份。  這和 Unmanaged 以及混合組件的預設行為不同，這兩者對於函式會使用 [\_\_cdecl](../cpp/cdecl.md) 呼叫慣例，而靜態資料會針對每個處理序 \(Process\) 儲存一份。  
  
 在純 MSIL \(以及使用 \/clr:safe 所編譯之可驗證的程式碼\) 內容中，這些預設行為是透明的，因為 [\_\_clrcall](../cpp/clrcall.md) 是 CLR 的預設呼叫慣例，且應用程式定義域是 .NET 應用程式中靜態和全域資料的原生範圍。  然而，和 Unmanaged 或混合的元件進行介面作業時，這些不同的函式和全域資料的處理方式會引起問題。  
  
 例如，如果純 MSIL 元件要呼叫 Unmanaged 或混合的 DLL 中的函式，則會使用 DLL 的標頭檔來編譯純組件。  但是，除非每個函式的呼叫慣例在標題中明確指定，不然會假設為 [\_\_clrcall](../cpp/clrcall.md)。  這在稍後會導致執行階段失敗，因為這些函式可能會使用 [\_\_cdecl](../cpp/cdecl.md) 慣例實作。  您可以將 Unmanaged 標頭檔中的函式明確地標記為 [\_\_cdecl](../cpp/cdecl.md)，否則整個 DLL 原始程式碼就必須使用 **\/clr:pure** 重新編譯。  
  
 同樣地，使用 **\/clr:pure** 編譯時，函式指標會假設指向 [\_\_clrcall](../cpp/clrcall.md) 函式。  這些函式指標也必須明確加註正確的呼叫慣例。  
  
 如需詳細資訊，請參閱[應用程式定義域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)。  
  
## 連結的限制  
 Visual C\+\+ 連結器不會嘗試連結混合的和純 OBJ 檔，因為儲存範圍和呼叫慣例都不一樣。  
  
## 請參閱  
 [純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)