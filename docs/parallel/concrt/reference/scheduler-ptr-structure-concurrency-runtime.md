---
title: scheduler_ptr結構
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 60d71a26e5dffcadfb900ef15c26a6d9dc6d6f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358774"
---
# <a name="scheduler_ptr-structure"></a>scheduler_ptr結構

代表排程器的指標。 此類的存在是為了通過使用shared_ptr或僅使用原始指標進行簡單引用來規範共用存留期。

## <a name="syntax"></a>語法

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|已多載。 從排程器 shared_ptr 建立排程器指標|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[scheduler_ptr:取得](#get)|傳回排程器的原始指標|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[scheduler_ptr::操作員布爾](#operator_bool)|測試排程器指標是否為非 null|
|[scheduler_ptr:操作員-&gt;](#operator_ptr)|作用如同指標|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`scheduler_ptr`

## <a name="requirements"></a>需求

**標題:** pplinterface.h

**命名空間:** 併發

## <a name="scheduler_ptrget-method"></a><a name="get"></a>scheduler_ptr:獲取方法

返回指向計劃程式的原始指標。

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>傳回值

## <a name="scheduler_ptroperator-bool"></a><a name="operator_bool"></a>scheduler_ptr::操作員布爾

測試計劃程式指標是否為非空。

```cpp
operator bool() const;
```

## <a name="scheduler_ptroperator-gt"></a><a name="operator_ptr"></a>scheduler_ptr:操作員-&gt;

像指標一樣。

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>傳回值

## <a name="scheduler_ptrscheduler_ptr-constructor"></a><a name="ctor"></a>scheduler_ptr:scheduler_ptr構造函數

從shared_ptr創建計劃程式指標到計畫程式。

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>參數

*調度*<br/>
要轉換的計畫程式。

*p 時間*<br/>
要轉換的計劃程式指標。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
