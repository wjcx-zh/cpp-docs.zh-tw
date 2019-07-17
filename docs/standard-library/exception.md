---
title: '&lt;exception&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: 5036f2efc782c3b2f385960cd9cbf6935212f720
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240759"
---
# <a name="ltexceptiongt"></a>&lt;exception&gt;

定義數個與例外狀況處理有關的類型和函式。 在系統可從錯誤復原的情況下，使用例外狀況處理。 它提供方式，將控制從函式傳回至程式。 併入例外狀況處理的目標是增加程式穩定性，同時以有次序的方式從錯誤復原。

## <a name="requirements"></a>需求

**標頭：** \<exception>

**命名空間：** std

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|描述例外狀況指標的類型。|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|類型，描述適合做為 `terminate_handler` 之函式的指標。|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|類型，描述適合做為 `unexpected_handler` 之函式的指標。|

### <a name="functions"></a>函式

|||
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|取得目前例外狀況的指標。|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|取得目前的 `terminate_handler` 函式。|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|取得目前的 `unexpected_handler` 函式。|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|建立持有例外狀況複本的 `exception_ptr` 物件。|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|擲回做為參數傳遞的例外狀況。|
|[rethrow_if_nested](../standard-library/exception-functions.md#rethrow_if_nested)|擲回例外狀況，如果巢狀和轉換。|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|建立新 `terminate_handler`，在程式終止時呼叫。|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|建立新的 `unexpected_handler`，當未預期的例外狀況發生時擲回。|
|[terminate](../standard-library/exception-functions.md#terminate)|呼叫終止處理常式。|
|[throw_with_nested](../standard-library/exception-functions.md#throw_with_nested)|如果巢狀，則會擲回例外狀況。|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|只有當系統正在處理擲回的例外狀況時，才傳回 **true**。|
|[unexpected](../standard-library/exception-functions.md#unexpected)|呼叫未預期的處理常式。|

### <a name="classes"></a>類別

|||
|-|-|
|[bad_exception 類別](../standard-library/bad-exception-class.md)|此類別描述從 `unexpected_handler` 所擲回的例外狀況。|
|[exception 類別](../standard-library/exception-class.md)|此類別可作為特定運算式和 C++ 標準程式庫所擲回之所有例外狀況的基底類別。|
|[nested_exception 類別](../standard-library/nested-exception-class.md)|此類別描述可以擷取和儲存供日後使用的例外狀況。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
