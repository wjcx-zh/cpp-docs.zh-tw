---
title: _purecall | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _purecall
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
dev_langs:
- C++
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c19324cde907f31ab18a312f3039c2da7a3a40c7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="purecall"></a>_purecall
預設的純虛擬函式呼叫錯誤處理常式。 呼叫純虛擬成員函式時，編譯器會產生程式碼以呼叫此函式。  
  
## <a name="syntax"></a>語法  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## <a name="remarks"></a>備註  
 `_purecall` 函式是 Microsoft Visual C++ 編譯器的 Microsoft 特定實作詳細資料。 此函式不是由您的程式碼直接呼叫，而且沒有公用標頭宣告。 因為它是 C 執行階段程式庫的公用匯出，所以會在此進行說明。  
  
 呼叫純虛擬函式會產生錯誤，因為它有沒有實作。 呼叫純虛擬函式時，編譯器會產生程式碼以叫用 `_purecall` 錯誤處理函式。 根據預設，`_purecall` 會終止程式。 終止前，`_purecall` 函式會叫用 `_purecall_handler` 函式 (如果已針對處理序設定一個函式)。 您可以為純虛擬函式呼叫安裝您自己的錯誤處理函式，以攔截它們，用於偵錯或報告目的。 若要使用您自己的錯誤處理常式，請建立具有 `_purecall_handler` 簽章的函式，然後使用 [_set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) 使其成為目前的處理常式。  
  
## <a name="requirements"></a>需求  
 `_purecall` 函式沒有標頭宣告。 `_purecall_handler` typedef 定義於 \<stdlib.h> 中。  
  
## <a name="see-also"></a>請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_purecall_handler、_set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)