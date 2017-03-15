---
title: "CRT 函式的安全性增強版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRT, 安全性增強"
  - "安全性 [CRT]"
  - "安全性增強 CRT"
ms.assetid: f87e5a01-4cb2-4379-9e8f-d4693828c55a
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# CRT 函式的安全性增強版本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行階段程式庫常式已有更安全的版本可用。 如需有關 CRT 中安全性增強功能的進一步資訊，請參閱[CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。  
  
 **安全函式**  
  
|CRT 函式|安全性增強功能|用法|  
|------------|-------------|--------|  
|[\_access、\_waccess](../c-runtime-library/reference/access-waccess.md)|[\_access\_s、\_waccess\_s](../c-runtime-library/reference/access-s-waccess-s.md)|判斷檔案存取權限|  
|[\_alloca](../c-runtime-library/reference/alloca.md)|[\_malloca](../c-runtime-library/reference/malloca.md)|在堆疊上配置記憶體|  
|[asctime、\_wasctime](../c-runtime-library/reference/asctime-wasctime.md)|[asctime\_s、\_wasctime\_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|將時間從類型 `struct tm` 轉換為字元字串|  
|[bsearch](../c-runtime-library/reference/bsearch.md)|[bsearch\_s](../c-runtime-library/reference/bsearch-s.md)|對經過排序的陣列執行二進位搜尋|  
|已過時的函式|[\_cgets\_s、\_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|從主控台取得字元字串|  
|[\_chsize](../c-runtime-library/reference/chsize.md)|[\_chsize\_s](../c-runtime-library/reference/chsize-s.md)|變更檔案大小|  
|[clearerr](../c-runtime-library/reference/clearerr.md)|[clearerr\_s](../c-runtime-library/reference/clearerr-s.md)|重設資料流的錯誤指標|  
|[\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[\_controlfp\_s](../c-runtime-library/reference/controlfp-s.md)|取得和設定浮點控制字組|  
|[\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|格式化並列印到主控台|  
|[\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)|[\_cscanf\_s、\_cscanf\_s\_l、\_cwscanf\_s、\_cwscanf\_s\_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|從主控台讀取格式化資料|  
|[ctime、\_ctime32、\_ctime64、\_wctime、\_wctime32、\_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)|[\_ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|將時間從類型 `time_t`, `__time32_t` 或 `__time64_t` 轉換為字元字串|  
|[\_ecvt](../c-runtime-library/reference/ecvt.md)|[\_ecvt\_s](../c-runtime-library/reference/ecvt-s.md)|將 `double` 數字轉換為字串|  
|[\_fcvt](../c-runtime-library/reference/fcvt.md)|[\_fcvt\_s](../c-runtime-library/reference/fcvt-s.md)|將浮點數轉換為字串|  
|[fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)|[fopen\_s、\_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|開啟檔案|  
|[fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|將格式化資料列印至資料流|  
|[fread](../c-runtime-library/reference/fread.md)|[fread\_s](../c-runtime-library/reference/fread-s.md)|從檔案讀取|  
|[\_fread\_nolock](../c-runtime-library/reference/fread-nolock.md)|[\_fread\_nolock\_s](../c-runtime-library/reference/fread-nolock-s2.md)|從檔案讀取，而不使用多執行緒寫入鎖定|  
|[freopen、\_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)|[freopen\_s、\_wfreopen\_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|重新開啟檔案|  
|[fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[fscanf\_s、\_fscanf\_s\_l、fwscanf\_s、\_fwscanf\_s\_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|從資料流讀取格式化資料|  
|[\_ftime、\_ftime32、\_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md)|[\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|取得目前時間|  
|[\_gcvt](../c-runtime-library/reference/gcvt.md)|[\_gcvt\_s](../c-runtime-library/reference/gcvt-s.md)|將浮點值轉換為字串，並將其儲存在緩衝區中|  
|[getenv、\_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)|[getenv\_s、\_wgetenv\_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|從目前環境取得值|  
|已過時的函式|[gets\_s、\_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md)|無法從 `stdin` 資料流取得行|  
|[gmtime、\_gmtime32、\_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)|[\_gmtime32\_s、\_gmtime64\_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|將時間從類型 `time_t` 轉換為 `struct``tm`，或從類型 `__time64_t` 轉換為 `struct tm`。|  
|[\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)|[\_itoa\_s、\_i64toa\_s、\_ui64toa\_s、\_itow\_s、\_i64tow\_s、\_ui64tow\_s](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|將整數轉換為字串|  
|[\_lfind](../c-runtime-library/reference/lfind.md)|[\_lfind\_s](../c-runtime-library/reference/lfind-s.md)|執行所指定索引鍵的線性搜尋|  
|[localtime，\_localtime32，\_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)|[localtime\_s、\_localtime32\_s、\_localtime64\_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|將時間從類型 `time_t` 轉換為 `struct tm`，或從類型 `__time64_t` 轉換為具有本機更正的 `struct tm`|  
|[\_lsearch](../c-runtime-library/reference/lsearch.md)|[\_lsearch\_s](../c-runtime-library/reference/lsearch-s.md)|執行值的線性搜尋；若找不到，則加入到清單的結尾|  
|[\_ltoa、\_ltow](../c-runtime-library/reference/ltoa-ltow.md)|[\_ltoa\_s、\_ltow\_s](../c-runtime-library/reference/ltoa-s-ltow-s.md)|將長整數轉換為字串|  
|[\_makepath、\_wmakepath](../c-runtime-library/reference/makepath-wmakepath.md)|[\_makepath\_s、\_wmakepath\_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|從元件建立路徑名稱|  
|[\_mbccpy、\_mbccpy\_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md)|[\_mbccpy\_s、\_mbccpy\_s\_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|在字串之間複製多位元組字元|  
|[\_mbsnbcat、\_mbsnbcat\_l](../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)|[\_mbsnbcat\_s、\_mbsnbcat\_s\_l](../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)|最多可將一個多位元組字元字串的前 `n` 個位元組附加到另一個多位元組字元字串之前|  
|[\_mbsnbcpy、\_mbsnbcpy\_l](../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)|[\_mbsnbcpy\_s、\_mbsnbcpy\_s\_l](../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)|將字串的 `n` 個位元組複製到目的地字串|  
|[\_mbsnbset、\_mbsnbset\_l](../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)|[\_mbsnbset\_s、\_mbsnbset\_s\_l](../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md)|將字串的前 `n` 個位元組設為指定的字元|  
|[mbsrtowcs](../c-runtime-library/reference/mbsrtowcs.md)|[mbsrtowcs\_s](../c-runtime-library/reference/mbsrtowcs-s.md)|將多位元組字元字串轉換為對應的寬字元字串|  
|[mbstowcs、\_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)|[mbstowcs\_s、\_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|將多位元組字元序列轉換為對應的寬字元序列|  
|[memcpy、wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)|[memcpy\_s、wmemcpy\_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|在緩衝區之間複製字元|  
|[memmove、wmemmove](../c-runtime-library/reference/memmove-wmemmove.md)|[memmove\_s、wmemmove\_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|在緩衝區之間移動|  
|[\_mktemp、\_wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md)|[\_mktemp\_s、\_wmktemp\_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|建立唯一的檔名|  
|[printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|將格式化輸出列印至標準輸出資料流|  
|[\_putenv、\_wputenv](../c-runtime-library/reference/putenv-wputenv.md)|[\_putenv\_s、\_wputenv\_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|建立、修改或移除環境變數|  
|[qsort](../c-runtime-library/reference/qsort.md)|[qsort\_s](../c-runtime-library/reference/qsort-s.md)|執行快速排序|  
|[rand](../c-runtime-library/reference/rand.md)|[rand\_s](../c-runtime-library/reference/rand-s.md)|產生虛擬亂數|  
|[scanf、\_scanf\_l、wscanf、\_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|從標準輸入資料流讀取格式化資料|  
|[\_searchenv、\_wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md)|[\_searchenv\_s、\_wsearchenv\_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|使用環境路徑來搜尋檔案|  
|[snprintf、\_snprintf、\_snprintf\_l、\_snwprintf、\_snwprintf\_l](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|[\_snprintf\_s、\_snprintf\_s\_l、\_snwprintf\_s、\_snwprintf\_s\_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|將格式化資料寫入字串|  
|[\_snscanf、\_snscanf\_l、\_snwscanf、\_snwscanf\_l](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md)|[\_snscanf\_s、\_snscanf\_s\_l、\_snwscanf\_s、\_snwscanf\_s\_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|從字串讀取所指定長度的格式化資料。|  
|[\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)|[\_sopen\_s、\_wsopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|開啟檔案以供共用|  
|[\_splitpath、\_wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md)|[\_splitpath\_s、\_wsplitpath\_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|將一個路徑名稱分割為多個元件|  
|[sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[sprintf\_s、\_sprintf\_s\_l、swprintf\_s、\_swprintf\_s\_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|將格式化資料寫入字串|  
|[sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)|[sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|從字串讀取格式化資料|  
|[strcat、wcscat、\_mbscat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)|[strcat\_s、wcscat\_s、\_mbscat\_s](../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)|附加字串|  
|[strcpy、wcscpy、\_mbscpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|[strcpy\_s、wcscpy\_s、\_mbscpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)|編輯字串|  
|[\_strdate、\_wstrdate](../c-runtime-library/reference/strdate-wstrdate.md)|[\_strdate\_s、\_wstrdate\_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|傳回字串形式的目前系統日期|  
|[strerror、\_strerror、\_wcserror、\_\_wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)|[strerror\_s、\_strerror\_s、\_wcserror\_s、\_\_wcserror\_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|取得系統錯誤訊息 \(`strerror`、`_wcserror`\)，或列印使用者提供的錯誤訊息 \(`_strerror`、`__wcserror`\)|  
|[\_strlwr、\_wcslwr、\_mbslwr、\_strlwr\_l、\_wcslwr\_l、\_mbslwr\_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)|[\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|將字串轉換成小寫|  
|[strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|[strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|將字元附加至字串|  
|[strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|[strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)|將某個字串的字元複製到另一個字串|  
|[\_strnset、\_strnset\_l、\_wcsnset、\_wcsnset\_l、\_mbsnset、\_mbsnset\_l](../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)|[\_strnset\_s、\_strnset\_s\_l、\_wcsnset\_s、\_wcsnset\_s\_l、\_mbsnset\_s、\_mbsnset\_s\_l](../c-runtime-library/reference/strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md)|將字串的前 n 個字元設為指定的字元|  
|[\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[\_strset\_s、\_strset\_s\_l、\_wcsset\_s、\_wcsset\_s\_l、\_mbsset\_s、\_mbsset\_s\_l](../c-runtime-library/reference/strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md)|將字串的所有字元設為指定的字元|  
|[\_strtime、\_wstrtime](../c-runtime-library/reference/strtime-wstrtime.md)|[\_strtime\_s、\_wstrtime\_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|傳回字串形式的目前系統時間|  
|[strtok、\_strtok\_l、wcstok、\_wcstok\_l、\_mbstok、\_mbstok\_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)|[strtok\_s、\_strtok\_s\_l、wcstok\_s、\_wcstok\_s\_l、\_mbstok\_s、\_mbstok\_s\_l](../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)|使用目前地區設定或傳入的地區設定，尋找字串中的下一個語彙基元|  
|[\_strupr、\_strupr\_l、\_mbsupr、\_mbsupr\_l、\_wcsupr\_l、\_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)|[\_strupr\_s、\_strupr\_s\_l、\_mbsupr\_s、\_mbsupr\_s\_l、\_wcsupr\_s、\_wcsupr\_s\_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|將字串轉換成大寫|  
|[tmpfile](../c-runtime-library/reference/tmpfile.md)|[tmpfile\_s](../c-runtime-library/reference/tmpfile-s.md)|建立暫存檔案|  
|[\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|[tmpnam\_s、\_wtmpnam\_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|產生可用來建立暫存檔的名稱|  
|[\_ultoa、\_ultow](../c-runtime-library/reference/ultoa-ultow.md)|[\_ultoa\_s、\_ultow\_s](../c-runtime-library/reference/ultoa-s-ultow-s.md)|將不帶正負號的長整數轉換為字串|  
|[\_umask](../c-runtime-library/reference/umask.md)|[\_umask\_s](../c-runtime-library/reference/umask-s.md)|設定預設的檔案權限遮罩|  
|[\_vcprintf、\_vcprintf\_l、\_vcwprintf、\_vcwprintf\_l](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[\_vcprintf\_s、\_vcprintf\_s\_l、\_vcwprintf\_s、\_vcwprintf\_s\_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|使用引數清單的指標，將格式化輸出寫入主控台|  
|[vfprintf、\_vfprintf\_l、vfwprintf、\_vfwprintf\_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[vfprintf\_s、\_vfprintf\_s\_l、vfwprintf\_s、\_vfwprintf\_s\_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|使用引數清單的指標，寫入格式化輸出|  
|[vfscanf、vfwscanf](../c-runtime-library/reference/vfscanf-vfwscanf.md)|[vfscanf\_s、vfwscanf\_s](../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)|從資料流讀取格式化資料|  
|[vprintf、\_vprintf\_l、vwprintf、\_vwprintf\_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[vprintf\_s、\_vprintf\_s\_l、vwprintf\_s、\_vwprintf\_s\_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|使用引數清單的指標，寫入格式化輸出|  
|[vscanf、vwscanf](../c-runtime-library/reference/vscanf-vwscanf.md)|[vscanf\_s、vwscanf\_s](../c-runtime-library/reference/vscanf-s-vwscanf-s.md)|從標準輸入資料流讀取格式化資料|  
|[vsnprintf、\_vsnprintf、\_vsnprintf\_l、\_vsnwprintf、\_vsnwprintf\_l](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|[vsnprintf\_s、\_vsnprintf\_s、\_vsnprintf\_s\_l、\_vsnwprintf\_s、\_vsnwprintf\_s\_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|使用引數清單的指標，寫入格式化輸出|  
|[vsprintf、\_vsprintf\_l、vswprintf、\_vswprintf\_l、\_\_vswprintf\_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[vsprintf\_s、\_vsprintf\_s\_l、vswprintf\_s、\_vswprintf\_s\_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|使用引數清單的指標，寫入格式化輸出|  
|[vsscanf、vswscanf](../c-runtime-library/reference/vsscanf-vswscanf.md)|[vsscanf\_s、vswscanf\_s](../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)|從字串讀取格式化資料|  
|[wcrtomb](../c-runtime-library/reference/wcrtomb.md)|[wcrtomb\_s](../c-runtime-library/reference/wcrtomb-s.md)|將寬字元轉換為其多位元組字元表示法|  
|[wcsrtombs](../c-runtime-library/reference/wcsrtombs.md)|[wcsrtombs\_s](../c-runtime-library/reference/wcsrtombs-s.md)|將寬字元字串轉換為其多位元組字元字串表示法|  
|[wcstombs、\_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)|[wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|將寬字元序列轉換為對應的多位元組字元序列|  
|[wctomb、\_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md)|[wctomb\_s、\_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|將寬字元轉換為對應的多位元組字元|  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)