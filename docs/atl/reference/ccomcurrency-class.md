---
title: CCom 貨幣類別
ms.date: 11/04/2016
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
ms.openlocfilehash: 541944e03e9caf6cba15612cf9e7cbbd239555ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327936"
---
# <a name="ccomcurrency-class"></a>CCom 貨幣類別

`CComCurrency` 有方法和運算子可建立及管理 CURRENCY 物件。

## <a name="syntax"></a>語法

```
class CComCurrency
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|`CComCurrency` 物件的建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|傳回 `m_currency` 資料成員的位址。|
|[CComCurrency::GetFraction](#getfraction)|呼叫此方法以傳回 `CComCurrency` 物件的小數部分。|
|[CComCurrency::GetInteger](#getinteger)|呼叫此方法以傳回 `CComCurrency` 物件的整數部分。|
|[CComCurrency::Round](#round)|呼叫此方法將 `CComCurrency` 物件四捨五入到最接近的整數值。|
|[CComCurrency::SetFraction](#setfraction)|呼叫此方法以設定 `CComCurrency` 物件的小數部分。|
|[CComCurrency::SetInteger](#setinteger)|呼叫此方法以設定 `CComCurrency` 物件的整數部分。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CCom貨幣::運算符 -](#operator_-)|此運算子用在 `CComCurrency` 物件上執行減法。|
|[CCom貨幣::操作員!*](#operator_neq)|比較兩個 `CComCurrency` 物件是否不相等。|
|[CCom貨幣::操作員 |](#operator_star)|此運算子用在 `CComCurrency` 物件上執行乘法。|
|[CCom貨幣::操作員 |](#operator_star_eq)|此運算子用在 `CComCurrency` 物件上執行乘法並指派結果。|
|[CCom貨幣::操作員/](#operator_div)|此運算子用在 `CComCurrency` 物件上執行除法。|
|[CCom貨幣::操作員/*](#operator_div_eq)|此運算子用在 `CComCurrency` 物件上執行除法並指派結果。|
|[CComCurrency::operator +](#operator_add)|此運算子用在 `CComCurrency` 物件上執行加法。|
|[CCom貨幣::操作員 |](#operator_add_eq)|此運算子用在 `CComCurrency` 物件上執行加法並指派結果給目前物件。|
|[CCom貨幣::操作員<](#operator_lt)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。|
|[CCom貨幣::操作員<|](#operator_lt_eq)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。|
|[CCom貨幣::運算符 |](#operator_eq)|此運算子將 `CComCurrency` 物件指派給新的值。|
|[CCom貨幣::運算符 -*](#operator_-_eq)|此運算子用在 `CComCurrency` 物件上執行減法並指派結果。|
|[CCom貨幣::運算符 |](#operator_eq_eq)|此運算子比較兩個 `CComCurrency` 物件是否相等。|
|[CCom貨幣::操作員>](#operator_gt)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。|
|[CCom貨幣::操作員>|](#operator_gt_eq)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。|
|[CCom貨幣::運營商貨幣](#operator_currency)|強制轉換貨幣物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|類實例創建的貨幣變數。|

## <a name="remarks"></a>備註

`CComCurrency` 是 CURRENCY 資料類型的包裝函式。 CURRENCY 實作為以 10,000 調整的 8 位元組二補數整數值。 這得出一個定點數字，小數點左邊 15 位數，小數點右邊 4 位數。 在涉及金額的計算中，或正確性很重要的任何固定點計算中，CURRENCY 資料類型相當有用。

包裝`CComCurrency`器實現此定點類型的算術、賦值和比較操作。 已選取支援的應用程式來控制固定點計算期間可能發生的四捨五入錯誤。

`CComCurrency` 物件讓您分兩部分來存取小數點兩側的數字：整數部分儲存小數點左邊的值，小數部分儲存小數點右邊的值。 小數部分在內部儲存為 -9999 (CY_MIN_FRACTION) 和 +9999 (CY_MAX_FRACTION) 之間的整數值。 方法[CCom貨幣:GetFraction](#getfraction)返回按 10000 (CY_SCALE) 因數縮放的值。

指定`CComCurrency`物件的整數和小數分量時,請記住小數分量是範圍 0 到 9999 中的數位。 在處理貨幣時，例如，美元在小數點後面只以兩個有效位數來表示金額，這就很重要。 即使沒有顯示最後兩位數，也必須納入考量。

|值|可能的 CComCurrency 指派|
|-----------|---------------------------------------|
|$10.50|CCom貨幣 (10,5000)*或*Ccom 貨幣 (10.50)|
|$10.05|CCom貨幣 (10,500)*或*CCom 貨幣 (10.05)|

atlcur.h 中定義 CY_MIN_FRACTION、CY_MAX_FRACTION 和 CY_SCALE 值。

## <a name="requirements"></a>需求

**標題:** atlcur.h

## <a name="ccomcurrencyccomcurrency"></a><a name="ccomcurrency"></a>CCom貨幣:Ccom貨幣

建構函式。

```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);
CComCurrency(USHORT usSrc);
CComCurrency(CHAR cSrc);
CComCurrency(DOUBLE dSrc);
CComCurrency(FLOAT fSrc);
CComCurrency(LONG lSrc);
CComCurrency(SHORT sSrc);
CComCurrency(BYTE bSrc);
CComCurrency(LONGLONG nInteger, SHORT nFraction);
explicit CComCurrency(LPDISPATCH pDispSrc);
explicit CComCurrency(const VARIANT& varSrc);
explicit CComCurrency(LPCWSTR szSrc);
explicit CComCurrency(LPCSTR szSrc);
```

### <a name="parameters"></a>參數

*庫爾斯克*<br/>
現有的 `CComCurrency` 物件。

*西斯爾克*<br/>
貨幣類型的變數。

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *ssrc*, *ulSrc, usSrc*<br/>
給成員變數`m_currency`的初始值。

*證監會*<br/>
包含給予成員變數`m_currency`的初始值的字元。

*nInteger*, *nfraction*<br/>
初始貨幣值的整數和小數分量。 有關詳細資訊,請參閱[CCom 貨幣](../../atl/reference/ccomcurrency-class.md)概述。

*pDispSrc*<br/>
指標`IDispatch`。

*varSrc*<br/>
VARIANT 類型的變數。 當前線程的區域設置用於執行轉換。

*什施爾克*<br/>
包含初始值的 Unicode 或 ANSI 字串。 當前線程的區域設置用於執行轉換。

### <a name="remarks"></a>備註

建構函數設置[CComCurrency::m_currency](#m_currency)的初始值,並接受各種資料類型,包括整數、字串、浮點數、貨幣變數和其他`CComCurrency`物件。 如果未提供任何值,`m_currency`則設定為 0。

如果出現錯誤(如溢出),構造函數缺少空異常規範 **(throw()**`AtlThrow`調用 ,HRESULT 描述錯誤。

當使用浮點或雙精度值分配值時,`CComCurrency(10.50)`註解等`CComCurrency(10,5000)`效`CComCurrency(10,50)`, 而不是 。

## <a name="ccomcurrencygetcurrencyptr"></a><a name="getcurrencyptr"></a>CCom貨幣:取得貨幣點

傳回 `m_currency` 資料成員的位址。

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>傳回值

傳`m_currency`回資料成員的位址

## <a name="ccomcurrencygetfraction"></a><a name="getfraction"></a>CCom貨幣:取得分數

呼叫此方法以返回`CComCurrency`物件的小數元件。

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>傳回值

返回`m_currency`數據成員的小數元件。

### <a name="remarks"></a>備註

小數分量是 -9999(CY_MIN_FRACTION)和 +9999 (CY_MAX_FRACTION) 之間的 4 位整數值。 `GetFraction`返回按 10000 (CY_SCALE) 縮放的此值。 CY_MIN_FRACTION、CY_MAX_FRACTION和CY_SCALE的值在 atlcur.h 中定義。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

## <a name="ccomcurrencygetinteger"></a><a name="getinteger"></a>CCom貨幣:取得Integer

呼叫此方法獲取`CComCurrency`物件的整數元件。

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>傳回值

返回數據成員的`m_currency`整數元件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

## <a name="ccomcurrencym_currency"></a><a name="m_currency"></a>CCom貨幣::m_currency

貨幣數據成員。

```
CURRENCY m_currency;
```

### <a name="remarks"></a>備註

此成員持有由此類的方法訪問和操作的貨幣。

## <a name="ccomcurrencyoperator--"></a><a name="operator_-"></a>CCom貨幣::運算符 -

此運算子用在 `CComCurrency` 物件上執行減法。

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*目前*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

返回表示`CComCurrency`減法結果的物件。 如果出現錯誤(如溢出),此操作員使用描述錯誤的 HRESULT`AtlThrow`調用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_neq"></a>CCom貨幣::操作員!*

此運算符比較兩個物件為不等式。

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*目前*<br/>
要比較的 `CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果要比較的項不等於物件,`CComCurrency`則返回 TRUE;否則,FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star"></a>CCom貨幣::操作員 |

