---
title: CW2CWEX 類別
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: 07dd0319586054403d8ed0c8efc813b4061e355a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330439"
---
# <a name="cw2cwex-class"></a>CW2CWEX 類別

此類由字串轉換宏 CW2CTEX 和 CT2CWEX 以及類型 def CW2W 使用。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
翻譯過程中使用的緩衝區的大小。 默認長度為 128 位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CW2CWEX:CW2CWEX](#cw2cwex)|建構函式。|
|[CW2CWEX:*CW2CWEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CW2CWEX::運營商LPCWSTR](#operator_lpcwstr)|轉換運算符。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|存儲原始碼字串的資料成員。|

## <a name="remarks"></a>備註

除非需要額外的功能,否則請使用代碼中的 CW2CTEX、CT2CWEX 或 CW2W。

此類在迴圈中使用是安全的,並且不會溢出堆疊。 默認情況下,ATL 轉換類和宏使用當前線程的 ANSI 代碼頁進行轉換。

以下巨集基於此類:

- CW2CTEX

- CT2CWEX

以下類型def基於此類:

- CW2W

有關這些文字轉換巨集的討論,請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="example"></a>範例

有關使用這些字串轉換巨集的範例,請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="requirements"></a>需求

**標題:** atlconv.h

## <a name="cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX:CW2CWEX

建構函式。

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*n代碼頁*<br/>
字碼頁。 此類中未使用。

### <a name="remarks"></a>備註

分配翻譯過程中使用的緩衝區。

## <a name="cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX:*CW2CWEX

解構函式。

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>備註

釋放分配的緩衝區。

## <a name="cw2cwexm_psz"></a><a name="m_psz"></a>CW2CWEX::m_psz

存儲原始碼字串的資料成員。

```
LPCWSTR m_psz;
```

## <a name="cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX::運營商LPCWSTR

轉換運算符。

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>傳回值

將文字字串返回為 LPCWSTR 類型。

## <a name="see-also"></a>另請參閱

[CA2AEX 類別](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 類別](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 類別](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 類別](../../atl/reference/cw2aex-class.md)<br/>
[CW2WEX 類別](../../atl/reference/cw2wex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
