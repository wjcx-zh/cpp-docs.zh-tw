---
title: "_set_se_translator | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_se_translator"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_se_translator"
  - "set_se_translator"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_se_translator 函式"
  - "例外狀況處理, 變更"
  - "set_se_translator 函式"
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_se_translator
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制代碼 Win32 例外狀況 \(C\# 結構化例外狀況\) 做為 C\+\+ 語言的例外狀況。  
  
## 語法  
  
```  
_se_translator_function _set_se_translator(  
   _se_translator_function seTransFunction  
);  
```  
  
#### 參數  
 `seTransFunction`  
 您撰寫的 C 結構化例外狀況轉議器函式的指標。  
  
## 傳回值  
 傳回前一個由 `_set_se_translator` 註冊的轉譯器函式指標，如此前一個函式即可之後被還原。  如果先前函式未設定，則傳回值可用來還原預設行為；此值可能為 null。  
  
## 備註  
 `_set_se_translator` 函式提供處理 Win32 例外狀況 \(C 結構化例外狀況\) 做為 C\+\+ 型別的例外狀況。  允許每個 C 例外狀況由 C \+\+ `catch` 處理常式處理，先定義一個可使用或衍生的 C 例外狀況包裝函式類別，將特定的類別型別歸給 C 例外狀況。  若要使用這個類別，您必須安裝自訂例外狀況轉譯器函式，每當 C 例外狀況發生，該函式由內部例外狀況處理機制呼叫。  在您的轉譯器函式內，您可以擲回可由相符的 C\+\+ `catch` 處理常式所攔截所有型別的例外狀況。  
  
 使用 `_set_se_translator`時，您必須使用 [\/EHa](../../build/reference/eh-exception-handling-model.md) 。  
  
 若要指定自訂轉譯函式，請呼叫 `_set_se_translator`  函式 \(這個函式以轉譯函式的名稱為其單一引數\)。  您撰寫的轉譯器函式會在每個函式在堆疊上叫用時呼叫一次，該堆疊擁有 `try`  區塊。  沒有預設轉譯器函式。  
  
 您的轉譯器函式應該不會超過擲回 C\+\+ 型別例外狀況。  如果它做除了擲回以外的任何事件 \(例如寫入記錄檔\)，您的程式可能不會如預期般運作，因為轉譯器函式叫用次數是依平台而定。  
  
 在多執行緒環境中，轉譯器函式為每個執行緒分開維護。  每個新執行緒需要安裝它自己的轉譯器函式。  因此，每個執行緒負責自己的轉譯器處理。  `_set_se_translator`  是針對執行緒；另一個 DLL 可以安裝不同的轉換函式。  
  
 您撰寫的必須是原生編譯函式的 `seTransFunction` 函式 \(不使用 \/clr 編譯\)。  它必須採用不帶正負號的整數和指標至 Win32 `_EXCEPTION_POINTERS` 結構做為引數。  引數分別為重複的呼叫 Win32 API `GetExceptionCode` 和 `GetExceptionInformation` 函式傳回值。  
  
```  
typedef void (*_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );  
```  
  
 如果是 `_set_se_translator`，當動態連結至 CRT 會有影響；處理序中的另一個 DLL 可能呼叫 `_set_se_translator` 並用它取代您的處理常式。  
  
 當從 Managed 程式碼 \(以 \/clr 編譯的程式碼\) 或混合的原生和 Managed 程式碼中使用 `_set_se_translator`，請注意轉譯器會影響僅由機器碼產生的例外狀況。  在 Managed 程式碼所產生的任何 Managed 例外狀況 \(例如，當引發 `System::Exception`時\) 沒有透過轉譯器函式傳送。  使用 Win32 函式 `RaiseException` 或由系統例外狀況所造成的在 Managed 程式碼中引發的例外狀況，例如除以零例外狀況會透過轉譯器傳送。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_set_se_translator`|\<eh.h\>|  
  
 `_set_se_translator` 所提供的功能無法在與 [\/clr:pure](../../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項一起編譯的程式碼中取得。  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
```  
// crt_settrans.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <windows.h>  
#include <eh.h>  
  
void SEFunc();  
void trans_func( unsigned int, EXCEPTION_POINTERS* );  
  
class SE_Exception  
{  
private:  
    unsigned int nSE;  
public:  
    SE_Exception() {}  
    SE_Exception( unsigned int n ) : nSE( n ) {}  
    ~SE_Exception() {}  
    unsigned int getSeNumber() { return nSE; }  
};  
int main( void )  
{  
    try  
    {  
        _set_se_translator( trans_func );  
        SEFunc();  
    }  
    catch( SE_Exception e )  
    {  
        printf( "Caught a __try exception with SE_Exception.\n" );  
    }  
}  
void SEFunc()  
{  
    __try  
    {  
        int x, y=0;  
        x = 5 / y;  
    }  
    __finally  
    {  
        printf( "In finally\n" );  
    }  
}  
void trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )  
{  
    printf( "In trans_func.\n" );  
    throw SE_Exception();  
}  
```  
  
  **In trans\_func.**  
**In finally**  
**Caught a \_\_try exception with SE\_Exception.**   
## 範例  
 雖然 `_set_se_translator` 所提供的功能不會在 Managed 程式碼中，但在機器碼中使用這個對應仍是有可能的，即使該機器碼在 `/clr` 參數下編譯， 只要使用 `#pragma unmanaged` 指出機器碼 。  如果結構化的例外狀況會擲入對應的 Managed 程式碼，必須以 `pragma`標記產生和處理例外狀況的程式碼。  下列程式碼示範一個可能的用途。  如需詳細資訊，請參閱[Pragma 指示詞和 \_\_Pragma 關鍵字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。  
  
```  
// crt_set_se_translator_clr.cpp  
// compile with: /clr  
#include <windows.h>  
#include <eh.h>  
#include <assert.h>  
#include <stdio.h>  
  
int thrower_func(int i) {  
   int j = i/0;  
  return 0;  
}  
  
class CMyException{  
};  
  
#pragma unmanaged  
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS pExp )  
{  
printf("Translating the structured exception to a C++"  
             " exception.\n");  
throw CMyException();  
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
  
int main(int argc, char** argv) {  
    _set_se_translator(my_trans_func);  
    DoTest();  
    return 0;  
}  
```  
  
  **Translating the structured exception to a C\+\+ exception.**  
**攔截 CMyException。**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [例外狀況處理常式](../../c-runtime-library/exception-handling-routines.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)