---
title: _nolock 函式
ms.date: 11/04/2016
helpviewer_keywords:
- _nolock functions
- nolock functions
ms.assetid: 7d651d87-38d2-4303-9897-fdb5f7a3e899
ms.openlocfilehash: 149c93c2488ae2b113af397c9e216aa1aeb4c6ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551238"
---
# <a name="nolock-functions"></a>_nolock 函式

這些是不會執行任何鎖定的函式。 它們專供需要最大效能的使用者使用。 如需詳細資訊，請參閱[多執行緒程式庫效能](../c-runtime-library/multithreaded-libraries-performance.md)。

只有在程式確實為單一執行緒，或是會自行進行鎖定的情況下，您才應該使用 _nolock 函式。

## <a name="no-lock-routines"></a>沒有鎖定常式

[_fclose_nolock](../c-runtime-library/reference/fclose-nolock.md)

[_fflush_nolock](../c-runtime-library/reference/fflush-nolock.md)

[_fgetc_nolock、_fgetwc_nolock](../c-runtime-library/reference/fgetc-nolock-fgetwc-nolock.md)

[_fread_nolock](../c-runtime-library/reference/fread-nolock.md)

[_fseek_nolock、_fseeki64_nolock](../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)

[_ftell_nolock、_ftelli64_nolock](../c-runtime-library/reference/ftell-nolock-ftelli64-nolock.md)

[_fwrite_nolock](../c-runtime-library/reference/fwrite-nolock.md)

[_getc_nolock、_getwc_nolock](../c-runtime-library/reference/getc-nolock-getwc-nolock.md)

[_getch_nolock、_getwch_nolock](../c-runtime-library/reference/getch-nolock-getwch-nolock.md)

[_getchar_nolock、_getwchar_nolock](../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md)

[_getche_nolock、_getwche_nolock](../c-runtime-library/reference/getche-nolock-getwche-nolock.md)

[_getdcwd_nolock、_wgetdcwd_nolock](../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md)

[_putc_nolock、_putwc_nolock](../c-runtime-library/reference/putc-nolock-putwc-nolock.md)

[_putch_nolock、_putwch_nolock](../c-runtime-library/reference/putch-nolock-putwch-nolock.md)

[_putchar_nolock、_putwchar_nolock](../c-runtime-library/reference/putchar-nolock-putwchar-nolock.md)

[_ungetc_nolock、_ungetwc_nolock](../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)

[_ungetch_nolock、_ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)

## <a name="see-also"></a>請參閱

[輸入和輸出](../c-runtime-library/input-and-output.md)<br/>
[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
