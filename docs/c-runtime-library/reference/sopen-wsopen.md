---
title: "_sopen、_wsopen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_sopen"
  - "_wsopen"
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
  - "_wsopen"
  - "wsopen"
  - "_sopen"
  - "_tsopen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sopen 函式"
  - "_wsopen 函式"
  - "檔案 [C++], 開啟"
  - "檔案 [C++], 共用"
  - "開啟檔案, 用於共用"
  - "共用檔案"
  - "sopen 函式"
  - "wsopen 函式"
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _sopen、_wsopen
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開啟檔案以供共用。  這些函式已有更安全的版本可用，請參閱 [\_sopen\_s、\_wsopen\_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md)。  
  
## 語法  
  
```  
int _sopen(    const char *filename,    int oflag,    int shflag [,    int pmode ]  ); int _wsopen(    const wchar_t *filename,    int oflag,    int shflag [,    int pmode ]  );  
```  
  
#### 參數  
 `filename`  
 檔案名稱  
  
 `oflag`  
 允許的作業類型。  
  
 `shflag`  
 允許的共用類型。  
  
 `pmode`  
 權限設定。  
  
## 傳回值  
 這些函式每一個都會傳回已開啟檔案的檔案描述項。  
  
 若 `filename` 或 `oflag` 是 `NULL` 指標，或者 `oflag` 或 `shflag` 不是在值的有效範圍內，就會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  若允許繼續執行，這些函式會傳回 \-1，並將 `errno` 設為下列其中一個值。  
  
 `EACCES`  
 指定的路徑為目錄，或是檔案為唯讀，但已嘗試「開啟以供寫入」作業。  
  
 `EEXIST`  
 指定了 `_O_CREAT` 和 `_O_EXCL` 旗標，但 `filename` 已存在。  
  
 `EINVAL`  
 無效的 `oflag` 或 `shflag` 引數。  
  
 `EMFILE`  
 沒有更多檔案描述項可用。  
  
 `ENOENT`  
 找不到檔案或路徑。  
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_sopen` 函式會開啟 `filename` 指定的檔案，並準備檔案，以供共用讀取或寫入 \(由 `oflag` 和 `shflag` 指定\)。  `_wsopen` 是寬字元版本的 `_sopen`；`_wsopen` 的 `filename` 引數是寬字元字串。  否則，`_wsopen` 和 `_sopen` 的行為即會相同。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tsopen`|`_sopen`|`_sopen`|`_wsopen`|  
  
 整數運算式 `oflag` 的組成包含定義在 \<fcntl.h\> 中的一或多個下列資訊清單常數。  當有兩個以上的常數形成 `oflag` 引數時，會使用位元 OR 運算子結合常數 \(  `|` \).  
  
 `_O_APPEND`  
 在每次寫入作業之前，將檔案指標重新置放到檔案的結尾。  
  
 `_O_BINARY`  
 以二進位 \(未轉譯\) 模式開啟檔案  \(如需二進位模式的說明，請參閱 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)\)。  
  
 `_O_CREAT`  
 建立檔案並開啟以供寫入。  若 `filename` 指定的檔案存在則無影響。  指定 `_O_CREAT` 時，需要 `pmode` 引數。  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 將檔案建立為暫存檔，若有可能的話，請勿清除至磁碟。  指定 `_O_CREAT` 時，需要 `pmode` 引數。  
  
 `_O_CREAT | _O_TEMPORARY`  
 將檔案建立為暫存檔；當最後一個檔案描述項關閉時會刪除檔案。  指定 `_O_CREAT` 時，需要 `pmode` 引數。  
  
 `_O_CREAT | _O_EXCL`  
 若 `filename` 指定的檔案存在，會傳回錯誤值。  搭配 `_O_CREAT` 使用時才套用。  
  
 `_O_NOINHERIT`  
 防止建立共用檔案描述項。  
  
 `_O_RANDOM`  
 從磁碟指定主要隨機存取。  
  
 `_O_RDONLY`  
 開啟檔案為僅供讀取。  指定時無法搭配 `_O_RDWR` 或 `_O_WRONLY`。  
  
 `_O_RDWR`  
 開啟檔案以進行讀取和寫入。  指定時無法搭配 `_O_RDONLY` 或 `_O_WRONLY`。  
  
 `_O_SEQUENTIAL`  
 從磁碟指定主要循序存取。  
  
 `_O_TEXT`  
 以文字 \(已轉譯\) 模式開啟檔案  \(如需詳細資訊，請參閱 [文字及二進位模式檔案 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 及 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)\)。  
  
 `_O_TRUNC`  
 開啟檔案，並將檔案截斷為零長度；檔案必須具有寫入權限。  指定時無法搭配 `_O_RDONLY`。  `_O_TRUNC` 用於搭配 `_O_CREAT` 以開啟現有檔案或建立檔案。  
  
