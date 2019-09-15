---
title: _set_se_translator
ms.date: 02/21/2018
api_name:
- _set_se_translator
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 781deaad091b6aed72350100f7575c566bbae793
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948387"
---
# <a name="_set_se_translator"></a>_set_se_translator

設定每個執行緒的回呼函式, 以將 Win32 例外狀況 (C 結構C++化例外狀況) 轉譯為具類型的例外狀況。

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

傳回 **_set_se_translator**所註冊之先前 translator 函式的指標，以便之後可以還原先前的函式。 如果未設定先前的函式, 則會使用傳回值來還原預設行為。這個值可以是**nullptr**。

## <a name="remarks"></a>備註

**_Set_se_translator**函式提供一種方法來處理 Win32 例外狀況（C 結構化C++例外狀況），做為具類型的例外狀況。 若要允許C++ **catch**處理常式處理每個 c 例外狀況, 請先定義可以使用或衍生自的 c 例外狀況包裝函式類別, 將特定類別類型的屬性設為 c 例外狀況。 若要使用這個類別，請安裝內部例外狀況處理機制在每次引發 C 例外狀況時呼叫的自訂 C 例外狀況轉譯器函式。 在您的 translator 函式內, 您可以擲回符合C++的**catch**處理常式可攔截的任何具類型的例外狀況。

使用 **_set_se_translator**時，您必須使用[/eha](../../build/reference/eh-exception-handling-model.md) 。

若要指定自訂轉譯函式，請使用轉譯函式的名稱做為其引數來呼叫 **_set_se_translator** 。 您撰寫的 translator 函式會針對堆疊上具有**try**區塊的每個函式呼叫呼叫一次。 沒有預設轉譯器函式。

您的轉譯器函式只應該擲回 C++ 類型化例外狀況。 因為轉譯器函式的叫用次數與平台有關，所以如果它還執行擲回以外的作業 (例如，寫入記錄檔)，則程式可能無法如預期運作。

在多執行緒環境中，會分別維護每個執行緒的轉譯器函式。 每個新執行緒都需要安裝它自己的轉譯器函式。 因此，每個執行緒都會負責它自己的轉譯處理。 **_set_se_translator**專門用於一個執行緒;另一個 DLL 可以安裝不同的轉譯功能。

您撰寫的*seTransFunction*函數必須是原生編譯的函式 (未以/clr 編譯)。 它必須採用不帶正負號的整數和 Win32 **_EXCEPTION_POINTERS**結構的指標做為引數。 引數是分別呼叫 WIN32 API **GetExceptionCode**和**GetExceptionInformation**函式的傳回值。

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

若為 **_set_se_translator**，則會在動態連結至 CRT 時造成影響;進程中的另一個 DLL 可能會呼叫 **_set_se_translator** ，並將您的處理常式取代為其本身。

從 managed 程式碼（以/clr 編譯的程式碼）使用 **_set_se_translator**或混合原生和 managed 程式碼時，請注意轉譯器只會影響機器碼中產生的例外狀況。 Managed 程式碼所產生的任何受管理例外狀況 (例如引發 `System::Exception` 時) 不會透過轉譯器函式進行傳遞。 使用 Win32 函式**RaiseException**或系統例外狀況 (例如零除的例外狀況) 所造成的 managed 程式碼中引發的例外狀況, 會透過翻譯工具進行路由傳送。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

這個範例會包裝呼叫來設定結構化例外狀況轉譯器, 並在 RAII 類別`Scoped_SE_Translator`中還原舊的。 此類別可讓您將特定範圍的轉譯程式引進為單一宣告。 當控制項離開範圍時, 類別的析構函式會還原原始的翻譯工具。

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
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
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

void trans_func( unsigned int u, EXCEPTION_POINTERS* )
{
    throw SE_Exception( u );
}

int main()
{
    Scoped_SE_Translator scoped_se_translator{ trans_func };
    try
    {
        SEFunc();
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught a __try exception, error %8.8x.\n", e.getSeNumber() );
    }
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>範例

雖然 **_set_se_translator**所提供的功能無法在 managed 程式碼中使用，但還是可以在機器碼中使用這個對應，即使該機器碼在 **/clr**參數下的編譯中，只要機器碼為使用`#pragma unmanaged`表示。 如果要對應的 managed 程式碼中擲回結構化例外狀況, 則產生和處理例外狀況的程式碼必須標記`#pragma unmanaged`為。 下列程式碼會示範可能用法。 如需詳細資訊，請參閱 [Pragma 指示詞和 __Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <stdio.h>
#include <exception>

int thrower_func( int i ) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS )
{
    throw SE_Exception( u );
}

void DoTest()
{
    try
    {
        thrower_func( 10 );
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught SE_Exception, error %8.8x\n", e.getSeNumber() );
    }
    catch(...)
    {
        printf( "Caught unexpected SEH exception.\n" );
    }
}
#pragma managed

int main() {
    Scoped_SE_Translator scoped_se_translator{ my_trans_func };

    DoTest();
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
