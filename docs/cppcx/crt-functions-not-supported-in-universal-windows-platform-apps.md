---
title: 通用 Windows 平台應用程式不支援 CRT 函式
description: 通用 Windows 平臺 apps 中不支援 CRT 函式的參考指南。
ms.date: 04/16/2020
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: cfe5fbc1ce505c255e074dda2c3a240b46754eee
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845714"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>通用 Windows 平台應用程式不支援 CRT 函式

當您建立通用 Windows 平臺 (UWP) 應用程式時，許多 C 執行時間 (CRT) 函式無法使用。 有時可使用因應措施，例如，您可以使用 Windows 執行階段或 Win32 Api。 在其他情況下，因為對應的功能或支援的 Api 不適用於 UWP 應用程式，所以已禁止 CRT 函數。 若要尋找 Windows 執行階段所支援的替代方法，請參閱 [UWP 應用程式中的 Windows Api 替代](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)方法。

下表列出當您建立 UWP 應用程式時無法使用的 CRT 函式。 它會指出適用的任何因應措施。

## <a name="unsupported-crt-functions"></a>不支援的 CRT 函式

|函式|描述|因應措施|
|-|-|-|
|`_beep` `_sleep` `_seterrormode`|這些函式在舊版 CRT 中已過時。 此外，UWP 應用程式沒有對應的 Win32 API。|沒有因應措施。|
|`chdir` `_chdrive` `getcwd`|這些函式已過時或不是安全執行緒。|使用 `_chdir` `_getcwd` 和相關函數。|
|`_cgets` `_cgets_s` `_cgetws` `_cgetws_s` `_cprintf` `_cprintf_l` `_cprintf_p` `_cprintf_p_l` `_cprintf_s` `_cprintf_s_l` `_cputs` `_cputws` `_cscanf` `_cscanf_l` `_cscanf_s` `_cscanf_s_l` `_cwait` `_cwprintf` `_cwprintf_l` `_cwprintf_p` `_cwprintf_p_l` `_cwprintf_s` `_cwprintf_s_l` `_cwscanf` `_cwscanf_l` `_cwscanf_s` `_cwscanf_s_l` `_vcprintf` `_vcprintf_l` `_vcprintf_p` `_vcprintf_p_l` `_vcprintf_s` `_vcprintf_s_l` `_vcwprintf` `_vcwprintf_l` `_vcwprintf_p` `_vcwprintf_p_l` `_vcwprintf_s` `_vcwprintf_s_l` `_getch` `_getch_nolock` `_getche` `_getche_nolock` `_getwch` `_getwch_nolock` `_getwche` `_getwche_nolock` `_putch` `_putch_nolock` `_putwch` `_putwch_nolock` `_ungetch` `_ungetch_nolock` `_ungetwch` `_ungetwch_nolock` `_kbhit` `kbhit` `putch` `cgets` `cprintf` `cputs` `cscanf` `cwait` `getch` `getche` `ungetch`|這些函式可用來從主控台直接讀取或直接寫入至主控台。 UWP 應用程式僅限 GUI，不支援主控台。|沒有因應措施。|
|`getpid` `_getpid` | 這些函式已被取代。|請使用 Win32 API `GetCurrentProcessId`。|
|`_getdiskfree`|無法使用。|請使用 Win32 API `GetDiskFreeSpaceExW`。|
|`_getdrive` `_getdrives`|UWP 應用程式沒有對應的 API。|沒有因應措施。|
|`_inp` `_inpd` `_inpw` `_outp` `_outpd` `_outpw` `inp` `inpd` `inpw` `outp` `outpd` `outpw`|UWP 應用程式不支援連接埠 IO。|沒有因應措施。|
|`_ismbcalnum` `_ismbcalnum_l` `_ismbcalpha` `_ismbcalpha_l` `_ismbcdigit` `_ismbcdigit_l` `_ismbcgraph` `_ismbcgraph_l` `_ismbchira` `_ismbchira_l` `_ismbckata` `_ismbckata_l` `_ismbcl0` `_ismbcl0_l` `_ismbcl1` `_ismbcl1_l` `_ismbcl2` `_ismbcl2_l` `_ismbclegal` `_ismbclegal_l` `_ismbclower` `_ismbclower_l` `_ismbcprint` `_ismbcprint_l` `_ismbcpunct` `_ismbcpunct_l` `_ismbcspace` `_ismbcspace_l` `_ismbcsymbol` `_ismbcsymbol_l` `_ismbcupper` `_ismbcupper_l` `_mbbtombc` `_mbbtombc_l` `_mbbtype` `_mbbtype_l` `_mbccpy` `_mbccpy_l` `_mbccpy_s` `_mbccpy_s_l` `_mbcjistojms` `_mbcjistojms_l` `_mbcjmstojis` `_mbcjmstojis_l` `_mbclen` `_mbclen_l` `_mbctohira` `_mbctohira_l` `_mbctokata` `_mbctokata_l` `_mbctolower` `_mbctolower_l` `_mbctombb` `_mbctombb_l` `_mbctoupper` `_mbctoupper_l` `_mbsbtype` `_mbsbtype_l` `_mbscat` `_mbscat_l` `_mbscat_s` `_mbscat_s_l` `_mbschr` `_mbschr_l` `_mbscmp` `_mbscmp_l` `_mbscoll` `_mbscoll_l` `_mbscpy` `_mbscpy_l` `_mbscpy_s` `_mbscpy_s_l` `_mbscspn` `_mbscspn_l` `_mbsdec` `_mbsdec_l` `_mbsicmp` `_mbsicmp_l` `_mbsicoll` `_mbsicoll_l` `_mbsinc` `_mbsinc_l` `_mbslen` `_mbslen_l` `_mbslwr` `_mbslwr_l` `_mbslwr_s` `_mbslwr_s_l` `_mbsnbcat` `_mbsnbcat_l` `_mbsnbcat_s` `_mbsnbcat_s_l` `_mbsnbcmp` `_mbsnbcmp_l` `_mbsnbcnt` `_mbsnbcnt_l` `_mbsnbcoll` `_mbsnbcoll_l` `_mbsnbcpy` `_mbsnbcpy_l` `_mbsnbcpy_s` `_mbsnbcpy_s_l` `_mbsnbicmp` `_mbsnbicmp_l` `_mbsnbicoll` `_mbsnbicoll_l` `_mbsnbset` `_mbsnbset_l` `_mbsnbset_s` `_mbsnbset_s_l` `_mbsncat` `_mbsncat_l` `_mbsncat_s` `_mbsncat_s_l` `_mbsnccnt` `_mbsnccnt_l` `_mbsncmp` `_mbsncmp_l` `_mbsncoll` `_mbsncoll_l` `_mbsncpy` `_mbsncpy_l` `_mbsncpy_s` `_mbsncpy_s_l` `_mbsnextc` `_mbsnextc_l` `_mbsnicmp` `_mbsnicmp_l` `_mbsnicoll` `_mbsnicoll_l` `_mbsninc` `_mbsninc_l` `_mbsnlen` `_mbsnlen_l` `_mbsnset` `_mbsnset_l` `_mbsnset_s` `_mbsnset_s_l` `_mbspbrk` `_mbspbrk_l` `_mbsrchr` `_mbsrchr_l` `_mbsrev` `_mbsrev_l` `_mbsset` `_mbsset_l` `_mbsset_s` `_mbsset_s_l` `_mbsspn` `_mbsspn_l` `_mbsspnp` `_mbsspnp_l` `_mbsstr` `_mbsstr_l` `_mbstok` `_mbstok_l` `_mbstok_s` `_mbstok_s_l` `_mbsupr` `_mbsupr_l` `_mbsupr_s` `_mbsupr_s_l` `is_wctype`|UWP 應用程式不支援多位元組字串。|請改用 Unicode 字串。|
|`_pclose` `_pipe` `_popen` `_wpopen`|UWP 應用程式無法使用管道功能。|沒有因應措施。|
|`_resetstkoflw`|UWP 應用程式沒有支援的 Win32 API。|沒有因應措施。|
|`_getsystime` `_setsystime`|這些是舊版 CRT 中已過時的 API。 此外，使用者因為缺少權限，所以無法在 UWP 應用程式中設定系統時間。|若只要取得系統時間，請使用 Win32 API `GetSystemTime`。 無法設定系統時間。|
|`_environ``_putenv` `_putenv_s` `_searchenv``_searchenv_s` `_dupenv_s` `_wputenv``_wputenv_s` `_wsearchenv` getenv `_wdupenv_s` `_wenviron` getenv_s `_wgetenv` putenv `_wgetenv_s` `_wsearchenv_s``tzset`|UWP 應用程式無法使用環境變數。|沒有因應措施。 若要設定時區，請使用 `_tzset` 。|
|`_loaddll` `_getdllprocaddr` `_unloaddll`|這些是舊版 CRT 中已過時的函式。 此外，使用者也無法載入相同應用程式封裝中的 Dll。|請使用 Win32 API `LoadPackagedLibrary`、 `GetProcAddress`和 `FreeLibrary` 來載入及使用封裝的 DLL。|
|`_wexecl``_wexecle` `_wexeclp` `_wexeclpe``_wexecv` `_wexecve` `_wexecvp``_wexecvpe` `_execl` `_execle``_execlp` `_execlpe` `_execv``_execve` `_execvp` `_execvpe``_spawnl` `_spawnle` `_spawnlp``_spawnlpe` `_spawnv` `_spawnve``_spawnvp` `_spawnvpe` `_wspawnl``_wspawnle` `_wspawnlp` `_wspawnlpe``_wspawnv` `_wspawnve` `_wspawnvp``_wspawnvpe` `_wsystem` `execl``execle` `execlp` `execlpe``execv` `execve` `execvp``execvpe`' ' spawnl ` ` spawnle ` ` spawnlp ` ` spawnlpe ` ` spawnv ` ` spawnve ` ` spawnvp ` ` spawnvpe ` ` system '|UWP 應用程式中無法使用此功能。 UWP 應用程式無法叫用另一個 UWP 應用程式或傳統型應用程式。|沒有因應措施。|
|`_heapwalk` `_heapadd` `_heapchk` `_heapset` `_heapused`|這些函式通常可用來處理堆積。 不過，UWP 應用程式不支援對應的 Win32 API。 此外，應用程式無法再建立或使用私用堆積。|沒有因應措施。 不過，DEBUG CRT 中可以使用 `_heapwalk` ，但僅限偵錯使用。 這些函數無法用於上傳至 Microsoft Store 的應用程式。|

