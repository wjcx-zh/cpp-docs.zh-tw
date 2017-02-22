---
title: "_splitpath、_wsplitpath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsplitpath"
  - "_splitpath"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wsplitpath"
  - "_splitpath"
  - "splitpath"
  - "_wsplitpath"
  - "_tsplitpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_splitpath 函式"
  - "_tsplitpath 函式"
  - "_wsplitpath 函式"
  - "路徑名稱"
  - "路徑名稱"
  - "splitpath 函式"
  - "tsplitpath 函式"
  - "wsplitpath 函式"
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _splitpath、_wsplitpath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Break a path name into components.  這些函式已有更安全的版本可用，請參閱 [\_splitpath\_s、\_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)。  
  
## 語法  
  
```  
void _splitpath(  
   const char *path,  
   char *drive,  
   char *dir,  
   char *fname,  
   char *ext   
);  
void _wsplitpath(  
   const wchar_t *path,  
   wchar_t *drive,  
   wchar_t *dir,  
   wchar_t *fname,  
   wchar_t *ext   
);  
```  
  
#### 參數  
 `path`  
 完整路徑。  
  
 `drive`  
 磁碟機代號，後面加上冒號 \(`:`\)。  如果不需要磁碟機代號，您可傳遞 `NULL` 作為這個參數。  
  
 `dir`  
 目錄路徑，包括斜線。  可以使用斜線 \( `/`\)，反斜線 \( `\` \)，或兩者。  如果不需要磁碟機代號，您可傳遞 `NULL` 作為這個參數。  
  
 `fname`  
 基底檔名 \(沒有副檔名\)。  如果不需要檔名，您可傳遞 `NULL` 作為這個參數。  
  
 `ext`  
 副檔名，包括前置句號 \(`.`\)。  如果不需要副檔名，您可傳遞 `NULL` 作為這個參數。  
  
## 備註  
 `_splitpath` 函式將路徑分給它的四個元件。  `_splitpath`適時地自動處理多位元組字元的字串參數，根據目前使用的多位元組字碼頁來辨認多位元組字元序列。  `_wsplitpath` 是 `_splitpath` 的寬字元版本；`_wsplitpath` 的引數是寬字元字串。  這三個函式其餘部分的運作相同。  
  
 **安全性提示** 這些函式會導致緩衝區滿溢問題的潛在威脅。  緩衝區溢位問題是系統攻擊的常見方法，它會導致權限不確定性的增加。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  這些函式更安全版本可用的；請參閱 [\_splitpath\_s、\_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE  & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|-----------------------------|----------------|-------------------|  
|`_tsplitpath`|`_splitpath`|`_splitpath`|`_wsplitpath`|  
  
 完整路徑的每個元件都在不同的緩衝區儲存；資訊清單常數 `_MAX_DRIVE`、 `_MAX_DIR`、 `_MAX_FNAME`和 `_MAX_EXT`\(定義於 STDLIB.H\) 為每個檔案組件中指定可允許的最大大小。  大於對應的資訊清單常數的檔案組件會造成堆積損毀。  
  
 每個緩衝區必須與其對應的資訊清單一樣大，來避免可能的緩衝區滿溢。  
  
 下表列出清單常數的值。  
  
|名稱|值|  
|--------|-------|  
|\_MAX\_DRIVE|3|  
|\_MAX\_DIR|256|  
|\_MAX\_FNAME|256|  
|\_MAX\_EXT|256|  
  
 如果完整路徑不含元件 \(例如檔名\)，`_splitpath` 將空字串指派給對應的緩衝區。  
  
 您可以將 `NULL` 傳遞至所有參數的 `_splitpath` 刪除不需要的 `path` 之外。  
  
 如果 `path` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `EINVAL`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_splitpath`|\<stdlib.h\>|  
|`_wsplitpath`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_makepath](../../c-runtime-library/reference/makepath-wmakepath.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_makepath、\_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [\_splitpath\_s、\_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)