此運算子用在 `CComCurrency` 物件上執行乘法。

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*恩奧佩安*<br/>
乘數。

*目前*<br/>
用作`CComCurrency`乘數的物件。

### <a name="return-value"></a>傳回值

返回表示`CComCurrency`乘法結果的物件。 如果出現錯誤(如溢出),此操作員使用描述錯誤的 HRESULT`AtlThrow`調用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star_eq"></a>CCom貨幣::運算子\*=

此運算子用在 `CComCurrency` 物件上執行乘法並指派結果。

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>參數

*恩奧佩安*<br/>
乘數。

*目前*<br/>
用作`CComCurrency`乘數的物件。

### <a name="return-value"></a>傳回值

返回更新`CComCurrency`的物件。 如果出現錯誤(如溢出),此操作員使用描述錯誤的 HRESULT`AtlThrow`調用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div"></a>CCom貨幣::操作員/

此運算子用在 `CComCurrency` 物件上執行除法。

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>參數

*恩奧佩安*<br/>
除數。

### <a name="return-value"></a>傳回值

返回表示`CComCurrency`除法結果的物件。 如果分器為 0,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div_eq"></a>CCom貨幣::操作員/*

此運算子用在 `CComCurrency` 物件上執行除法並指派結果。

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>參數

*恩奧佩安*<br/>
除數。

