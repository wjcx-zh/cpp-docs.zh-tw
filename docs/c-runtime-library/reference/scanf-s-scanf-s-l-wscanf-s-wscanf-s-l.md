---
title: "scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wscanf_s"
  - "_wscanf_s_l"
  - "scanf_s"
  - "_scanf_s_l"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wscanf_s"
  - "_tscanf_s_l"
  - "_wscanf_s_l"
  - "scanf_s"
  - "_tscanf_s"
  - "_scanf_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "從輸入資料流讀取資料 [c + +]"
  - "緩衝區 [C++]，緩衝區滿溢"
  - "_scanf_s_l 函式"
  - "_wscanf_s_l 函式"
  - "tscanf_s_l 函式"
  - "tscanf_s 函式"
  - "scanf_s 函式"
  - "從輸入資料流讀取的資料 [c + +]"
  - "wscanf_s 函式"
  - "_tscanf_s_l 函式"
  - "_tscanf_s 函式"
  - "scanf_s_l 函式"
  - "從輸入資料流格式化的資料 [c + +]"
  - "wscanf_s_l 函式"
  - "緩衝區 [C++]，避免滿溢"
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
caps.latest.revision: 33
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 33
---
# scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從標準輸入資料流讀取格式化資料。 這些版本 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 中所述，具有安全性增強功能， [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
int scanf_s(  
   const char *format [,  
   argument]...   
);  
int _scanf_s_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wscanf_s(  
   const wchar_t *format [,  
   argument]...   
);  
int _wscanf_s_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### 參數  
 `format`  
 格式控制字串。  
  
 `argument`  
 選擇性引數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 這會在成功轉換並指派時傳回欄位數；傳回值不包含已讀取但尚未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值為 `EOF` 時表示錯誤，或表示第一次嘗試讀取字元時遇到檔案結尾字元或字串結尾字元。 如果 `format` 是 `NULL` 指標、 無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則 `scanf_s` 和 `wscanf_s` 會傳回 `EOF`，且 `errno` 設為 `EINVAL`。  
  
 如需這些錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `scanf_s` 函式會從標準輸入資料流 `stdin` 讀取資料，並將資料寫入至由 `argument` 指定的位置。 每個 `argument` 必須是 `format` 中對應至型別指定名稱的型別變數指標。 如果在重疊的字串之間進行複製，則行為是未定義的。  
  
 `wscanf_s` 是寬字元版本的 `scanf_s`；`format` 的 `wscanf_s` 引數是寬字元字串。 如果資料流在 ANSI 模式中開啟，則 `wscanf_s` 和 `scanf_s` 的行為相同。`scanf_s` 目前不支援來自 UNICODE 資料流的輸入。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定參數，而不使用目前的執行緒地區設定。  
  
 不同於 `scanf` 和 `wscanf`，`scanf_s` 和 `wscanf_s` 需要針對型別 `c`、`C`、`s` 和 `S` 的所有輸入參數指定緩衝區大小，或以 `[]` 括住的字串控制項集合。 以字元為單位的緩衝區大小會作為緊接指標的額外參數傳遞至緩衝區或變數。 例如，如果您正在讀取字串，則該字串的緩衝區大小將以下列方式傳遞：  
  
 `char s[10];`  
  
 `scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9`  
  
 緩衝區大小包含結束的 null。 您可以使用寬度規格欄位，以確保在讀取的語彙基元可納入緩衝區。 如果沒有使用寬度規格欄位，則讀取的語彙基元太大而無法納入緩衝區中，並且不會寫入該緩衝區。  
  
> [!NOTE]
>  大小參數為型別 `unsigned`，而非 `size_t`。 使用靜態轉型轉換 `size_t` 值 `unsigned` 64 位元的組建組態。  
  
 下列範例顯示緩衝區大小參數會描述字元數目上限，而非位元組。 呼叫 `wscanf_s` 時，緩衝區型別所指示的字元寬度不符合格式指定名稱所指示的字元寬度。  
  
```  
wchar_t ws[10];  
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));  
```  
  
 `S` 格式指定名稱表示使用字元寬度是「相對於」函式所支援的預設寬度。 字元寬度是單一位元組，但函式支援雙位元組字元。 此範例會以最多 9 個單一位元組寬度字元的字串方式讀取，並將它們放在雙位元組寬度字元的緩衝區。 字元會視為單一位元組值；前兩個字元會儲存在 `ws[0]` 中，而後兩個會儲存在 `ws[1]` 中，依此類推。  
  
 如果是字元，則單一字元可能會以下列方式讀取：  
  
 `char c;`  
  
 `scanf_s("%c", &c, 1);`  
  
 讀取非 null 終止字串的多個字元時，整數會用於寬度規格和緩衝區大小。  
  
 `char c[4];`  
  
 `scanf_s("%4c", &c, (unsigned)_countof(c)); // not null terminated`  
  
 如需詳細資訊，請參閱[scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tscanf_s`|`scanf_s`|`scanf_s`|`wscanf_s`|  
|`_tscanf_s_l`|`_scanf_s_l`|`_scanf_s_l`|`_wscanf_s_l`|  
  
 如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`scanf_s`、 `_scanf_s_l`|\<stdio.h\>|  
|`wscanf_s`, `_wscanf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。 與主控台 \(`stdin`、`stdout` 和 `stderr`\) 關聯的標準資料流控制代碼必須重新導向，之後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_scanf_s.c  
// This program uses the scanf_s and wscanf_s functions  
// to read formatted input.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int      i,  
            result;  
   float    fp;  
   char     c,  
            s[80];  
   wchar_t  wc,  
            ws[80];  
  
   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,  
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );  
   printf( "The number of fields input is %d\n", result );  
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,  
           wc, s, ws);  
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,  
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );  
   wprintf( L"The number of fields input is %d\n", result );  
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,  
            c, wc, s, ws);  
}  
```  
  
 此程式會在提供此輸入時產生下列輸出：  
  
 `71 98.6 h z Byte characters`  
  
 `36 92.3 y n Wide characters`  
  
```Output  
欄位輸入的數目為的 6 的內容︰ 71 98.599998 h z 位元組字元的輸入欄位數目為的 6 的內容︰ 36 92.300003 y n 寬字元  
```  
  
## .NET Framework 對等用法  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
-   [System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)  
  
-   另請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)