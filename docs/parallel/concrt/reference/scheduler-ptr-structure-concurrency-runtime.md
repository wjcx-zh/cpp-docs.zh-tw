---
title: scheduler_ptr 結構
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: fd044a6255a17882c26183223f71564f98c9f7b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142776"
---
# <a name="scheduler_ptr-structure"></a>scheduler_ptr 結構

代表排程器的指標。 這個類別是用來允許使用 shared_ptr 或只使用原始指標的一般參考，來指定共用存留期間的規格。

## <a name="syntax"></a>語法

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[scheduler_ptr：： scheduler_ptr](#ctor)|已多載。 從排程器 shared_ptr 建立排程器指標|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[scheduler_ptr：： get](#get)|傳回排程器的原始指標|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[scheduler_ptr：： operator bool](#operator_bool)|測試排程器指標是否為非 null|
|[scheduler_ptr：： operator-&gt;](#operator_ptr)|作用如同指標|

## <a name="inheritance-hierarchy"></a>繼承階層

`scheduler_ptr`

## <a name="requirements"></a>需求

**標頭：** pplinterface。h

**命名空間：** concurrency

## <a name="get"></a>scheduler_ptr：： get 方法

傳回排程器的原始指標。

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>傳回值

## <a name="operator_bool"></a>scheduler_ptr：： operator bool

測試排程器指標是否為非 null。

```cpp
operator bool() const;
```

## <a name="operator_ptr"></a>scheduler_ptr：： operator-&gt;

行為就像指標。

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>傳回值

## <a name="ctor"></a>scheduler_ptr：： scheduler_ptr 的構造函式

建立從 shared_ptr 到排程器的排程器指標。

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>參數

*日程*<br/>
要轉換的排程器。

*pScheduler*<br/>
要轉換的排程器指標。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
