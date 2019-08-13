---
title: 標準類型
ms.date: 11/04/2016
f1_keywords:
- __time64_t
- _diskfree_t
- _CRT_DUMP_CLIENT
- _fsize_t
- __timeb64
- File
- __utimeb64
- jmp_buf
- __finddata64_t
- _wfinddata_t
- _finddata_t
- utimbuf64
- wint_t
- wctrans_t
- wctype_t
- _HFILE
- _secerr_handler_func
- clock_t
- fpos_t
- _dev_t
- time64_t
- wfinddata64_t
- stat64
- ldiv_t
- _EXCEPTION_POINTERS
- terminate_function
- size_t
- timeb64
- tm
- _HEAPINFO
- unexpected_function
- _CrtMemState
- _se_translator_function
- sig_atomic_t
- _CRT_REPORT_HOOK
- _complex
- _w_finddatai64_t
- _timeb
- _onexit_t
- _RTC_ErrorNumber
- lconv
- _PNH
- _off_t
- ptrdiff_t
- time_t
- _FPIEEE_RECORD
- _exception
- __w_finddata64_t
- __stat64
- _utimbuf
- __utimbuf64
- div_t
- _CRT_ALLOC_HOOK
- int8_t
- uint8_t
- int16_t
- uint16_t
- int32_t
- uint32_t
- int64_t
- int_least8_t
- uint_least8_t
- int_least16_t
- uint_least16_t
- int_least32_t
- uint_least32_t
- int_least64_t
- uint_least64_t
- int_fast8_t
- uint_fast8_t
- int_fast16_t
- uint_fast16_t
- int_fast32_t
- uint_fast32_t
- int_fast64_t
- uint_fast64_t
- intmax_t
- uintmax_t
helpviewer_keywords:
- __timeb64 type
- tm type
- clock_t type
- intptr_t type
- diskfree_t type
- wctype_t type
- CRT_DUMP_CLIENT type
- sig_atomic_t type
- _PNH type
- time_t type
- wfinddata_t type
- timeb64
- CRT, standard types
- wint_t type
- _RTC_ErrorNumber type
- _diskfree_t type
- _dev_t type
- _wfinddata_t type
- HFILE type
- __utimbuf64 type
- div_t type
- _onexit_t type
- _secerr_handler_func type
- FPIEEE_RECORD type
- HEAPINFO type
- PNH type
- _CRT_ALLOC_HOOK type
- _se_translater_function type
- va_list type
- wctrans_t type
- secerr_handler_func type
- _locale_t type
- timeb type
- lconv type
- utimbuf type
- dev_t type
- unexpected_function typedef
- _complex type
- _off_t type
- off_t type
- RTC_ErrorNumber type
- _FPIEEE_RECORD type
- exception type
- _CRT_REPORT_HOOK type
- _HEAPINFO type
- ldiv_t type
- terminate_function type
- uintptr_t type
- _CRT_DUMP_CLIENT type
- _utimbuf type
- wfinddatai64_t type
- fpos_t type
- wchar_t type
- CRT_ALLOC_HOOK type
- _HFILE type
- __time64_t type
- _timeb type
- CrtMemState type
- __finddata64_t type
- _exception type
- stat type
- onexit_t type
- FILE constant
- _stat type
- finddata_t type
- __wfinddata64_t type
- ptrdiff_t type
- complex types
- _wfinddatai64_t type
- _EXCEPTION_POINTERS type
- jmp_buf type
- se_translater_function type
- size_t type
- EXCEPTION_POINTERS type
- __stat64 type
- _fsize_t type
- CRT_REPORT_HOOK type
- _finddata_t type
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
ms.openlocfilehash: d2b209e29b0690ec2003031e160ce9fd1f749b13
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915308"
---
# <a name="standard-types"></a>標準類型

Microsoft 執行階段程式庫定義下列標準類型和 Typedefs。

### <a name="fixed-width-integral-types-stdinth"></a>固定寬度的整數類資料類型 (stdint.h)

