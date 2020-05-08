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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 19ad6c2f517d9ddf277a7bdda6e46c7940f0d3f1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913334"
---
# <a name="_purecall"></a>_purecall

預設的純虛擬函式呼叫錯誤處理常式。 呼叫純虛擬成員函式時，編譯器會產生程式碼以呼叫此函式。

## <a name="syntax"></a>語法

```C
extern "C" int __cdecl _purecall();
```

## <a name="remarks"></a>備註

**_Purecall**函式是 microsoft 特定的 Microsoft c + + 編譯器的執行詳細資料。 此函式不是由您的程式碼直接呼叫，而且沒有公用標頭宣告。 因為它是 C 執行階段程式庫的公用匯出，所以會在此進行說明。

呼叫純虛擬函式會產生錯誤，因為它有沒有實作。 呼叫純虛擬函式時，編譯器會產生程式碼來叫用 **_purecall**錯誤處理常式函式。 根據預設， **_purecall**會終止程式。 在終止之前， **_purecall**函式會叫用 **_purecall_handler**函式（如果已為進程設定一個函式）。 您可以為純虛擬函式呼叫安裝您自己的錯誤處理常式函式，以攔截它們，用於偵錯或報告目的。 若要使用您自己的錯誤處理常式，請建立具有 **_purecall_handler**簽章的函式，然後使用[_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)將它設為目前的處理常式。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

**_Purecall**函數沒有標頭宣告。 **_Purecall_handler** typedef 定義于 stdlib.h>> \<中。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](crt-alphabetical-function-reference.md)<br/>
[_get_purecall_handler、_set_purecall_handler](get-purecall-handler-set-purecall-handler.md)<br/>
