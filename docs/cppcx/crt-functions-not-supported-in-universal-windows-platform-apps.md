---
title: "通用 Windows 平台應用程式不支援 CRT 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 15
---
# 通用 Windows 平台應用程式不支援 CRT 函式
當您建置通用 Windows 平台 \(UWP\) 應用程式時，許多 C 執行階段 \(CRT\) 函式都無法使用。 在某些情況下有因應措施可用，例如您可以使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 或 Win32 API。 不過，在其他情況下則已禁止使用 CRT 函式，因為 UWP 應用程式無法使用對應至這些函式的功能或支援的 API。  
  
 下表列出當您建置 UWP 應用程式時無法使用的 CRT 函式，並指出任何可行的因應措施。  
  
## 不支援的 CRT 函式  
  
||||  
|-|-|-|  
|\_beep \_sleep \_seterrormode|這些函式在舊版 CRT 中已過時。 此外，UWP 應用程式沒有對應的 Win32 API。|沒有因應措施。|  
|chdir \_chdrive getcwd|這些函式已過時或不是安全執行緒。|Use \_chdir、\_getcwd 和相關函式。|  
|\_cgets \_cgets\_s \_cgetws \_cgetws\_s \_cprintf \_cprintf\_l \_cprintf\_p \_cprintf\_p\_l \_cprintf\_s \_cprintf\_s\_l \_cputs \_cputws \_cscanf \_cscanf\_l \_cscanf\_s \_cscanf\_s\_l \_cwait \_cwprintf \_cwprintf\_l \_cwprintf\_p \_cwprintf\_p\_l \_cwprintf\_s \_cwprintf\_s\_l \_cwscanf \_cwscanf\_l \_cwscanf\_s \_cwscanf\_s\_l \_vcprintf \_vcprintf\_l \_vcprintf\_p \_vcprintf\_p\_l \_vcprintf\_s \_vcprintf\_s\_l \_vcwprintf \_vcwprintf\_l \_vcwprintf\_p \_vcwprintf\_p\_l \_vcwprintf\_s \_vcwprintf\_s\_l \_getch \_getch\_nolock \_getche \_getche\_nolock \_getwch \_getwch\_nolock \_getwche \_getwche\_nolock \_putch \_putch\_nolock \_putwch \_putwch\_nolock \_ungetch \_ungetch\_nolock \_ungetwch \_ungetwch\_nolock \_kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|這些函式可用來從主控台直接讀取或直接寫入至主控台。 UWP 應用程式僅限 GUI，不支援主控台。|沒有因應措施。|  
|getpid|此函式已被取代。|請使用 \_getpid 或 Win32 API `GetCurrentProcessId()`。|  
|\_getdiskfree|不適用。|請使用 Win32 API `GetDiskFreeSpaceExW()`。|  
|\_getdrive \_getdrives|UWP 應用程式沒有對應的 API。|沒有因應措施。|  
|\_inp \_inpd \_inpw \_outp \_outpd \_outpw inp inpd inpw outp outpd outpw|UWP 應用程式不支援連接埠 IO。|沒有因應措施。|  
|\_ismbcalnum \_ismbcalnum\_l \_ismbcalpha \_ismbcalpha\_l \_ismbcdigit \_ismbcdigit\_l \_ismbcgraph \_ismbcgraph\_l \_ismbchira \_ismbchira\_l \_ismbckata \_ismbckata\_l \_ismbcl0 \_ismbcl0\_l \_ismbcl1 \_ismbcl1\_l \_ismbcl2 \_ismbcl2\_l \_ismbclegal \_ismbclegal\_l \_ismbclower \_ismbclower\_l \_ismbcprint \_ismbcprint\_l \_ismbcpunct \_ismbcpunct\_l \_ismbcspace \_ismbcspace\_l \_ismbcsymbol \_ismbcsymbol\_l \_ismbcupper \_ismbcupper\_l \_mbbtombc \_mbbtombc\_l \_mbbtype \_mbbtype\_l \_mbccpy \_mbccpy\_l \_mbccpy\_s \_mbccpy\_s\_l \_mbcjistojms \_mbcjistojms\_l \_mbcjmstojis \_mbcjmstojis\_l \_mbclen \_mbclen\_l \_mbctohira \_mbctohira\_l \_mbctokata \_mbctokata\_l \_mbctolower \_mbctolower\_l \_mbctombb \_mbctombb\_l \_mbctoupper \_mbctoupper\_l \_mbsbtype \_mbsbtype\_l \_mbscat \_mbscat\_l \_mbscat\_s \_mbscat\_s\_l \_mbschr \_mbschr\_l \_mbscmp \_mbscmp\_l \_mbscoll \_mbscoll\_l \_mbscpy \_mbscpy\_l \_mbscpy\_s \_mbscpy\_s\_l \_mbscspn \_mbscspn\_l \_mbsdec \_mbsdec\_l \_mbsicmp \_mbsicmp\_l \_mbsicoll \_mbsicoll\_l \_mbsinc \_mbsinc\_l \_mbslen \_mbslen\_l \_mbslwr \_mbslwr\_l \_mbslwr\_s \_mbslwr\_s\_l \_mbsnbcat \_mbsnbcat\_l \_mbsnbcat\_s \_mbsnbcat\_s\_l \_mbsnbcmp \_mbsnbcmp\_l \_mbsnbcnt \_mbsnbcnt\_l \_mbsnbcoll \_mbsnbcoll\_l \_mbsnbcpy \_mbsnbcpy\_l \_mbsnbcpy\_s \_mbsnbcpy\_s\_l \_mbsnbicmp \_mbsnbicmp\_l \_mbsnbicoll \_mbsnbicoll\_l \_mbsnbset \_mbsnbset\_l \_mbsnbset\_s \_mbsnbset\_s\_l \_mbsncat \_mbsncat\_l \_mbsncat\_s \_mbsncat\_s\_l \_mbsnccnt \_mbsnccnt\_l \_mbsncmp \_mbsncmp\_l \_mbsncoll \_mbsncoll\_l \_mbsncpy \_mbsncpy\_l \_mbsncpy\_s \_mbsncpy\_s\_l \_mbsnextc \_mbsnextc\_l \_mbsnicmp \_mbsnicmp\_l \_mbsnicoll \_mbsnicoll\_l \_mbsninc \_mbsninc\_l \_mbsnlen \_mbsnlen\_l \_mbsnset \_mbsnset\_l \_mbsnset\_s \_mbsnset\_s\_l \_mbspbrk \_mbspbrk\_l \_mbsrchr \_mbsrchr\_l \_mbsrev \_mbsrev\_l \_mbsset \_mbsset\_l \_mbsset\_s \_mbsset\_s\_l \_mbsspn \_mbsspn\_l \_mbsspnp \_mbsspnp\_l \_mbsstr \_mbsstr\_l \_mbstok \_mbstok\_l \_mbstok\_s \_mbstok\_s\_l \_mbsupr \_mbsupr\_l \_mbsupr\_s \_mbsupr\_s\_l is\_wctype|UWP 應用程式不支援多位元組字串。|請改用 Unicode 字串。|  
|\_pclose \_pipe \_popen \_wpopen|UWP 應用程式無法使用管道功能。|沒有因應措施。|  
|\_resetstkoflw|UWP 應用程式沒有支援的 Win32 API。|沒有因應措施。|  
|\_getsystime \_setsystime|這些是舊版 CRT 中已過時的 API。 此外，使用者因為缺少權限，所以無法在 UWP 應用程式中設定系統時間。|若只要取得系統時間，請使用 Win32 API `GetSystemTime`。 無法設定系統時間。|  
|\_environ \_putenv \_putenv\_s \_searchenv \_searchenv\_s \_dupenv\_s \_wputenv \_wputenv\_s \_wsearchenv getenv getenv\_s putenv \_wdupenv\_s \_wenviron \_wgetenv \_wgetenv\_s \_wsearchenv\_s tzset|UWP 應用程式無法使用環境變數。|沒有因應措施。 若要設定時區，請使用 \_tzset。|  
|\_loaddll \_getdllprocaddr \_unloaddll|這些是舊版 CRT 中已過時的函式。 此外，除非來自相同的應用程式封裝，否則使用者無法載入 DLL。|請使用 Win32 API `LoadPackagedLibrary`、`GetProcAddress` 和 `FreeLibrary` 來載入及使用封裝的 DLL。|  
|\_wexecl \_wexecle \_wexeclp \_wexeclpe \_wexecv \_wexecve \_wexecvp \_wexecvpe \_execl \_execle \_execlp \_execlpe \_execv \_execve \_execvp \_execvpe \_spawnl \_spawnle \_spawnlp \_spawnlpe \_spawnv \_spawnve \_spawnvp \_spawnvpe \_wspawnl \_wspawnle \_wspawnlp \_wspawnlpe \_wspawnv \_wspawnve \_wspawnvp \_wspawnvpe \_wsystem execl execle execlp execlpe execv execve execvp execvpe spawnl spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|UWP 應用程式中無法使用此功能。 UWP 應用程式無法叫用另一個 UWP 應用程式或傳統型應用程式。|沒有因應措施。|  
|\_heapwalk \_heapadd \_heapchk \_heapset \_heapused|這些函式通常可用來處理堆積。 不過，UWP 應用程式不支援對應的 Win32 API。 此外，應用程式無法再建立或使用私用堆積。|沒有因應措施。 不過，DEBUG CRT 中可以使用 `_heapwalk`，但僅限偵錯使用。 這些函式無法用於上傳至 Windows 市集的應用程式。|  
  
 下列函式可在適用於 UWP 應用程式的 CRT 中使用，但是只有在無法使用對應的 Win32 或 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] API 時才能使用，例如，當您移植大型程式碼基底時。  
  
