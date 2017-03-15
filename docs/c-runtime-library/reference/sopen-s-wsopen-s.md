---
title: "_sopen_s、_wsopen_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_sopen_s"
  - "_wsopen_s"
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
  - "_sopen_s"
  - "wsopen_s"
  - "_wsopen_s"
  - "sopen_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sopen_s 函式"
  - "_wsopen_s 函式"
  - "檔案 [C++], 開啟"
  - "檔案 [C++], 共用"
  - "開啟檔案, 用於共用"
  - "sopen_s 函式"
  - "wsopen_s 函式"
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _sopen_s、_wsopen_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開啟用於共用的檔案。  這些 [\_sopen and \_wsopen](../../c-runtime-library/reference/sopen-wsopen.md) 版本具有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t _sopen_s(    int* pfh,    const char *filename,    int oflag,    int shflag,    int pmode ); errno_t _wsopen_s(    int* pfh,    const wchar_t *filename,    int oflag,    int shflag,    int pmode, );  
```  
  
#### 參數  
 \[輸出\] `pfh`  
 檔案控制代碼，如果有錯誤，則為 \-1。  
  
 \[in\] `filename`  
 檔案名稱  
  
 \[輸入\] `oflag`  
 允許的作業種類。  
  
 \[輸入\] `shflag`  
 容許的共用種類。  
  
 \[輸入\] `pmode`  
 權限設定。  
  
## 傳回值  
 非零傳回值指出發生錯誤，在該情況下，`errno` 會設為下列其中一個值。  
  
 `EACCES`  
 指定的路徑是目錄，或者檔案為唯讀，但已嘗試「開啟以供寫入」作業。  
  
 `EEXIST`  
 指定 `_O_CREAT` 和 `_O_EXCL` 旗標，但 `filename` 已存在。  
  
 `EINVAL`  
 無效的 `oflag`、`shflag` 或 `pmode` 引數，或者 `pfh` 或 `filename` 為 null 指標。  
  
 `EMFILE`  
 沒有更多可用的檔案描述元。  
  
 `ENOENT`  
 找不到檔案或路徑。  
  
 如果無效的引數傳遞至函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則 `errno` 會設定為 `EINVAL`，且會傳回 `EINVAL`。  
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果發生錯誤，則會透過 `pfh` 傳回 \-1 \(除非 `pfh` 為 null 指標\)。  
  
## 備註  
 `_sopen_s` 函式會開啟 `filename` 指定的檔案，並準備用於共用讀取或寫入的檔案，如 `oflag` 和 `shflag` 所定義。  `_wsopen_s` 是 `_sopen_s` 的寬字元版本，`_wsopen_s` 的 `filename` 引數是寬字元字串。  否則，`_wsopen_s` 和 `_sopen_s` 的行為即會相同。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tsopen_s`|`_sopen_s`|`_sopen_s`|`_wsopen_s`|  
  
 整數運算式 `oflag` 由一個或多個資訊清單常數組合而成，這些常數在 \<fcntl.h\> 中定義。  當兩個或多個常數構成引數 `oflag` 時，它們會與位元 OR 運算子結合常數 \(  `|` \).  
  
 `_O_APPEND`  
 在每一次寫入作業之前，將檔案指標重新定位到檔案的結尾。  
  
 `_O_BINARY`  
 以二進位 \(未轉譯\) 模式開啟檔案   \(如需二進位模式的說明，請參閱 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)\)。  
  
 `_O_CREAT`  
 建立檔案並開啟以供寫入。  若 `filename` 指定的檔案存在則無影響。  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 將檔案建立為暫存檔，若有可能的話，請勿清除至磁碟。  
  
 `_O_CREAT | _O_TEMPORARY`  
 將檔案建立為暫存檔；當最後一個檔案描述項關閉時會刪除檔案。  
  
 `_O_CREAT | _O_EXCL`  
 如果 `filename` 指定的檔案已存在，會傳回錯誤值。  搭配 `_O_CREAT` 使用時才套用。  
  
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
 以文字 \(已轉譯\) 模式開啟檔案   \(如需詳細資訊，請參閱[文字和二進位模式檔案 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)\)。  
  
 `_O_TRUNC`  
 開啟檔案，並將檔案截斷為零長度；檔案必須具有寫入權限。  指定時無法搭配 `_O_RDONLY`。  `_O_TRUNC` 用於搭配 `_O_CREAT` 以開啟現有檔案或建立檔案。  
  
