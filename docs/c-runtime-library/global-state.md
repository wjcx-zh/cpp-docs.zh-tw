---
title: CRT 的全球狀態
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 1b32e8d4f23d2361a52a9b81150ef7c5c7422761
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745359"
---
# <a name="global-state-in-the-crt"></a>CRT 的全球狀態

通用 C 運行時 (UCRT) 中的某些函數使用全域狀態。 例如,`setlocale()`為整個程式設置區域設置,這會影響數位分隔符、文本代碼頁等。

UCRT 的全域狀態不會在應用程式和作業系統之間共用。 例如,如果應用程式調用`setlocale()`,則不會影響使用 C 運行時的任何作業系統元件的區域設置,反之亦然。

## <a name="os-specific-versions-of-crt-functions"></a>特定於作業系統的 CRT 功能版本

在 UCRT 中,與全域狀態互動的函數具有「雙」函數,`_o_`以預綴於 。 例如：

- `setlocale()`影響特定於應用的全域狀態。
- `_o_setlocale()`影響所有作業系統元件共用的全域狀態,但不會影響應用。

這些「孿生」函數的唯一區別是,當他們讀取/寫入全域 CRT 狀態時,特定於作業系統的版本(即`_o_`以 開頭的版本)使用全域狀態的 OS 副本,而不是應用的全域狀態副本。

這些函數的特定於作業系統的版本在中`ucrt.osmode.lib`。 例如,特定於作業系統的版本`setlocale()`是`_o_setlocale()`

有兩種方法可以將元件的 CRT 狀態與應用的 CRT 狀態隔離開來:

- 使用編譯器選項 /MT(發佈)或 MTd(調試)靜態連結元件。 有關詳細資訊,請參閱[/MD、/MT、/LD](https://docs.microsoft.com/cpp/build/reference/md-mt-ld-use-run-time-library?view=vs-2019)。 請注意,靜態連結可以大大增加二進位大小。
- 從 Windows 10 20H2 開始,透過動態連結到 CRT 但調用 OS 模式匯出(以_o_開頭的函數)來獲取 CRT 狀態隔離。 要調用 OS 模式匯出,請像以前一樣靜態連結,但使用連結`/NODEFAULTLIB:libucrt.lib`器選項 (`/NODEFAULTLIB:libucrtd.lib`發佈)或 (調試)忽略靜態 UCRT,請參閱[/NODEFAULTLIB(忽略庫)](https://docs.microsoft.com/cpp/build/reference/nodefaultlib-ignore-libraries?view=vs-2019)瞭解詳細資訊。 並添加到`ucrt.osmode.lib`鏈接器輸入。

> [!Note]
> 在原始碼中,寫入`setlocale()``_o_setlocale()`而不是 。 當您連結到`ucrt.osmode.lib`時 ,連結器將自動替換特定於作業系統的函數版本。 也就是說,`setlocale()`將取代`_o_setlocale()`為 。

連結將`ucrt.osmode.lib`禁用僅在應用模式下可用的某些 UCRT 調用。 嘗試調用這些將導致連結錯誤。

## <a name="global-state-affected-by-appos-separation"></a>受應用/作業系統分離影響的全域狀態

受應用和作業系統狀態分離影響的全域狀態包括:

- [區域設定資料](locale.md)
- 信號處理程式由[信號](reference/signal.md)設定
- 結束設定的[終止](reference/set-terminate-crt.md)例程
- [厄諾和_doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- [蘭特](reference/rand.md)與[srand](reference/srand.md)使用的隨機數產生狀態
- 返回使用者不需要釋放的緩衝區的功能[:strtok、wcstok、_mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam、_wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime、_wasctime](reference/asctime-wasctime.md) [gmtime、_gmtime32、_gmtime64_fcvt_ecvt](reference/gmtime-gmtime32-gmtime64.md)[_fcvt](reference/fcvt.md)[_ecvt](reference/ecvt.md)[串錯誤、_strerror、_wcserror、__wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- [_putch使用的緩衝區,_putwch](reference/putch-putwch.md)
- [_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md)和[_set_new_mode](reference/set-new-mode.md)
- [fmode](text-and-binary-mode-file-i-o.md)
- [時區資訊](time-management.md)

## <a name="see-also"></a>另請參閱

[C 執行時庫參考](c-run-time-library-reference.md)
