---
title: CRT 程式庫功能 | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- MSVCR71.dll
- libraries [C++], multithreaded
- library files, run-time
- LIBCMT.lib
- LIBCP.lib
- LIBCPMT.lib
- run-time libraries, C
- CRT, release versions
- MSVCP71.dll
- LIBC.lib
- libraries [C++]
- libraries [C++], run-time
- linking [C++], libraries
ms.assetid: a889fd39-807d-48f2-807f-81492612463f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b20fa6862a835ca913a2865a651112584966af3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="crt-library-features"></a>CRT 程式庫功能

本主題討論組成 C 執行階段程式庫的各種 .lib 檔案，以及其相關聯的編譯器選項與前置處理器指示詞。

## <a name="c-run-time-libraries-crt"></a>C 執行階段程式庫 (CRT)

C 執行階段程式庫 (CRT) 是納入 ISO C99 標準程式庫之 C++ 標準程式庫的一部分。 實作 CRT 的 Visual C++ 程式庫支援機器碼開發，以及混合的機器碼與受控碼。 CRT 的所有版本都支援多執行緒開發。 大部分程式庫都支援靜態連結和動態連結，靜態連結可將程式庫直接連結到您的程式碼，而動態連結則可讓您的程式碼使用通用 DLL 檔案。

自 Visual Studio 2015 起，CRT 已重構為新的二進位檔。 通用 CRT (UCRT) 包含標準 C99 CRT 程式庫所匯出的函式和全域變數。 UCRT 現在是 Windows 元件，而且隨附於 Windows 10。 靜態程式庫、DLL 匯入程式庫和 UCRT 的標頭檔現在都位於 Windows 10 SDK 中。 當您安裝 Visual C++ 時，Visual Studio 安裝程式會安裝使用 UCRT 所需的一部分 Windows 10 SDK。 您可以在 Visual Studio 2015 及以上版本支援的任何 Windows 版本上使用 UCRT。 您可以針對 Windows 10 以外的 Windows 支援版本，使用 vcredist 來轉散發。 如需詳細資訊，請參閱 [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md)。

下表列出實作 UCRT 的程式庫。

|程式庫|相關聯的 DLL|特性|選項|前置處理器指示詞|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libucrt.lib|無|以靜態方式將 UCRT 連結到您的程式碼。|**/MT**|_MT|
|libucrtd.lib|無|用於靜態連結的偵錯版 UCRT。 不可轉散發。|**/MTd**|_DEBUG、_MT|
|ucrt.lib|ucrtbase.dll|UCRT 的 DLL 匯入程式庫。|**/MD**|_MT、_DLL|
|ucrtd.lib|ucrtbased.dll|偵錯版 UCRT 的 DLL 匯入程式庫。 不可轉散發。|**/MDd**|_DEBUG、_MT、_DLL|

內含 Visual C++ CRT 實作特定程式碼的 vcruntime 程式庫，例如例外狀況處理和偵錯支援、執行階段檢查和類型資訊、實作詳細資料和特定擴充程式庫函式。 這個程式庫會因所使用的編譯器版本而有所不同。

下表列出實作 vcruntime 程式庫的程式庫。

|程式庫|相關聯的 DLL|特性|選項|前置處理器指示詞|
|-------------|--------------------|---------------------|------------|-----------------------------|
|libvcruntime.lib|無|以靜態方式連結到您的程式碼。|**/MT**|_MT|
|libvcruntimed.lib|無|用於靜態連結的偵錯版本。 不可轉散發。|**/MTd**|_MT、_DEBUG|
|vcruntime.lib|vcruntime\<版本>.dll|vcruntime 的 DLL 匯入程式庫。|**/MD**|_MT、_DLL|
|vcruntimed.lib|vcruntime\<版本>d.dll|偵錯 vcruntime 的 DLL 匯入程式庫。 不可轉散發。|**/MDd**|_DEBUG、_MT、_DLL|

根據 CRT 程式庫為靜態或動態連結，為機器碼、Managed 程式碼或混合程式碼，初始化 CRT 的程式碼會位於上述幾個程式庫的其中一個。 這段程式碼會處理 CRT 啟始、內部每個執行緒資料的初始化及終止。 它會因所使用的編譯器版本而有所不同。 這個程式庫一律會以靜態方式連結，即使使用動態連結的 UCRT 亦然。

下表列出實作 CRT 初始化和終止的程式庫。

|程式庫|特性|選項|前置處理器指示詞|
|-------------|---------------------|------------|-----------------------------|
|LIBCMT.lib|以靜態方式將原生 UCRT 啟始連結到您的程式碼。|**/MT**|_MT|
|libcmtd.lib|以靜態方式連結到偵錯版的原生 CRT 啟始。 不可轉散發。|**/MTd**|_DEBUG、_MT|
|msvcrt.lib|搭配 DLL UCRT 和 vcruntime 使用之原生 CRT 啟始的靜態程式庫。|**/MD**|_MT、_DLL|
|msvcrtd.lib|搭配 DLL UCRT 和 vcruntime 使用之偵錯版原生 CRT 啟始的靜態程式庫。 不可轉散發。|**/MDd**|_DEBUG、_MT、_DLL|
|msvcmrt.lib|搭配 DLL UCRT 和 vcruntime 使用之混合原生與 Managed CRT 啟始的靜態程式庫。|**/clr**||
|msvcmrtd.lib|搭配 DLL UCRT 和 vcruntime 使用之偵錯版混合原生與 Managed CRT 啟始的靜態程式庫。 不可轉散發。|**/clr**||
|msvcurt.lib|**已被取代** 純粹 Managed CRT 的靜態程式庫。|**/clr:pure**||
|msvcurtd.lib|**已被取代** 偵錯版之純粹 Managed CRT 的靜態程式庫。 不可轉散發。|**/clr:pure**||

