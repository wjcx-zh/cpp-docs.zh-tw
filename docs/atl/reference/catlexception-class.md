---
title: CAtlException 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs:
- C++
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56038ffe4c6062422ea34a439e73b0d90a37cfb8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097727"
---
# <a name="catlexception-class"></a>CAtlException 類別

這個類別會定義 ATL 例外狀況。

## <a name="syntax"></a>語法

```
class CAtlException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlException::CAtlException](#catlexception)|建構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlException::operator HRESULT](#operator_hresult)|將轉換的 HRESULT 值目前的物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlException::m_hr](#m_hr)|物件所建立的 HRESULT，以及用來儲存錯誤狀況的類型的變數。|

## <a name="remarks"></a>備註

A`CAtlException`物件都代表與 ATL 作業相關的例外狀況。 `CAtlException`類別包含儲存轉換運算子，可讓您將處理例外狀況，如同它是 HRESULT 的例外狀況原因的狀態碼的公用資料成員。

一般情況下，您會呼叫`AtlThrow`而不是建立`CAtlException`直接物件。

## <a name="requirements"></a>需求

**標頭：** atlexcept.h

##  <a name="catlexception"></a>  CAtlException::CAtlException

建構函式。

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>參數

*hr*<br/>
HRESULT 錯誤碼。

##  <a name="operator_hresult"></a>  CAtlException::operator HRESULT

將轉換的 HRESULT 值目前的物件。

```
operator HRESULT() const throw ();
```

##  <a name="m_hr"></a>  CAtlException::m_hr

HRESULT 資料成員。

```
HRESULT m_hr;
```

### <a name="remarks"></a>備註

儲存錯誤條件之資料成員。 HRESULT 值建構函式，設定[CAtlException::CAtlException](#catlexception)。

## <a name="see-also"></a>另請參閱

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[類別概觀](../../atl/atl-class-overview.md)
