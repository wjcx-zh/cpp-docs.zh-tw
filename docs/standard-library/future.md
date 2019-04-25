---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: 189a9f16b65ae74fc2a86bee62bf8bd548c486aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159856"
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
> 在編譯使用的程式碼 **/clr**，此標頭會遭到封鎖。

「非同步提供者」會儲存函式呼叫的結果。 「非同步傳回物件」可用來擷取函式呼叫的結果。 「相關非同步狀態」可提供非同步提供者與一或多個非同步傳回物件之間的通訊。

程式不會直接建立任何相關非同步狀態物件。 程式會在每當需要非同步提供者時便建立一個，然後從該提供者建立非同步傳回物件，以將其相關非同步狀態與提供者共用。 非同步提供者和非同步傳回物件會管理保存其共用相關非同步狀態的物件。 當最後一個參考相關非同步狀態的物件釋出它，系統就會終結保存相關非同步狀態的物件。

沒有相關非同步狀態的非同步提供者或非同步傳回物件會是「空的」。

相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成「就緒」。

範本函式 `async` 及範本類別 `promise` 和 `packaged_task` 是非同步提供者。 範本類別 `future` 和 `shared_future` 則描述非同步傳回物件。

每個範本類別`promise`， `future`，並`shared_future`具有類型的特製化**void**和部分特製化來儲存和擷取值的參考。 這些特製化與主要範本只有在儲存和擷取傳回值的函式簽章及語意上有差異。

範本類別`future`和`shared_future`永遠不會封鎖在其解構函式，除了在保留回溯相容性的其中一個案例：與所有其他 future，不同的`future`— 或最後一個`shared_future`— 連結至工作`std::async`解構函式區塊，如果尚未完成的工作; 也就是說，它會封鎖如果此執行緒尚未呼叫`.get()`或`.wait()`工作仍在執行中。 已新增下列可用性附註的描述`std::async`草稿標準中: 「 [附註：使用未來的其他程式碼取自 std::async future 移出的區域範圍，如果必須知道未來的解構函式可能會封鎖共用狀態變成就緒。 — 結束附註] 」 在所有其他情況下，`future`和`shared_future`解構函式所需，而且保證絕對不會封鎖。

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

|名稱|描述|
|----------|-----------------|
|[is_error_code_enum 結構](../standard-library/is-error-code-enum-structure.md)|指出 `future_errc` 適用於儲存 `error_code` 的特製化。|
|[uses_allocator 結構](../standard-library/uses-allocator-structure.md)|永遠成立的特製化。|

### <a name="functions"></a>函式

|名稱|描述|
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
|[launch](../standard-library/future-enums.md#launch)|代表一種位元遮罩類型，描述範本函式 `async` 可能的模式。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
