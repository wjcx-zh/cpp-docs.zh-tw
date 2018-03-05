---
title: "CRT 函式的安全性增強版本 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- security [CRT]
- security-enhanced CRT
- CRT, security enhancements
ms.assetid: f87e5a01-4cb2-4379-9e8f-d4693828c55a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 468f63d8e98dd161baec0b0db33f5dab8e750695
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="security-enhanced-versions-of-crt-functions"></a>CRT 函式的安全性增強版本
執行階段程式庫常式已有更安全的版本可用。 如需 CRT 中安全性增強的進一步資訊，請參閱 [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。  
  
 **安全函式**  
  
|CRT 函式|安全性增強功能|使用|  
|------------------|--------------------------------|---------|  
|[_access、_waccess](../c-runtime-library/reference/access-waccess.md)|[_access_s、_waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|判斷檔案存取權限|  
|[_alloca](../c-runtime-library/reference/alloca.md)|[_malloca](../c-runtime-library/reference/malloca.md)|在堆疊上配置記憶體|  
|[asctime、_wasctime](../c-runtime-library/reference/asctime-wasctime.md)|[asctime_s、_wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|將時間從類型 `struct tm` 轉換為字元字串|  
|[bsearch](../c-runtime-library/reference/bsearch.md)|[bsearch_s](../c-runtime-library/reference/bsearch-s.md)|對經過排序的陣列執行二進位搜尋|  
|已過時的函式|[_cgets_s、_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|從主控台取得字元字串|  
|[_chsize](../c-runtime-library/reference/chsize.md)|[_chsize_s](../c-runtime-library/reference/chsize-s.md)|變更檔案大小|  
|[clearerr](../c-runtime-library/reference/clearerr.md)|[clearerr_s](../c-runtime-library/reference/clearerr-s.md)|重設資料流的錯誤指標|  
|[_control87、_controlfp、\__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|取得和設定浮點控制字組|  
|[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|格式化並列印到主控台|  
|[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)|[_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|從主控台讀取格式化資料|  
|[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)|[_ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|將時間從類型 `time_t`, `__time32_t` 或 `__time64_t` 轉換為字元字串|  
|[_ecvt](../c-runtime-library/reference/ecvt.md)|[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|將 `double` 數字轉換為字串|  
|[_fcvt](../c-runtime-library/reference/fcvt.md)|[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|將浮點數轉換為字串|  
|[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)|[fopen_s、_wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|開啟檔案|  
|[fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|將格式化資料列印至資料流|  
|[fread](../c-runtime-library/reference/fread.md)|[fread_s](../c-runtime-library/reference/fread-s.md)|從檔案讀取|  
|[_fread_nolock](../c-runtime-library/reference/fread-nolock.md)|[_fread_nolock_s](../c-runtime-library/reference/fread-nolock-s2.md)|從檔案讀取，而不使用多執行緒寫入鎖定|  
|f[reopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)|[freopen_s、_wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|重新開啟檔案|  
|[fscanf、_fscanf_l、fwscanf、_fwscanf_l](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|從資料流讀取格式化資料|  
|[_ftime、_ftime32、_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md)|[_ftime_s、_ftime32_s、_ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|取得目前時間|  
|[_gcvt](../c-runtime-library/reference/gcvt.md)|[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|將浮點值轉換為字串，並將其儲存在緩衝區中|  
|[getenv、_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)|[getenv_s、_wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|從目前環境取得值|  
|已過時的函式|[gets_s、_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|無法從 `stdin` 資料流取得行|  
|[gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)|[_gmtime32_s、_gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|將時間從類型 `time_t` 轉換為 `struct tm`，或從類型 `__time64_t` 轉換為 `struct tm`|  
|[_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)|[_itoa_s、_i64toa_s、_ui64toa_s、_itow_s、_i64tow_s、_ui64tow_s](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|將整數轉換為字串|  
|[_lfind](../c-runtime-library/reference/lfind.md)|[_lfind_s](../c-runtime-library/reference/lfind-s.md)|執行所指定索引鍵的線性搜尋|  
|[localtime、_localtime32、_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)|[localtime_s、_localtime32_s、_localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|將時間從類型 `time_t` 轉換為 `struct tm`，或從類型 `__time64_t` 轉換為經過本機校正的 `struct tm`。|  
|[_lsearch](../c-runtime-library/reference/lsearch.md)|[_lsearch_s](../c-runtime-library/reference/lsearch-s.md)|執行值的線性搜尋；若找不到，則加入到清單的結尾|  
|[_ltoa、_ltow](../c-runtime-library/reference/ltoa-ltow.md)|[_ltoa_s、_ltow_s](../c-runtime-library/reference/ltoa-s-ltow-s.md)|將長整數轉換為字串|  
|[_makepath、_wmakepath](../c-runtime-library/reference/makepath-wmakepath.md)|[_makepath_s、_wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|從元件建立路徑名稱|  
|[_mbccpy、_mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md)|[_mbccpy_s、_mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|在字串之間複製多位元組字元|  
|[_mbsnbcat、_mbsnbcat_l](../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)|[_mbsnbcat_s、_mbsnbcat_s_l](../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)|最多可將一個多位元組字元字串的前 `n` 個位元組附加到另一個多位元組字元字串之前|  
|[_mbsnbcpy、_mbsnbcpy_l](../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)|[_mbsnbcpy_s、_mbsnbcpy_s_l](../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)|將字串的 `n` 個位元組複製到目的地字串|  
|[_mbsnbset、_mbsnbset_l](../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)|[_mbsnbset_s、_mbsnbset_s_l](../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md)|將字串的前 `n` 個位元組設為指定的字元|  
|[mbsrtowcs](../c-runtime-library/reference/mbsrtowcs.md)|[mbsrtowcs_s](../c-runtime-library/reference/mbsrtowcs-s.md)|將多位元組字元字串轉換為對應的寬字元字串|  
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)|[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|將多位元組字元序列轉換為對應的寬字元序列|  
|[memcpy、wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)|[memcpy_s、wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|在緩衝區之間複製字元|  
|[memmove、wmemmove](../c-runtime-library/reference/memmove-wmemmove.md)|[memmove_s、wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|在緩衝區之間移動|  
|[_mktemp、_wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md)|[_mktemp_s、_wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|建立唯一的檔名|  
|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|將格式化輸出列印至標準輸出資料流|  
|[_putenv、_wputenv](../c-runtime-library/reference/putenv-wputenv.md)|[_putenv_s、_wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|建立、修改或移除環境變數|  
|[qsort](../c-runtime-library/reference/qsort.md)|[qsort_s](../c-runtime-library/reference/qsort-s.md)|執行快速排序|  
|[rand](../c-runtime-library/reference/rand.md)|[rand_s](../c-runtime-library/reference/rand-s.md)|產生虛擬亂數|  
|[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|從標準輸入資料流讀取格式化資料|  
|[_searchenv、_wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md)|[_searchenv_s、_wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|使用環境路徑來搜尋檔案|  
|[snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|[_snprintf_s、_snprintf_s_l、_snwprintf_s、_snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|將格式化資料寫入字串|  
|[_snscanf、_snscanf_l、_snwscanf、_snwscanf_l](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md)|[_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|從字串讀取所指定長度的格式化資料。|  
|[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)|[_sopen_s、_wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|開啟檔案以供共用|  
|[_splitpath、_wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md)|[_splitpath_s、_wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|將一個路徑名稱分割為多個元件|  
|[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|將格式化資料寫入字串|  
|[sscanf、_sscanf_l、swscanf、_swscanf_l](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)|[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|從字串讀取格式化資料|  
|[strcat、wcscat、_mbscat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)|[strcat_s、wcscat_s、_mbscat_s](../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)|附加字串|  
|[strcpy、wcscpy、_mbscpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|[strcpy_s、wcscpy_s、_mbscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)|編輯字串|  
|[_strdate、_wstrdate](../c-runtime-library/reference/strdate-wstrdate.md)|[_strdate_s、_wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|傳回字串形式的目前系統日期|  
|[strerror、_strerror、_wcserror、\__wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)|[strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|取得系統錯誤訊息 (`strerror`、 `_wcserror`)，或列印使用者提供的錯誤訊息 (`_strerror`、 `__wcserror`)|  
|[_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)|[_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|將字串轉換成小寫|  
|[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|將字元附加至字串|  
|[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)|將某個字串的字元複製到另一個字串|  
|[_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)|[_strnset_s、_strnset_s_l、_wcsnset_s、_wcsnset_s_l、_mbsnset_s、_mbsnset_s_l](../c-runtime-library/reference/strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md)|將字串的前 n 個字元設為指定的字元|  
|[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[_strset_s、_strset_s_l、_wcsset_s、_wcsset_s_l、_mbsset_s、_mbsset_s_l](../c-runtime-library/reference/strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md)|將字串的所有字元設為指定的字元|  
|[_strtime、_wstrtime](../c-runtime-library/reference/strtime-wstrtime.md)|[_strtime_s、_wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|傳回字串形式的目前系統時間|  
|[strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)|[strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l](../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)|使用目前地區設定或傳入的地區設定，尋找字串中的下一個語彙基元|  
|[_strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)|[_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|將字串轉換成大寫|  
|[tmpfile](../c-runtime-library/reference/tmpfile.md)|[tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|建立暫存檔案|  
|[_tempnam、_wtempnam、tmpnam、_wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|[tmpnam_s、_wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|產生可用來建立暫存檔的名稱|  
|[_ultoa、_ultow](../c-runtime-library/reference/ultoa-ultow.md)|[_ultoa_s、_ultow_s](../c-runtime-library/reference/ultoa-s-ultow-s.md)|將不帶正負號的長整數轉換為字串|  
|[_umask](../c-runtime-library/reference/umask.md)|[_umask_s](../c-runtime-library/reference/umask-s.md)|設定預設的檔案權限遮罩|  
|[_vcprintf、_vcprintf_l、_vcwprintf、_vcwprintf_l](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[_vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|使用引數清單的指標，將格式化輸出寫入主控台|  
|[vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|使用引數清單的指標，寫入格式化輸出|  
|[vfscanf、vfwscanf](../c-runtime-library/reference/vfscanf-vfwscanf.md)|[vfscanf_s、vfwscanf_s](../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)|從資料流讀取格式化資料|  
|[vprintf、_vprintf_l、vwprintf、_vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|使用引數清單的指標，寫入格式化輸出|  
|[vscanf、vwscanf](../c-runtime-library/reference/vscanf-vwscanf.md)|[vscanf_s、vwscanf_s](../c-runtime-library/reference/vscanf-s-vwscanf-s.md)|從標準輸入資料流讀取格式化資料|  
|[vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|[vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|使用引數清單的指標，寫入格式化輸出|  
|[vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、\__vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|使用引數清單的指標，寫入格式化輸出|  
|[vsscanf、vswscanf](../c-runtime-library/reference/vsscanf-vswscanf.md)|[vsscanf_s、vswscanf_s](../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)|從字串讀取格式化資料|  
|[wcrtomb](../c-runtime-library/reference/wcrtomb.md)|[wcrtomb_s](../c-runtime-library/reference/wcrtomb-s.md)|將寬字元轉換為其多位元組字元表示法|  
|[wcsrtombs](../c-runtime-library/reference/wcsrtombs.md)|[wcsrtombs_s](../c-runtime-library/reference/wcsrtombs-s.md)|將寬字元字串轉換為其多位元組字元字串表示法|  
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)|[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|將寬字元序列轉換為對應的多位元組字元序列|  
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)|[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|將寬字元轉換為對應的多位元組字元|  
  
## <a name="see-also"></a>請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)