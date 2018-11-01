---
title: unexpected (CRT)
ms.date: 11/04/2016
apiname:
- unexpected
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
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 78538c0a10e183e72c742b041b297275c0859a03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534014"
---
# <a name="unexpected-crt"></a>unexpected (CRT)

呼叫**終止**或您使用指定的函式**set_unexpected**。

## <a name="syntax"></a>語法

```C
void unexpected( void );
```

## <a name="remarks"></a>備註

**意外**常式不能搭配目前的 c + + 例外狀況處理實作。 **未預期**呼叫**終止**預設。 您可以變更此預設行為，方法是撰寫自訂中止函式，並呼叫**set_unexpected**您作為其引數的函式的名稱。 **未預期**呼叫最後一個指定為引數的函式**set_unexpected**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**unexpected**|\<eh.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
