---
title: _purecall
ms.date: 4/2/2020
api_name:
- _purecall
- _o__purecall
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- purecall
- _purecall
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
ms.openlocfilehash: f841bc70a4a5365bb9cc6086dd752bd2a1b583ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338480"
---
# <a name="_purecall"></a>_purecall

預設的純虛擬函式呼叫錯誤處理常式。 呼叫純虛擬成員函式時，編譯器會產生程式碼以呼叫此函式。

## <a name="syntax"></a>語法

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>備註

**_purecall**函數是 Microsoft C++編譯器的特定於 Microsoft 的實現詳細資訊。 此函式不是由您的程式碼直接呼叫，而且沒有公用標頭宣告。 因為它是 C 執行階段程式庫的公用匯出，所以會在此進行說明。

呼叫純虛擬函式會產生錯誤，因為它有沒有實作。 呼叫純虛擬函數時,編譯器將生成代碼以呼叫 **_purecall**錯誤處理程式函數。 預設情況下 **,_purecall**終止程式。 在終止之前,如果已為進程設置了 **_purecall_handler**函數,**則_purecall**函數將調用該函數。 您可以為純虛擬函式呼叫安裝您自己的錯誤處理常式函式，以攔截它們，用於偵錯或報告目的。 要使用自己的錯誤處理程式,請創建具有 **_purecall_handler**簽名的函數,然後使用[_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)使其成為當前處理程式。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

**_purecall**函數沒有標頭聲明。 **_purecall_handler**類型def在 stdlib.h>中\<定義。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler、_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
