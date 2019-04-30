---
title: 在 C++ 中使用明確的 PInvoke (DllImport 屬性)
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
ms.openlocfilehash: ee9d77920f04f7eba5112c66a906b02b7fc4a658
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384422"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>在 C++ 中使用明確的 PInvoke (DllImport 屬性)

.NET Framework 會提供明確的平台叫用 （或 PInvoke） 功能與`Dllimport`屬性，以允許呼叫 unmanaged 函式的 Dll 內封裝的 managed 應用程式。 需要的情況下，需要 unmanaged 的 Api 會封裝為 Dll 原始程式碼沒有明確的 PInvoke。 呼叫 Win32 函式，例如，需要 PInvoke。 否則，請使用隱含的 P {叫用; 請參閱[使用C++Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)如需詳細資訊。

PInvoke 的運作方式是使用<xref:System.Runtime.InteropServices.DllImportAttribute>。 這個屬性，會使用第一個引數為 DLL 的名稱，被放在將用於每個 DLL 進入點函式宣告之前。 函式的簽章必須符合由 DLL 匯出的函式的名稱 (但可以隱含地執行一些類型轉換，藉由定義`DllImport`根據 managed 類型的宣告。)

結果是必要的轉換程式碼 （或 thunk） 包含每個原生 DLL 函式的 managed 的進入點和簡單資料轉換。 透過這些進入點 dll，就可以呼叫 managed 函式。 完全受控的 PInvoke 結果插入模組的程式碼。

## <a name="in-this-section"></a>本節內容

- [從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)

- [如何：使用 PInvoke 從受控程式碼呼叫原生 DLL](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)

- [如何：使用 PInvoke 封送處理字串](../dotnet/how-to-marshal-strings-using-pinvoke.md)

- [如何：使用 PInvoke 封送處理結構](../dotnet/how-to-marshal-structures-using-pinvoke.md)

- [如何：使用 PInvoke 封送處理陣列](../dotnet/how-to-marshal-arrays-using-pinvoke.md)

- [如何：使用 PInvoke 封送處理函式指標](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)

- [如何：使用 PInvoke 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)

## <a name="see-also"></a>另請參閱

[從 Managed 程式碼呼叫原生函式](../dotnet/calling-native-functions-from-managed-code.md)
