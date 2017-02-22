---
title: "在 /CLR 之下例外狀況處理行為的差異 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXCEPTION_CONTINUE_EXECUTION 巨集"
  - "set_se_translator 函式"
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# 在 /CLR 之下例外狀況處理行為的差異
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[在使用 Managed 例外狀況的基本概念](../dotnet/basic-concepts-in-using-managed-exceptions.md) 在 Managed 應用程式討論例外處理。  本主題中，從例外狀況處理標準行為的差異和一些限制詳細討論。  如需詳細資訊，請參閱 [\_set\_se\_translator 函式](../c-runtime-library/reference/set-se-translator.md)。  
  
##  <a name="vcconjumpingoutofafinallyblock"></a> 跳出 finally 區塊  
 用原生 C\/C\+\+ 程式碼，跳出**finally** 區塊使用處理 \(SEH\) 的結構化例外狀況允許，雖然它產生警告。在 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)下，跳出 **finally** 區塊會產生錯誤:  
  
```  
// clr_exception_handling_4.cpp  
// compile with: /clr  
int main() {  
   try {}  
   finally {  
      return 0;   // also fails with goto, break, continue  
    }  
}   // C3276  
```  
  
##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a> 會在例外狀況篩選條件內的例外狀況。  
 在處理在 Managed 程式碼中，的 [例外狀況篩選條件](../cpp/writing-an-exception-filter.md) 引發例外狀況，例外狀況並被視為，當做篩選條件會傳回 0。  
  
 這是與行為要用巢狀例外狀況發生的機器碼， **EXCEPTION\_RECORD** 結構的 **ExceptionRecord** 欄位 \(如傳回 [GetExceptionInformation](http://msdn.microsoft.com/library/windows/desktop/ms679357)\) 設定和 **ExceptionFlags** 欄位集合 0x10 位元。  以下範例會說明兩者之間的差異:  
  
```  
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
  
### Output  
  
```  
Caught a nested exception  
We should execute this handler if compiled to native  
```  
  
##  <a name="vccondisassociatedrethrows"></a> 分隔重新擲回  
 **\/clr** 不支援重新擲回一個例外狀況在 Catch 處理常式外 \(稱為一分隔重新擲回\)。  這個型別的例外狀況視為標準 C\+\+ 重新擲回。  如果一分隔重新擲回時，發生有使用中的 Managed 例外狀況時，例外狀況包裝在 C \+\+. 例外狀況會重新擲回。  這個型別的例外狀況可能只會攔截做為 [System::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx)型別的例外狀況。  
  
 下列範例會示範 Managed 例外狀況重新擲回當 C \+\+. 例外狀況:  
  
```  
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
  
### Output  
  
```  
caught an SEH Exception  
```  
  
##  <a name="vcconexceptionfiltersandexception_continue_execution"></a> 例外濾器和 EXCEPTION\_CONTINUE\_EXECUTION ：例外狀況已解除  
 如果篩選條件會在 Managed 應用程式的 `EXCEPTION_CONTINUE_EXECUTION` ，則會將它視為，好像篩選傳回 `EXCEPTION_CONTINUE_SEARCH`。  如需這些常數的詳細資訊，請參閱 [嘗試除了陳述式](../cpp/try-except-statement.md)。  
  
 下列範例說明此差異：  
  
```  
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
  
### Output  
  
```  
Counter=-3  
```  
  
##  <a name="vcconthe_set_se_translatorfunction"></a> \_set\_se\_translator 函式  
 轉譯器函式，在 Unmanaged 程式碼是呼叫 `_set_se_translator`只影響集合攔截。  下列範例說明此限制：  
  
```  
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
  
### Output  
  
```  
This is invoked since _set_se_translator is not supported when /clr is used  
In my_trans_func.  
Caught an SEH exception with exception code: e0000101  
```  
  
## 請參閱  
 [Exception Handling](../windows/exception-handling-cpp-component-extensions.md)   
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)