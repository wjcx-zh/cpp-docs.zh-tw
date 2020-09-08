---
title: CRT 中的全域狀態
description: 描述通用 C 執行時間中共用全域狀態的處理方式。
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: d1c787147ea3df36ce120837ef5b2c68b1bf58b1
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554665"
---
# <a name="global-state-in-the-crt"></a>CRT 中的全域狀態

通用 C 執行時間中的某些函式 (UCRT) 使用全域狀態。 例如， `setlocale()` 設定整個程式的地區設定，這會影響數位分隔符號、文字字碼頁等等。

在應用程式與 OS 之間，不會共用 UCRT 的全域狀態。 例如，如果您的應用程式呼叫 `setlocale()` ，就不會影響使用 C 執行時間的任何 OS 元件的地區設定，反之亦然。

## <a name="os-specific-versions-of-crt-functions"></a>CRT 函式的作業系統特定版本

在 UCRT 中，與全域狀態互動的函式具有 "對應項" 函式，並在前面加上 `_o_` 。 例如：

- `setlocale()` 影響應用程式特定的全域狀態。
- `_o_setlocale()` 影響所有 OS 元件所共用的全域狀態，但不會影響應用程式。

這些「對應項」函式的唯一差異在於，當它們讀取/寫入全域 CRT 狀態時，作業系統特定版本 (亦即，以) 開頭的版本會 `_o_` 使用全域狀態的作業系統複本，而不是應用程式的全域狀態複本。

這些函式的作業系統特定版本位於中 `ucrt.osmode.lib` 。 例如，的作業系統特定版本 `setlocale()` 為 `_o_setlocale()`

有兩種方式可從應用程式的 CRT 狀態隔離元件的 CRT 狀態：

- 使用編譯器選項/MT (release) 或 MTd (debug) ，以靜態方式連結您的元件。 如需詳細資訊，請參閱 [/md、/mt、/ld](../build/reference/md-mt-ld-use-run-time-library.md)。 請注意，靜態連結可能會大幅增加二進位檔大小。
- 從 Windows 10 20H2 開始，藉由動態連結至 CRT 來取得 CRT 狀態隔離，但 (以 _o_) 開頭的函式呼叫作業系統模式匯出。 若要呼叫作業系統模式匯出，請以先前的方式靜態連結，但是 (發行) 或 (debug，請使用連結器選項來忽略靜態 UCRT， `/NODEFAULTLIB:libucrt.lib` 或 `/NODEFAULTLIB:libucrtd.lib` debug) 如需詳細資料，請參閱 [/NODEFAULTLIB (忽略程式庫 ](../build/reference/nodefaultlib-ignore-libraries.md)) 。 並加入 `ucrt.osmode.lib` 至連結器輸入。

> [!Note]
> 在原始程式碼中，寫入 `setlocale()` ，而不是 `_o_setlocale()` 。 當您連結時 `ucrt.osmode.lib` ，連結器會自動取代作業系統特定版本的函式。 也就是說， `setlocale()` 會將取代為 `_o_setlocale()` 。

連結 `ucrt.osmode.lib` 會停用一些只能在應用程式模式中使用的 UCRT 呼叫。 嘗試呼叫這些將會導致連結錯誤。

## <a name="global-state-affected-by-appos-separation"></a>受應用程式/OS 分隔影響的全域狀態

受應用程式和 OS 狀態分隔影響的全域狀態包括：

- [地區設定資料](locale.md)
- 以[信號](reference/signal.md)設定的信號處理常式
- [終止的終止](reference/set-terminate-crt.md)常式設定
- [errno 和 _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- [Rand](reference/rand.md)和[>srand](reference/srand.md)所使用的亂數字產生狀態
- 傳回使用者不需要釋放之緩衝區的函式：   [strtok、wcstok、_mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam、_wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime、_wasctime](reference/asctime-wasctime.md) [gmtime、_gmtime32、_gmtime64](reference/gmtime-gmtime32-gmtime64.md) [_fcvt](reference/fcvt.md) [_ecvt](reference/ecvt.md) [strerror、_strerror、_wcserror、__wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- _Putch 所使用的緩衝區 [，_putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) 和 [_set_new_mode](reference/set-new-mode.md)
- [fmode] (text-and-binary-mode-file-i-o.md) 
- [時區資訊](time-management.md)

## <a name="see-also"></a>另請參閱

[C 執行時間程式庫參考](c-run-time-library-reference.md)