下列函式可在適用于 UWP 應用程式的 CRT 中使用。 不過，只有在您無法使用對應的 Win32 或 Windows 執行階段 Api （例如移植大型程式碼基底）時，才使用它們：

|Functions|因應措施|
|-|-|
|單一位元組字串函式，例如 `strcat`、 `strcpy`、 `strlwr`等。|將您的 UWP 應用程式設為嚴格的 Unicode，因為所有公開的 Win32 Api 和 Windows 執行階段 Api 都只使用 Unicode 字元集。  單一位元組函式是為了移植大型程式碼基底而保留的，但應該避免此情況。 如果可能的話，應該改用對應的寬字元函數。|
|資料流 IO 和低階檔案 IO 函式，例如 `fopen`、 `open`等。|這些函式是同步的，不建議用於 UWP 應用程式。 在 UWP 應用程式中，請使用非同步 API 開啟、讀取和寫入檔案，以避免鎖定 UI 執行緒。 `Windows::Storage::FileIO` 類別中的 API 即為這類 API 範例。|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Windows 8.x 市集應用程式和 Windows Phone 8.x 應用程式

上述的 Api 和下列 Api 都無法在 Windows 8. x 存放區應用程式和 Windows Phone 8.x 應用程式中使用。

|Functions|描述|因應措施|
|-|-|-|
|`_beginthread` `_beginthreadex` `_endthread` `_endthreadex`|Windows 8.x 市集應用程式中無法使用執行緒 Win32 API。|請改用 `Windows Runtime Windows::System::Threading::ThreadPool` 或 `concurrency::task` 。|
|`_chdir` `_wchdir` `_getcwd` `_getdcwd` `_wgetcwd` `_wgetdcwd`|工作目錄的概念不適用於 Windows 8.x 市集應用程式。|請改用完整路徑。|
|`_isleadbyte_l` `_ismbbalnum`, `_ismbbalnum_l`, `_ismbbalpha`, `_ismbbalpha` `_ismbbalpha_l` `_ismbbgraph` `_ismbbgraph_l` `_ismbbkalnum` `_ismbbkalnum_l` `_ismbbkana` `_ismbbkana_l` `_ismbbkprint` `_ismbbkprint_l` `_ismbbkpunct` `_ismbbkpunct_l` `_ismbblead` `_ismbblead_l` `_ismbbprint` `_ismbbprint_l` `_ismbbpunct` `_ismbbpunct_l` `_ismbbtrail` `_ismbbtrail_l` `_ismbslead` `_ismbslead_l` `_ismbstrail` `_ismbstrail_l` `_mbsdup` `isleadbyte`|Windows 8.x 市集應用程式不支援多位元組字串。|請改用 Unicode 字串。|
|`_tzset`|Windows 8.x 市集應用程式無法使用環境變數。|沒有因應措施。|
|`_get_heap_handle`, `_heapmin`|Windows 8.x 市集應用程式不支援對應的 Win32 API。 此外，應用程式無法再建立私用堆積。|沒有因應措施。 不過，DEBUG CRT 中可以使用 ``_get_heap_handle`` ，但僅限偵錯使用。|
