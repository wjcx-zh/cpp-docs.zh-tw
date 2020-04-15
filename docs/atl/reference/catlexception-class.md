---
title: CAtl 例外類
ms.date: 11/04/2016
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
ms.openlocfilehash: 6da56e4d6c443520eb6f857624a5923e71a1e580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319000"
---
# <a name="catlexception-class"></a>CAtl 例外類

此類定義 ATL 異常。

## <a name="syntax"></a>語法

```
class CAtlException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[例外:CAtlException](#catlexception)|建構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlException::操作員 HRESULT](#operator_hresult)|將當前物件強制轉換為 HRESULT 值。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CAtlException:m_hr](#m_hr)|由物件創建並用於儲存錯誤條件的 HRESULT 類型的變數。|

## <a name="remarks"></a>備註

`CAtlException`物件表示與 ATL 操作相關的異常條件。 類別`CAtlException`包括儲存指示異常原因的狀態代碼的公共資料成員,以及允許您將異常視為 HRESULT 的強制轉換運算符。

通常,您將調用`AtlThrow`而不是直接`CAtlException`創建 物件。

## <a name="requirements"></a>需求

**標題:** atlexcept.h

## <a name="catlexceptioncatlexception"></a><a name="catlexception"></a>例外:CAtlException

建構函式。

```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```

### <a name="parameters"></a>參數

*人力資源*<br/>
HRESULT 錯誤碼。

## <a name="catlexceptionoperator-hresult"></a><a name="operator_hresult"></a>CAtlException::操作員 HRESULT

將當前物件強制轉換為 HRESULT 值。

```
operator HRESULT() const throw ();
```

## <a name="catlexceptionm_hr"></a><a name="m_hr"></a>CAtlException:m_hr

HRESULT 資料成員。

```
HRESULT m_hr;
```

### <a name="remarks"></a>備註

存儲錯誤條件的數據成員。 HRESULT 值由建構函數[CAtlException 設定::CAtlexception](#catlexception)。

## <a name="see-also"></a>另請參閱

[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)<br/>
[類別概觀](../../atl/atl-class-overview.md)
