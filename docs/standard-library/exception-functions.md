---
title: "&lt;exception&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
caps.latest.revision: "12"
manager: ghogen
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: 616c8d4dd0982f0cd96a3678f6f8595b074f291f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ltexceptiongt-functions"></a>&lt;exception&gt; 函式
||||  
|-|-|-|  
|[current_exception](#current_exception)|[get_terminate](#get_terminate)|[get_unexpected](#get_unexpected)|  
|[make_exception_ptr](#make_exception_ptr)|[rethrow_exception](#rethrow_exception)|[set_terminate](#set_terminate)|  
|[set_unexpected](#set_unexpected)|[terminate](#terminate)|[uncaught_exception](#uncaught_exception)|  
|[unexpected](#unexpected)|  
  
##  <a name="current_exception"></a>  current_exception  
 取得目前例外狀況的智慧型指標。  
  
```cpp  
exception_ptr current_exception();
```  
  
### <a name="return-value"></a>傳回值  
 指向目前例外狀況的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) 物件。  
  
### <a name="remarks"></a>備註  
 在 catch 區塊中呼叫 `current_exception` 函式。 如果例外狀況正在進行中，而且 catch 區塊可以攔截例外狀況，則 `current_exception` 函式會傳回參考例外狀況的 `exception_ptr` 物件。 否則，函式會傳回 Null `exception_ptr` 物件。  
  
 不論 `catch` 陳述式是否指定[例外狀況宣告](../cpp/try-throw-and-catch-statements-cpp.md)陳述式，`current_exception` 函式都會擷取執行中的例外狀況。  
  
 若不重新擲回例外狀況，則會在 `catch` 區塊結尾呼叫目前例外狀況的解構函式。 不過，即使在解構函式中呼叫 `current_exception` 函式，該函式仍會傳回參考目前例外狀況的 `exception_ptr` 物件。  
  
 `current_exception` 函式的後續呼叫會傳回參考目前例外狀況不同複本的 `exception_ptr` 物件。 因此，物件比較結果會是不相等，因為兩者參考不同的複本 (即使複本的二進位值相同也一樣)。  
  
##  <a name="make_exception_ptr"></a>  make_exception_ptr  
 建立持有例外狀況複本的 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) 物件。  
  
```cpp  
template <class E>  
exception_ptr make_exception_ptr(E Except);
```  
  
### <a name="parameters"></a>參數  
 `Except`  
 具有待複製例外狀況的類別。 雖然任何類別物件都可以是 `make_exception_ptr` 函式的引數，但一般會指定 [exception 類別](../standard-library/exception-class.md)物件作為其引數。  
  
### <a name="return-value"></a>傳回值  
 [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) 物件，指向 `Except` 的目前例外狀況複本。  
  
### <a name="remarks"></a>備註  
 呼叫 `make_exception_ptr` 函式相當於擲回 C++ 例外狀況、在 catch 區塊中攔截例外狀況，然後呼叫 [current_exception](../standard-library/exception-functions.md#current_exception) 函式以傳回參考例外狀況的 `exception_ptr` 物件。 Microsoft 實作`make_exception_ptr` 函式比在擲回例外狀況之後攔截來得更有效率。  
  
 一般來說，應用程式通常不需要使用 `make_exception_ptr` 函式，所以我們不建議使用此功能。  
  
##  <a name="rethrow_exception"></a>  rethrow_exception  
 擲回做為參數傳遞的例外狀況。  
  
```cpp  
void rethrow_exception(exception_ptr P);
```  
  
### <a name="parameters"></a>參數  
 `P`  
 要重新擲回的已攔截例外狀況。 如果 `P` 是 null [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)，函式會擲回 [std::bad_exception](../standard-library/bad-exception-class.md)。  
  
### <a name="remarks"></a>備註  
 將攔截到的例外狀況儲存在 `exception_ptr` 物件之後，主執行緒即可處理物件。 在主執行緒中呼叫 `rethrow_exception` 函式，並使用 `exception_ptr` 物件做為其引數。 `rethrow_exception` 函式會從 `exception_ptr` 物件擷取例外狀況，然後在主執行緒的內容中擲回該例外狀況。  
  
##  <a name="get_terminate"></a>  get_terminate  
 取得目前的 `terminate_handler` 函式。  
  
```cpp  
terminate_handler get_terminate();
```  
  
##  <a name="set_terminate"></a>  set_terminate  
 建立新 `terminate_handler`，在程式終止時呼叫。  
  
```  
terminate_handler set_terminate(terminate_handler fnew) throw();
```  
  
### <a name="parameters"></a>參數  
 `fnew`  
 要在終止時呼叫的函式。  
  
### <a name="return-value"></a>傳回值  
 先前用來在終止時呼叫的函式位址。  
  
### <a name="remarks"></a>備註  
 此函式會將新的 [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) 建立為 * `fnew` 函式。 因此，`fnew` 不能是 null 指標。 此函數會傳回上一個終止處理常式的位址。  
  
### <a name="example"></a>範例  
  
```cpp  
// exception_set_terminate.cpp  
// compile with: /EHsc  
#include <exception>  
#include <iostream>  
  
using namespace std;  
  
void termfunction()  
{  
    cout << "My terminate function called." << endl;  
    abort();  
}  
  
int main()  
{  
    terminate_handler oldHandler = set_terminate(termfunction);  
  
    // Throwing an unhandled exception would also terminate the program  
    // or we could explicitly call terminate();  
  
    //throw bad_alloc();  
    terminate();  
}  
  
```  
  
##  <a name="get_unexpected"></a>  get_unexpected  
 取得目前的 `unexpected_handler` 函式。  
  
```cpp  
unexpected_handler get_unexpected();
```  
  
##  <a name="set_unexpected"></a>  set_unexpected  
 建立新的 `unexpected_handler`，當未預期的例外狀況發生時擲回。  
  
```  
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```  
  
### <a name="parameters"></a>參數  
 `fnew`  
 當未預期的例外狀況發生時要呼叫的函式。  
  
### <a name="return-value"></a>傳回值  
 上一個 `unexpected_handler` 的位址。  
  
### <a name="remarks"></a>備註  
 `fnew` 不能是 null 指標。  
  
 C++ 標準要求在函式擲回例外狀況時，必須呼叫 `unexpected`。 目前的實作不支援此項目。 下列範例會直接呼叫 `unexpected`，這會引發呼叫 `unexpected_handler`。  
  
### <a name="example"></a>範例  
  
```cpp  
// exception_set_unexpected.cpp  
// compile with: /EHsc  
#include <exception>  
#include <iostream>  
  
using namespace std;  
  
void uefunction()  
{  
    cout << "My unhandled exception function called." << endl;  
    terminate(); // this is what unexpected() calls by default  
}  
  
int main()  
{  
    unexpected_handler oldHandler = set_unexpected(uefunction);  
  
    unexpected(); // library function to force calling the   
                  // current unexpected handler  
}  
  
```  
  
##  <a name="terminate"></a>  terminate  
 呼叫終止處理常式。  
  
```  
void terminate();
```  
  
### <a name="remarks"></a>備註  
 函式會呼叫終止處理常式，其為 `void` 類型的函式。 如果程式直接呼叫 **terminate**，終止處理常式即為 [set_terminate](../standard-library/exception-functions.md#set_terminate) 呼叫最近設定的項目。 如果在 throw 運算式的評估期間因故呼叫 **terminate**，終止處理常式就會在評估 throw 運算式後立即生效。  
  
 終止處理常式可能無法傳回至其呼叫端。 在程式啟動時，終止處理常式會呼叫一個函數，其會呼叫 **abort**。  
  
### <a name="example"></a>範例  
  如需 **terminate** 的用法範例，請參閱 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。  
  
##  <a name="uncaught_exception"></a>  uncaught_exception  
 只有當系統正在處理擲回的例外狀況時，才傳回 `true`。  
  
```  
bool uncaught_exception();
```  
  
### <a name="return-value"></a>傳回值  
 在完成 throw 運算式評估之後，以及完成相符處理常式中例外狀況宣告的初始化之前，或呼叫 [unexpected](../standard-library/exception-functions.md#unexpected) 作為 throw 運算式的結果之前，系統會傳回 `true`。 特別之處在於：如果呼叫 `uncaught_exception` 的解構函式在例外狀況回溯期間受到叫用，則會傳回 `true`。 `uncaught_exception` 僅支援 Windows CE 5.00 或更新版本的裝置，包括 Windows Mobile 2005 平台。  
  
### <a name="example"></a>範例  
  
```cpp  
// exception_uncaught_exception.cpp  
// compile with: /EHsc  
#include <exception>  
#include <iostream>  
#include <string>  
  
class Test   
{  
public:  
   Test( std::string msg ) : m_msg( msg )   
   {  
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;  
   }  
   ~Test( )   
   {  
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl  
         << "        std::uncaught_exception( ) = "  
         << std::uncaught_exception( )  
         << std::endl;  
   }  
private:  
    std::string m_msg;  
};  
  
// uncaught_exception will be true in the destructor   
// for the object created inside the try block because   
// the destructor is being called as part of the unwind.  
  
int main( void )  
   {  
      Test t1( "outside try block" );  
      try   
      {  
         Test t2( "inside try block" );  
         throw 1;  
      }  
      catch (...) {  
   }  
}  
```  
  
```Output  
In Test::Test("outside try block")  
In Test::Test("inside try block")  
In Test::~Test("inside try block")  
        std::uncaught_exception( ) = 1  
In Test::~Test("outside try block")  
        std::uncaught_exception( ) = 0  
```  
  
##  <a name="unexpected"></a>  unexpected  
 呼叫未預期的處理常式。  
  
```  
void unexpected();
```  
  
### <a name="remarks"></a>備註  
 C++ 標準要求在函式擲回例外狀況時，必須呼叫 `unexpected`。 目前的實作不支援此項目。 範例會直接呼叫 `unexpected`，這會引發呼叫非預期的處理常式。  
  
 函式會呼叫未預期的處理常式，其為 `void` 類型的函式。 如果程式直接呼叫 `unexpected`，未預期的處理常式即為 [set_unexpected](../standard-library/exception-functions.md#set_unexpected) 呼叫最近設定的項目。  
  
 未預期的處理常式可能無法傳回至其呼叫端。 它可能會透過下列方式來終止程式執行：  
  
-   擲回例外狀況規格中提列的物件，或者，如果程式直接呼叫未預期的處理常式，則會擲回任何類型的物件。  
  
-   擲回 [bad_exception](../standard-library/bad-exception-class.md) 類型的物件。  
  
-   呼叫 [terminate](../standard-library/exception-functions.md#terminate)、**abort** 或 **exit**( `int`)。  
  
 在程式啟動時，未預期的處理常式會呼叫一個函數，其會呼叫 [terminate](../standard-library/exception-functions.md#terminate)。  
  
### <a name="example"></a>範例  
  如需 **unexpected.** 的用法範例，請參閱 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。  
  
## <a name="see-also"></a>另請參閱  
 [\<exception>](../standard-library/exception.md)

