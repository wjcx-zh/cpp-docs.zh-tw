---
title: setjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- setjmp
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
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc4673485577f5a12024d31e94063c82a8c7b8c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="setjmp"></a>setjmp

儲存程式的目前狀態。

## <a name="syntax"></a>語法

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>參數

*env*<br/>
儲存環境的變數。

## <a name="return-value"></a>傳回值

儲存堆疊環境之後，會傳回 0。 如果**setjmp**傳回的**longjmp**呼叫時，它會傳回**值**引數的**longjmp**，或如果**值**引數的**longjmp**為 0， **setjmp**傳回 1。 不會傳回錯誤。

## <a name="remarks"></a>備註

**Setjmp**函式會將儲存在堆疊環境中，您可以接著還原時，使用**longjmp**。 一起使用時， **setjmp**和**longjmp**提供一個方式來執行非區域**goto**。 它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用一般呼叫或傳回慣例。

呼叫**setjmp**將儲存在目前的堆疊環境*env*。 後續呼叫**longjmp**還原先前儲存的環境，並對應之後，立即將控制權傳回給點**setjmp**呼叫。 所有的變數 （除了暫存器變數） 常式，接收控制項存取包含這些應用程式啟動時的值**longjmp**呼叫。

不可能使用**setjmp**從 managed 程式碼的原生跳。

**請注意** **setjmp**和**longjmp**不支援 c + + 物件語意。 在 C++ 程式中，使用 C++ 例外狀況處理機制。

如需詳細資訊，請參閱[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_fpreset](fpreset.md) 的範例。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)<br/>
[_setjmp3](../../c-runtime-library/setjmp3.md)<br/>
