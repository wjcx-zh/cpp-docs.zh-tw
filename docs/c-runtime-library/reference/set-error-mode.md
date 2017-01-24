---
title: "_set_error_mode | Microsoft Docs"
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
  - "_set_error_mode"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "set_error_mode"
  - "_set_error_mode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_error_mode 函式"
  - "set_error_mode 函式"
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_error_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

修改 `__error_mode` 來判斷非預設位置，其中 C 執行階段寫入可能結束程式之錯誤的錯誤訊息。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _set_error_mode(  
   int modeval   
);  
```  
  
#### 參數  
 `modeval`  
 錯誤訊息的目的地。  
  
## 傳回值  
 如果發生錯誤，則會傳回舊設定或 \-1。  
  
## 備註  
 設定 `__error_mode` 的值，以控制錯誤輸出接收。  例如，您可以將輸出導向至標準錯誤，或使用 `MessageBox` API。  
  
 可以將 `modeval` 參數設為下列其中一個值。  
  
|參數|描述|  
|--------|--------|  
|`_OUT_TO_DEFAULT`|錯誤接收是透過 `__app_type` 所決定。|  
|`_OUT_TO_STDERR`|錯誤接收是標準錯誤。|  
|`_OUT_TO_MSGBOX`|錯誤接收是訊息方塊。|  
|`_REPORT_ERRMODE`|報告目前 `__error_mode` 值。|  
  
 如果傳入非列出的值，則會叫用無效參數處理常式 \(如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述\)。  如果允許繼續執行，`_set_error_mode` 會將 `errno` 設為 `EINVAL`，並傳回 \-1。  
  
 將它與[判斷提示](../../c-runtime-library/reference/assert-macro-assert-wassert.md)搭配使用時，`_set_error_mode` 會在對話方塊中顯示失敗的陳述式，並提供選項讓您選擇 `Ignore` 按鈕，以繼續執行程式。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_set_error_mode`|\<stdlib.h\>|  
  
## 範例  
  
```  
// crt_set_error_mode.c  
// compile with: /c  
#include <stdlib.h>  
#include <assert.h>  
  
int main()  
{  
   _set_error_mode(_OUT_TO_STDERR);  
   assert(2+2==5);  
}  
```  
  
  **判斷提示失敗：2\+2\=\=5、檔案 crt\_set\_error\_mode.c、第 8 行**  
**此應用程式已要求執行階段以異常方式終止它。  如需詳細資訊，請連絡應用程式支援小組。**    
## 請參閱  
 [assert 巨集、\_assert、\_wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)