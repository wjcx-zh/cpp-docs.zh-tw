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
ms.openlocfilehash: d1f960f8ec94b8e573490d4e708d4240b894b5ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277148"
---
# <a name="cw2cwex-class"></a>CW2CWEX 類別

這個類別會使用字串轉換巨集 CW2CTEX CT2CWEX 和 typedef CW2W。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
轉譯程序中使用的緩衝區大小。 預設長度為 128 位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|建構函式。|
|[CW2CWEX::~CW2CWEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|轉換運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|儲存在來源字串資料成員。|

## <a name="remarks"></a>備註

除非需要額外的功能，使用 CW2CTEX、 CT2CWEX 或 CW2W 程式碼中。

這個類別能夠安全地在迴圈中使用，而且不會堆疊溢位。 根據預設，ATL 轉換類別和巨集會使用目前的執行緒 ANSI 字碼頁轉換。

下列巨集根據此類別：

- CW2CTEX

- CT2CWEX

下列的 typedef 根據此類別：

- CW2W

如需這些文字轉換巨集的討論，請參閱 < [ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="example"></a>範例

請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)如需使用這些字串轉換巨集的範例。

## <a name="requirements"></a>需求

**標頭：** atlconv.h

##  <a name="cw2cwex"></a>  CW2CWEX::CW2CWEX

建構函式。

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*nCodePage*<br/>
字碼頁。 不使用這個類別中。

### <a name="remarks"></a>備註

配置轉譯程序中使用的緩衝區。

##  <a name="dtor"></a>  CW2CWEX:: ~ CW2CWEX

解構函式。

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>備註

釋放配置的緩衝區。

##  <a name="m_psz"></a>  CW2CWEX::m_psz

儲存在來源字串資料成員。

```
LPCWSTR m_psz;
```

##  <a name="operator_lpcwstr"></a>  CW2CWEX::operator LPCWSTR

轉換運算子。

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>傳回值

當輸入 LPCWSTR，傳回文字字串。

## <a name="see-also"></a>另請參閱

[CA2AEX 類別](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 類別](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 類別](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 類別](../../atl/reference/cw2aex-class.md)<br/>
[CW2WEX 類別](../../atl/reference/cw2wex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
