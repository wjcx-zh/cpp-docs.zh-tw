---
title: '&lt;shared_mutex&gt;'
ms.date: 03/27/2019
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
ms.openlocfilehash: f33a9c5fe4c5058d039feff896f7e53fe40cbf31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217476"
---
# <a name="ltshared_mutex"></a>&lt;shared_mutex>

&lt;Shared_mutex> 標頭會提供同步處理原始物件，以保護可由多個執行緒存取的共用資料。 除了 mutex 類別所提供的獨佔存取權控制，共用的 mutex 類別也允許由多個執行緒共用擁有權以進行非獨佔存取。 共用的 mutex 可用來控制可供數個執行緒讀取，而不會造成競爭情形，但必須由單一執行緒獨佔寫入的資源。

標頭 &lt; shared_mutex> 會定義類別 `shared_mutex` 和 `shared_timed_mutex` 、類別範本 `shared_lock` ，以及 `swap` 共用 mutex 支援的範本函式。

|類別|說明|
|-------------|-----------------|
|[shared_mutex 類別](#class_shared_mutex)|共用的 mutex 類型，可由一個代理程式以獨佔方式鎖定，或者由多個代理程式以非獨佔方式共用。|
|[shared_timed_mutex 類別](#class_shared_timed_mutex)|共用的計時 mutex 類型，可由一個代理程式以獨佔方式鎖定，或者由多個代理程式以非獨佔方式共用。|
|[shared_lock 類別](#class_shared_lock)|包裝共用 mutex 以支援多個代理程式之計時鎖定作業和非獨佔共用的類別範本。|

|函式|說明|
|---------------|-----------------|
|[調換](#function_swap)|交換函式參數所參考的共用 mutex 物件內容。|

## <a name="syntax"></a>語法

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>備註

`shared_mutex` 類別的執行個體是「共用的 mutex 類型」**，此類型可控制某個範圍內 mutex 的共用擁有權。 共用的 mutex 類型符合 mutex 類型以及成員的所有需求，以支援共用的非獨佔擁有權。

共用的 mutex 類型支援 `lock_shared`、`unlock_shared` 和 `try_lock_shared` 等其他方法：

- `lock_shared` 方法會封鎖呼叫執行緒，直到執行緒取得 mutex 的共用擁有權。

- `unlock_shared` 方法會釋放呼叫執行緒所持有之 mutex 的共用擁有權。

- `try_lock_shared` 方法會嘗試在不造成封鎖的情況下取得 mutex 的共用擁有權。 其傳回型別可以轉換成 **`bool`** ，而且 **`true`** 如果方法取得擁有權，則為，否則為 **`false`** 。

`shared_timed_mutex` 類別是「共用的計時 mutex 類型」**，此類型符合共用 mutex 類型和計時 mutex 類型的需求。

共用的計時 mutex 類型支援 `try_lock_shared_for` 和 `try_lock_shared_until` 等其他方法：

- `try_lock_shared_for` 方法會嘗試取得 mutex 的共用擁有權，直到經過了參數所指定的持續時間為止。 如果持續時間不是正數，此方法就相當於 `try_lock_shared`。 除非取得了共用擁有權，否則此方法不會在指定的持續期間內傳回。 **`true`** 如果方法取得擁有權，則其傳回值為，否則為 **`false`** 。

- `try_lock_shared_until` 方法會嘗試取得 mutex 的共用擁有權，直到經過了指定的絕對時間為止。 如果已經過了指定的時間，此方法就相當於 `try_lock_shared`。 除非取得了共用擁有權，否則此方法不會在指定的時間之前傳回。 **`true`** 如果方法取得擁有權，則其傳回值為，否則為 **`false`** 。

`shared_lock`類別樣板擴充對計時鎖定的支援，並將擁有權轉移到共用的 mutex。 擁有權可在建構期間或完成之後取得，並可轉移到另一個 `shared_lock` 物件。 `shared_lock` 類型的物件可以移動，但無法複製。

> [!WARNING]
> 從 Visual Studio 2015 開始，c + + 標準程式庫同步處理類型是以 Windows 同步處理原始物件為基礎，且不再使用 ConcRT （除非目標平臺是 Windows XP）。 Shared_mutex> 中定義的類型 &lt; 不應該與任何 ConcRT 類型或函式搭配使用。

## <a name="classes"></a>類別

### <a name="shared_mutex-class"></a><a name="class_shared_mutex"></a> shared_mutex 類別

`shared_mutex` 類別會利用共用擁有權語意來實作非遞迴的 mutex。

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

### <a name="shared_timed_mutex-class"></a><a name="class_shared_timed_mutex"></a>shared_timed_mutex 類別

`shared_timed_mutex` 類別會利用符合計時 mutex 類型需求的共用擁有權語意，來實作非遞迴的 mutex。

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

### <a name="shared_lock-class"></a><a name="class_shared_lock"></a> shared_lock 類別

類別範本 `shared_lock` 控制範圍內共用 mutex 物件的共用擁有權。 樣板參數必須是共用的 mutex 類型。

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>函式

### <a name="swap"></a><a name="function_swap"></a>調換

交換 `shared_lock` 物件。

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

交換兩個 `shared_lock` 物件的內容。 效力等同於 `x.swap(y)`。

## <a name="requirements"></a>需求

**標頭︰** &lt;shared_mutex >

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[&lt;mutex>](../standard-library/mutex.md)