如果您從命令列連接程式，但未使用編譯器選項來指定 C 執行階段程式庫，連結器將會使用靜態連結的 CRT 程式庫：libcmt.lib、libvcruntime.lib 和 libucrt.lib。

使用靜態連結的 CRT 表示 C 執行階段程式庫所儲存的任何狀態資訊，都會是 CRT 執行個體的本機資訊。 例如，如果您在使用靜態連結的 CRT 時使用 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)，`strtok` 剖析器的位置與連結到其他靜態 CRT 執行個體之同一處理序 (但位於不同的 DLL 或 EXE) 中程式碼所用的 `strtok` 狀態無關。 反之，動態連結的 CRT 在動態連結到該 CRT 之處理序中，會共用所有程式碼的狀態。 如果您使用更安全的新函式版本，就無須考慮此問題。例如 `strtok_s` 就沒有此問題。

因為藉由連結到靜態 CRT 所建置的 DLL，會具備自己的 CRT 狀態，因此除非您已確實了解此結果並有此需要，否則不建議在 DLL 中以靜態方式連結到 CRT。 例如，如果您在載入連結到其自身靜態 CRT 之 DLL 的可執行檔中呼叫 [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) ，轉譯器將攔截不到 DLL 中的程式碼所產生的任何硬體例外狀況，而只會攔截到主要可執行檔中的程式碼所產生的硬體例外狀況。

如果您使用 **/clr** 編譯器參數，您的程式碼將會連結到靜態程式庫 msvcurt.lib。 靜態程式庫會提供 Managed 程式碼與原生 CRT 之間的 Proxy。 請勿將靜態連結的 CRT ( **/MT** 或 **/MTd** 選項) 與 **/clr**並用。 請改用動態連結程式庫 (**/MD** 或 **/MDd**)。

如需使用 CRT 與 **/clr** 的詳細資訊，請參閱[混合 (機器與受控) 組件](../dotnet/mixed-native-and-managed-assemblies.md)。

若要建置應用程式的偵錯版本，必須定義 [_DEBUG](../c-runtime-library/debug.md) 旗標，且應用程式必須連結到這些程式庫的任一偵錯版本。 如需如何使用程式庫檔案之偵錯版本的詳細資訊，請參閱 [CRT 偵錯技術](/visualstudio/debugger/crt-debugging-techniques)。

本版 CRT 不完全符合 C99 標準。 具體而言，\<tgmath.h> 標頭和 CX_LIMITED_RANGE/FP_CONTRACT pragma 巨集並不受支援。 像是標準 IO 函式的參數規範意義等特定項目，預設會使用舊版解譯。 您可以使用 /Zc 編譯器一致性選項並指定連結器選項，來控制程式庫一致性的某些層面。

## <a name="c-standard-library"></a>C++ 標準程式庫

|C++ 標準程式庫|特性|選項|前置處理器指示詞|
|----------------------------|---------------------|------------|-----------------------------|
|libcpmt.lib|多執行緒、靜態連結|**/MT**|_MT|
|msvcprt.lib|多執行緒的動態連結 (MSVCP*版本*.dll 的匯入程式庫)|**/MD**|_MT、_DLL|
|libcpmtd.lib|多執行緒、靜態連結|**/MTd**|_DEBUG、_MT|
|msvcprtd.lib|多執行緒的動態連結 (MSVCP*版本*D.DLL 的匯入程式庫)|**/MDd**|_DEBUG、_MT、_DLL|

當您建置專案的發行版本時，預設會依據您選擇的編譯器選項 (多執行緒、DLL、/clr)，連結其中一個基本的 C 執行階段程式庫 (libcmt.lib、msvcmrt.lib、msvcrt.lib)。 如果您在程式碼中包含其中一個 [C++ 標準程式庫標頭檔](../standard-library/cpp-standard-library-header-files.md)，Visual C++ 就會在編譯時間自動連入 C++ 標準程式庫。 例如: 

```cpp
#include <ios>
```

為了要能夠和二進位碼相容，單一匯入程式庫會指定多個 DLL 檔案。 版本更新會導入 *dot 程式庫*，其為其他引入新程式庫功能的 Dll。 例如，Visual Studio 2017 15.6 版會導入 msvcp140_1.dll 以支援其他標準程式庫功能，完全不會中斷由 msvcp140.dll 支援的 ABI。 工具組中所包含的 Visual Studio 2017 15.6 版 msvcprt.lib 匯入程式庫，支援這兩個 Dll，且此版本的 vcredist 會安裝這兩個 Dll。 送出後，dot 程式庫即會有固定的 ABI，且絕對不會相依於更新版的程式庫。

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>如果應用程式使用多種 CRT 版本，將會發生什麼問題？

無論您是否使用不同版本的 Visual C++，只要有多個 DLL 或 EXE，就可能會有多個 CRT。 例如，以靜態方式將 CRT 連結到多個 DLL 就可能會出現相同的問題。 已指示遇到此靜態 CRT 問題的開發人員使用 **/MD** 編譯，如此就能使用 CRT DLL。 如果您的 DLL 跨 DLL 界限傳遞 CRT 資源，您可能會遇到 CRT 不相符的問題，而且必須使用 Visual C++ 重新編譯專案。

如果您的程式使用多種版本的 CRT，在跨 DLL 界限傳遞特定 CRT 物件 (例如檔案控制代碼、地區設定及環境變數) 時，必須特別留意。 如需涉及問題及解決方法的相關資訊，請參閱[跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)。

## <a name="see-also"></a>另請參閱

[C 執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)
