---
title: 呼叫慣例、參數和傳回型別
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: 8343c17828040ca36b042cb99e0c51c37548d3b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654424"
---
# <a name="calling-conventions-parameters-and-return-type"></a>呼叫慣例、參數和傳回型別

Helper 常式的原型是：

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>參數

*pidd*<br/>
`const` 指標指向 `ImgDelayDescr` (請參閱 delayimp.h)，其中包含各種匯入相關資料的位移、繫結資訊的時間戳記，以及一組提供描述元內容之進一步資訊的屬性。 目前只有一個屬性 `dlattrRva`，它指出描述元中的位址是相對的虛擬位址 (與虛擬位址相反)。

定義`PCImgDelayDescr`結構，請參閱[結構和常數定義](../../build/reference/structure-and-constant-definitions.md)。

*ppfnIATEntry*<br/>
延遲載入匯入位址資料表 (IAT) 中的位置指標，要以匯入的函式位址更新。 Helper 常式需要儲存它將傳回此位置的相同值。

## <a name="expected-return-values"></a>預期的傳回值

如果函式成功，它會傳回匯入函式的位址。

如果函式失敗，則會引發例外狀況並傳回 0。 可以引發的例外狀況有三種：

- 參數無效，發生在 `pidd` 中的屬性未正確指定時。

- 指定 DLL 上的 `LoadLibrary` 失敗

- `GetProcAddress` 失敗。

您要負責處理這些例外狀況。

## <a name="remarks"></a>備註

Helper 函式的呼叫慣例是 `__stdcall`。 傳回值的類型不相關，因此使用 FARPROC。 此函式具有 C 連結。

延遲載入 Helper 的傳回值需要儲存在傳入的函式指標位置，除非您想要讓 Helper 函式用來作為通知攔截函式。 在那種情況下，您的程式碼要負責尋找適合傳回的函式指標。 連結器產生的 Thunk 程式碼便會以該傳回值作為匯入的真實目標，並直接跳到該處。

## <a name="sample"></a>範例

下列程式碼示範如何實作簡單的攔截函式。

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere
PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>另請參閱

[了解協助協助程式函式](../../build/reference/understanding-the-helper-function.md)