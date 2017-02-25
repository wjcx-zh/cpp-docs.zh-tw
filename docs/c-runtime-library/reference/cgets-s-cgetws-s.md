---
title: "_cgets_s、_cgetws_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cgetws_s"
  - "_cgets_s"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_cgets_s"
  - "cgets_s"
  - "cgetws_s"
  - "_cgetws_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cgets_s 函式"
  - "_cgetws_s 函式"
  - "cget_s 函式"
  - "cgetws_s 函式"
  - "主控台, 取得字串來源"
  - "字串 [C++], 從主控台取得"
ms.assetid: 38b74897-afe6-4dd9-a43f-36a3c0d72c5c
caps.latest.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 31
---
# _cgets_s、_cgetws_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從主控台取得字元字串。  這些版本的 [\_cgets 和 \_cgetws](../../c-runtime-library/cgets-cgetws.md) 具有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t _cgets_s(   
   char *buffer,  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
errno_t _cgetws_s(  
   wchar_t *buffer  
   size_t numberOfElements,  
   size_t *pSizeRead  
);  
template <size_t size>  
errno_t _cgets_s(   
   char (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
template <size_t size>  
errno_t _cgetws_s(  
   wchar_t (&buffer)[size],  
   size_t *pSizeRead  
); // C++ only  
```  
  
#### 參數  
 \[輸出\] `buffer`  
 資料的儲存位置。  
  
 \[in\] `numberOfElements`  
 緩衝區的大小，以單一位元組或寬字元為單位，也是要讀取的字元數上限。  
  
 \[in\] `pSizeRead`  
 實際讀取的字元數。  
  
## 傳回值  
 如果成功則傳回值為零；否則，如果發生失敗則為錯誤碼。  
  
### 錯誤狀況  
  
|`buffer`|`numberOfElements`|`pSizeRead`|返回|`buffer` 的內容。|  
|--------------|------------------------|-----------------|--------|-------------------|  
|`NULL`|任何|任何|`EINVAL`|N\/A|  
|非 `NULL`|零|任何|`EINVAL`|未修改|  
|非 `NULL`|任何|`NULL`|`EINVAL`|零長度字串|  
  
## 備註  
 `_cgets_s` 和 `_cgetws_s` 從主控台讀取字串和將字串 \(包括 null 結束字元\) 複製到 `buffer`。  `_cgetws_s` 是函式的寬字元版本；除了字元大小之外，這兩個函式行為相同。  要讀取的資料大小的最大值會做為 `numberOfElements` 參數傳入。  這個大小應該包含結束的 null 之額外字元。  實際讀取的字元數會放在 `pSizeRead`。  
  
 如果在作業期間或在驗證參數時發生錯誤，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則 `errno` 會設定為 `EINVAL`，且會傳回 `EINVAL`。  
  
 在 C\+\+ 中，樣板多載簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以自動將較舊且較不安全的函式取代成其較新且較安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_cgetts_s`|`_cgets_s`|`_cgets_s`|`_cgetws_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_cgets_s`|\<conio.h\>|  
|`_cgetws_s`|\<conio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)