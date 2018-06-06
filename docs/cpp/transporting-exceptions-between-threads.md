---
title: 執行緒之間傳輸例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- std::current_exception
- transporting exceptions between threads
- std::copy_exception
- exception_ptr
- std::exception_ptr
- std::rethrow_exception
- current_exception
- transport exceptions between threads
- copy_exception
- rethrow_exception
- move exceptions between threads
ms.assetid: 5c95d57b-acf5-491f-8122-57c5df0edd98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1066da6545a2e0689fbfed33be466e001142dc9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704642"
---
# <a name="transporting-exceptions-between-threads"></a>執行緒之間傳輸例外狀況

Visual c + + 支援*傳輸例外狀況*從另一個執行緒。 傳輸例外狀況可以讓您在某個執行緒攔截例外狀況，再使該例外狀況看似在另一個執行緒中擲回。 舉例來說，您可以使用此功能撰寫多執行緒應用程式，其中由主執行緒處理其次要執行緒所擲回的所有例外狀況。 傳輸例外狀況對於建立平行程式設計程式庫或系統的開發人員最有用。 若要實作傳輸例外狀況，Visual c + + 提供[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)型別和[current_exception](../standard-library/exception-functions.md#current_exception)， [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)，和[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)函式。

## <a name="syntax"></a>語法

```cpp
namespace std
{
   typedef unspecified exception_ptr;
   exception_ptr current_exception();
   void rethrow_exception(exception_ptr p);
   template<class E>
       exception_ptr make_exception_ptr(E e) noexcept;
}
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*未指定*|用於實作 `exception_ptr` 類型的未指定內部類別。|
|*p*|參考例外狀況的 `exception_ptr` 物件。|
|*E*|代表例外狀況的類別。|
|*e*|參數 `E` 類別的執行個體。|

## <a name="return-value"></a>傳回值

`current_exception` 函式會將 `exception_ptr` 物件傳回，此物件則參考目前進行中的例外狀況。 如果沒有正在進行中的例外狀況，該函式會傳回與所有例外狀況皆不具關聯性的 `exception_ptr` 物件。

`make_exception_ptr`函式會傳回`exception_ptr`參照所指定的例外狀況物件*e*參數。

## <a name="remarks"></a>備註

### <a name="scenario"></a>情節

假設您需要建立一個能縮放以處理不同工作量的應用程式， 為達成此目標，您可以在一開始設計一個多執行緒的應用程式，而其主執行緒可以視工作執行所需建立任何數量的次要執行緒。 次要執行緒能協助主執行緒管理資源、平衡負載和提升輸送量。 透過分配工作的方式，多執行緒應用程式的運行效率可以優於單一執行緒應用程式。

不過，若次要執行緒擲回例外狀況，需由主要執行緒處理。 這是因為無論次要執行緒的數量多寡，您的應用程式最好都能夠以一致、統一的方式處理例外狀況。

### <a name="solution"></a>方案

為處理以上情況，C++ Standard 支援在執行緒之間傳輸例外狀況。 如果次要執行緒擲回例外狀況，該例外狀況就會變成*目前例外狀況*。 以真實世界比喻，目前的例外狀況要*在途中*。 從目前例外狀況被擲回那一刻起，一直到攔截到該例外狀況的例外狀況處理常式傳回為止，目前例外狀況都在執行中。

次要執行緒可以在 `catch` 區塊攔截目前的例外狀況，然後呼叫 `current_exception` 函式將例外狀況儲存於 `exception_ptr` 物件中。 `exception_ptr` 物件必須可供次要執行緒與主執行緒使用。 舉例來說，`exception_ptr` 物件可以是由 Mutex 控制存取的全域變數。 詞彙*傳輸例外狀況*表示一個執行緒中的發生例外狀況可以轉換成可由另一個執行緒存取的表單。

接下來，主執行緒會呼叫 `rethrow_exception` 函式，而該函式再擷取並從 `exception_ptr` 物件擲回例外狀況。 例外狀況被擲回時會變成主執行緒中目前的例外狀況。 也就是說，該例外狀況看起來就像源自於主執行緒。

最後，主執行緒可以在 `catch` 區塊中攔截目前的例外狀況，然後進行處理或將其擲回更高階的例外狀況處理常式。 或者，主執行緒可以忽略該例外狀況並允許處理序結束。

大部分的應用程式不需要在執行緒之間傳輸例外狀況。 不過，由於系統可以區分次要執行緒、處理器或核心的工作，因此此功能對於平行計算系統非常有用。 在平行計算環境下，一個專屬的執行緒可以處理次要執行緒擲回的所有例外狀況，而且可以對任何應用程式呈現一致的例外狀況處理模型。

如需關於 C++ Standard 委員會提案的詳細資訊，請上網搜尋文件編號 N2179，標題為「在執行緒之間傳輸例外狀況的語言支援」。

### <a name="exception-handling-models-and-compiler-options"></a>例外狀況處理模型和編譯器選項

應用程式的例外狀況處理模型決定該應用程式是否可以攔截和傳輸例外狀況。 Visual C++ 支援三種可以處理 C++ 例外狀況、結構化例外處理 (SEH) 例外狀況，以及通用語言執行平台 (CLR) 例外狀況的模型。 使用[/EH](../build/reference/eh-exception-handling-model.md)和[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項來指定您的應用程式例外狀況處理模型。

只有以下的編譯器選項和程式設計陳述式組合可以傳輸例外狀況， 其他組合無法攔截例外狀況或可以攔截但無法傳輸例外狀況。

- **/EHa**編譯器選項和`catch`陳述式可以傳輸 SEH 和 c + + 例外狀況。

- **/EHa**， **/EHs**，和 **/EHsc**編譯器選項和`catch`陳述式可以傳輸 c + + 例外狀況。

- **/CLR**編譯器選項和`catch`陳述式可以傳輸 c + + 例外狀況。 **/CLR**編譯器選項表示的規格 **/EHa**選項。 請注意，編譯器不支援傳輸 Managed 例外狀況， 這是因為 managed 例外狀況衍生自[System.Exception 類別](../standard-library/exception-class.md)，已經是您可以使用通用語言執行平台的功能在執行緒之間移動的物件。

   > [!IMPORTANT]
   > 我們建議您指定 **/EHsc**編譯器選項並只攔截 c + + 例外狀況。 您會在安全性威脅如果您使用 **/EHa**或 **/CLR**編譯器選項和**攔截**陳述式，以省略符號*例外狀況宣告*(`catch(...)`)。 也許您會使用 `catch` 陳述式擷取特定的例外狀況。 不過，`catch(...)` 陳述式會擷取所有 C++ 和 SEH 例外狀況，其中包括嚴重的非預期例外狀況。 如果您忽略非預期的例外狀況或處理不當，惡意程式碼可能會利用此機會破壞程式的安全性。

## <a name="usage"></a>使用量

下列各節說明如何使用傳輸例外狀況`exception_ptr`型別，而`current_exception`， `rethrow_exception`，和`make_exception_ptr`函式。

## <a name="exceptionptr-type"></a>exception_ptr 類型

利用 `exception_ptr` 物件參考目前的例外狀況或使用者指定的例外狀況執行個體。 在 Microsoft 實作中，例外狀況是以 [EXCEPTION_RECORD](https://msdn.microsoft.com/library/windows/desktop/aa363082) 結構表示。 每個 `exception_ptr` 物件均包含一個例外狀況參考欄位，指向代表該例外狀況的 `EXCEPTION_RECORD` 結構複本。

當您宣告 `exception_ptr` 變數時，此變數尚未關聯任何例外狀況。 也就是說，其例外狀況參考欄位為 NULL。 這樣的 `exception_ptr` 物件稱為 *null exception_ptr*。

利用 `current_exception` 或 `make_exception_ptr` 函式將例外狀況指派給 `exception_ptr` 物件。 當您將例外狀況指派給 `exception_ptr` 變數時，此變數的例外狀況參考欄位會指向該例外狀況的複本。 如果記憶體空間不足，無法複製該例外狀況，則例外狀況參考欄位會指向 [std::bad_alloc](../standard-library/bad-alloc-class.md) 例外狀況的複本。 如果`current_exception`或`make_exception_ptr`函式不能複製該例外狀況的任何其他原因，函式呼叫[終止](../c-runtime-library/reference/terminate-crt.md)函式來結束目前的程序。

`exception_ptr` 物件本身並不是指標 (儘管其名稱如此)。 它不遵守指標語意，並不能搭配指標成員存取 (`->`) 或間接取值 (`*`) 運算子。 `exception_ptr` 物件沒有公用資料成員或成員函式。

### <a name="comparisons"></a>比較

您可以使用等於 (`==`) 和不等於 (`!=`) 運算子比較兩個 `exception_ptr` 物件。 運算子不會比較代表例外狀況之 `EXCEPTION_RECORD` 結構的二進位值 (位元模式)。 相反地，運算子會比較 `exception_ptr` 物件的例外狀況參考欄位位址。 因此，Null `exception_ptr` 和 Null 值的比較結果是相等。

## <a name="currentexception-function"></a>current_exception 函式

在 `current_exception` 區塊呼叫 `catch` 函式。 如果例外狀況在執行中，且 `catch` 區塊可以攔截該例外狀況，則 `current_exception` 函式會傳回參考該例外狀況的 `exception_ptr` 物件。 否則，函式會傳回 Null `exception_ptr` 物件。

### <a name="details"></a>詳細資料

不論 `catch` 陳述式是否指定[例外狀況宣告](../cpp/try-throw-and-catch-statements-cpp.md)陳述式，`current_exception` 函式都會擷取執行中的例外狀況。

若不重新擲回例外狀況，則會在 `catch` 區塊結尾呼叫目前例外狀況的解構函式。 不過，即使在解構函式中呼叫 `current_exception` 函式，該函式仍會傳回參考目前例外狀況的 `exception_ptr` 物件。

`current_exception` 函式的後續呼叫會傳回參考目前例外狀況不同複本的 `exception_ptr` 物件。 因此，物件比較結果會是不相等，因為兩者參考不同的複本 (即使複本的二進位值相同也一樣)。

### <a name="seh-exceptions"></a>SEH 例外狀況

如果您使用 **/EHa**編譯器選項，您可以在 c + + 攔截 SEH 例外狀況`catch`區塊。 `current_exception` 函式會傳回參考 SEH 例外狀況的 `exception_ptr` 物件。 和`rethrow_exception`函式擲回 SEH 例外狀況，如果您呼叫具有 thetransported`exception_ptr`物件做為其引數。

如果您在 SEH `current_exception` 終止處理常式、`exception_ptr` 例外狀況處理常式或 `__finally` 篩選條件運算式中呼叫 `__except` 函式，該函式會傳回 Null `__except`。

傳輸例外狀況不支援巢狀例外狀況。 處理例外狀況時，如果再擲出另一個例外狀況，則會發生巢狀例外狀況。 如果您攔截巢狀例外狀況，`EXCEPTION_RECORD.ExceptionRecord` 資料成員會指向描述關聯例外狀況的 `EXCEPTION_RECORD` 結構鏈結。 `current_exception` 函式不支援巢狀例外狀況，因為該函式會傳回已清空 `exception_ptr` 資料成員的 `ExceptionRecord` 物件。

如果您攔截 SEH 例外狀況，則必須管理 `EXCEPTION_RECORD.ExceptionInformation` 資料成員陣列中任何指標所參考的記憶體。 您必須保證對應 `exception_ptr` 物件存留期的記憶體是有效的，並在刪除 `exception_ptr` 物件時釋放其記憶體。

您可以同時使用結構化例外狀況 (SE) 轉譯器函式和傳輸例外狀況功能。 如果 SEH 例外狀況轉譯為 C++ 例外狀況，`current_exception` 函式會傳回參考轉譯的例外狀況而非原始的 SEH 例外狀況的 `exception_ptr`。 `rethrow_exception` 函式後續會擲回轉譯的例外狀況，而非原始的例外狀況。 如需 SE 轉譯器函式的詳細資訊，請參閱[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)。

## <a name="rethrowexception-function"></a>rethrow_exception 函式

將攔截到的例外狀況儲存在 `exception_ptr` 物件之後，主執行緒即可處理物件。 在主執行緒中呼叫 `rethrow_exception` 函式，並使用 `exception_ptr` 物件做為其引數。 `rethrow_exception` 函式會從 `exception_ptr` 物件擷取例外狀況，然後在主執行緒的內容中擲回該例外狀況。 如果`p`參數`rethrow_exception`函式是 null `exception_ptr`，函式會擲回[std:: bad_exception](../standard-library/bad-exception-class.md)。

擷取到的例外狀況現在會變成主執行緒中的目前例外狀況，因此，您可以按照處理其他任何例外狀況的方式進行處理。 如果您攔截例外狀況，可以選擇立即處理或使用 `throw` 陳述式將該例外狀況傳送給更高階的例外狀況處理常式。 否則，請勿執行任何動作，並讓預設系統例外狀況處理常式終止處理序。

## <a name="makeexceptionptr-function"></a>make_exception_ptr 函式

`make_exception_ptr` 函式會以類別的執行個體做為其引數，並傳回參考該執行個體的 `exception_ptr`。 雖然任何類別物件都可以是 `make_exception_ptr` 函式的引數，但一般會指定 [exception 類別](../standard-library/exception-class.md)物件作為其引數。

呼叫 `make_exception_ptr` 函式相當於擲回 C++ 例外狀況、在 `catch` 區塊中攔截該例外狀況，然後呼叫 `current_exception` 函式以傳回參考該例外狀況的 `exception_ptr` 物件。 Microsoft 實作`make_exception_ptr` 函式比在擲回例外狀況之後攔截來得更有效率。

一般來說，應用程式通常不需要使用 `make_exception_ptr` 函式，所以我們不建議使用此功能。

## <a name="example"></a>範例

以下範例會在執行緒之間傳輸標準 C++ 例外狀況和自訂的 C++ 例外狀況。

```cpp
// transport_exception.cpp
// compile with: /EHsc /MD
#include <windows.h>
#include <stdio.h>
#include <exception>
#include <stdexcept>

using namespace std;

// Define thread-specific information.
#define THREADCOUNT 2
exception_ptr aException[THREADCOUNT];
int           aArg[THREADCOUNT];

DWORD WINAPI ThrowExceptions( LPVOID );

// Specify a user-defined, custom exception.
// As a best practice, derive your exception
// directly or indirectly from std::exception.
class myException : public std::exception {
};
int main()
{
    HANDLE aThread[THREADCOUNT];
    DWORD ThreadID;

    // Create secondary threads.
    for( int i=0; i < THREADCOUNT; i++ )
    {
        aArg[i] = i;
        aThread[i] = CreateThread(
            NULL,       // Default security attributes.
            0,          // Default stack size.
            (LPTHREAD_START_ROUTINE) ThrowExceptions,
            (LPVOID) &aArg[i], // Thread function argument.
            0,          // Default creation flags.
            &ThreadID); // Receives thread identifier.
        if( aThread[i] == NULL )
        {
            printf("CreateThread error: %d\n", GetLastError());
            return -1;
        }
    }

    // Wait for all threads to terminate.
    WaitForMultipleObjects(THREADCOUNT, aThread, TRUE, INFINITE);
    // Close thread handles.
    for( int i=0; i < THREADCOUNT; i++ ) {
        CloseHandle(aThread[i]);
    }

    // Rethrow and catch the transported exceptions.
    for ( int i = 0; i < THREADCOUNT; i++ ) {
        try {
            if (aException[i] == NULL) {
                printf("exception_ptr %d: No exception was transported.\n", i);
            }
            else {
                rethrow_exception( aException[i] );
            }
        }
        catch( const invalid_argument & ) {
            printf("exception_ptr %d: Caught an invalid_argument exception.\n", i);
        }
        catch( const myException & ) {
            printf("exception_ptr %d: Caught a  myException exception.\n", i);
        }
    }
}
// Each thread throws an exception depending on its thread
// function argument, and then ends.
DWORD WINAPI ThrowExceptions( LPVOID lpParam )
{
    int x = *((int*)lpParam);
    if (x == 0) {
        try {
            // Standard C++ exception.
            // This example explicitly throws invalid_argument exception.
            // In practice, your application performs an operation that
            // implicitly throws an exception.
            throw invalid_argument("A C++ exception.");
        }
        catch ( const invalid_argument & ) {
            aException[x] = current_exception();
        }
    }
    else {
        // User-defined exception.
        aException[x] = make_exception_ptr( myException() );
    }
    return TRUE;
}
```

```Output
exception_ptr 0: Caught an invalid_argument exception.
exception_ptr 1: Caught a  myException exception.
```

## <a name="requirements"></a>需求

**標頭：**\<exception>

## <a name="see-also"></a>另請參閱

- [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)
- [/EH (例外狀況處理模型)](../build/reference/eh-exception-handling-model.md)
- [/clr (通用語言執行平台編譯)](../build/reference/clr-common-language-runtime-compilation.md)
