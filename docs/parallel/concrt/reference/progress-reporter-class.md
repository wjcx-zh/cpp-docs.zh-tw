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
ms.openlocfilehash: dac74085278418153ddec502f6257ce13885704d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282535"
---
# <a name="progressreporter-class"></a>progress_reporter 類別

進度報告程式類別可供報告特定類型的進度通知。 每個 progress_reporter 物件都會繫結至特定非同步動作或作業。

## <a name="syntax"></a>語法

```
template<typename _ProgressType>
class progress_reporter;
```

#### <a name="parameters"></a>參數

*_ProgressType*<br/>
透過進度報告程式報告之每個進度通知的承載類型。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[progress_reporter](#ctor)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[report](#report)|將進度報告傳送至這個進度報告程式所繫結的非同步動作或作業。|

## <a name="remarks"></a>備註

此類型只適用於 Windows 執行階段應用程式的。

## <a name="inheritance-hierarchy"></a>繼承階層

`progress_reporter`

## <a name="requirements"></a>需求

**標頭：** ppltasks.h

**命名空間：** concurrency

##  <a name="ctor"></a> progress_reporter

```
progress_reporter();
```

##  <a name="report"></a> 報表

將進度報告傳送至這個進度報告程式所繫結的非同步動作或作業。

```
void report(const _ProgressType& val) const;
```

### <a name="parameters"></a>參數

*val*<br/>
透過進度通知報告的承載。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
