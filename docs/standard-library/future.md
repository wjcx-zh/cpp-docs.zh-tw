---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: c852b3040a94035f6a84b1f717c3583fababbb2c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688024"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

包含標準標頭 \<future > 來定義類別樣板和支援的範本，以簡化函式的執行（可能在不同的執行緒中），並抓取其結果。 結果會是函式所傳回的值，或是函式所發出但未在函式中攔截到的例外狀況。

此標頭使用「並行執行階段」(ConcRT)，因此您可以將它與其他 ConcRT 機制搭配使用。 如需有關 ConcRT 的詳細資訊，請參閱[並行執行階段](../parallel/concrt/concurrency-runtime.md)。

## <a name="syntax"></a>語法

```cpp
#include <future>
```

## <a name="remarks"></a>備註

> [!NOTE]
> 在使用 **/clr**編譯的程式碼中，此標頭會遭到封鎖。

「非同步提供者」會儲存函式呼叫的結果。 「非同步傳回物件」可用來擷取函式呼叫的結果。 「相關非同步狀態」可提供非同步提供者與一或多個非同步傳回物件之間的通訊。

程式不會直接建立任何相關非同步狀態物件。 程式會在每當需要非同步提供者時便建立一個，然後從該提供者建立非同步傳回物件，以將其相關非同步狀態與提供者共用。 非同步提供者和非同步傳回物件會管理保存其共用相關非同步狀態的物件。 當最後一個參考相關非同步狀態的物件釋出它，系統就會終結保存相關非同步狀態的物件。

沒有相關非同步狀態的非同步提供者或非同步傳回物件會是「空的」。

只有在非同步提供者儲存了傳回值或儲存了例外狀況之後，相關聯的非同步狀態才會「就緒」。

@No__t_0 範本函式和類別樣板 `promise` 和 `packaged_task` 是非同步提供者。 類別樣板 `future` 和 `shared_future` 描述非同步傳回物件。

@No__t_0、`future` 和 `shared_future` 的每個類別樣板都具有類型**void**的特製化，以及用於以傳址方式儲存和抓取值的部分特製化。 這些特製化與主要範本只有在儲存和擷取傳回值的函式簽章及語意上有差異。

類別樣板 `future` 和 `shared_future` 永遠不會在其析構函數中封鎖，不同之處在于為了回溯相容性而保留的一種情況：不同于所有其他未來、針對 `future` （或最後一個 `shared_future`）附加至以開頭的工作 `std::async`，如果工作尚未完成，則此函式會封鎖;也就是說，它會封鎖此執行緒是否尚未呼叫 `.get()` 或 `.wait()`，而且工作仍在執行中。 下列可用性附註已經在草稿標準中新增到 `std::async` 的描述：「[附註：如果將從 std::async 取得的 future 移到區域範圍外，其他使用該 future 的程式碼必須知悉該 future 的解構函式可能進行封鎖來讓共用狀態變成就緒。—結束附註]」在所有其他情況下，都必須要有 `future` 和 `shared_future` 解構函式，並且保證它們一律不進行封鎖。

## <a name="members"></a>Members

### <a name="classes"></a>類別

|[屬性]|描述|
|----------|-----------------|
|[future 類別](../standard-library/future-class.md)|描述非同步傳回物件。|
|[future_error 類別](../standard-library/future-error-class.md)|描述可由管理 `future` 物件之類型的方法擲回的例外狀況物件。|
|[packaged_task 類別](../standard-library/packaged-task-class.md)|描述作為呼叫包裝函式且呼叫簽章為 `Ty(ArgTypes...)` 的非同步提供者。 除了可能的結果之外，它的相關非同步狀態還會保存一份它的可呼叫物件複本。|
|[promise 類別](../standard-library/promise-class.md)|描述非同步提供者。|
|[shared_future 類別](../standard-library/shared-future-class.md)|描述非同步傳回物件。 與 `future` 物件對比，非同步提供者可以與任意數目的 `shared_future` 物件相關聯。|

### <a name="structures"></a>結構

|[屬性]|描述|
|----------|-----------------|
|[is_error_code_enum 結構](../standard-library/is-error-code-enum-structure.md)|指出 `future_errc` 適用於儲存 `error_code` 的特製化。|
|[uses_allocator 結構](../standard-library/uses-allocator-structure.md)|永遠成立的特製化。|

### <a name="functions"></a>函式

|[屬性]|描述|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|代表非同步提供者。|
|[future_category](../standard-library/future-functions.md#future_category)|傳回對 `error_category` 物件的參考，此物件會描述 `future` 物件之相關錯誤的特性。|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|建立具有 `error_category` 物件的 `error_code`，該物件會描述 `future` 錯誤的特性。|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|建立具有 `error_category` 物件的 `error_condition`，該物件會描述 `future` 錯誤的特性。|
|[swap](../standard-library/future-functions.md#swap)|將一個 `promise` 物件的「相關非同步狀態」與另一個物件的該狀態交換。|

### <a name="enumerations"></a>列舉

|[屬性]|描述|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|為 `future_error` 類別所回報的錯誤提供符號名稱。|
|[future_status](../standard-library/future-enums.md#future_status)|為計時的 wait 函式可傳回的原因提供符號名稱。|
|[產品](../standard-library/future-enums.md#launch)|代表一種位元遮罩類型，描述範本函式 `async` 可能的模式。|

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
