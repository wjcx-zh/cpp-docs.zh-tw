---
title: stdin、stdout、stderr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- stdin
- stderr
- stdout
dev_langs:
- C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f6226a6e38326a39ce2921e2a0d6219d01f005b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="stdin-stdout-stderr"></a>stdin、stdout、stderr
## <a name="syntax"></a>語法  
  
```  
  
      FILE *stdin;   
FILE *stdout;   
FILE *stderr;   
#include <stdio.h>  
```  
  
## <a name="remarks"></a>備註  
 這些是輸入、輸出和錯誤輸出的標準資料流。  
  
 根據預設，標準輸入是從鍵盤讀取，而標準輸出與標準錯誤則會列印至螢幕。  
  
 下列資料流指標可用來存取標準資料流：  
  
|Pointer|資料流|  
|-------------|------------|  
|`stdin`|標準輸入|  
|**stdout**|標準輸出|  
|`stderr`|標準錯誤|  
  
 這些指標可以作為函式的引數使用。 某些函式 (例如 **getchar** 和 `putchar`) 會自動使用 `stdin` 和 **stdout**。  
  
 這些指標是常數，且無法指派新值給它們。 `freopen` 函式可用來將資料流重新導向到磁碟檔案或其他裝置。 作業系統可讓您在命令層級對程式的標準輸入和輸出進行重新導向。  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../c-runtime-library/stream-i-o.md)   
 [全域常數](../c-runtime-library/global-constants.md)