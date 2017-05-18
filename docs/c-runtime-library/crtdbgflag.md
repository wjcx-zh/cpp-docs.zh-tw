---
title: _crtDbgFlag | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
caps.latest.revision: 8
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 4f4c3a874d59095d620a04d5ebb6ac88e2bdfa66
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="crtdbgflag"></a>_CRTDBG_CHECK_CRT_DF
**_crtDbgFlag** 旗標包含五個位元欄位，可控制要追蹤、驗證、報告及傾印偵錯版本的堆積中多少記憶體。 旗標的位元欄位使用 [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 函式加以設定。 此旗標及其欄位會宣告於 Crtdbg.h 中。 只有當應用程式中已定義 [_DEBUG](../c-runtime-library/debug.md) 旗標時，才能使用此旗標。  
  
 如需搭配其他偵錯函式使用此旗標的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="see-also"></a>另請參閱  
 [控制旗標](../c-runtime-library/control-flags.md)
