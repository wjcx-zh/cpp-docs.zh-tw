---
title: "_nolock 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- _nolock functions
- nolock functions
ms.assetid: 7d651d87-38d2-4303-9897-fdb5f7a3e899
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: b1a3e559bd3060bd29b62b07c7b47cd17ea5d3c0
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="nolock-functions"></a>_nolock 函式
這些是不會執行任何鎖定的函式。 它們專供需要最大效能的使用者使用。 如需詳細資訊，請參閱[多執行緒程式庫效能](../c-runtime-library/multithreaded-libraries-performance.md)。  
  
 只有在程式確實為單一執行緒，或是會自行進行鎖定的情況下，您才應該使用 _nolock 函式。  
  
 [_fclose_nolock](../c-runtime-library/reference/fclose-nolock.md)  
  
 [_fflush_nolock](../c-runtime-library/reference/fflush-nolock.md)  
  
 [_fgetc_nolock、_fgetwc_nolock](../c-runtime-library/reference/fgetc-nolock-fgetwc-nolock.md)  
  
 [_fread_nolock](../c-runtime-library/reference/fread-nolock.md)  
  
 [_fseek_nolock、_fseeki64_nolock](../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)  
  
 [_ftell_nolock、_ftelli64_nolock](../c-runtime-library/reference/ftell-nolock-ftelli64-nolock.md)  
  
 [_fwrite_nolock](../c-runtime-library/reference/fwrite-nolock.md)  
  
 [_getc_nolock、_getwc_nolock](../c-runtime-library/reference/getc-nolock-getwc-nolock.md)  
  
 [_getch_nolock、_getwch_nolock](../c-runtime-library/reference/getch-nolock-getwch-nolock.md)  
  
 [_getchar_nolock、_getwchar_nolock](../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md)  
  
 [_getche_nolock、_getwche_nolock](../c-runtime-library/reference/getche-nolock-getwche-nolock.md)  
  
 [_getdcwd_nolock、_wgetdcwd_nolock](../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md)  
  
 [_putc_nolock、_putwc_nolock](../c-runtime-library/reference/putc-nolock-putwc-nolock.md)  
  
 [_putch_nolock、_putwch_nolock](../c-runtime-library/reference/putch-nolock-putwch-nolock.md)  
  
 [_putchar_nolock、_putwchar_nolock](../c-runtime-library/reference/putchar-nolock-putwchar-nolock.md)  
  
 [_ungetc_nolock、_ungetwc_nolock](../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)  
  
 [_ungetch_nolock、_ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)  
  
## <a name="see-also"></a>另請參閱  
 [輸入和輸出](../c-runtime-library/input-and-output.md)   
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
