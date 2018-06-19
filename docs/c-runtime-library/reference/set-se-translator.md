---
title: _set_se_translator | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d4a5c9e86023ea47f23b648cad1a4dffedf905b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411516"
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

*seTransFunction*<br/>
所撰寫之 C 結構化例外狀況轉譯器函式的指標。

## <a name="return-value"></a>傳回值

傳回先前的轉譯器函式的指標註冊 **_set_se_translator**，如此一來，可以將其還原先前的函數。 如果尚未設定任何先前的函數，傳回的值可用來還原預設行為。這個值可以是**nullptr**。

## <a name="remarks"></a>備註

**_Set_se_translator**函式可用來為 c + + 中處理 Win32 例外狀況 （C 結構化例外狀況） 輸入例外狀況。 若要允許每個 C 例外狀況，由 c + +**攔截**處理常式，首先會定義 C 例外狀況包裝函式類別，可以使用，或衍生自，給特定類別類型的屬性設定為 C 例外狀況。 若要使用這個類別，請安裝內部例外狀況處理機制在每次引發 C 例外狀況時呼叫的自訂 C 例外狀況轉譯器函式。 在您翻譯工具函式中，您可以擲回任何類型的例外狀況可以攔截的比對的 c + +**攔截**處理常式。

您必須使用[/EHa](../../build/reference/eh-exception-handling-model.md)時使用 **_set_se_translator**。

若要指定自訂轉譯函式，呼叫 **_set_se_translator**做為其引數使用的轉譯函式名稱。 您撰寫的轉譯器函式呼叫一次，已經在堆疊上的每個函式引動過程**再試一次**區塊。 沒有預設轉譯器函式。

您的轉譯器函式只應該擲回 C++ 類型化例外狀況。 因為轉譯器函式的叫用次數與平台有關，所以如果它還執行擲回以外的作業 (例如，寫入記錄檔)，則程式可能無法如預期運作。

在多執行緒環境中，會分別維護每個執行緒的轉譯器函式。 每個新執行緒都需要安裝它自己的轉譯器函式。 因此，每個執行緒都會負責它自己的轉譯處理。 **_set_se_translator**特有一個執行緒; 另一個 DLL 可以安裝不同的轉譯函式。

*SeTransFunction*您撰寫的函式必須是原生編譯函式 （不是以 /clr 編譯）。 它必須採取的不帶正負號的整數和一個指標到 Win32 **_EXCEPTION_POINTERS**結構做為引數。 引數是對 Win32 API 呼叫的傳回值**GetExceptionCode**和**GetExceptionInformation**分別函式。

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

如 **_set_se_translator**，有影響動態連結到 CRT 的資訊時，另一個處理序中的 DLL 可能會呼叫 **_set_se_translator** ，並以它自己取代您的處理常式。

當使用 **_set_se_translator**從 managed 程式碼 （以 /clr 編譯的程式碼） 或混合的原生和 managed 程式碼，請注意，轉譯器會影響原生程式碼產生的例外狀況。 Managed 程式碼所產生的任何受管理例外狀況 (例如引發 `System::Exception` 時) 不會透過轉譯器函式進行傳遞。 在 managed 程式碼使用的 Win32 函式所引發的例外狀況**RaiseException**或系統例外狀況，像是透過轉譯器進行路由傳送 「 除以零的例外狀況所造成。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

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

雖然所提供的功能 **_set_se_translator**是以 managed 程式碼無法使用，便可使用這項對應原生程式碼，即使該原生程式碼是在編譯中 **/clr**參數，如原生程式碼會指出使用`#pragma unmanaged`。 如果結構化例外狀況被擲回對應的 managed 程式碼中，會產生和處理例外狀況的程式碼必須標示為`#pragma unmanaged`。 下列程式碼會示範可能用法。 如需詳細資訊，請參閱 [Pragma 指示詞和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

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

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
