---
title: 例外狀況處理行為的差異-CLR
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: b84c51bc6adbb4fd879aadbca2856887e51fc401
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311656"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>在 /CLR 之下例外狀況處理行為的差異

[使用 Managed 例外狀況的基本概念](../dotnet/basic-concepts-in-using-managed-exceptions.md)討論 managed 應用程式中的例外狀況處理。 在本主題中會詳細討論例外狀況處理之標準行為差異和一些限制。 如需詳細資訊，請參閱[_Set_se_translator 函數](../c-runtime-library/reference/set-se-translator.md)。

##  <a name="vcconjumpingoutofafinallyblock"></a>跳出 Finally 區塊

在原生 CC++ /程式碼中，允許使用結構化例外狀況處理（SEH）跳出 __**finally**區塊，雖然它會產生警告。  在[/clr](../build/reference/clr-common-language-runtime-compilation.md)底下，跳出**finally**區塊會造成錯誤：

```cpp
// clr_exception_handling_4.cpp
// compile with: /clr
int main() {
   try {}
   finally {
      return 0;   // also fails with goto, break, continue
    }
}   // C3276
```

##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a>在例外狀況篩選準則中引發例外狀況

在 managed 程式碼內的[例外狀況篩選](../cpp/writing-an-exception-filter.md)處理期間引發例外狀況時，會攔截例外狀況，並將它視為篩選準則傳回0。

這與引發嵌套例外狀況的機器碼中的行為相反，已設定**EXCEPTION_RECORD**結構中的**ExceptionRecord**欄位（如[GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)所傳回），而**ExceptionFlags**欄位設定0x10 位。 以下範例說明行為中的差異：

```cpp
// clr_exception_handling_5.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

#ifndef false
#define false 0
#endif

int *p;

int filter(PEXCEPTION_POINTERS ExceptionPointers) {
   PEXCEPTION_RECORD ExceptionRecord =
                     ExceptionPointers->ExceptionRecord;

   if ((ExceptionRecord->ExceptionFlags & 0x10) == 0) {
      // not a nested exception, throw one
      *p = 0; // throw another AV
   }
   else {
      printf("Caught a nested exception\n");
      return 1;
    }

   assert(false);

   return 0;
}

void f(void) {
   __try {
      *p = 0;   // throw an AV
   }
   __except(filter(GetExceptionInformation())) {
      printf_s("We should execute this handler if "
                 "compiled to native\n");
    }
}

int main() {
   __try {
      f();
   }
   __except(1) {
      printf_s("The handler in main caught the "
               "exception\n");
    }
}
```

### <a name="output"></a>Output

```Output
Caught a nested exception
We should execute this handler if compiled to native
```

##  <a name="vccondisassociatedrethrows"></a>取消關聯重新擲回

**/clr**不支援重新擲回 catch 處理常式之外的例外狀況（稱為解除關聯重新擲回）。 這個類型的例外狀況會視為標準 C++ 重新擲回。 若在發生作用中 Managed 例外狀況時遇到取消關聯重新擲回，例外狀況會包裝為 C ++. 例外狀況，然後重新擲回。 此類型的例外狀況只能捕捉為類型<xref:System.Runtime.InteropServices.SEHException>的例外狀況。

下列範例示範 Managed 例外狀況重新擲回為 C ++. 例外狀況：

```cpp
// clr_exception_handling_6.cpp
// compile with: /clr
using namespace System;
#include <assert.h>
#include <stdio.h>

void rethrow( void ) {
   // This rethrow is a dissasociated rethrow.
   // The exception would be masked as SEHException.
   throw;
}

int main() {
   try {
      try {
         throw gcnew ApplicationException;
      }
      catch ( ApplicationException^ ) {
         rethrow();
         // If the call to rethrow() is replaced with
         // a throw statement within the catch handler,
         // the rethrow would be a managed rethrow and
         // the exception type would remain
         // System::ApplicationException
      }
   }

    catch ( ApplicationException^ ) {
      assert( false );

      // This will not be executed since the exception
      // will be masked as SEHException.
    }
   catch ( Runtime::InteropServices::SEHException^ ) {
      printf_s("caught an SEH Exception\n" );
    }
}
```

### <a name="output"></a>Output

```Output
caught an SEH Exception
```

##  <a name="vcconexceptionfiltersandexception_continue_execution"></a>例外狀況篩選準則和 EXCEPTION_CONTINUE_EXECUTION

如果篩選條件在 Managed 應用程式中傳回 `EXCEPTION_CONTINUE_EXECUTION`，則會視為篩選條件已傳回 `EXCEPTION_CONTINUE_SEARCH`。 如需這些常數的詳細資訊，請參閱[try-Except 語句](../cpp/try-except-statement.md)。

下列範例示範這項差異：

```cpp
// clr_exception_handling_7.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

int main() {
   int Counter = 0;
   __try {
      __try  {
         Counter -= 1;
         RaiseException (0xe0000000|'seh',
                         0, 0, 0);
         Counter -= 2;
      }
      __except (Counter) {
         // Counter is negative,
         // indicating "CONTINUE EXECUTE"
         Counter -= 1;
      }
    }
    __except(1) {
      Counter -= 100;
   }

   printf_s("Counter=%d\n", Counter);
}
```

### <a name="output"></a>Output

```Output
Counter=-3
```

##  <a name="vcconthe_set_se_translatorfunction"></a>_Set_se_translator 函式

由呼叫 `_set_se_translator` 設定的翻譯工具函式，只影響 Unmanaged 程式碼中的攔截。 下列範例示範此限制：

```cpp
// clr_exception_handling_8.cpp
// compile with: /clr /EHa
#include <iostream>
#include <windows.h>
#include <eh.h>
#pragma warning (disable: 4101)
using namespace std;
using namespace System;

#define MYEXCEPTION_CODE 0xe0000101

class CMyException {
public:
   unsigned int m_ErrorCode;
   EXCEPTION_POINTERS * m_pExp;

   CMyException() : m_ErrorCode( 0 ), m_pExp( NULL ) {}

   CMyException( unsigned int i, EXCEPTION_POINTERS * pExp )
         : m_ErrorCode( i ), m_pExp( pExp ) {}

   CMyException( CMyException& c ) : m_ErrorCode( c.m_ErrorCode ),
                                      m_pExp( c.m_pExp ) {}

   friend ostream& operator <<
                 ( ostream& out, const CMyException& inst ) {
      return out <<  "CMyException[\n" <<
             "Error Code: " << inst.m_ErrorCode <<  "]";
    }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS pExp ) {
   cout <<  "In my_trans_func.\n";
   throw CMyException( u, pExp );
}

#pragma managed
void managed_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE, 0, 0, 0 );
   }
   catch ( CMyException x ) {}
   catch ( ... ) {
      printf_s("This is invoked since "
               "_set_se_translator is not "
               "supported when /clr is used\n" );
    }
}

#pragma unmanaged
void unmanaged_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE,
                      0, 0, 0 );
   }
   catch ( CMyException x ) {
      printf("Caught an SEH exception with "
             "exception code: %x\n", x.m_ErrorCode );
    }
    catch ( ... ) {}
}

// #pragma managed
int main( int argc, char ** argv ) {
   _set_se_translator( my_trans_func );

   // It does not matter whether the translator function
   // is registered in managed or unmanaged code
   managed_func();
   unmanaged_func();
}
```

### <a name="output"></a>Output

```Output
This is invoked since _set_se_translator is not supported when /clr is used
In my_trans_func.
Caught an SEH exception with exception code: e0000101
```

## <a name="see-also"></a>另請參閱

[例外狀況處理](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)