> [!NOTE]
>  `_O_TRUNC` 旗標會終結指定檔案的內容。  
  
 `_O_WRONLY`  
 將檔案開啟為僅供寫入。  無法使用 `_O_RDONLY` 或 `_O_RDWR` 指定。  
  
 `_O_U16TEXT`  
 以 Unicode UTF\-16 模式開啟檔案。  
  
 `_O_U8TEXT`  
 以 Unicode UTF\-8 模式開啟檔案。  
  
 `_O_WTEXT`  
 以 Unicode 模式開啟檔案。  
  
 若要指定檔案存取模式，您必須指定 `_O_RDONLY`、`_O_RDWR` 或 `_O_WRONLY`。  存取模式沒有預設值。  
  
 使用 `_O_WTEXT`、`_O_U8TEXT` 或 `_O_U16TEXT`，以 Unicode 模式開啟檔案時，請輸入函式，將從檔案讀取的資料，轉譯為儲存為類型 `wchar_t` 的 UTF\-16 資料。  寫入檔案的函示會以 Unicode 模式開啟，但包含儲存為類型 `wchar_t` 之 UTF\-16 資料的緩衝區除外。  如果檔案編碼為 UTF\-8，則在寫入時，UTF\-16 資料會轉譯為 UTF\-8，而在讀取時，該檔案 UTF\-8 編碼的內容會轉譯為 UTF\-16。  嘗試以 Unicode 模式讀取或寫入奇數數目位元組會導致參數驗證錯誤。  若要讀取或寫入程式中儲存為 UTF\-8 的資料，請使用文字或二進位檔模式而不是 Unicode 模式。  您負責任何必要的編碼轉譯。  
  
 如果 `_sopen_s` 使用 `_O_WRONLY | _O_APPEND` \(附加模式\) 及 `_O_WTEXT`、`_O_U16TEXT` 或 `_O_U8TEXT` 呼叫，則它會先嘗試開啟檔案，以供讀取及寫入，接著讀取 BOM，然後重新開啟該檔案，以僅供寫入。  如果開啟檔案以供讀取及寫入失敗，則它會開啟該檔案以僅供寫入，並使用 Unicode 模式設定的預設值。  
  
 引數 `shflag` 是常數運算式，其包含下列其中一個在 \<share.h\> 中定義的資訊清單常數。  
  
 `_SH_DENYRW`  
 拒絕檔案的讀取及寫入權限。  
  
 `_SH_DENYWR`  
 拒絕檔案的寫入權限。  
  
 `_SH_DENYRD`  
 拒絕檔案的讀取權限。  
  
 `_SH_DENYNO`  
 允許讀取及寫入權限。  
  
 與在 `_sopen` 中不同，`pmode` 引數一定是需要的。  當您指定 `_O_CREAT` 時，如果該檔案不存在，則 `pmode` 會指定檔案的權限設定，在第一次關閉新檔案時，會設定這些設定。  否則，會忽略 `pmode`。  `pmode` 是整數運算式，其包含在 \<sys\\stat.h\> 中定義的其中一個或兩個資訊清單常數 `_S_IWRITE` 和 `_S_IREAD`。  當提供兩個常數時，它們以位元 OR 運算子結合。  `pmode` 的意義如下。  
  
 `_S_IWRITE`  
 允許寫入。  
  
 `_S_IREAD`  
 允許讀取。  
  
 `_S_IREAD | _S_IWRITE`  
 允許讀取及寫入。  
  
 如果未提供寫入權限，則檔案是唯讀的。  在 Windows 作業系統中，所有檔案都是可讀取的；不可能提供唯寫權限。  因此，模式 `_S_IWRITE` 和 `_S_IREAD | _S_IWRITE` 是相當的。  
  
 在設定權限之前，`_sopen_s` 會將目前檔案權限遮罩套用至 `pmode` \(請參閱 [\_umask](../../c-runtime-library/reference/umask.md)\)。  
  
## 需求  
  
|常式|必要的標頭|選用標頭|  
|--------|-----------|----------|  
|`_sopen_s`|\<io.h\>|\<fcntl.h\>、\<sys\\types.h\>、\<sys\\stat.h\>、\<share.h\>|  
|`_wsopen_s`|\<io.h\> 或 \<wchar.h\>|\<fcntl.h\>、\<sys\/types.h\>、\<sys\/stat.h\>、\<share.h\>|  
  
 `_sopen_s` 和 `_wsopen_s` 是 Microsoft 擴充功能。  如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_locking](../../c-runtime-library/reference/locking.md) 的範例。  
  
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_fsopen、\_wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)