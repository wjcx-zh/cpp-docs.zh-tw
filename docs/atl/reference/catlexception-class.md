---
title: CAtlException 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: f09d9b2f46233cf356f5ade8a5b90e08a213d276
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168198"
---
# <a name="catlexception-class"></a>CAtlException 類別

這個類別會定義 ATL 例外狀況。

## <a name="syntax"></a>語法

```cpp
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
|[CAtlException：： operator HRESULT](#operator_hresult)|將目前的物件轉換為 HRESULT 值。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlException：： m_hr](#m_hr)|由物件建立並用來儲存錯誤狀況之 HRESULT 類型的變數。|

## <a name="remarks"></a>備註

`CAtlException`物件代表與 ATL 作業相關的例外狀況條件。 `CAtlException`類別包含的公用資料成員，會儲存指出例外狀況原因的狀態碼，以及可讓您將例外狀況視為 HRESULT 的轉換運算子。

一般來說，您會呼叫`AtlThrow` ，而不是直接`CAtlException`建立物件。

## <a name="requirements"></a>需求

**標頭：** atlexcept。h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>CAtlException::CAtlException

建構函式。

```cpp
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>參數

*hr*<br/>
HRESULT 錯誤碼。

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException：： operator HRESULT

將目前的物件轉換為 HRESULT 值。

```cpp
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException：： m_hr

HRESULT 資料成員。

```cpp
HRESULT m_hr;
```

### <a name="remarks"></a>備註

儲存錯誤條件的資料成員。 HRESULT 值是由[CAtlException：： CAtlException](#catlexception)函數設定。

## <a name="see-also"></a>另請參閱

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[類別概觀](../../atl/atl-class-overview.md)
