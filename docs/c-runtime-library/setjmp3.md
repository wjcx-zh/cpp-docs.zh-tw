---
title: _setjmp3 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setjmp3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- setjmp3
- _setjmp3
dev_langs:
- C++
helpviewer_keywords:
- _setjmp3 function
- setjmp3 function
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72bc1e833ddaa72979e25274b7328d8987f62763
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setjmp3"></a>_setjmp3
內部 CRT 函式。 `setjmp` 函式的新實作。  
  
## <a name="syntax"></a>語法  
  
```  
int _setjmp3(  
   OUT jmp_buf env,  
   int count,  
   (optional parameters)  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `env`  
 用於儲存狀態資訊之緩衝區的位址。  
  
 [輸入] `count`  
 儲存在 `DWORD` 中之資訊的其他 `optional parameters` 數目。  
  
 [輸入] `optional parameters`  
 `setjmp` 內建函式向下推展的其他資料。 第一個 `DWORD` 是用於回溯額外資料並回復至非暫時性註冊狀態的函式指標。 第二個 `DWORD` 是要還原的嘗試層級。 所有進一步資料都會以泛型資料陣列儲存在 `jmp_buf` 中。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
## <a name="remarks"></a>備註  
 請勿在 C++ 程式中使用此函式。 這是不支援 C++ 的內建函式。 如需如何使用 `setjmp` 的詳細資訊，請參閱[使用 setjmp/longjmp](../cpp/using-setjmp-longjmp.md)。  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [setjmp](../c-runtime-library/reference/setjmp.md)