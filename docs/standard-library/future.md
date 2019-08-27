---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: d33b67ed17a95b6717878aaca2f61682b1807c15
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454012"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

包含標準標頭 \<future> 除了可以定義範本類別之外，也可以定義單純執行函式 (可能在個別的執行緒中) 並擷取其結果的支援範本。 結果會是函式所傳回的值，或是函式所發出但未在函式中攔截到的例外狀況。

此標頭使用「並行執行階段」(ConcRT)，因此您可以將它與其他 ConcRT 機制搭配使用。 如需有關 ConcRT 的詳細資訊，請參閱[並行執行階段](../parallel/concrt/concurrency-runtime.md)。

## <a name="syntax"></a>語法

```cpp
#include <future>
```

## <a name="remarks"></a>備註

> [!NOTE]
> 在使用 **/clr**編譯的程式碼中, 此標頭會遭到封鎖。

「非同步提供者」會儲存函式呼叫的結果。 「非同步傳回物件」可用來擷取函式呼叫的結果。 「相關非同步狀態」可提供非同步提供者與一或多個非同步傳回物件之間的通訊。

程式不會直接建立任何相關非同步狀態物件。 程式會在每當需要非同步提供者時便建立一個，然後從該提供者建立非同步傳回物件，以將其相關非同步狀態與提供者共用。 非同步提供者和非同步傳回物件會管理保存其共用相關非同步狀態的物件。 當最後一個參考相關非同步狀態的物件釋出它，系統就會終結保存相關非同步狀態的物件。

沒有相關非同步狀態的非同步提供者或非同步傳回物件會是「空的」。

相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成「就緒」。

範本函式 `async` 及範本類別 `promise` 和 `packaged_task` 是非同步提供者。 範本類別 `future` 和 `shared_future` 則描述非同步傳回物件。

每個樣板`promise`類別、 `future`和`shared_future`都具有類型**void**的特製化, 以及用於以傳址方式儲存和抓取值的部分特製化。 這些特製化與主要範本只有在儲存和擷取傳回值的函式簽章及語意上有差異。

範本類別`future`和`shared_future`永遠不會在其析構函數中封鎖, 但在保留為回溯相容性的情況下除外:不同于附加至`future`以開頭`std::async`的工作的所有其他`shared_future`未來, 或最後一個, 如果工作尚未完成, 則此函式會封鎖; 也就是說, 它會封鎖此執行緒是否尚未呼叫`.get()`或`.wait()`而且工作仍在執行中。 下列可用性注意事項已新增至草稿標準`std::async`中的描述: "[注意:如果從 std:: async 取得的未來是在本機範圍外移動, 其他使用未來的程式碼就必須注意, 未來的析構函式可能會封鎖, 讓共用狀態變成「就緒」。在所有其他情況下, 則`future`為`shared_future` 「結束附注」」, 而析構函數是必要的, 而且保證永遠不會封鎖。

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[future 類別](../standard-library/future-class.md)|描述非同步傳回物件。|
|[future_error 類別](../standard-library/future-error-class.md)|描述可由管理 `future` 物件之類型的方法擲回的例外狀況物件。|
|[packaged_task 類別](../standard-library/packaged-task-class.md)|描述作為呼叫包裝函式且呼叫簽章為 `Ty(ArgTypes...)` 的非同步提供者。 除了可能的結果之外，它的相關非同步狀態還會保存一份它的可呼叫物件複本。|
|[promise 類別](../standard-library/promise-class.md)|描述非同步提供者。|
|[shared_future 類別](../standard-library/shared-future-class.md)|描述非同步傳回物件。 與 `future` 物件對比，非同步提供者可以與任意數目的 `shared_future` 物件相關聯。|

### <a name="structures"></a>結構

|名稱|說明|
|----------|-----------------|
|[is_error_code_enum 結構](../standard-library/is-error-code-enum-structure.md)|指出 `future_errc` 適用於儲存 `error_code` 的特製化。|
|[uses_allocator 結構](../standard-library/uses-allocator-structure.md)|永遠成立的特製化。|

### <a name="functions"></a>函式

|名稱|說明|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|代表非同步提供者。|
|[future_category](../standard-library/future-functions.md#future_category)|傳回對 `error_category` 物件的參考，此物件會描述 `future` 物件之相關錯誤的特性。|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|建立具有 `error_category` 物件的 `error_code`，該物件會描述 `future` 錯誤的特性。|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|建立具有 `error_category` 物件的 `error_condition`，該物件會描述 `future` 錯誤的特性。|
|[swap](../standard-library/future-functions.md#swap)|將一個 `promise` 物件的「相關非同步狀態」與另一個物件的該狀態交換。|

### <a name="enumerations"></a>列舉

|名稱|描述|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|為 `future_error` 類別所回報的錯誤提供符號名稱。|
|[future_status](../standard-library/future-enums.md#future_status)|為計時的 wait 函式可傳回的原因提供符號名稱。|
|[產品](../standard-library/future-enums.md#launch)|代表一種位元遮罩類型，描述範本函式 `async` 可能的模式。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
