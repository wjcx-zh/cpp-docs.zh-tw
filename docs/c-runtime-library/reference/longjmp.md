---
title: longjmp
ms.date: 08/14/2018
api_name:
- longjmp
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
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: b4527a29475f9e393dc5abf19b866d926bec2ccc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953134"
---
# <a name="longjmp"></a>longjmp

還原`setjmp`呼叫所設定的堆疊環境和執行地區設定。

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

**Longjmp**函數會還原先前儲存在`setjmp` *env*中的堆疊環境和執行地區設定。 `setjmp`和**longjmp**提供一種方法來執行非本機的**goto**;它們通常用來將執行控制傳遞給先前呼叫的常式中的錯誤處理或復原程式碼，而不需要使用正常的呼叫和傳回慣例。

的呼叫`setjmp`會導致目前的堆疊環境儲存在*env*中。 後續的**longjmp**呼叫會還原儲存的環境，並將控制權傳回給緊接在對應`setjmp`呼叫之後的點。 執行會繼續，就像是 `setjmp` 呼叫剛傳回 *value* 一樣。 常式接收控制項可存取的所有變數值（register 變數除外）包含呼叫**longjmp**時所擁有的值。 無法預測暫存器變數的值。 `setjmp` 所傳回的值必須為非零。 如果傳遞的 *value* 為 0，實際傳回時會以值 1 替代。

**Microsoft 專屬**

在 Windows C++上的 Microsoft 程式碼中， **longjmp**會使用相同的堆疊回溯語義做為例外狀況處理常式代碼。 可以安全地使用在引發C++例外狀況的相同位置。 不過，這種使用方式並不是可移植的，而且有一些重要的注意事項。

只在呼叫的`setjmp`函式之前呼叫 longjmp，否則結果會是無法預測的。

使用**longjmp**時，請注意下列限制：

- 請勿假設暫存器變數的值將保持不變。 在執行 longjmp 之後，可能無法將呼叫`setjmp`常式中的 register 變數值還原成適當的值。

- 除非中斷是因浮點例外狀況所造成，否則請不要使用**longjmp**將控制權轉移至中斷處理常式。 在此情況下，如果程式第一次藉由呼叫[_fpreset](fpreset.md)重新初始化浮點數學封裝，則可能會透過**longjmp**從中斷處理常式傳回。

- 請勿使用**longjmp** ，從 Windows 程式碼直接或間接叫用的回呼常式傳送控制權。

- 如果程式碼是使用 **/ehs**或 **/ehsc**進行編譯，而且包含**longjmp**呼叫的函式是**noexcept** ，則在堆疊回溯期間，可能不會解構該函式中的本機物件。

**結束 Microsoft 專屬**

> [!NOTE]
> 在可C++移植程式碼中， `setjmp`您`longjmp`無法C++假設和支持對象的語義。 具體而言， `setjmp`如果將/ `setjmp` `longjmp`和取代為 catch，而 throw 會針對任何自動物件叫用任何非一般的析構函數，則呼叫組會有未定義的行為。 `longjmp` 在C++ [ C++程式] 中，我們建議您使用例外狀況處理機制。

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
