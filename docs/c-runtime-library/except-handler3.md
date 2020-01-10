---
title: _except_handler3
ms.date: 11/04/2016
api_name:
- _except_handler3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: 5e1dbab97e0f193d4ff59c19229d2c00e2cd7d6a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944474"
---
# <a name="_except_handler3"></a>_except_handler3

內部 CRT 函式。 供架構用於尋找適當的例外狀況處理常式以處理目前的例外狀況。

## <a name="syntax"></a>語法

```
int _except_handler3(
   PEXCEPTION_RECORD exception_record,
   PEXCEPTION_REGISTRATION registration,
   PCONTEXT context,
   PEXCEPTION_REGISTRATION dispatcher
);
```

#### <a name="parameters"></a>參數

*exception_record*<br/>
[in] 特定例外狀況的資訊。

*registration*<br/>
[in] 指出應該使用哪個範圍資料表尋找例外狀況處理常式的記錄。

*context*<br/>
[in] 保留。

*dispatcher*<br/>
[in] 保留。

## <a name="return-value"></a>傳回值

若應關閉例外狀況，則傳回 `DISPOSITION_DISMISS`。 若應將例外狀況往上傳遞一個層級至封裝例外狀況處理常式，則傳回 `DISPOSITION_CONTINUE_SEARCH`。

## <a name="remarks"></a>備註

若此方法找到適當的例外狀況處理常式，會將例外狀況傳遞至處理常式。 在此情況中，此方法不會回復至呼叫它的程式碼，且傳回值亦不相關。

## <a name="see-also"></a>另請參閱

[依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
