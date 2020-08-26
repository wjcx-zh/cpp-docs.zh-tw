---
title: '&lt;thread&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: 64a62180243d77f361c243b2a89de56b0a14920e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845038"
---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt; 函式

[get_id](#get_id)\
[sleep_for](#sleep_for)\
[sleep_until](#sleep_until)\
[交換](#swap)\
[yield](#yield)

## <a name="get_id"></a><a name="get_id"></a> get_id

可唯一識別執行目前的執行緒。

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>傳回值

[thread:: id](../standard-library/thread-class.md) 類型的物件，可唯一識別執行目前的執行緒。

## <a name="sleep_for"></a><a name="sleep_for"></a> sleep_for

封鎖呼叫執行緒。

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>參數

*Rel_time*\
[duration](../standard-library/duration-class.md) 物件，可指定時間間隔。

### <a name="remarks"></a>備註

函式至少會封鎖呼叫執行緒的 *Rel_time*所指定的時間。 這個函式不會擲回任何例外狀況。

## <a name="sleep_until"></a><a name="sleep_until"></a> sleep_until

封鎖呼叫執行緒，至少直到指定的時間。

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>參數

*Abs_time*\
表示時間點。

### <a name="remarks"></a>備註

這個函式不會擲回任何例外狀況。

## <a name="swap"></a><a name="swap"></a> 交換

交換兩個 `thread` 物件的狀態。

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>參數

*離開*\
左 `thread` 物件。

*對*\
右 `thread` 物件。

### <a name="remarks"></a>備註

此函式會呼叫 `Left.swap(Right)`。

## <a name="yield"></a><a name="yield"></a> 產量

向作業系統表示執行其他執行緒，即使目前的執行緒通常會繼續執行。

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>另請參閱

[\<thread>](../standard-library/thread.md)
