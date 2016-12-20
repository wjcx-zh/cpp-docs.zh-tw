---
title: "檔案名稱搜尋函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "檔案名稱 [C++], 搜尋"
  - "_find 函式"
  - "wfind 函式"
  - "find 函式"
  - "_wfind 函式"
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 檔案名稱搜尋函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些函式會針對指定的檔案名稱進行搜尋或關閉搜尋：  
  
-   [\_findnext、\_wfindnext](../c-runtime-library/reference/findnext-functions.md)  
  
-   [\_findfirst、\_wfindfirst](../c-runtime-library/reference/findfirst-functions.md)  
  
-   [\_findclose](../c-runtime-library/reference/findclose.md)  
  
## 備註  
 `_findfirst` 函式提供檔案名稱第一個執行個體的相關資訊，此檔案名稱與 `filespec` 引數所指定的檔案相符。 您可以在 `filespec` 使用主機作業系統支援的任何萬用字元組合。  
  
 這些函式以 IO.h 中所定義的 \_`finddata_t` 結構傳回檔案資訊。 家族中的不同函式在 `_finddata_t` 結構上有多種變化。 基本 `_finddata_t` 結構包含下列項目：  
  
 `unsigned attrib`  
 檔案屬性。  
  
 `time_t time_create`  
 檔案建立時間 \(於 FAT 檔案系統為 –1L\)。 此時間以 UTC 格式儲存。 若要轉換為本地時間，請使用 [localtime\_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)。  
  
 `time_t time_access`  
 上次檔案存取時間 \(於 FAT 檔案系統為 –1L\)。 此時間以 UTC 格式儲存。 若要轉換為本地時間，請使用 `localtime_s`。  
  
 `time_t time_write`  
 上次寫入檔案時間。 此時間以 UTC 格式儲存。 若要轉換為本地時間，請使用 `localtime_s`。  
  
 `_fsize_t size`  
 檔案的長度 \(以位元組為單位\)。  
  
 `char name`\[ `_MAX_PATH`\]  
 以 Null 結尾的相符檔案或目錄名稱，不含路徑。  
  
 在不支援檔案建立時間及上次存取時間的檔案系統 \(例如 FAT 系統\) 中，`time_create`  和 `time_access`  欄位一律為 –1L。  
  
 `_MAX_PATH`  在 Stdlib.h 中定義為 260 位元組。  
  
 您可以指定目標屬性 \(例如 `_A_RDONLY`\) 以限制搜尋作業。 這些屬性會在 `_finddata_t`  結構的 `attrib` 欄位內傳回，而且可以有下列值 \(定義於 IO.h\)。 使用者不應依賴這些僅適用於 `attrib` 欄位的值。  
  
 `_A_ARCH`  
 封存。 每當 **BACKUP** 命令變更或清除檔案時即設定。 值：0x20。  
  
 `_A_HIDDEN`  
 隱藏的檔案。 除非您使用 **\/AH** 選項，否則使用 DIR 命令時並不常見。 傳回有關一般檔案或具有此屬性之檔案的資訊。 值：0x02。  
  
 `_A_NORMAL`  
 一般。 未設定其他屬性，而且可不受限制進行讀取或寫入的檔案。 值：0x00。  
  
 `_A_RDONLY`  
 唯讀。 無法開啟以進行寫入的檔案，以及名稱相同而無法建立的檔案。 值：0x01。  
  
 `_A_SUBDIR`  
 子目錄。 值：0x10。  
  
 `_A_SYSTEM`  
 系統檔案。 除非使用了 **\/A** 或 **\/A:S** 選項，否則使用 **DIR** 命令時並不常見。 值：0x04。  
  
 如果有符合稍早 `_findfirst` 呼叫中所指定 `filespec` 引數的名稱，`_findnext` 便會往下搜尋。`fileinfo` 引數應該會指向由先前 `_findfirst` 呼叫所初始化的結構。 如果找到相符名稱，`fileinfo` 結構內容便會如上述方式變更。 否則會維持不變。`_findclose` 會關閉指定的搜尋控制代碼，並為 `_findfirst` 和 `_findnext` 同時釋出相關聯的資源。 由 `_findfirst` 或 `_findnext` 之一所傳回的控制代碼必須先傳遞到  `_findclose`，然後才能在組成其傳遞路徑的目錄上執行修改作業，例如刪除。  
  
 您可以將 `_find` 函式巢狀化。 例如，如果 `_findfirst` 或 `_findnext` 的呼叫發現是子目錄的檔案，就可以另外使用 `_findfirst` 或 `_findnext` 呼叫來啟始新的搜尋。  
  
 `_wfindfirst` 和 `_wfindnext` 是寬字元版本的 `_findfirst` 和 `_findnext`。 寬字元版本的結構引數具有 `_wfinddata_t` 定義於 IO.h 和 Wchar.h 的資料類型。 此資料類型的欄位與 `_finddata_t` 資料類型的欄位相同，除了在 `_wfinddata_t` 中，名稱欄位屬於類型 `wchar_t` 而非類型 `char`。 否則 `_wfindfirst` 和 `_wfindnext` 的行為與 `_findfirst` 和 `_findnext` 相同。  
  
 `_findfirst` 和 `_findnext` 皆使用 64 位元時間類型。 如果您必須使用舊的 32 位元時間類型，則可以定義 `_USE_32BIT_TIME_T`。 名稱中包含 `32` 後置詞的這些函式版本皆使用 32 位元時間類型，而具有 `64` 的後置詞則使用 64 位元時間類型。  
  
 函式 `_findfirst32i64`、`_findnext32i64`、`_wfindfirst32i64`和 `_wfindnext32i64` 的行為也與這些函式版本的 32 位元時間類型相同，除非這些函式使用並傳回 64 位元的檔案長度。 函式 `_findfirst64i32`、`_findnext64i32`、`_wfindfirst64i32` 和 `_wfindnext64i32`使用 64 位元時間類型，但使用 32 位元檔案長度。 這些函式皆使用適當的 `_finddata_t` 類型變化，此類型中的欄位類型針對時間和檔案大小會有所不同。  
  
 `_finddata_t` 事實上是評估 `_finddata64i32_t` \(或 `_USE_32BIT_TIME_T` 遭拒則為 `_finddata32_t`\) 的巨集。 下表摘要說明 `_finddata_t` 的各種版本：  
  
