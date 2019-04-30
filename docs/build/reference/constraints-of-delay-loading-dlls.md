---
title: 延遲載入 DLL 的條件約束
ms.date: 11/04/2016
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
ms.openlocfilehash: e37890fcd757a52ddeff0ccd79289bbc0c35e042
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344170"
---
# <a name="constraints-of-delay-loading-dlls"></a>延遲載入 DLL 的條件約束

關於匯入的延遲載入有一些限制。

- 不支援匯入資料。 解決方法是使用 `LoadLibrary` (或在您知道延遲載入 Helper 已載入 DLL 之後使用 `GetModuleHandle`) 和 `GetProcAddress` 自行明確地處理資料匯入。

- 不支援延遲載入 Kernel32.dll。 延遲載入 Helper 需要這個 DLL 才能執行延遲載入。

- [繫結](binding-imports.md)轉送的點不支援項目。

- 如果有發生在延遲載入 DLL 進入點的各處理序初始化，延遲載入 DLL 可能不會造成相同的處理序行為。 其他情況包括靜態 TLS （執行緒本機儲存體） 使用宣告[__declspec （thread)](../../cpp/thread.md)，這不會處理透過載入 DLL 時`LoadLibrary`。 動態 TLS (使用 `TlsAlloc`、`TlsFree`、`TlsGetValue` 和 `TlsSetValue`) 仍可用於靜態或延遲載入 DLL。

- 第一次呼叫函式之後，應該對匯入的函式重新初始化靜態 (全域) 函式指標。 這是因為第一次使用函式指標時將會指向 Thunk。

- 目前在使用一般匯入機制時，無法只從 DLL 延遲載入特定程序。

- 不支援自訂呼叫慣例 (例如在 x86 架構上使用條件碼)。 此外，在任何平台上都不會儲存浮點暫存器。 如果您的自訂 Helper 常式或攔截常式使用浮點類型，它們需要在具有使用浮點參數之暫存器呼叫慣例的電腦上，完整地儲存和還原浮點狀態。 如果您呼叫的 CRT 函式在 help 函式的數值資料處理器 (NDP) 堆疊上使用浮點參數，那麼在延遲載入 CRT DLL 時請小心。

## <a name="see-also"></a>另請參閱

[延遲載入 DLL 的連結器支援](linker-support-for-delay-loaded-dlls.md)<br/>
[LoadLibrary 函式](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)<br/>
[GetModuleHandle 函式](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulehandlea)<br/>
[GetProcAddress 函式](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress)<br/>
[TlsAlloc 函式](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)<br/>
[TlsFree 函式](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsfree)<br/>
[TlsGetValue 函式](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)<br/>
[TlsSetValue 函式](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)
