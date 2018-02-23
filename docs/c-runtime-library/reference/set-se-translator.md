---
title: _set_se_translator | Microsoft Docs
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_se_translator
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
- _set_se_translator
- set_se_translator
dev_langs:
- C++
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b5eec59acfe65189368a9b0555c3065b7159aae
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2018
---
# <a name="setsetranslator"></a>_set_se_translator

設定要轉譯成 c + + 的 Win32 例外狀況 （C 結構化例外狀況） 的每個執行緒回呼函式具類型的例外狀況。

## <a name="syntax"></a>語法

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>參數

*seTransFunction*  
所撰寫之 C 結構化例外狀況轉譯器函式的指標。

## <a name="return-value"></a>傳回值

傳回 `_set_se_translator` 所註冊之先前轉譯器函式的指標，因此，稍後可以還原先前函式。 如果尚未設定任何先前的函數，傳回的值可用來還原預設行為。這個值可以是**nullptr**。

## <a name="remarks"></a>備註

`_set_se_translator` 函式提供一種方式，以 C++ 類型化例外狀況處理 Win32 例外狀況 (C 結構化例外狀況)。 若要允許 C++ `catch` 處理常式處理每個 C 例外狀況，請先定義 C 例外狀況包裝函式類別，使用或衍生自這個類別即可將特定類別類型的屬性設為 C 例外狀況。 若要使用這個類別，請安裝內部例外狀況處理機制在每次引發 C 例外狀況時呼叫的自訂 C 例外狀況轉譯器函式。 在轉譯器函式內，您可以擲回相符 C++ `catch` 處理常式可攔截的任何類型化例外狀況。

使用 `_set_se_translator` 時，您必須使用 [/EHa](../../build/reference/eh-exception-handling-model.md)。

若要指定自訂轉譯函式，呼叫`_set_se_translator`做為其引數使用的轉譯函式名稱。 每次在包含 `try` 區塊的堆疊叫用函式時，都會呼叫您所撰寫的轉譯器函式。 沒有預設轉譯器函式。

您的轉譯器函式只應該擲回 C++ 類型化例外狀況。 因為轉譯器函式的叫用次數與平台有關，所以如果它還執行擲回以外的作業 (例如，寫入記錄檔)，則程式可能無法如預期運作。

在多執行緒環境中，會分別維護每個執行緒的轉譯器函式。 每個新執行緒都需要安裝它自己的轉譯器函式。 因此，每個執行緒都會負責它自己的轉譯處理。 `_set_se_translator` 是其中一個執行緒所特有；另一個 DLL 則可以安裝不同的轉譯函式。

*SeTransFunction*您撰寫的函式必須是原生編譯函式 （不是以 /clr 編譯）。 它必須接受不帶正負號的整數以及 Win32 `_EXCEPTION_POINTERS` 結構的指標作為引數。 這些引數分別是呼叫 Win32 API `GetExceptionCode` 和 `GetExceptionInformation` 函式的傳回值。

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

對於 `_set_se_translator`，在動態連結至 CRT 時會有暗示；處理序中的另一個 DLL 可能會呼叫 `_set_se_translator`，並將您的處理常式取代為它自己的處理常式。

透過 Managed 程式碼 (使用 /clr 編譯的程式碼) 或混合機器碼和 Managed 程式碼使用 `_set_se_translator` 時，請注意轉譯器只會影響機器碼所產生的例外狀況。 Managed 程式碼所產生的任何受管理例外狀況 (例如引發 `System::Exception` 時) 不會透過轉譯器函式進行傳遞。 使用 Win32 函式 `RaiseException` 於 Managed 程式碼中所引發的例外狀況，或系統例外狀況所造成的除以零例外狀況這類例外狀況，都是透過轉譯器所傳遞。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|`_set_se_translator`|\<eh.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class SE_Exception
{
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception( unsigned int n ) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func(unsigned int u, EXCEPTION_POINTERS*)
{
    throw SE_Exception(u);
}

int main()
{
    auto original = _set_se_translator(trans_func); 
    try
    {
        SEFunc();
    }
    catch(SE_Exception& e)
    {
        printf("Caught a __try exception, error %8.8x.\n", e.getSeNumber());
    }
    _set_se_translator(original);
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>範例

只要使用 `#pragma unmanaged` 來表示機器碼，雖然無法透過 Managed 程式碼使用 `_set_se_translator` 所提供的功能，但是可能會透過機器碼使用此對應，即使該機器碼正在透過 `/clr` 參數編譯也是一樣。 如果結構化例外狀況被擲回對應的 managed 程式碼中，會產生和處理例外狀況的程式碼必須標示為`#pragma unmanaged`。 下列程式碼會示範可能用法。 如需詳細資訊，請參閱 [Pragma 指示詞和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class CMyException{
private:
    unsigned int nSE;
public:
    CMyException() : nSE{ 0 } {}
    CMyException(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw CMyException(u);
}

void DoTest()
{
    try
    {
        thrower_func(10);
    }
    catch(CMyException e)
    {
        printf("Caught CMyException.\n");
    }
    catch(...)
    {
        printf("Caught unexpected SEH exception.\n");
    }
}
#pragma managed

int main() {
    auto original = _set_se_translator(my_trans_func);
    DoTest();
    _set_se_translator(original);
}
```

```Output
Caught CMyException, error c0000094
```

## <a name="see-also"></a>另請參閱

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)  
[set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)  
[set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)  
[terminate](../../c-runtime-library/reference/terminate-crt.md)  
[unexpected](../../c-runtime-library/reference/unexpected-crt.md)  