|結構|時間類型|檔案大小類型|  
|--------|----------|------------|  
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|  
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|  
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|  
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|  
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|  
  
 `_fsize_t` 是 `unsigned long` \(32 位元\) 的 `typedef`。  
  
## 範例  
  
```  
// crt_find.c // This program uses the 32-bit _find functions to print // a list of all files (and their attributes) with a .C extension // in the current directory. #include <stdio.h> #include <stdlib.h> #include <io.h> #include <time.h> int main( void ) { struct _finddata_t c_file; intptr_t hFile; // Find first .c file in current directory if( (hFile = _findfirst( "*.c", &c_file )) == -1L ) printf( "No *.c files in current directory!\n" ); else { printf( "Listing of .c files\n\n" ); printf( "RDO HID SYS ARC  FILE         DATE %25c SIZE\n", ' ' ); printf( "--- --- --- ---  ----         ---- %25c ----\n", ' ' ); do { char buffer[30]; printf( ( c_file.attrib & _A_RDONLY ) ? " Y  " : " N  " ); printf( ( c_file.attrib & _A_HIDDEN ) ? " Y  " : " N  " ); printf( ( c_file.attrib & _A_SYSTEM ) ? " Y  " : " N  " ); printf( ( c_file.attrib & _A_ARCH )   ? " Y  " : " N  " ); ctime_s( buffer, _countof(buffer), &c_file.time_write ); printf( " %-12s %.24s  %9ld\n", c_file.name, buffer, c_file.size ); } while( _findnext( hFile, &c_file ) == 0 ); _findclose( hFile ); } }  
```  
  
```Output  
.c 檔案清單 RDO HID SYS ARC  檔案         日期                           大小 --- --- --- ---  ----         ----                           ---- N   N   N   Y   blah.c       2002 年 2 月 13 日週三 09:21:42       1715 N   N   N   Y   test.c       2002 年 2 月 6 日週三 14:30:44        312  
```  
  
## 請參閱  
 [系統呼叫](../c-runtime-library/system-calls.md)