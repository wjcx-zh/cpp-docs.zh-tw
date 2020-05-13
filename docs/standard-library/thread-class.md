---
title: thread 類別
ms.date: 11/04/2016
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
helpviewer_keywords:
- std::thread [C++]
- std::thread [C++], thread
- std::thread [C++], detach
- std::thread [C++], get_id
- std::thread [C++], hardware_concurrency
- std::thread [C++], join
- std::thread [C++], joinable
- std::thread [C++], native_handle
- std::thread [C++], swap
ms.openlocfilehash: 13996a8ec4ab56fc56a78606d1a2ce8d76994c0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375860"
---
# <a name="thread-class"></a>thread 類別

定義一個物件，用來觀察和管理應用程式內執行的執行緒。

## <a name="syntax"></a>語法

```cpp
class thread;
```

## <a name="remarks"></a>備註

可以使用**線程**物件觀察和管理應用程式中的執行線程。 使用預設建構函式建立的執行緒物件不會與執行的任何執行緒產生關聯。 使用可呼叫物件建構的執行緒物件會建立執行的新執行緒，並在該執行緒中呼叫可呼叫的物件。 執行緒物件可以移動，但無法複製。 因此，執行的執行緒只能與一個執行緒物件產生關聯。

執行的每個執行緒都有 `thread::id` 類型的唯一識別碼。 函式 `this_thread::get_id` 會傳回呼叫執行緒的識別碼。 成員函式 `thread::get_id` 會傳回執行緒物件所管理之執行緒的識別碼。 針對預設建構的執行緒物件，`thread::get_id` 方法所傳回的物件值會與所有預設建構的執行緒物件相同，但不同於 `this_thread::get_id` 針對可在呼叫期間加入之執行的任何執行緒所傳回的值。

## <a name="members"></a>成員

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[thread::id 類別](#id_class)|可唯一識別相關聯的執行緒。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[執行緒](#thread)|構造**線程**物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[分離](#detach)|從**線程**物件分離關聯的線程。|
|[get_id](#get_id)|傳回相關聯執行緒的唯一識別碼。|
|[hardware_concurrency](#hardware_concurrency)|靜態。 傳回硬體執行緒內容的估計數目。|
|[加入](#join)|封鎖，直到相關聯的執行緒完成為止。|
|[可聯結](#joinable)|指定是否可加入相關聯的執行緒。|
|[native_handle](#native_handle)|傳回代表執行緒控制代碼的實作特定類型。|
|[交換](#swap)|將物件狀態與指定的**線程**物件交換。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[執行緒::運算符*](#op_eq)|將線程與當前**線程**物件關聯。|

## <a name="requirements"></a>需求

**標題:**\<執行緒>

**命名空間：** std

## <a name="threaddetach"></a><a name="detach"></a>線程::d埃塔奇

中斷連結相關聯的執行緒。 作業系統會變成負責在終止時釋放執行緒資源。

```cpp
void detach();
```

### <a name="remarks"></a>備註

呼叫 `detach` 之後，後續呼叫 [get_id](#get_id) 會傳回 [id](#id_class)。

如果與呼叫物件相關聯的執行緒不是可加入的，函式會擲回 [system_error](../standard-library/system-error-class.md)，且錯誤碼為 `invalid_argument`。

如果與呼叫物件相關聯的執行緒無效，函式會擲回 `system_error`，且錯誤碼為 `no_such_process`。

## <a name="threadget_id"></a><a name="get_id"></a>線程::get_id

取得相關聯執行緒的唯一識別碼。

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>傳回值

可唯一識別相關聯執行緒的 [thread:: id](#id_class) 物件，或者，如果沒有與物件相關聯的執行緒，則會傳回 `thread::id()`。

## <a name="threadhardware_concurrency"></a><a name="hardware_concurrency"></a>線程::hardware_concurrency

靜態方法，會傳回硬體執行緒內容的估計數目。

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>傳回值

硬體執行緒內容的估計數目。 如果無法計算或無法妥善定義值，此方法就會傳回 0。

## <a name="threadid-class"></a><a name="id_class"></a>執行緒::id 類別

針對程序中執行的每個執行緒提供唯一識別碼。

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>備註

預設建構函式所建立的物件，不會針對任何現有的執行緒比較是否等於 `thread::id` 物件。

所有預設建構的 `thread::id` 物件都會比較是否相等。

## <a name="threadjoin"></a><a name="join"></a>線程::聯接

封鎖，直到與呼叫物件相關聯之執行的執行緒完成為止。

```cpp
void join();
```

### <a name="remarks"></a>備註

如果呼叫成功，針對呼叫物件後續呼叫 [get_id](#get_id) 就會傳回預設的 [thread:: id](#id_class)，而其不會比較是否等於任何現有執行緒的 `thread::id`；如果呼叫失敗，則 `get_id` 所傳回的值就會保持不變。

## <a name="threadjoinable"></a><a name="joinable"></a>線程::可聯接

指定關聯的線程是否*可連發*。

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>傳回值

如果關聯的線程*是可聯接的*,**則為 true** ;否則,**假**。

### <a name="remarks"></a>備註

如果 `get_id() != id()`，執行緒物件就是「可加入」**。

## <a name="threadnative_handle"></a><a name="native_handle"></a>線程::native_handle

傳回代表執行緒控制代碼的實作特定類型。 您可以利用實作特定的方式來使用執行緒控制代碼。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>傳回值

`native_handle_type` 會定義為 Win32 `HANDLE`，這會轉換為 `void *`。

## <a name="threadoperator"></a><a name="op_eq"></a>執行緒::運算符*

將指定物件的執行緒關聯至目前的物件。

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*\
**線程**物件。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

如果呼叫物件是可加入的，方法即會呼叫 detach。

建立關聯之後，會將 `Other` 設為預設建構狀態。

## <a name="threadswap"></a><a name="swap"></a>執行緒::交換

將物件狀態與指定**線程**物件的狀態交換。

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*\
**線程**物件。

## <a name="threadthread-constructor"></a><a name="thread"></a>執行緒:執行緒建構函數

構造**線程**物件。

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>參數

*F*\
由執行緒執行的應用程式定義函式。

*A*\
要傳遞給*F*的參數清單。

*其他*\
現有**線程**物件。

### <a name="remarks"></a>備註

第一個建構函式會建構未關聯至執行之執行緒的物件。 針對建構物件呼叫 `get_id` 所傳回的值是 `thread::id()`。

第二個構造函數建構一個與新的執行線程關聯的物件,並執行在`INVOKE`[\<函數>](../standard-library/functional.md)中定義的偽函數。 如果沒有足夠的資源可用來啟動新的執行緒，此函式就會擲回 [system_error](../standard-library/system-error-class.md) 物件，且錯誤碼為 `resource_unavailable_try_again`。 如果對*F*的呼叫以未捕捉的例外終止,則呼叫[。](../standard-library/exception-functions.md#terminate)

第三個建構函式會建構與 `Other` 相關聯之執行緒相關聯的物件。 接著會將 `Other` 設為預設建構狀態。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<執行緒>](../standard-library/thread.md)
