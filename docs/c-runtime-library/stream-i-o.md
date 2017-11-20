---
title: "資料流 I/O | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72772912097cf868538a496d3350d4708af5dc83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="stream-io"></a>資料流 I/O
這些函式會處理不同大小和格式的資料，範圍從單一字元到大型資料結構。 它們也提供緩衝處理，如此可改善效能。 資料流緩衝區的預設大小是 4K。 這些常式只會影響執行階段程式庫常式所建立的緩衝區，而且不會影響作業系統所建立的緩衝區。  
  
### <a name="stream-io-routines"></a>資料流 I/O 常式  
  
|常式|用法|  
|-------------|---------|  
|[clearerr](../c-runtime-library/reference/clearerr.md)( [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|清除資料流的錯誤指標|  
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|關閉資料流|  
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|關閉所有開啟的資料流，但 `stdin`, `stdout`和 `stderr`除外|  
|[_fdopen、wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|關聯資料流與已開啟檔案的檔案描述項|  
|[feof](../c-runtime-library/reference/feof.md)|測試資料流上的檔案結尾|  
|[ferror](../c-runtime-library/reference/ferror.md)|測試資料流上的錯誤|  
|[fflush](../c-runtime-library/reference/fflush.md)|將資料流清除至緩衝區或存放裝置|  
|[fgetc、fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|從資料流讀取字元 ( `getc` 和 `getwc`的函式版本)|  
|[_fgetchar、_fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|從 `stdin` 讀取字元 ( `getchar` 和 `getwchar`的函式版本)|  
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|取得資料流的位置指標|  
|[fgets、fgetws](../c-runtime-library/reference/fgets-fgetws.md)|從資料流讀取字串|  
|[_fileno](../c-runtime-library/reference/fileno.md)|取得與資料流相關聯的檔案描述項|  
|[_flushall](../c-runtime-library/reference/flushall.md)|將所有資料流清除至緩衝區或存放裝置|  
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)、 [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|開啟資料流|  
|[fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|將格式化資料寫入資料流|  
|[fputc、fputwc](../c-runtime-library/reference/fputc-fputwc.md)|將字元寫入資料流 ( `putc` 和 `putwc`的函式版本)|  
|[_fputchar、_fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|將字元寫入 `stdout` ( `putchar` 和 `putwchar`的函式版本)|  
|[fputs、fputws](../c-runtime-library/reference/fputs-fputws.md)|將字串寫入資料流|  
|[fread](../c-runtime-library/reference/fread.md)|從資料流讀取未格式化資料|  
|[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)( [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|將 `FILE` 資料流指標重新指派給新的檔案或裝置|  
|[fscanf、fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|從資料流讀取格式化資料|  
|[fseek、_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|將檔案位置移至指定的位置|  
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|設定資料流的位置指標|  
|[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|以檔案共用開啟資料流|  
|[ftell、_ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|取得目前檔案位置|  
|[fwrite](../c-runtime-library/reference/fwrite.md)|將未格式化資料項目寫入資料流|  
|[getc、getwc](../c-runtime-library/reference/getc-getwc.md)|從資料流讀取字元 ( `fgetc` 和 `fgetwc`的巨集版本)|  
|[getchar、getwchar](../c-runtime-library/reference/getc-getwc.md)|從 `stdin` 讀取字元 ( `fgetchar` 和 `fgetwchar`的巨集版本)|  
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|傳回允許在資料流 I/O 層級同時開啟的檔案數目。|  
|[gets_s、_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|從 `stdin` 讀取行|  
|[_getw](../c-runtime-library/reference/getw.md)|從資料流讀取二進位 `int`|  
|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|將格式化資料寫入 `stdout`|  
|[putc、putwc](../c-runtime-library/reference/putc-putwc.md)|將字元寫入資料流 ( `fputc` 和 `fputwc`的巨集版本)|  
|[putchar、putwchar](../c-runtime-library/reference/putc-putwc.md)|將字元寫入 `stdout` ( `fputchar` 和 `fputwchar`的巨集版本)|  
|[puts、_putws](../c-runtime-library/reference/puts-putws.md)|將行寫入資料流|  
|[_putw](../c-runtime-library/reference/putw.md)|將二進位 `int` 寫入資料流|  
|[rewind](../c-runtime-library/reference/rewind.md)|將檔案位置移至資料流開頭|  
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|移除 `tmpfile` 所建立的暫存檔案|  
|[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)、[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|從 `stdin` 讀取格式化資料|  
|[setbuf](../c-runtime-library/reference/setbuf.md)|控制資料流緩衝|  
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|設定在資料流 I/O 層級同時開啟的檔案數目上限。|  
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|控制資料流緩衝和緩衝區大小|  
|[_snprintf、_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)( [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|將所指定長度的格式化資料寫入字串|  
|[_snscanf、_snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md)、[_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|從標準輸入資料流讀取所指定長度的格式化資料。|  
|[sprintf、swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)、[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|將格式化資料寫入字串|  
|[sscanf、swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)、[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|從字串讀取格式化資料|  
|[_tempnam、_wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|在指定的目錄中產生暫存檔名|  
|[tmpfile](../c-runtime-library/reference/tmpfile.md)( [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|建立暫存檔|  
|[tmpnam、_wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)( [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|產生暫存檔名|  
|[ungetc、ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|將字元推送回資料流|  
|[_vcprintf、_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)、[_vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|將格式化資料寫入主控台。|  
|[vfprintf、vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)、[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|將格式化資料寫入資料流|  
|[vprintf、vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)、[vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|將格式化資料寫入 `stdout`|  
|[_vsnprintf、_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)、[vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|將所指定長度的格式化資料寫入緩衝區|  
|[vsprintf、vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)、[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|將格式化資料寫入緩衝區|  
  
 程式開始執行時，啟動程式碼會自動開啟數個資料流：標準輸入 (由 `stdin`指向)、標準輸出 (由 `stdout`指向) 和標準誤差 (由 `stderr`指向)。 預設會將這些資料流導向主控台 (鍵盤和螢幕)。 使用 `freopen` 將 `stdin`、 `stdout`或 `stderr` 重新導向磁碟檔案或裝置。  
  
 預設會緩衝處理使用資料流常式所開啟的檔案。 在每次程式庫呼叫之後， `stdout` 和 `stderr` 函式只有在填滿或您撰寫至字元裝置時才會予以清除。 如果程式異常終止，則可能未清除輸出緩衝區，導致資料遺失。 使用 `fflush` 或 `_flushall` 確保與所指定檔案相關聯的緩衝區或是所有開啟的緩衝區都已清除至作業系統，這樣可以在寫入磁碟之前快取資料。 認可至磁碟功能確保清除的緩衝區內容不會在系統失敗時遺失。  
  
 有兩種方式可以將緩衝區內容認可至磁碟：  
  
-   使用檔案 COMMODE.OBJ 進行連結，以設定全域認可旗標。 全域旗標的預設設定是 `n`(表示「不認可」)。  
  
-   使用 `c` 或 `fopen` ，將模式旗標設為 `_fdopen`。  
  
 不論全域認可/不認可旗標的狀態為何，特別使用 `c` 或 `n` 旗標所開啟的任何檔案都是根據旗標所運作。  
  
 如果您的程式未明確地關閉資料流，則會在程式終止時自動關閉資料流。 不過，您應該在程式完成資料流的處理時關閉資料流，因為一次可以開啟的資料流數目有限。 如需這項限制的相關資訊，請參閱 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) 。  
  
 只有在具有 `fflush` 或是檔案定位函式 (`fseek`、 `fsetpos`或 `rewind`) 的中間呼叫時，輸入才能直接遵循輸出。 如果輸入作業遇到檔案結尾，則輸出可以遵循輸入，而沒有檔案定位函式的中間呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [輸入和輸出](../c-runtime-library/input-and-output.md)   
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)