|||  
|-|-|  
|單一位元組字串函式，例如 `strcat`、`strcpy`、`strlwr` 等。|讓 UWP 應用程式完全採用 Unicode，因為所有公開的 Win32 API 和 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] API 只使用 Unicode 字元集。 單一位元組函式已保留下來移植大型程式碼基底，但是在其他情況下應該避免使用，而且應該盡可能改用對應的萬用字元函式。|  
|資料流 IO 和低階檔案 IO 函式，例如 `fopen`、`open` 等。|這些是同步函式，不建議 UWP 應用程式使用。 在 UWP 應用程式中，請使用非同步 API 開啟、讀取和寫入檔案，以避免鎖定 UI 執行緒。`Windows::Storage::FileIO` 類別中的 API 即為這類 API 範例。|  
  
## Windows 8.x 市集應用程式和 Windows Phone 8.x 應用程式  
 除了上述 API 之外，下列 API 也不適用於 Windows 8.x 市集應用程式和 Windows Phone 8.x 應用程式。  
  
||||  
|-|-|-|  
|\_beginthread \_beginthreadex \_endthread \_endthreadex|Windows 8.x 市集應用程式中無法使用執行緒 Win32 API。|請改用 `Windows Runtime Windows::System::Threading::ThreadPool` 或 `concurrency::task`。|  
|\_chdir \_wchdir \_getcwd \_getdcwd \_wgetcwd \_wgetdcwd|工作目錄的概念不適用於 Windows 8.x 市集應用程式。|請改用完整路徑。|  
|\_getpid|這個函式在舊版 CRT 中已過時。|請使用 Win32 API `GetCurrentProcessId()`。|  
|\_isleadbyte\_l \_ismbbalnum, \_ismbbalnum\_l, \_ismbbalpha, \_ismbbalpha \_ismbbalpha\_l \_ismbbgraph \_ismbbgraph\_l \_ismbbkalnum \_ismbbkalnum\_l \_ismbbkana \_ismbbkana\_l \_ismbbkprint \_ismbbkprint\_l \_ismbbkpunct \_ismbbkpunct\_l \_ismbblead \_ismbblead\_l \_ismbbprint \_ismbbprint\_l \_ismbbpunct \_ismbbpunct\_l \_ismbbtrail \_ismbbtrail\_l \_ismbslead \_ismbslead\_l \_ismbstrail \_ismbstrail\_l \_mbsdup isleadbyte|Windows 8.x 市集應用程式不支援多位元組字串。|請改用 Unicode 字串。|  
|\_tzset|Windows 8.x 市集應用程式無法使用環境變數。|沒有因應措施。|  
|\_get\_heap\_handle、\_heapmin|Windows 8.x 市集應用程式不支援對應的 Win32 API。 此外，應用程式無法再建立私用堆積。|沒有因應措施。 不過，DEBUG CRT 中可以使用 `_get_heap_handle`，但僅限偵錯使用。|