> [!NOTE]
>  `_O_TRUNC` 旗標會終結指定檔案的內容。  
  
 `_O_WRONLY`  
 將檔案開啟為僅供寫入。  指定時無法搭配 `_O_RDONLY` 或 `_O_RDWR`。  
  
 `_O_U16TEXT`  
 以 Unicode UTF\-16 模式開啟檔案。  
  
 `_O_U8TEXT`  
 以 Unicode UTF\-8 模式開啟檔案。  
  
 `_O_WTEXT`  
 以 Unicode 模式開啟檔案。  
  
 若要指定檔案存取模式，您必須指定 `_O_RDONLY`、`_O_RDWR` 或 `_O_WRONLY`。  存取模式沒有預設值。  
  
 使用 `_O_WTEXT`、`_O_U8TEXT` 或 `_O_U16TEXT` 以 Unicode 模式開啟檔案時，請輸入函式，將從檔案讀取的資料，轉譯為儲存為類型 `wchar_t` 的 UTF\-16 資料。  寫入檔案的函示會以 Unicode 模式開啟，但包含儲存為類型 `wchar_t` 之 UTF\-16 資料的緩衝區除外。  若檔案是編碼為 UTF\-8，則會在寫入 UTF\-16 資料時轉譯為 UTF\-8，且會在讀取檔案的 UTF\-8 編碼內容時轉譯成 UTF\-16。  嘗試以 Unicode 模式讀取或寫入奇數位元組會導致參數驗證錯誤。  若要讀取或寫入作為 UTF\-8 儲存在您程式裡的資料時，請使用文字或二進位檔案模式，不要使用 Unicode 模式。  您要負責所有必要的編碼轉譯。  
  
 若搭配 `_O_WRONLY | _O_APPEND` \(附加模式\) 及 `_O_WTEXT`、`_O_U16TEXT` 或 `_O_U8TEXT` 呼叫 `_sopen`，會先嘗試開啟檔案以供讀取和寫入，再讀取 BOM，然後重新開啟檔案且僅供寫入。  若開啟檔案以供讀取和寫入失敗，則會僅針對寫入開啟檔案，並使用 Unicode 模式設定的預設值。  
  
 引數 `shflag` 是常數運算式，其中包含定義在 \<share.h\> 中的下列資訊清單常數之一。  
  
 `_SH_DENYRW`  
 拒絕對檔案的讀取和寫入存取。  
  
 `_SH_DENYWR`  
 拒絕對檔案的寫入存取。  
  
 `_SH_DENYRD`  
 拒絕對檔案的讀取存取。  
  
 `_SH_DENYNO`  
 允許讀取和寫入存取。  
  
 指定 `_O_CREAT` 時，才需要 `pmode` 引數。  若檔案不存在，`pmode` 會指定檔案的權限設定 \(新檔案第一次關閉時會進行此設定\)。  否則會忽略 `pmode`。  `pmode` 是整數運算式，其中包含定義在 \<sys\\stat.h\> 中的一或兩個資訊清單常數 `_S_IWRITE` 和 `_S_IREAD`。  指定兩個常數時，會使用位元 OR 運算子加以結合。  `pmode` 的含意如下。  
  
 `_S_IWRITE`  
 允許寫入。  
  
 `_S_IREAD`  
 允許讀取。  
  
 `_S_IREAD | _S_IWRITE`  
 允許讀取和寫入。  
  
 若沒有指定寫入權限，則檔案為唯讀。  在 Windows 作業系統中，所有檔案皆為可讀取，不可能授與僅限寫入的權限。  因此，模式 `_S_IWRITE` 和 `_S_IREAD | _S_IWRITE` 相同。  
  
 `_sopen` 會在設定權限之前，將目前的檔案權限遮罩套用至 `pmode` \(請參閱 [\_umask](../../c-runtime-library/reference/umask.md)\)。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_sopen`|\<io.h\>|\<fcntl.h\>、\<sys\\types.h\>、\<sys\\stat.h\>、\<share.h\>|  
|`_wsopen`|\<io.h\> 或 \<wchar.h\>|\<fcntl.h\>、\<sys\\types.h\>、\<sys\\stat.h\>、\<share.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_locking](../../c-runtime-library/reference/locking.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_fsopen、\_wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)