### <a name="return-value"></a>傳回值

返回更新`CComCurrency`的物件。 如果分器為 0,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add"></a>CCom貨幣::運算符 |

此運算子用在 `CComCurrency` 物件上執行加法。

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*目前*<br/>
要`CComCurrency`添加到原始物件的物件。

### <a name="return-value"></a>傳回值

返回表示`CComCurrency`添加結果的物件。 如果出現錯誤(如溢出),此操作員使用描述錯誤的 HRESULT`AtlThrow`調用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add_eq"></a>CCom貨幣::操作員 |

此運算子用在 `CComCurrency` 物件上執行加法並指派結果給目前物件。

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>參數

*目前*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

返回更新`CComCurrency`的物件。 如果出現錯誤(如溢出),此操作員使用描述錯誤的 HRESULT`AtlThrow`調用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt"></a>CCom貨幣::運算子&lt;

此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*目前*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於第二個物件 FALSE,則返回 TRUE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt_eq"></a>CCom貨幣::運算子&lt;=

此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*目前*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於或等於第二個物件 FALSE,則返回 TRUE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq"></a>CCom貨幣::運算符 |

此運算子將 `CComCurrency` 物件指派給新的值。

```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```

### <a name="parameters"></a>參數

*庫爾斯克*<br/>
`CComCurrency` 物件。

*西斯爾克*<br/>
貨幣類型的變數。

*sSrc,* *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *csrc,* *ulSrc,* *dSrc*<br/>
要分配給`CComCurrency`物件的數值。

### <a name="return-value"></a>傳回值

返回更新`CComCurrency`的物件。 如果出現錯誤(如溢出),此操作員使用描述錯誤的 HRESULT`AtlThrow`調用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

## <a name="ccomcurrencyoperator--"></a><a name="operator_-_eq"></a>CCom貨幣::運算符 -*

此運算子用在 `CComCurrency` 物件上執行減法並指派結果。

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>參數

*目前*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

返回更新`CComCurrency`的物件。 如果出現錯誤(如溢出),此操作員使用描述錯誤的 HRESULT`AtlThrow`調用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq_eq"></a>CCom貨幣::運算符 |

此運算子比較兩個 `CComCurrency` 物件是否相等。

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*目前*<br/>
要比較的 `CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果物件相等(即兩個對`m_currency`象 中的數據成員(整數和小數)具有相同的值,則返回 TRUE),否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt"></a>CCom貨幣::運算子&gt;

此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*目前*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於第二個物件 FALSE,則返回 TRUE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt_eq"></a>CCom貨幣::運算子&gt;=

此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*目前*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於或等於第二個物件 FALSE,則返回 TRUE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

## <a name="ccomcurrencyoperator-currency"></a><a name="operator_currency"></a>CCom貨幣::運營商貨幣

這些運算元用於將`CComCurrency`物件轉換為貨幣數據類型。

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>傳回值

返回對貨幣物件的引用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

## <a name="ccomcurrencyround"></a><a name="round"></a>CCom貨幣:圓形

調用此方法將貨幣舍入到指定的小數位數。

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>參數

*n 十進位*<br/>
將在範圍 0`m_currency`到 4 內舍入到的位數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

## <a name="ccomcurrencysetfraction"></a><a name="setfraction"></a>CCom貨幣::設定分數

呼叫此方法以設定 `CComCurrency` 物件的小數部分。

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>參數

*n 分數*<br/>
要分配給`m_currency`數據成員的小陣件的值。 小數分量的符號必須與整數分量相同,並且值必須在 -9999 (CY_MIN_FRACTION) 到 +9999 (CY_MAX_FRACTION) 範圍內。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

## <a name="ccomcurrencysetinteger"></a><a name="setinteger"></a>CCom貨幣::Setinteger

呼叫此方法以設定 `CComCurrency` 物件的整數部分。

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>參數

*內特格*<br/>
要分配給`m_currency`數據成員的整數元件的值。 整數元件的符號必須與現有小數元件的符號匹配。

*nInteger*必須在CY_MIN_INTEGER範圍內CY_MAX_INTEGER包含。 這些值在 atlcur.h 中定義。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>另請參閱

[COleCurrency 類別](../../mfc/reference/colecurrency-class.md)<br/>
[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy~r1)<br/>
[類別概觀](../../atl/atl-class-overview.md)
