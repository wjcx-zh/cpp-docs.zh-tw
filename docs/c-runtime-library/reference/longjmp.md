---
title: longjmp | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- longjmp
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
- longjmp
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 196f95ae134458f2eaf00ab037c3a560d1317515
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109681"
---
# <a name="longjmp"></a>longjmp

還原堆疊環境和執行地區設定來設定`setjmp`呼叫。

## <a name="syntax"></a>語法

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>參數

*env*<br/>
儲存環境的變數。

*值*<br/>
要傳回至 `setjmp` 呼叫的值。

## <a name="remarks"></a>備註

**Longjmp**函式會還原先前儲存的堆疊環境和執行地區設定*env*由`setjmp`。 `setjmp` 並**longjmp**可用來執行非區域**goto**; 它們通常用來執行控制項傳遞至之前所呼叫常式中的錯誤處理或復原程式碼，而不需使用一般的呼叫和傳回慣例。

呼叫`setjmp`導致儲存在目前的堆疊環境*env*。 後續呼叫**longjmp**還原已儲存的環境，並將控制權還給緊接在對應的點`setjmp`呼叫。 執行會繼續，就像是 `setjmp` 呼叫剛傳回 *value* 一樣。 接收控制項的常式可存取的所有變數 （暫存器變數） 除外的值包含的值時所擁有**longjmp**呼叫。 無法預測暫存器變數的值。 `setjmp` 所傳回的值必須為非零。 如果傳遞的 *value* 為 0，實際傳回時會以值 1 替代。

**Microsoft 專屬**

Windows，Microsoft c + + 程式碼中**longjmp**例外狀況處理程式碼會使用相同的堆疊回溯語意。 它會安全地使用 c + + 例外狀況可能會引發的相同位置中。 不過，這種用法可攜性，並不需要注意的一些重要的事項。

只呼叫**longjmp**呼叫的函式之前`setjmp`傳回; 否則會無法預測結果。

使用時，請注意下列限制**longjmp**:

- 請勿假設暫存器變數的值將保持不變。 例行性的呼叫中的暫存器變數的值`setjmp`可能不會還原為適當的值之後**longjmp**執行。

- 請勿使用**longjmp**將控制項移出中斷處理常式除非插斷浮點例外狀況所造成。 在此情況下，程式可能會從透過的插斷處理常式傳回**longjmp**如果它第一次重新初始化浮點數學套件藉由呼叫[_fpreset](fpreset.md)。

- 請勿使用**longjmp**將控制項從 Windows 程式碼直接或間接叫用的回呼常式。

- 如果程式碼會使用編譯 **/EHs**或 **/EHsc**和 包含的函式**longjmp**呼叫**noexcept**然後本機物件在該堆疊回溯期間，可能解構函式。

**結束 Microsoft 專屬**

> [!NOTE]
> 在可攜式 c + + 程式碼，您不能假設`setjmp`和`longjmp`支援 c + + 物件語意。 具體而言， `setjmp` / `longjmp`組有未定義行為，如果取代的呼叫`setjmp`並`longjmp`由**攔截**和**擲回**會叫用任何自動物件的任何非 trivial 解構函式。 在 c + + 程式中，我們建議您在使用 c + + 例外狀況處理機制。

如需詳細資訊，請參閱[使用 setjmp 和 longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_fpreset](fpreset.md) 的範例。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