|名稱|對等的內建類型|
|----------|-------------------------------|
|int8\_t、uint8\_t|signed char、unsigned char|
|int16\_t、uint16\_t|short、unsigned short|
|int32\_t、uint32\_t|int、unsigned int|
|int64\_t、uint64\_t|long long、unsigned long long|
|int_least8_t、uint_least8_t|signed char、unsigned char|
|int_least16_t、uint_least16_t|short、unsigned short|
|int_least32_t、uint_least32_t|int、unsigned int|
|int_least64_t、uint_least64_t|long long、unsigned long long|
|int_fast8_t、uint_fast8_t|signed char、unsigned char|
|int_fast16_t、uint_fast16_t|int、unsigned int|
|int_fast32_t、uint_fast32_t|int、unsigned int|
|int_fast64_t、uint_fast64_t|long long、unsigned long long|
|intmax_t、uintmax_t|long long、unsigned long long|

|類型|說明|宣告於|
|----------|-----------------|-----------------|
|`clock_t` (long)|儲存時間值，由[時鐘](../c-runtime-library/reference/clock.md)使用。|TIME.H|
|`_complex` 結構|儲存複數的實數和虛數部分，由 [_cabs](../c-runtime-library/reference/cabs.md) 使用。|MATH.H|
|`_CRT_ALLOC_HOOK`|使用者定義之 hook 函式的類型定義。 用於 [_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)。|CRTDBG.H|
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|將在 [_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md) 被呼叫之回呼函式的類型定義。|CRTDBG.H|
|`_CrtMemState` 結構|提供關於 C 執行階段偵錯堆積的目前狀態資訊。|CRTDBG.H|
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|將在 [_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 被呼叫之回呼函式的類型定義。<br /><br /> 這個函式的參數是：來自回呼函式的報告類型、輸出訊息和傳回值。|CRTDBG.H|
|`dev_t`、`_dev_t` 短的或不帶正負號的整數。|表示裝置控制代碼。|SYS\TYPES.H|
|`_diskfree_t` 結構|包含磁碟機的詳細資訊。 由 [_getdiskfree](../c-runtime-library/reference/getdiskfree.md)使用。 |DOS.H 和 DIRECT.H|
|`div_t`、`ldiv_t` 和 `lldiv_t` 結構|將 [div](../c-runtime-library/reference/div.md)、[ldiv](../c-runtime-library/reference/ldiv-lldiv.md) 和 [lldiv](../c-runtime-library/reference/ldiv-lldiv.md) 所傳回的值分別儲存。|STDLIB.H|
|`errno_t` 整數|用於處理 `errno`錯誤碼的函式傳回類型或參數。|STDDEF.H,<br /><br /> CRTDEFS.H|
|`_exception` 結構|儲存 [_matherr](../c-runtime-library/reference/matherr.md) 的錯誤資訊。|MATH.H|
|`_EXCEPTION_POINTERS`|包含例外狀況記錄。 如需詳細資訊，請參閱 [EXCEPTION_POINTERS](/windows/desktop/api/winnt/ns-winnt-exception_pointers)。|FPIEEE.H|
|`FILE` 結構|儲存有關資料流目前狀態的資訊，用於所有資料流 I/O 作業。|STDIO.H|
|`_finddata_t`、`_wfinddata_t`、`_finddata32_t`、`_wfinddata32_t`、`_finddatai64_t`、`_wfinddatai64_t`、`__finddata64_t`、`__wfinddata64_t`、`__finddata32i64_t`、`__wfinddata32i64_t`、`__finddata64i32_t`、`__wfinddata64i32_t` 結構|儲存 [_findfirst、_wfindfirst 以及相關函式](../c-runtime-library/reference/findfirst-functions.md)和 [_findnext、_wfindnext 以及相關函式](../c-runtime-library/reference/findnext-functions.md)傳回的檔案屬性資訊。 如需結構成員的詳細資訊，請參閱[檔案名稱搜尋函式](../c-runtime-library/filename-search-functions.md)。|IO.H, WCHAR.H|
|`_FPIEEE_RECORD` 結構|包含有關於 IEEE 浮點例外狀況的資訊，會由 [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md) 傳遞至使用者定義的設陷處理常式。|FPIEEE.H|
|`fpos_t` (長整數、`__int64` 或結構，視目標平台而定)|由 [fgetpos](../c-runtime-library/reference/fgetpos.md) 和 [fsetpos](../c-runtime-library/reference/fsetpos.md) 使用，可記錄獨特指定檔案中每個位置的資訊。|STDIO.H|
|`_fsize_t`(不帶正負號長整數)|用來表示檔案的大小。|IO.H,<br /><br /> WCHAR.H|
|`_HEAPINFO` 結構|包含下一個 [_heapwalk](../c-runtime-library/reference/heapwalk.md) 堆積輸入的相關資訊。|MALLOC.H|
|`_HFILE` (void \*)|作業系統檔案控制代碼。|CRTDBG.H|
|`imaxdiv_t`|由 [imaxdiv](../c-runtime-library/reference/imaxdiv.md) 函式傳回的值類型，包含商和餘數。|inttypes.h|
|`ino_t`, `_ino_t` (unsigned short)|用於傳回狀態資訊。|WCHAR.H|
|`intmax_t`|帶正負號的整數類型可以代表任何帶正負號的整數類型的任何值。|stdint.h|
|`intptr_t` (長整數或`__int64`，視目標平台而定)|在 Win32 和 Win64 平台儲存指標 (或 HANDLE)。|STDDEF.H 和其他 include 檔案|
|`jmp_buf` 陣列|由 [setjmp](../c-runtime-library/reference/setjmp.md) 和 [longjmp](../c-runtime-library/reference/longjmp.md) 使用，可儲存和還原程式環境。|SETJMP.H|
|`lconv` 結構|包含不同國家/地區的數值格式化規則。 由 [localeconv](../c-runtime-library/reference/localeconv.md) 使用。|LOCALE.H|
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12` (長雙精度浮點數或不帶正負號的字元陣列)|用來表示長雙精度浮點數值。|STDLIB.H|
|`_locale_t` 結構|儲存目前地區設定值，使用於所有地區設定特定的 C 執行階段程式庫。|CRTDEF.H|
|`mbstate_t`|追蹤多位元組字元轉換的狀態。|WCHAR.H|
|`off_t`, `_off_t` 長整數|表示檔案位移值。|WCHAR.H, SYS\TYPES.H|
|`_onexit_t`,<br /><br /> `_onexit_m_t` 指標|由 [_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md) 傳回。|STDLIB.H|
|指向函式的 `_PNH` 指標|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md) 的引數類型。|NEW.H|
|`ptrdiff_t` (長整數或`__int64`，視目標平台而定)|兩個指標減法運算的結果。|CRTDEFS.H|
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|當呼叫純虛擬函式時所呼叫之回呼函式的類型定義。 由 [_get_purecall_handler、_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) 使用。 `_purecall_handler` 函式應該具有 void 傳回類型。|STDLIB.H|
|`_RTC_error_fn` 類型定義|將處理執行階段錯誤檢查之函式的類型定義。 用於 [_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)。|RTCAPI.H|
|`_RTC_error_fnW` 類型定義|將處理執行階段錯誤檢查之函式的類型定義。 用於 [_RTC_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md)。|RTCAPI.H|
|`_RTC_ErrorNumber` 列舉類型|定義 [_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) 和 [_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md) 的錯誤條件。|RTCAPI.H|
|`_se_translator_function`|轉譯例外狀況之回呼函式的類型定義。 第一個參數是例外狀況代碼，第二個參數則是例外狀況記錄。 由 [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) 使用。|EH.H|
|`sig_atomic_t` 整數|可以修改為不可部分完成實體的物件類型，出現非同步中斷亦然，可搭配 [signal](../c-runtime-library/reference/signal.md) 使用。|SIGNAL.H|
|`size_t` (unsigned __int64 或不帶正負號的整數，視目標平台而定)|`sizeof` 運算子的結果。|CRTDEFS.H 和其他 include 檔案|
|`_stat` 結構|包含由 [_stat](../c-runtime-library/reference/stat-functions.md) 和 [_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) 傳回的檔案狀態資訊。|SYS\STAT.H|
|`__stat64` 結構|包含由 [_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)、[_stat64](../c-runtime-library/reference/stat-functions.md) 和 [_wstat64](../c-runtime-library/reference/stat-functions.md) 傳回的檔案狀態資訊。|SYS\STAT.H|
|`_stati64` 結構|包含由 [_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)、[_stati64](../c-runtime-library/reference/stat-functions.md) 和 [_wstati64](../c-runtime-library/reference/stat-functions.md) 傳回的檔案狀態資訊。|SYS\STAT.H|
|`terminate_function` 類型定義|當呼叫 [terminate](../c-runtime-library/reference/terminate-crt.md) 時，所呼叫之回呼函式的類型定義。 由 [set_terminate](../c-runtime-library/reference/set-terminate-crt.md) 使用。|EH.H|
|`time_t` (__int64 或長整數)|表示 [mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[time](../c-runtime-library/reference/time-time32-time64.md)、[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) 和 [gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 中的時間值。 從 1970 年 1 月 1 日 0:00 UTC 開始到現在的秒數。 如果已定義 _USE_32BIT_TIME_T，則 `time_t` 為長整數。 如果未定義，則為 64 位元整數。|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time32_t` (長整數)|表示 [mktime、_mktime32、_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) and [localtime、_localtime32、_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) 中的時間值。|CRTDEFS.H, SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time64_t` (`__int64`)|表示 [mktime、_mktime32、_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)、[_ctime64、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)、[_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) and [_time64](../c-runtime-library/reference/time-time32-time64.md) 中的時間值。|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`_timeb` 結構|由 [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [_ftime_s、_ftime32_s、_ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) 使用，可儲存目前系統時間。|SYS\TIMEB.H|
|`__timeb32` 結構|由 [_ftime、_ftime32、_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [_ftime_s、_ftime32_s、_ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) 使用，可儲存目前系統時間。|SYS\TIMEB.H|
|`__timeb64` 結構|由 [_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [_ftime_s、_ftime32_s、_ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) 使用，可儲存目前系統時間。|SYS\TIMEB.H|
|`tm` 結構|由 [asctime、_wasctime](../c-runtime-library/reference/asctime-wasctime.md)、[asctime_s、_wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)、[gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[gmtime_s、_gmtime32_s、_gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)、[localtime、_localtime32、_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)、[localtime_s、_localtime32_s、_localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)、[mktime、_mktime32、_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) 和 [strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 使用，可儲存和擷取時間資訊。|TIME.H|
|`uintmax_t`|不帶正負號的整數類型，可以代表任何不帶正負號的整數類型的任何值。|stdint.h|
|`uintptr_t` (長整數或`__int64`，視目標平台而定)|`intptr_t`的不帶正負號的整數或 __int64 版本。|STDDEF.H 和其他 include 檔案|
|`unexpected_function`|當呼叫 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 時，所呼叫之回呼函式的類型定義。 由 [set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md) 使用。|EH.H|
|`_utimbuf` 結構|儲存 [_utime、_wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 和 [_futime、_futime32、_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) 所使用的檔案存取和修改時間，以變更檔案修改日期。|SYS\UTIME.H|
|`_utimbuf32` 結構|儲存 [_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 和 [_futime、_futime32、_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) 所使用的檔案存取和修改時間，以變更檔案修改日期。|SYS\UTIME.H|
|`__utimbuf64` 結構|由 [_utime64、_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 和 [_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) 使用，可儲存目前的時間。|SYS\UTIME.H|
|`va_list` 結構|用來保存 [va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 和 [va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 巨集所需的資訊。 呼叫的函式，宣告可當做引數傳遞給另一個函式類型 `va_list` 的變數。|STDARG.H,<br /><br /> CRTDEFS.H|
|`wchar_t` 寬字元|對於撰寫國際市場的可攜程式非常有用。|STDDEF.H, STDLIB.H,<br /><br /> CRTDEFS.H,<br /><br /> SYS\STAT.H|
|`wctrans_t` 整數|表示地區設定特定的字元對應。|WCTYPE.H|
|`wctype_t` 整數|可以表示任何語言字元集的所有字元。|WCHAR.H,<br /><br /> CRTDEFS.H|
|`wint_t` 整數|可以保留任何寬字元或寬檔案結尾值的資料物件類型。|WCHAR.H,<br /><br /> CRTDEFS.H|

## <a name="see-also"></a>另請參閱

[C 執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)
