---
title: _set_se_translator
ms.date: 02/21/2018
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
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 18ee500d7b884d1934c29dc91d9bcb03d507680d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356546"
---
# <a name="setsetranslator"></a>_set_se_translator

設定每個執行緒的回呼函數轉譯 Win32 例外狀況 （C 結構化例外狀況） 至C++類型的例外狀況。

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

傳回所註冊之先前轉譯器函式的指標 **_set_se_translator**，如此一來，稍後可以還原先前函式。 如果尚未設定先前函式，傳回的值可用來還原預設行為。這個值可以是**nullptr**。

## <a name="remarks"></a>備註

**_Set_se_translator**函式可用來處理 Win32 例外狀況 （C 結構化例外狀況），做為C++類型的例外狀況。 若要允許來處理每個 C 例外狀況C++**攔截**處理常式，首先會定義 C 例外狀況包裝函式類別，可以使用，或衍生自來的特定類別類型的屬性設為 C 例外狀況。 若要使用這個類別，請安裝內部例外狀況處理機制在每次引發 C 例外狀況時呼叫的自訂 C 例外狀況轉譯器函式。 在您的轉譯器函式，您可以擲回的相符就可以攔截任何類型化例外狀況C++**攔截**處理常式。

您必須使用[/EHa](../../build/reference/eh-exception-handling-model.md)使用時 **_set_se_translator**。

若要指定自訂轉譯函式，呼叫 **_set_se_translator**作為其引數使用的轉譯函式的名稱。 您撰寫的轉譯器函式會呼叫一次有在堆疊上的每個函式引動過程**嘗試**區塊。 沒有預設轉譯器函式。

您的轉譯器函式只應該擲回 C++ 類型化例外狀況。 因為轉譯器函式的叫用次數與平台有關，所以如果它還執行擲回以外的作業 (例如，寫入記錄檔)，則程式可能無法如預期運作。

在多執行緒環境中，會分別維護每個執行緒的轉譯器函式。 每個新執行緒都需要安裝它自己的轉譯器函式。 因此，每個執行緒都會負責它自己的轉譯處理。 **_set_se_translator**專為一個執行緒; 另一個 DLL 則可以安裝不同的轉譯函式。

*SeTransFunction*您撰寫的函式必須是原生編譯的函式 （不使用 /clr 所編譯）。 它必須採取 Win32 的不帶正負號的整數和指標 **_EXCEPTION_POINTERS**結構做為引數。 引數是 Win32 API 呼叫的傳回值**GetExceptionCode**並**GetExceptionInformation**分別函式。

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

針對 **_set_se_translator**，以動態方式連結至 CRT 時會有暗示; 處理序中的 DLL 可能會呼叫另一個 **_set_se_translator**並以您的處理常式取代為 自己。

使用時 **_set_se_translator**從 managed 程式碼 （使用 /clr 所編譯的程式碼） 或混合的原生和 managed 程式碼，請注意，轉譯器會影響原生程式碼產生的例外狀況。 Managed 程式碼所產生的任何受管理例外狀況 (例如引發 `System::Exception` 時) 不會透過轉譯器函式進行傳遞。 使用 Win32 函式的 managed 程式碼中引發的例外狀況**RaiseException**或系統例外狀況，例如除以零的例外狀況會路由傳送透過轉譯器所造成。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
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
#include <exception>

class SE_Exception : public std::exception
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

雖然所提供的功能 **_set_se_translator**是以 managed 程式碼無法使用，就可以使用此對應原生程式碼，即使該機器碼編譯 **/clr**切換，只要原生程式碼會指出使用`#pragma unmanaged`。 如果結構化例外狀況擲回之對應的 managed 程式碼中，會產生和處理例外狀況的程式碼必須標示`#pragma unmanaged`。 下列程式碼會示範可能用法。 如需詳細資訊，請參閱 [Pragma 指示詞和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>
#include <exception>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception {
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw SE_Exception(u);
}

void DoTest()
{
    try
    {
        thrower_func(10);
    }
    catch(SE_Exception& e)
    {
        printf("Caught SE_Exception, error %8.8x\n", e.getSeNumber());
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
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>另請參閱

[例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
