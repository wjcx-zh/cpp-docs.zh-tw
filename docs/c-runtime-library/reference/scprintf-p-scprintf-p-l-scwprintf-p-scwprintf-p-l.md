---
title: "_scprintf_p、_scprintf_p_l、_scwprintf_p、_scwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_scwprintf_p"
  - "_scprintf_p_l"
  - "_scwprintf_p_l"
  - "_scprintf_p"
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
  - "_scwprintf_p_l"
  - "_sctprintf_p"
  - "scprintf_p_l"
  - "scprintf_p"
  - "_sctprintf_p_l"
  - "scwprintf_p"
  - "_scprintf_p_l"
  - "scwprintf_p_l"
  - "_scprintf_p"
  - "_scwprintf_p"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_scprintf_p 函式"
  - "_scprintf_p_l 函式"
  - "_sctprintf_p 函式"
  - "_sctprintf_p_l 函式"
  - "_scwprintf_p 函式"
  - "_scwprintf_p_l 函式"
  - "scprintf_p 函式"
  - "scprintf_p_l 函式"
  - "sctprintf_p 函式"
  - "sctprintf_p_l 函式"
  - "scwprintf_p 函式"
  - "scwprintf_p_l 函式"
ms.assetid: 8390d1e1-2826-47a4-851f-6635a88087cc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _scprintf_p、_scprintf_p_l、_scwprintf_p、_scwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回字元數在格式化字串中，且能夠指定參數用於格式字串的命令。  
  
## 語法  
  
```  
int _scprintf_p(  
   const char *format [,  
   argument] ...   
);  
int _scprintf_p_l(  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _scwprintf_p (  
   const wchar_t *format [,  
   argument] ...   
);  
int _scwprintf_p _l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
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
 如果字串使用指定的格式化程式碼列印或傳送到檔案或緩衝區，傳回將產生的字元數。  傳回的值不包含結束的 null 字元。  `_scwprintf_p` 實作寬字元的相同功能函式。  
  
 `_scprintf_p` 和 `_scprintf` 的差異在於 `_scprintf_p` 支援的位置參數，可以指定命令引數使用格式字串。  如需詳細資訊，請參閱[printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 如果 `format` 為 `NULL` 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 \-1 並將`errno` 設定為 `EINVAL`。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 每個 `argument` \(如果有的話\) 是根據 `format` 中的對應格式規格進行轉換。  此格式包含一般字元，與 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 的 `format` 引數具有相同的形式和功能。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_sctprintf_p`|`_scprintf_p`|`_scprintf_p`|`_scwprintf_p`|  
|`_sctprintf_p_l`|`_scprintf_p_l`|`_scprintf_p_l`|`_scwprintf_p_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_scprintf_p`, `_scprintf_p_l`|\<stdio.h\>|  
|`_scwprintf_p`, `_scwprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_scprintf、\_scprintf\_l、\_scwprintf、\_scwprintf\_l](../../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md)   
 [\_printf\_p、\_printf\_p\_l、\_wprintf\_p、\_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)