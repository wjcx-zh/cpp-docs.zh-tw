---
title: "packaged_task 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
dev_langs:
- C++
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 3ca8c4c008daa02af2bba0df8468bea3c063c28a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="packagedtask-class"></a>packaged_task 類別
描述「非同步提供者」，它是呼叫簽章為 `Ty(ArgTypes...)` 的呼叫包裝函式。 除了可能的結果外，它的「相關聯非同步狀態」會保存其可呼叫物件的複本。  
  
## <a name="syntax"></a>語法  
  
```
template <class>
class packaged_task;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[packaged_task](#packaged_task)|建構 `packaged_task` 物件。|  
|[packaged_task::~packaged_task 解構函式](#dtorpackaged_task_destructor)|終結 `packaged_task` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[get_future](#get_future)|傳回 [future](../standard-library/future-class.md) 物件，該物件具有相同的相關聯非同步狀態。|  
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|呼叫儲存在相關聯非同步狀態中的可呼叫物件，並以不可部分完成的方式儲存傳回的值。|  
|[reset](#reset)|取代相關聯的非同步狀態。|  
|[swap](#swap)|交換指定之物件的相關聯非同步狀態。|  
|[有效](#valid)|指定物件是否具有相關的非同步狀態。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[packaged_task::operator=](#op_eq)|從指定的物件轉移相關聯的非同步狀態。|  
|[packaged_task::operator()](#op_call)|呼叫儲存在相關聯非同步狀態中的可呼叫物件，以不可部分完成的方式儲存傳回的值，並將狀態設定為「就緒」。|  
|[packaged_task::operator bool](#op_bool)|指定物件是否具有相關聯的非同步狀態。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \<未來 >  
  
 **命名空間：** std  
  
##  <a name="get_future"></a>  packaged_task::get_future  
 傳回類型 `future<Ty>` 的物件，該物件具有相同的「相關聯非同步狀態」。  
  
```
future<Ty> get_future();
```  
  
### <a name="remarks"></a>備註  
 如果 `packaged_task` 物件沒有相關聯的非同步狀態，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。  
  
 如果已經針對具有同一個相關聯的非同步狀態的 `packaged_task` 物件呼叫這個方法，方法會擲回具有錯誤碼 `future_already_retrieved` 的 `future_error`。  
  
##  <a name="make_ready_at_thread_exit"></a>  packaged_task::make_ready_at_thread_exit  
 呼叫儲存在「相關聯非同步狀態」中的可呼叫物件，並以不可部分完成的方式儲存傳回的值。  
  
```
void make_ready_at_thread_exit(ArgTypes... args);
```  
  
### <a name="remarks"></a>備註  
 如果 `packaged_task` 物件沒有相關聯的非同步狀態，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。  
  
 如果已經針對具有同一個相關聯的非同步狀態的 `packaged_task` 物件呼叫這個方法或 [make_ready_at_thread_exit](#make_ready_at_thread_exit)，方法會擲回具有錯誤碼 `promise_already_satisfied` 的 `future_error`。  
  
 否則，此運算子會呼叫 `INVOKE(fn, args..., Ty)`，其中 *fn* 是儲存在相關聯非同步狀態中的可呼叫物件。 任何傳回的值會以不可部分完成的方式儲存為相關聯非同步狀態的傳回結果。  
  
 與 [packaged_task::operator()](#op_call) 相反，除非呼叫之執行緒中所有的執行緒區域物件皆已終結，否則相關聯的非同步狀態不會設定為 `ready`。 通常，除非呼叫的執行緒結束，否則被封鎖於相關聯非同步狀態的執行緒不會解除封鎖。  
  
##  <a name="op_eq"></a>  packaged_task::operator=  
 從指定的物件轉移「相關聯的非同步狀態」。  
  
```
packaged_task& operator=(packaged_task&& Right);
```  
  
### <a name="parameters"></a>參數  
 `Right`  
 `packaged_task` 物件。  
  
### <a name="return-value"></a>傳回值  
 `*this`  
  
### <a name="remarks"></a>備註  
 在作業完成後，`Right` 不再具有相關聯的非同步狀態。  
  
##  <a name="op_call"></a>  packaged_task::operator()  
 呼叫儲存在「相關聯非同步狀態」中的可呼叫物件，以不可部分完成的方式儲存傳回的值，並將狀態設定為「就緒」。  
  
```
void operator()(ArgTypes... args);
```  
  
### <a name="remarks"></a>備註  
 如果 `packaged_task` 物件沒有相關聯的非同步狀態，則這個方法會擲回含有 `no_state` 錯誤碼的 [future_error](../standard-library/future-error-class.md)。  
  
 如果已經針對具有同一個相關聯的非同步狀態的 `packaged_task` 物件呼叫這個方法或 [make_ready_at_thread_exit](#make_ready_at_thread_exit)，方法會擲回具有錯誤碼 `promise_already_satisfied` 的 `future_error`。  
  
 否則，此運算子會呼叫 `INVOKE(fn, args..., Ty)`，其中 *fn* 是儲存在相關聯非同步狀態中的可呼叫物件。 任何傳回的值會以不可部分完成的方式儲存為相關聯非同步狀態的傳回結果，並將狀態設為就緒。 如此一來，封鎖於相關聯非同步狀態上的所有執行緒都會解除封鎖。  
  
##  <a name="op_bool"></a>  packaged_task::operator bool  
 指定物件是否具有 `associated asynchronous state`。  
  
```
operator bool() const noexcept;
```  
  
### <a name="return-value"></a>傳回值  
 如果物件有關聯的非同步狀態，就是 `true`，否則為 `false`。  
  
##  <a name="packaged_task"></a>  packaged_task::packaged_task 建構函式  
 建構 `packaged_task` 物件。  
  
```
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```  
  
### <a name="parameters"></a>參數  
 `Right`  
 `packaged_task` 物件。  
  
 `alloc`  
 記憶體配置器。 如需詳細資訊，請參閱 [\<allocators>](../standard-library/allocators-header.md)。  
  
 `fn`  
 函式物件。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會建構不具有「相關聯非同步狀態」的 `packaged_task` 物件。  
  
 第二個建構函式建構 `packaged_task` 物件並從 `Right` 中轉移關聯的非同步狀態。 在作業完成後，`Right` 不再具有相關聯的非同步狀態。  
  
 第三個建構函式建構 `packaged_task` 物件，其 `fn` 複本儲存在其相關的非同步狀態中。  
  
 第四個建構函式建構 `packaged_task` 物件，其 `fn` 複本儲存在其相關的非同步狀態中，並使用 `alloc` 供記憶體配置。  
  
##  <a name="dtorpackaged_task_destructor"></a>  packaged_task::~packaged_task 解構函式  
 終結 `packaged_task` 物件。  
  
```
~packaged_task();
```  
  
### <a name="remarks"></a>備註  
 如果「相關聯的非同步狀態」不是「就緒」，解構函式會將具有錯誤碼 `broken_promise` 的 [future_error](../standard-library/future-error-class.md) 例外狀況在相關聯的非同步狀態中儲存為結果，且封鎖於相關聯非同步狀態上的所有執行緒都會解除封鎖。  
  
##  <a name="reset"></a>  packaged_task::reset  
 使用新的「相關聯非同步狀態」來取代現有的相關聯非同步狀態。  
  
```
void reset();
```  
  
### <a name="remarks"></a>備註  
 實際上，這個方法會執行 `*this = packaged_task(move(fn))`，其中 *fn* 是儲存於此物件之相關聯非同步狀態中的函式物件。 因此，會清除物件的狀態，並且可以像在新建構的物件上一樣地呼叫 [get_future](#get_future)、[operator()](#op_call) 和 [make_ready_at_thread_exit](#make_ready_at_thread_exit)。  
  
##  <a name="swap"></a>  packaged_task::swap  
 交換指定之物件的相關聯非同步狀態。  
  
```
void swap(packaged_task& Right) noexcept;
```  
  
### <a name="parameters"></a>參數  
 `Right`  
 `packaged_task` 物件。  
  
##  <a name="valid"></a>  packaged_task::valid  
 指定物件是否具有 `associated asynchronous state`。  
  
```
bool valid() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果物件有關聯的非同步狀態，就是 `true`，否則為 `false`。  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)




