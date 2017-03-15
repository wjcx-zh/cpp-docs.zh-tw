---
title: "低層級 I/O | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案控制代碼 [C++]"
  - "檔案控制代碼 [C++], I/O 函式"
  - "I/O [CRT], 函式"
  - "I/O [CRT], 低層級"
  - "低層級 I/O 常式"
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 低層級 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些函式直接從低階作業呼叫作業系統而非從I\/O資料流所提供的作業。  低階輸入和輸出呼叫並不暫存也不格式化資料。  
  
 低階常式可以使用下列預先定義的檔案描述以存取在程式啟動時開啟的標準資料流。  
  
|資料流|檔案描述項。|  
|---------|------------|  
|`stdin`|0|  
|`stdout`|1|  
|`stderr`|2|  
  
 在發生錯誤時，低階 I\/O 常式會設定 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 全域變數。  當您使用低階函式時，只有在您的程式需要在 STDIO.H 定義的常數，例如檔案結尾標記 \(`EOF`\)，的時候您必須包含 STDIO.H，。  
  
### 低階 I\/O 函式  
  
|功能|用法|  
|--------|--------|  
|[\_close](../c-runtime-library/reference/close.md)|Close file|  
|[\_commit](../c-runtime-library/reference/commit.md)|磁碟有足夠的檔案|  
|[\_creat、\_wcreat](../c-runtime-library/reference/creat-wcreat.md)|建立檔案|  
|[\_dup](../c-runtime-library/reference/dup-dup2.md)|回傳下個可用的檔案描述給指定的檔案|  
|[\_dup2](../c-runtime-library/reference/dup-dup2.md)|建立特定檔案的第二個描述項|  
|[\_eof](../c-runtime-library/reference/eof.md)|測試檔案結尾|  
|[\_lseek、\_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|重新定位檔案指標到特定位置|  
|[\_open, \_wopen](../c-runtime-library/reference/open-wopen.md)|Open file|  
|[\_read](../c-runtime-library/reference/read.md)|從檔案讀取資料|  
|[\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md), [\_sopen\_s、\_wsopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|開啟檔案以共用|  
|[\_tell, \_telli64](../c-runtime-library/reference/tell-telli64.md)|取得目前檔案指標位置|  
|[\_umask](../c-runtime-library/reference/umask.md), [\_umask\_s](../c-runtime-library/reference/umask-s.md)|設定檔案權限遮罩|  
|[\_write](../c-runtime-library/reference/write.md)|寫入檔案的資料|  
  
 `_dup` 和 `_dup2` 通常用以連結 預先定義的檔案描述與不同檔案。  
  
## 請參閱  
 [輸入和輸出](../c-runtime-library/input-and-output.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [系統呼叫](../c-runtime-library/system-calls.md)