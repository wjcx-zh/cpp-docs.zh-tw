---
title: C + + （DllImport 屬性） 中使用明確的 PInvoke |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 82215e4815d25dd116cf930be9cc0f40da761bf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169500"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>在 C++ 中使用明確的 PInvoke (DllImport 屬性)
.NET Framework 提供明確的平台叫用 （或 PInvoke） 功能與`Dllimport`屬性，以允許受管理的應用程式呼叫 Dll 內封裝的 unmanaged 函式。 Unmanaged 的 Api 會封裝為 Dll，以及不提供原始程式碼的情況下需要明確的 PInvoke。 呼叫 Win32 函式，例如，需要 PInvoke。 否則，請使用隱含 P {叫用，請參閱 <<c0> [ 使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)如需詳細資訊。  
  
 PInvoke 的運作方式是使用<xref:System.Runtime.InteropServices.DllImportAttribute>。 這個屬性，會為其第一個引數的 dll 名稱，將會使用每個 DLL 進入點的函式宣告之前放置。 函式的簽章必須符合的 dll 匯出的函式的名稱 (但可以隱含地執行某些類型轉換，藉由定義`DllImport`宣告以受管理的型別。)  
  
 結果是必要的轉換程式碼 （或 thunk） 包含每個原生 DLL 函式的 managed 的進入點和簡單的資料轉換。 透過這些的進入點 DLL 然後可以呼叫 managed 函式。 完全管理將程式碼插入模組產生的 PInvoke。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理字串](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理結構](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理陣列](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理函式指標](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## <a name="see-also"></a>另請參閱  
 [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)