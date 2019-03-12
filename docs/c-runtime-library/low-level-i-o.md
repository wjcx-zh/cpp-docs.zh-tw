---
title: 低層級 I/O
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
ms.openlocfilehash: 7812656bdcb3f58866f91009b6ad3de9fd67cebe
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740149"
---
# <a name="low-level-io"></a>低層級 I/O

這些函式會針對比資料流 I/O 所提供還要更低層級的作業，直接叫用作業系統。 低層級輸入和輸出呼叫不會對資料進行緩衝或格式化。

低層級常數可以使用下列預先定義的檔案描述項，來存取於程式啟動時開啟的標準資料流。

|資料流|檔案描述項|
|------------|---------------------|
|**stdin**|0|
|**stdout**|1|
|**stderr**|2|

低層級 I/O 常式會在發生錯誤時設定 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 全域變數。 當您使用低層級函式時，只有在程式需要於 STDIO.H 中定義之常數 (例如檔案結尾指標 **EOF**) 的情況下，才必須包含 STDIO.H。

## <a name="low-level-io-functions"></a>低層級 I/O 函式

|功能|使用|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|關閉檔案|
|[_commit](../c-runtime-library/reference/commit.md)|將檔案排清到磁碟|
|[_creat、_wcreat](../c-runtime-library/reference/creat-wcreat.md)|建立檔案|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|傳回指定檔案的下一個可用的檔案描述項|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|為指定檔案建立第二個描述項|
|[_eof](../c-runtime-library/reference/eof.md)|測試檔案結尾|
|[_lseek、_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|將檔案指標重新置放到指定位置|
|[_open、_wopen](../c-runtime-library/reference/open-wopen.md)|開啟檔案|
|[_read](../c-runtime-library/reference/read.md)|從檔案讀取資料|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)、 [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|針對檔案共用開啟檔案|
|[_tell、_telli64](../c-runtime-library/reference/tell-telli64.md)|取得目前檔案指標位置|
|[_umask](../c-runtime-library/reference/umask.md)、 [_umask_s](../c-runtime-library/reference/umask-s.md)|設定檔案權限遮罩|
|[_write](../c-runtime-library/reference/write.md)|將資料寫入檔案|

**_dup** 和 **_dup2** 通常是用來建立預先定義的檔案描述項與不同檔案的關聯。

## <a name="see-also"></a>另請參閱

[輸入和輸出](../c-runtime-library/input-and-output.md)<br/>
[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
[系統呼叫](../c-runtime-library/system-calls.md)<br/>
