---
title: "在 C++ 中使用明確的 PInvoke (DllImport 屬性) | Microsoft Docs"
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
  - "C++ Interop, 平台叫用"
  - "資料封送處理 [C++], 平台叫用"
  - "Interop [C++], 平台叫用"
  - "封送處理 [C++], 平台叫用"
  - "平台叫用 [C++], C++ 中的封送處理"
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 C++ 中使用明確的 PInvoke (DllImport 屬性)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

.NET Framework 為 `Dllimport` 屬性 \(Attribute\) 提供明確的平台叫用 \(或 PInvoke\) 功能，可讓 Managed 應用程式呼叫封裝於 DLL 內部的 Unmanaged 函式。  當 API 封裝成 DLL 且無法取得原始程式碼時，就需要使用明確的 PInvoke。  例如，呼叫 Win32 函式時必須使用 PInvoke，  其他情形則使用隱含的 P{Invoke。如需詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 PInvoke 是利用 <xref:System.Runtime.InteropServices.DllImportAttribute> 來運作。  這個屬性使用 DLL 的名稱做為第一個引數，它應該置於每個要使用之 DLL 進入點 \(Entry Point\) 的函式宣告之前。  函式的簽章 \(Signature\) 必須與 DLL 匯出的函式名稱相符 \(但是就 Managed 型別而言，某些型別轉換可以藉由定義 `DllImport` 宣告隱含地執行\)。  
  
 結果就是會為每個原生 \(Native\) DLL 函式 \(包含必要的轉換代碼 \(或 Thunk\) 和簡單的資料轉換\) 產生 Managed 進入點。  然後，Managed 函式就可以透過這些進入點，呼叫到 DLL。  插入模組做為 PInvoke 結果的程式碼完全屬於 Managed 程式碼，並且 **\/clr**、**\/clr:pure** 和 **\/clr:safe** 等編譯支援明確 PInvoke。  如需詳細資訊，請參閱[純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## 在本節中  
  
-   [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理字串](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理結構](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理陣列](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理函式指標](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## 請參閱  
 [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)