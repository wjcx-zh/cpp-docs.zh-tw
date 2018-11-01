---
title: CA2CAEX 類別
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: 42115df5d70121d90631bf18c5d3fa83b130485b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487274"
---
# <a name="ca2caex-class"></a>CA2CAEX 類別

這個類別會使用字串轉換巨集 CA2CTEX CT2CAEX 和 typedef CA2CA。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<int t_nBufferLength = 128>
class CA2CAEX
```

#### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
轉譯程序中使用的緩衝區大小。 預設長度為 128 位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|建構函式。|
|[CA2CAEX:: ~ CA2CAEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CA2CAEX::operator LPCSTR](#operator_lpcstr)|轉換運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CA2CAEX::m_psz](#m_psz)|儲存在來源字串資料成員。|

## <a name="remarks"></a>備註

除非需要額外的功能，使用 CA2CTEX、 CT2CAEX 或 CA2CA 在自己的程式碼。

這個類別能夠安全地在迴圈中使用，而且不會堆疊溢位。 根據預設，ATL 轉換類別及巨集將使用目前的執行緒 ANSI 字碼頁，來進行轉換。

下列巨集根據此類別：

- CA2CTEX

- CT2CAEX

下列的 typedef 根據此類別：

- CA2CA

如需這些文字轉換巨集的討論，請參閱 < [ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="example"></a>範例

請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)如需使用這些字串轉換巨集的範例。

## <a name="requirements"></a>需求

**標頭：** atlconv.h

##  <a name="ca2caex"></a>  CA2CAEX::CA2CAEX

建構函式。

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*nCodePage*<br/>
未使用這個類別中。

### <a name="remarks"></a>備註

建立做為轉換所需的緩衝區。

##  <a name="dtor"></a>  CA2CAEX:: ~ CA2CAEX

解構函式。

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>備註

釋放配置的緩衝區。

##  <a name="m_psz"></a>  CA2CAEX::m_psz

儲存在來源字串資料成員。

```
LPCSTR m_psz;
```

##  <a name="operator_lpcstr"></a>  CA2CAEX::operator LPCSTR

轉換運算子。

```
operator LPCSTR() const throw();
```

### <a name="return-value"></a>傳回值

當輸入 LPCSTR，傳回文字字串。

## <a name="see-also"></a>另請參閱

[CA2AEX 類別](../../atl/reference/ca2aex-class.md)<br/>
[CA2WEX 類別](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 類別](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 類別](../../atl/reference/cw2wex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
