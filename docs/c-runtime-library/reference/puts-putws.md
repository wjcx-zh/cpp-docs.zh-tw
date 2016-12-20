---
title: "puts、_putws | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putws"
  - "puts"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_putts"
  - "_putws"
  - "puts"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putts 函式"
  - "_putws 函式"
  - "puts 函式"
  - "putts 函式"
  - "putws 函式"
  - "標準輸出, 寫入至"
  - "字串 [C++], 撰寫"
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# puts、_putws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

寫一個字串到 **stdout**。  
  
## 語法  
  
```  
  
      int puts(  
   const char *str   
);  
int _putws(  
   const wchar_t *str   
);  
```  
  
#### 參數  
 `str`  
 輸出字串。  
  
## 傳回值  
 如果成功，傳回非負數的值。  如果 `puts` 失敗，則會傳回 `EOF`;如果 `_putws` 失敗，則會傳回 **WEOF**。  如果 `str` 如  [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述為 null 指標，則叫用無效參數處理常式。  如果允許繼續執行，函式會將 `errno` 設為 `EINVAL`，並傳回 `EOF` or **WEOF**。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 對應至標準輸出資料流 **stdout**的 `puts` 函式寫入 `str` ，取代在輸出資料流的字串結束 null 字元 \(「\\ 0 」\) 與換行字元 \(「\\ n」\) 。  
  
 `_putws` 是 `puts`的寬字元版本;如果資料流在 ANSI 模式中開啟，則兩個函式的作用完全相同。  `puts` 目前不支援輸出到 UNICODE 串流。  
  
 在 Windows 2000 和以後的版本， **\_putwch** 寫入使用目前主控台地區設定的 Unicode 字元。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_putts`|`puts`|`puts`|`_putws`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`puts`|\<stdio.h\>|  
|`_putws`|\<stdio.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_puts.c  
/* This program uses puts to write a string to stdout.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   puts( "Hello world from puts!" );  
}  
```  
  
## Output  
  
```  
Hello world from puts!  
```  
  
## .NET Framework 對等用法  
 [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputs、fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)