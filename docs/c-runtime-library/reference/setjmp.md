---
title: setjmp | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: 06073527aae8112d231dbd971b3daae35276efef
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42572344"
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

*env*  
儲存環境的變數。

## <a name="return-value"></a>傳回值

儲存堆疊環境之後，會傳回 0。 如果**setjmp**傳回的`longjmp`呼叫，它會傳回*值*引數`longjmp`，或如果*值*引數`longjmp`為 0，**setjmp**會傳回 1。 不會傳回錯誤。

## <a name="remarks"></a>備註

**Setjmp**函式會儲存堆疊環境中，您可以接著還原時，使用`longjmp`。 一起使用時， **setjmp**並`longjmp`提供方法來執行非區域**goto**。 它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用一般呼叫或傳回慣例。

呼叫**setjmp**儲存在目前的堆疊環境*env*。 後續呼叫`longjmp`還原已儲存的環境，並對應之後，立即將控制權還給點**setjmp**呼叫。 接收控制權之常式可存取的所有變數 (暫存器變數除外) 都會包含呼叫 `longjmp` 時所擁有的值。

不可以使用**setjmp**來從機器碼跳到 managed 程式碼。

**Microsoft 專屬**

Windows，Microsoft c + + 程式碼中**longjmp**例外狀況處理程式碼會使用相同的堆疊回溯語意。 它會安全地使用 c + + 例外狀況可能會引發的相同位置中。 不過，這種用法可攜性，並不需要注意的一些重要的事項。 如需詳細資訊，請參閱 < [longjmp](longjmp.md)。

**結束 Microsoft 專屬**

> [!NOTE]  
> 在可攜式 c + + 程式碼，您不能假設`setjmp`和`longjmp`支援 c + + 物件語意。 具體而言， `setjmp` / `longjmp`組有未定義行為，如果取代的呼叫`setjmp`並`longjmp`由**攔截**和**擲回**會叫用任何自動物件的任何非 trivial 解構函式。 在 c + + 程式中，我們建議您在使用 c + + 例外狀況處理機制。

如需詳細資訊，請參閱[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_fpreset](fpreset.md) 的範例。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)  
[longjmp](longjmp.md)  
