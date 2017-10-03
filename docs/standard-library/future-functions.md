---
title: "&lt;future&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
caps.latest.revision: 11
manager: ghogen
helpviewer_keywords:
- std::async [C++]
- std::future_category [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::swap [C++]
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 6ce0ef5ebc19ed9861c4eeb3dd9b3605ff3383b3
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltfuturegt-functions"></a>&lt;future&gt; 函式
||||  
|-|-|-|  
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|  
|[make_error_condition](#make_error_condition)|[swap](#swap)|  
  
##  <a name="async"></a>  async  
 代表「非同步提供者」。  
  
```
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```  
  
### <a name="parameters"></a>參數  
 `policy`  
 [launch](../standard-library/future-enums.md#launch) 值。  
  
### <a name="remarks"></a>備註  
 縮寫的定義：  
  
|||  
|-|-|  
|*dfn*|呼叫 `decay_copy(forward<Fn>(fn))` 的結果。|  
|*dargs*|呼叫 `decay_copy(forward<ArgsTypes>(args...))` 的結果。|  
|*Ty*|`result_of<Fn(ArgTypes...)>::type` 類型。|  
  
 第一個範本函式會傳回 `async(launch::any, fn, args...)`。  
  
 第二個函式會傳回一個其「相關非同步狀態」同時保存結果及 *dfn* 和 *dargs* 值的 `future<Ty>` 物件，以及一個用來管理個別執行緒的執行緒物件。  
  
 除非 `decay<Fn>::type` 是 launch 以外的類型，否則第二個函式不會參與多載解析。  
  
 如果 `policy` 是 `launch::any`，則函式可能會選擇 `launch::async` 或 `launch::deferred`。 在此實作中，此函式會使用 `launch::async`。  
  
 如果 `policy` 是 `launch::async`，此函式就會建立一個評估 `INVOKE(dfn, dargs..., Ty)` 的執行緒。 此函式在建立執行緒後便會返回，而不會等待結果。 如果系統無法開始一個新的執行緒，此函式將會擲回一個錯誤碼為 `resource_unavailable_try_again` 的 [system_error](../standard-library/system-error-class.md)。  
  
 如果 `policy` 是 `launch::deferred`，此函式就會將其相關非同步狀態標示為持有「deferred 函式」並返回。 第一次呼叫任何等待相關非同步狀態變成就緒的非計時函式時，實際上會透過評估 `INVOKE(dfn, dargs..., Ty)` 來呼叫 deferred 函式。  
  
 在所有情況下，`future` 物件的相關非同步狀態都不會設定成「就緒」，直到透過擲回例外狀況或正常返回來完成 `INVOKE(dfn, dargs..., Ty)` 評估為止。 如果擲回例外狀況，相關非同步狀態的結果就會是例外狀況，否則會是評估所傳回的任何值。  
  
> [!NOTE]
>  針對連結至開頭為 `std::async` 之工作的 `future` (或最後一個 [shared_future](../standard-library/shared-future-class.md))，如果該工作尚未完成，解構函式就會進行封鎖；也就是說，如果此執行緒尚未呼叫 `.get()` 或 `.wait()` 且該工作仍在執行，解構函式就會進行封鎖。 如果將從 `std::async` 取得的 `future` 移到區域範圍外，其他使用它的程式碼必須知悉其解構函式可能進行封鎖來讓共用狀態變成就緒。  
  
 虛擬函式 `INVOKE` 是在 [\<functional>](../standard-library/functional.md) 中定義。  
  
##  <a name="future_category"></a>  future_category  
 傳回對 [error_category](../standard-library/error-category-class.md) 物件的參考，此物件會描述 `future` 物件之相關錯誤的特性。  
  
```
const error_category& future_category() noexcept;
```  
  
##  <a name="make_error_code"></a>  make_error_code  
 建立 [error_code](../standard-library/error-code-class.md) 連同描述 [future](../standard-library/future-class.md) 錯誤特性的 [error_category](../standard-library/error-category-class.md) 物件。  
  
```
inline error_code make_error_code(future_errc Errno) noexcept;
```  
  
### <a name="parameters"></a>參數  
 `Errno`  
 [future_errc](../standard-library/future-enums.md#future_errc) 值，可識別所回報的錯誤。  
  
### <a name="return-value"></a>傳回值  
 `error_code(static_cast<int>(Errno), future_category());`  
  
##  <a name="make_error_condition"></a>  make_error_condition  
 建立 [error_condition](../standard-library/error-condition-class.md) 連同描述 [future](../standard-library/future-class.md) 錯誤特性的 [error_category](../standard-library/error-category-class.md) 物件。  
  
```
inline error_condition make_error_condition(future_errc Errno) noexcept;
```  
  
### <a name="parameters"></a>參數  
 `Errno`  
 [future_errc](../standard-library/future-enums.md#future_errc) 值，可識別所回報的錯誤。  
  
### <a name="return-value"></a>傳回值  
 `error_condition(static_cast<int>(Errno), future_category());`  
  
##  <a name="swap"></a>  swap  
 將一個 `promise` 物件的「相關非同步狀態」與另一個物件的該狀態交換。  
  
```
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```  
  
### <a name="parameters"></a>參數  
 `Left`  
 左 `promise` 物件。  
  
 `Right`  
 右 `promise` 物件。  
  
## <a name="see-also"></a>另請參閱  
 [\<future>](../standard-library/future.md)




