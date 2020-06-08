---
title: 連結選項
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- legacy_stdio_float_rounding.obj
- loosefpmath.obj
- smallheap.obj
- fp10.obj
- nochkclr.obj
- chkstk.obj
- pcommode.obj
- pnoenv.obj
- link options [C++]
- invalidcontinue.obj
- pnothrownew.obj
- pwsetargv.obj
- pinvalidcontinue.obj
- wsetargv.obj
- binmode.obj
- setargv.obj
- noarg.obj
- pnewmode.obj
- commode.obj
- pthreadlocale.obj
- pbinmode.obj
- threadlocale.obj
- pnoarg.obj
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
ms.openlocfilehash: 146722fb0dd3a4fc774ede692808b1e6bfb1e5c7
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84506854"
---
# <a name="link-options"></a>連結選項

CRT lib 目錄包含多個小型物件檔案，不需要變更任何程式碼即可啟用特定的 CRT 功能。 它們稱之為「連結選項」，因為它們必須加入連結器命令列才能使用。

這些物件的純粹 CLR 模式版本在 Visual Studio 2015 中已被取代，而在 Visual Studio 2017 中已不受支援。 請使用機器碼與 /clr 程式碼的一般版本。

|原生和 /clr|純的模式|說明|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|將預設檔案轉譯模式設為二進位。 請參閱 [_fmode](../c-runtime-library/fmode.md)。|
|chkstk.obj|n/a|不使用 CRT 時提供堆疊檢查和 alloca 支援。|
|commode.obj|pcommode.obj|將全域認可旗標設定為「認可」。 請參閱 [fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md) 和 [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)。|
|exe_initialize_mta.lib|n/a|在 EXE 啟動期間將 MTA Apartment 初始化，以允許在全域智慧指標中使用 COM 物件。 因為此選項會在關機期間流失 MTA Apartment 參考，所以請勿將其用於 DLL。 連結至此項目相當於包含 combase.h 及定義 _EXE_INITIALIZE_MTA。 |
|fp10.obj|n/a|將預設的精確度控制變更為 64 位元。 請參閱[浮點支援](../c-runtime-library/floating-point-support.md)。|
|invalidcontinue.obj|pinvalidcontinue.obj|設定不做任何動作的預設無效的參數處理常式，表示傳遞至 CRT 函式的無效參數只會設定 errno 並傳回錯誤結果。|
|legacy_stdio_float_rounding .obj|n/a|已修正與 Windows 10 19041 通用 C 執行時間一起列印的浮點值（例如，使用[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)時）。 它現在會正確地舍入完全可以顯示的浮點數，並遵循[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)所要求的浮點舍入。 此行為更新適用于 Visual Studio 2019 16.2 版和更新版本。 舊版的行為會用於舊版的 Visual Studio，或藉由提供此連結選項。|
|loosefpmath.obj|n/a|確保浮點程式碼容許異常值。|
|newmode.obj|pnewmode.obj|使 [malloc](../c-runtime-library/reference/malloc.md) 在失敗時呼叫新的處理常式。 請參閱 [_set_new_mode](../c-runtime-library/reference/set-new-mode.md)、[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)、[calloc](../c-runtime-library/reference/calloc.md) 和 [realloc](../c-runtime-library/reference/realloc.md)。|
|noarg.obj|pnoarg.obj|停用所有的 argc 和 argv 處理。|
|nochkclr.obj|n/a|不執行任何動作。 從專案中移除。|
|noenv.obj|pnoenv.obj|停用建立 CRT 快取環境。|
|nothrownew.obj|pnothrownew.obj|啟用 CRT 的非擲回版本新功能。 請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)。|
|setargv.obj|psetargv.obj|啟用命令列引數萬用字元展開。 請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。|
|threadlocale.obj|pthreadlocale.obj|所有的新執行緒預設啟用每個執行緒地區設定。|
|wsetargv.obj|pwsetargv.obj|啟用命令列引數萬用字元展開。 請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。|

## <a name="see-also"></a>另請參閱

- [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
