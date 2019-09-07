---
title: CComCurrency 類別
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
ms.openlocfilehash: d6eb67e04ebb2b9084874a586eafc744df2d3f40
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739774"
---
# <a name="ccomcurrency-class"></a>CComCurrency 類別

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
|[CComCurrency：： operator-](#operator_-)|此運算子用在 `CComCurrency` 物件上執行減法。|
|[CComCurrency::operator !=](#operator_neq)|比較兩個 `CComCurrency` 物件是否不相等。|
|[CComCurrency：： operator *](#operator_star)|此運算子用在 `CComCurrency` 物件上執行乘法。|
|[CComCurrency::operator *=](#operator_star_eq)|此運算子用在 `CComCurrency` 物件上執行乘法並指派結果。|
|[CComCurrency：： operator/](#operator_div)|此運算子用在 `CComCurrency` 物件上執行除法。|
|[CComCurrency::operator /=](#operator_div_eq)|此運算子用在 `CComCurrency` 物件上執行除法並指派結果。|
|[CComCurrency：： operator +](#operator_add)|此運算子用在 `CComCurrency` 物件上執行加法。|
|[CComCurrency：： operator + =](#operator_add_eq)|此運算子用在 `CComCurrency` 物件上執行加法並指派結果給目前物件。|
|[CComCurrency：： operator <](#operator_lt)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。|
|[CComCurrency：： operator < =](#operator_lt_eq)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。|
|[CComCurrency：： operator =](#operator_eq)|此運算子將 `CComCurrency` 物件指派給新的值。|
|[CComCurrency::operator -=](#operator_-_eq)|此運算子用在 `CComCurrency` 物件上執行減法並指派結果。|
|[CComCurrency：： operator = =](#operator_eq_eq)|此運算子比較兩個 `CComCurrency` 物件是否相等。|
|[CComCurrency：： operator >](#operator_gt)|此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。|
|[CComCurrency::operator >=](#operator_gt_eq)|此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。|
|[CComCurrency：： operator 貨幣](#operator_currency)|轉換貨幣物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|您的類別實例所建立的貨幣變數。|

## <a name="remarks"></a>備註

`CComCurrency`這是 CURRENCY 資料類型的包裝函式。 貨幣會實作為8個位元組的2補數整數值，並以10000進行調整。 這得出一個定點數字，小數點左邊 15 位數，小數點右邊 4 位數。 CURRENCY 資料類型對於涉及 money 的計算，或精確度很重要的任何固定點計算而言非常有用。

此`CComCurrency`包裝函式會針對此固定點類型執行算術、指派和比較作業。 已選取支援的應用程式來控制固定點計算期間可能發生的四捨五入錯誤。

`CComCurrency` 物件讓您分兩部分來存取小數點兩側的數字：整數部分儲存小數點左邊的值，小數部分儲存小數點右邊的值。 小陣列件會在內部儲存為介於-9999 （CY_MIN_FRACTION）和 + 9999 （CY_MAX_FRACTION）之間的整數值。 方法[CComCurrency：： getfraction 會](#getfraction)傳回的值是以10000（CY_SCALE）的因數來調整。

指定`CComCurrency`物件的整數和小陣列件時，請記住小陣列件是介於0到9999範圍內的數位。 在處理貨幣時，例如，美元在小數點後面只以兩個有效位數來表示金額，這就很重要。 即使沒有顯示最後兩位數，也必須納入考量。

|值|可能的 CComCurrency 指派|
|-----------|---------------------------------------|
|$10.50|CComCurrency （10，5000）*或*CComCurrency （10.50）|
|$10.05|CComCurrency （10500）*或*CComCurrency （10.05）|

CY_MIN_FRACTION、CY_MAX_FRACTION 和 CY_SCALE 值定義于 atlcur.h 中。

## <a name="requirements"></a>需求

**標頭：** atlcur.h。h

##  <a name="ccomcurrency"></a>CComCurrency：： CComCurrency

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

*curSrc*<br/>
現有的 `CComCurrency` 物件。

*cySrc*<br/>
貨幣類型的變數。

*bSrc*、 *dSrc*、 *fSrc*、 *lSrc*、 *sSrc*、 *ulSrc、usSrc*<br/>
給定給成員變數`m_currency`的初始值。

*cSrc*<br/>
包含指定給成員變數`m_currency`之初始值的字元。

*nInteger*、 *nFraction*<br/>
初始貨幣值的整數和小數部分。 如需詳細資訊，請參閱[CComCurrency](../../atl/reference/ccomcurrency-class.md)總覽。

*pDispSrc*<br/>
`IDispatch`指標。

*varSrc*<br/>
VARIANT 類型的變數。 目前線程的地區設定是用來執行轉換。

*szSrc*<br/>
包含初始值的 Unicode 或 ANSI 字串。 目前線程的地區設定是用來執行轉換。

### <a name="remarks"></a>備註

此函式會設定[CComCurrency：： m_currency](#m_currency)的初始值，並接受各種資料類型，包括整數、字串、浮點數、貨幣變數和其他`CComCurrency`物件。 如果未提供任何值， `m_currency`會設定為0。

如果發生錯誤（例如溢位），則會使用 HRESULT （描述錯誤）來呼叫`AtlThrow`缺少空的例外狀況規格（**throw （）** ）。

當使用浮點或雙精度值來指派值時，請注意`CComCurrency(10.50)`相當於`CComCurrency(10,5000)`和 not `CComCurrency(10,50)`。

##  <a name="getcurrencyptr"></a>CComCurrency：： GetCurrencyPtr

傳回 `m_currency` 資料成員的位址。

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>傳回值

傳回`m_currency`資料成員的位址

##  <a name="getfraction"></a>CComCurrency：： Getfraction 會

呼叫這個方法，以傳回`CComCurrency`物件的小數部分。

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>傳回值

傳回`m_currency`資料成員的小數部分。

### <a name="remarks"></a>備註

小陣列件是介於-9999 （CY_MIN_FRACTION）和 + 9999 （CY_MAX_FRACTION）之間的4位整數值。 `GetFraction`傳回以10000（CY_SCALE）縮放的這個值。 CY_MIN_FRACTION、CY_MAX_FRACTION 和 CY_SCALE 的值定義于 atlcur.h 中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

##  <a name="getinteger"></a>CComCurrency：： GetInteger

呼叫這個方法，以取得`CComCurrency`物件的整數部分。

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>傳回值

傳回`m_currency`資料成員的整數部分。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

##  <a name="m_currency"></a>CComCurrency：： m_currency

貨幣資料成員。

```
CURRENCY m_currency;
```

### <a name="remarks"></a>備註

這個成員會保留這個類別的方法所存取和操作的貨幣。

##  <a name="operator_-"></a>CComCurrency：： operator-

此運算子用在 `CComCurrency` 物件上執行減法。

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*cur*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

`CComCurrency`傳回物件，代表減法的結果。 發生錯誤（例如溢位）時，這個運算子會呼叫`AtlThrow`並描述錯誤的 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

##  <a name="operator_neq"></a>CComCurrency：： operator！ =

這個運算子會比較兩個物件是否不相等。

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*cur*<br/>
要比較的 `CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果要比較的專案不等於`CComCurrency`物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

##  <a name="operator_star"></a>CComCurrency：： operator *

此運算子用在 `CComCurrency` 物件上執行乘法。

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*nOperand*<br/>
乘數。

*cur*<br/>
當做`CComCurrency`乘數使用的物件。

### <a name="return-value"></a>傳回值

`CComCurrency`傳回物件，代表相乘的結果。 發生錯誤（例如溢位）時，這個運算子會呼叫`AtlThrow`並描述錯誤的 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

##  <a name="operator_star_eq"></a>CComCurrency：： operator\*=

此運算子用在 `CComCurrency` 物件上執行乘法並指派結果。

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>參數

*nOperand*<br/>
乘數。

*cur*<br/>
當做`CComCurrency`乘數使用的物件。

### <a name="return-value"></a>傳回值

傳回已更新`CComCurrency`的物件。 發生錯誤（例如溢位）時，這個運算子會呼叫`AtlThrow`並描述錯誤的 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

##  <a name="operator_div"></a>CComCurrency：： operator/

此運算子用在 `CComCurrency` 物件上執行除法。

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>參數

*nOperand*<br/>
除數。

### <a name="return-value"></a>傳回值

傳回代表除法結果的物件。`CComCurrency` 如果除數為0，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

##  <a name="operator_div_eq"></a>CComCurrency：： operator/=

此運算子用在 `CComCurrency` 物件上執行除法並指派結果。

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>參數

*nOperand*<br/>
除數。

### <a name="return-value"></a>傳回值

傳回已更新`CComCurrency`的物件。 如果除數為0，就會發生判斷提示失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

##  <a name="operator_add"></a>CComCurrency：： operator +

此運算子用在 `CComCurrency` 物件上執行加法。

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*cur*<br/>
要`CComCurrency`加入至原始物件的物件。

### <a name="return-value"></a>傳回值

`CComCurrency`傳回物件，表示加法的結果。 發生錯誤（例如溢位）時，這個運算子會呼叫`AtlThrow`並描述錯誤的 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

##  <a name="operator_add_eq"></a>CComCurrency：： operator + =

此運算子用在 `CComCurrency` 物件上執行加法並指派結果給目前物件。

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>參數

*cur*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CComCurrency`的物件。 發生錯誤（例如溢位）時，這個運算子會呼叫`AtlThrow`並描述錯誤的 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

##  <a name="operator_lt"></a>CComCurrency：： operator&lt;

此運算子比較兩個 `CComCurrency` 物件來判斷何者較小。

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*cur*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於第二個物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

##  <a name="operator_lt_eq"></a>CComCurrency：： operator&lt;=

此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較小。

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*cur*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於或等於第二個物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

##  <a name="operator_eq"></a>CComCurrency：： operator =

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

*curSrc*<br/>
`CComCurrency` 物件。

*cySrc*<br/>
貨幣類型的變數。

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
要指派給`CComCurrency`物件的數值。

### <a name="return-value"></a>傳回值

傳回已更新`CComCurrency`的物件。 發生錯誤（例如溢位）時，這個運算子會呼叫`AtlThrow`並描述錯誤的 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

##  <a name="operator_-_eq"></a>CComCurrency：： operator-=

此運算子用在 `CComCurrency` 物件上執行減法並指派結果。

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>參數

*cur*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CComCurrency`的物件。 發生錯誤（例如溢位）時，這個運算子會呼叫`AtlThrow`並描述錯誤的 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

##  <a name="operator_eq_eq"></a>CComCurrency：： operator = =

此運算子比較兩個 `CComCurrency` 物件是否相等。

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*cur*<br/>
要`CComCurrency`比較的物件。

### <a name="return-value"></a>傳回值

如果物件相等，則傳回 TRUE （也就是， `m_currency`兩個物件中的資料成員（整數和小數）都具有相同的值），否則傳回 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

##  <a name="operator_gt"></a>CComCurrency：： operator&gt;

此運算子比較兩個 `CComCurrency` 物件來判斷何者較大。

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*cur*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於第二個物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

##  <a name="operator_gt_eq"></a>CComCurrency：： operator&gt;=

此運算子比較兩個 `CComCurrency` 物件來判斷是否相等或何者較大。

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>參數

*cur*<br/>
`CComCurrency` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於或等於第二個物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

##  <a name="operator_currency"></a>CComCurrency：： operator 貨幣

這些運算子是用來將`CComCurrency`物件轉換成貨幣資料類型。

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>傳回值

傳回貨幣物件的參考。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

##  <a name="round"></a>CComCurrency：： Round

呼叫這個方法，將貨幣四捨五入為指定的小數位數。

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>參數

*nDecimals*<br/>
`m_currency`將四捨五入的位數，範圍介於0到4之間。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

##  <a name="setfraction"></a>CComCurrency：： SetFraction

呼叫此方法以設定 `CComCurrency` 物件的小數部分。

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>參數

*nFraction*<br/>
要指派給`m_currency`資料成員之小數部分的值。 小陣列件的正負號必須與整陣列件相同，而且值必須介於-9999 （CY_MIN_FRACTION）到 + 9999 （CY_MAX_FRACTION）之間。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

##  <a name="setinteger"></a>CComCurrency：： SetInteger

呼叫此方法以設定 `CComCurrency` 物件的整數部分。

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>參數

*nInteger*<br/>
要指派給`m_currency`資料成員之整陣列件的值。 整陣列件的正負號必須符合現有小陣列件的正負號。

*nInteger*必須在 CY_MIN_INTEGER 到 CY_MAX_INTEGER （含）的範圍內。 這些值會在 atlcur.h 中定義。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>另請參閱

[COleCurrency 類別](../../mfc/reference/colecurrency-class.md)<br/>
[符號](/windows/win32/api/wtypes/ns-wtypes-cy~r1)<br/>
[類別總覽](../../atl/atl-class-overview.md)
