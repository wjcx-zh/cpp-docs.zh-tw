---
title: progress_reporter 類別
ms.date: 11/04/2016
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
ms.openlocfilehash: bd8f50a8c9829ff9de3e2412b89aa4de88d90db6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138765"
---
# <a name="progress_reporter-class"></a>progress_reporter 類別

進度報告程式類別可供報告特定類型的進度通知。 每個 progress_reporter 物件都會繫結至特定非同步動作或作業。

## <a name="syntax"></a>語法

```cpp
template<typename _ProgressType>
class progress_reporter;
```

### <a name="parameters"></a>參數

*_ProgressType*<br/>
透過進度報告程式報告之每個進度通知的承載類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[彙報](#report)|將進度報告傳送至這個進度報告程式所繫結的非同步動作或作業。|

## <a name="remarks"></a>備註

此類型僅適用于 Windows 執行階段應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層

`progress_reporter`

## <a name="requirements"></a>需求

**標頭：** ppltasks.h。h

**命名空間：** concurrency

## <a name="ctor"></a>progress_reporter

```cpp
progress_reporter();
```

## <a name="report"></a>彙報

將進度報告傳送至這個進度報告程式所繫結的非同步動作或作業。

```cpp
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>參數

*val*<br/>
要報告進度通知的承載。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
