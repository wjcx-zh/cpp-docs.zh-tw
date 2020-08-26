---
title: '&lt;future&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
helpviewer_keywords:
- std::async [C++]
- std::future_category [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::swap [C++]
ms.openlocfilehash: d419984243d3970533f30814fe0ff451199afb34
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837966"
---
# <a name="ltfuturegt-functions"></a>&lt;future&gt; 函式

[非同步](#async)\
[future_category](#future_category)\
[make_error_code](#make_error_code)\
[make_error_condition](#make_error_condition)\
[交換](#swap)|

## <a name="async"></a><a name="async"></a> 非同步

代表「非同步提供者」**。

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>參數

*政策*\
[launch](../standard-library/future-enums.md#launch) 值。

### <a name="remarks"></a>備註

縮寫的定義：

|縮寫|描述|
|-|-|
|*dfn*|呼叫 `decay_copy(forward<Fn>(fn))` 的結果。|
|*dargs*|呼叫 `decay_copy(forward<ArgsTypes>(args...))` 的結果。|
|*泰*|`result_of<Fn(ArgTypes...)>::type` 類型。|

第一個範本函式會傳回 `async(launch::any, fn, args...)`。

第二個函式會傳回一個其「相關非同步狀態」** 同時保存結果及 *dfn* 和 *dargs* 值的 `future<Ty>` 物件，以及一個用來管理個別執行緒的執行緒物件。

除非 `decay<Fn>::type` 是 launch 以外的類型，否則第二個函式不會參與多載解析。

C + + 標準指出如果原則為啟動：： async，則函式會建立新的執行緒。 但是 Microsoft 的實施目前不符合規範。 它會從 Windows 執行緒集區取得其執行緒，在某些情況下，可能會提供回收的執行緒，而不是新的執行緒。 這表示 `launch::async` 原則其實實作為 `launch::async|launch::deferred` 。  以 ThreadPool 為基礎之實作為的另一種含意是，無法保證執行緒區域變數會線上程完成時終結。 如果執行緒已回收，並提供給的新呼叫 `async` ，舊的變數仍會存在。 因此，我們建議您不要搭配使用執行緒區域變數 `async` 。

如果 *原則* 為，則函式會將 `launch::deferred` 其相關聯的非同步狀態標示為保留 *延* 後的函式，並傳回。 第一次呼叫任何等待相關非同步狀態變成就緒的非計時函式時，實際上會透過評估 `INVOKE(dfn, dargs..., Ty)` 來呼叫 deferred 函式。

在所有情況下，`future` 物件的相關非同步狀態都不會設定成「就緒」**，直到透過擲回例外狀況或正常返回來完成 `INVOKE(dfn, dargs..., Ty)` 評估為止。 如果擲回例外狀況，相關非同步狀態的結果就會是例外狀況，否則會是評估所傳回的任何值。

> [!NOTE]
> 針對連結至開頭為 `std::async` 之工作的 `future` (或最後一個 [shared_future](../standard-library/shared-future-class.md))，如果該工作尚未完成，解構函式就會進行封鎖；也就是說，如果此執行緒尚未呼叫 `.get()` 或 `.wait()` 且該工作仍在執行，解構函式就會進行封鎖。 如果將從 `std::async` 取得的 `future` 移到區域範圍外，其他使用它的程式碼必須知悉其解構函式可能進行封鎖來讓共用狀態變成就緒。

虛擬函數 `INVOKE` 是在中定義 [\<functional>](../standard-library/functional.md) 。

## <a name="future_category"></a><a name="future_category"></a> future_category

傳回對 [error_category](../standard-library/error-category-class.md) 物件的參考，此物件會描述 `future` 物件之相關錯誤的特性。

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a><a name="make_error_code"></a> make_error_code

建立 [error_code](../standard-library/error-code-class.md) 連同描述 [future](../standard-library/future-class.md) 錯誤特性的 [error_category](../standard-library/error-category-class.md) 物件。

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>參數

*Errno*\
[future_errc](../standard-library/future-enums.md#future_errc) 值，可識別所回報的錯誤。

### <a name="return-value"></a>傳回值

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a><a name="make_error_condition"></a> make_error_condition

建立 [error_condition](../standard-library/error-condition-class.md) 連同描述 [future](../standard-library/future-class.md) 錯誤特性的 [error_category](../standard-library/error-category-class.md) 物件。

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>參數

*Errno*\
[future_errc](../standard-library/future-enums.md#future_errc) 值，可識別所回報的錯誤。

### <a name="return-value"></a>傳回值

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a><a name="swap"></a> 交換

將一個 `promise` 物件的「相關非同步狀態」** 與另一個物件的該狀態交換。

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>參數

*離開*\
左 `promise` 物件。

*對*\
右 `promise` 物件。

## <a name="see-also"></a>另請參閱

[\<future>](../standard-library/future.md)
