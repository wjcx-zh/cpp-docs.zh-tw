---
title: setjmp
description: 適用于 setjmp 的 API 參考;這會儲存程式的目前狀態。
ms.date: 08/14/2018
api_name:
- setjmp
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
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: 3ea08e5379433e313e08870f735322b7d985aa64
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555601"
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

*Env*<br/>
儲存環境的變數。

## <a name="return-value"></a>傳回值

儲存堆疊環境之後，會傳回 0。 如果 **setjmp** 傳回做為呼叫的結果 `longjmp` ，它會傳回的 *值* 引數 `longjmp` ，或者如果的 *值* 引數 `longjmp` 為0，則 **setjmp** 會傳回1。 不會傳回錯誤。

## <a name="remarks"></a>備註

**Setjmp**函式會儲存堆疊環境，之後您可以使用來還原該環境 `longjmp` 。 搭配使用時， **setjmp** 和 `longjmp` 提供方法來執行非本機 **`goto`** 。 它們通常用於將執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不使用一般呼叫或傳回慣例。

對 **setjmp** 的呼叫會將目前的堆疊環境儲存在 *env*中。 後續的呼叫會 `longjmp` 還原儲存的環境，並將控制權傳回給緊接在對應的 **setjmp** 呼叫之後的時間點。 接收控制權之常式可存取的所有變數 (暫存器變數除外) 都會包含呼叫 `longjmp` 時所擁有的值。

您無法使用 **setjmp** 從原生跳至 managed 程式碼。

**Microsoft 特定的**

在 Windows 上的 Microsoft c + + 程式碼中， **longjmp** 會使用相同的堆疊回溯語義作為例外狀況處理常式代碼。 您可以安全地在可引發 c + + 例外狀況的相同位置中使用。 不過，這種使用方式不是可移植的，而且會有一些重要的警告。 如需詳細資訊，請參閱 [longjmp](longjmp.md)。

**結束 Microsoft 專有**

> [!NOTE]
> 在可移植的 c + + 程式碼中，您無法假設 `setjmp` 和 `longjmp` 支援 c + + 物件語義。 明確地說， `setjmp` / `longjmp` 如果將和取代為，呼叫組會有未定義的行為， `setjmp` `longjmp` **`catch`** 而且 **`throw`** 會針對任何自動物件叫用任何非一般的析構函數。 在 c + + 程式中，我們建議使用 c + + 例外狀況處理機制。

如需詳細資訊，請參閱[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_fpreset](fpreset.md) 的範例。

## <a name="see-also"></a>另請參閱

[流程式控制制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
