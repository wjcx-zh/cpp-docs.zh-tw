---
title: 延遲載入 Dll 的條件約束 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40774d6307eb9b423ebd4fd303a48acbd87eda24
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42571674"
---
# <a name="constraints-of-delay-loading-dlls"></a>延遲載入 DLL 的條件約束
關於匯入的延遲載入有一些限制。  
  
-   不支援匯入資料。 解決方法是使用 `LoadLibrary` (或在您知道延遲載入 Helper 已載入 DLL 之後使用 `GetModuleHandle`) 和 `GetProcAddress` 自行明確地處理資料匯入。  
  
-   不支援延遲載入 Kernel32.dll。 延遲載入 Helper 需要這個 DLL 才能執行延遲載入。  
  
-   [繫結](../../build/reference/binding-imports.md)轉送的點不支援項目。  
  
-   如果有發生在延遲載入 DLL 進入點的各處理序初始化，延遲載入 DLL 可能不會造成相同的處理序行為。 其他情況包括靜態 TLS （執行緒本機儲存體） 使用宣告[__declspec （thread)](../../cpp/thread.md)，這不會處理透過載入 DLL 時`LoadLibrary`。 動態 TLS (使用 `TlsAlloc`、`TlsFree`、`TlsGetValue` 和 `TlsSetValue`) 仍可用於靜態或延遲載入 DLL。  
  
-   第一次呼叫函式之後，應該對匯入的函式重新初始化靜態 (全域) 函式指標。 這是因為第一次使用函式指標時將會指向 Thunk。  
  
-   目前在使用一般匯入機制時，無法只從 DLL 延遲載入特定程序。  
  
-   不支援自訂呼叫慣例 (例如在 x86 架構上使用條件碼)。 此外，在任何平台上都不會儲存浮點暫存器。 如果您的自訂 Helper 常式或攔截常式使用浮點類型，它們需要在具有使用浮點參數之暫存器呼叫慣例的電腦上，完整地儲存和還原浮點狀態。 如果您呼叫的 CRT 函式在 help 函式的數值資料處理器 (NDP) 堆疊上使用浮點參數，那麼在延遲載入 CRT DLL 時請小心。  
  
## <a name="see-also"></a>另請參閱  
 [延遲載入 Dll 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [LoadLibrary 函式](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [GetModuleHandle 函式](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [GetProcAddress 函式](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [TlsAlloc 函式](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)   
 [TlsFree 函式](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsfree)   
 [TlsGetValue 函式](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)   
 [TlsSetValue 函式](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)