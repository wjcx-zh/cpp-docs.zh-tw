---
title: COleCurrency 類別
ms.date: 11/04/2016
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: 00515e6822dad000c6745063c72d0ffaf367670b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504258"
---
# <a name="colecurrency-class"></a>COleCurrency 類別

封裝 OLE Automation 的 `CURRENCY` 資料類型。

## <a name="syntax"></a>語法

```
class COleCurrency
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|建構 `COleCurrency` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleCurrency::Format](#format)|產生`COleCurrency`物件的格式化字串表示。|
|[COleCurrency::GetStatus](#getstatus)|取得這個`COleCurrency`物件的狀態 (有效性)。|
|[COleCurrency::ParseCurrency](#parsecurrency)|從字串讀取貨幣值, 並設定的值`COleCurrency`。|
|[COleCurrency::SetCurrency](#setcurrency)|設定這個`COleCurrency`物件的值。|
|[COleCurrency::SetStatus](#setstatus)|設定這個`COleCurrency`物件的狀態 (有效性)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator =](#operator_eq)|`COleCurrency`複製值。|
|[operator +、-](#operator_plus_minus)|新增、減去和變更值的`COleCurrency`正負號。|
|[operator +=, -=](#operator_plus_minus_eq)|加入和減去此`COleCurrency` `COleCurrency`物件的值。|
|[operator */](#operator_star)|根據整數值來調整值。`COleCurrency`|
|[operator *=, /=](#operator_star_div_eq)|以整數`COleCurrency`值來調整此值。|
|[運算子 < <](#operator_stream)|將值輸出至`CArchive`或`CDumpContext`。 `COleCurrency`|
|[operator >>](#operator_stream)|`COleCurrency` 從`CArchive`輸入物件。|
|[運算子貨幣](#operator_currency)|`COleCurrency`將值轉換成貨幣。|
|[operator = =、<、< = 等等。](#colecurrency_relational_operators)|比較兩`COleCurrency`個值。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|包含這個`COleCurrency`物件的基礎貨幣。|
|[COleCurrency::m_status](#m_status)|包含此`COleCurrency`物件的狀態。|

## <a name="remarks"></a>備註

`COleCurrency`沒有基類。

貨幣會實作為8個位元組、兩個補數的整數值, 並以10000進行調整。 這得出一個定點數字，小數點左邊 15 位數，小數點右邊 4 位數。 CURRENCY 資料類型對於涉及 money 的計算, 或精確度很重要的任何固定點計算而言非常有用。 這是 OLE automation `VARIANT`資料類型的其中一種可能的類型。

`COleCurrency`也會針對此固定點類型執行一些基本的算數運算。 已選取支援的作業, 以控制在固定點計算期間發生的舍入錯誤。

## <a name="inheritance-hierarchy"></a>繼承階層

`COleCurrency`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="colecurrency"></a>COleCurrency:: COleCurrency

建構 `COleCurrency` 物件。

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
  COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>參數

*cySrc*<br/>
要複製到新`COleCurrency`物件中的貨幣值。

*curSrc*<br/>
要複製`COleCurrency`到新`COleCurrency`物件中的現有物件。

*varSrc*<br/>
要轉換`VARIANT`成貨幣值 (VT_CY `COleVariant` ) 並複製到新`COleCurrency`物件中的現有資料結構 (可能是物件)。

*nUnits*, *nFractionalUnits*指出要複製到新`COleCurrency`物件中的值單位和小數部分 (在 1/10000 中)。

### <a name="remarks"></a>備註

所有這些函式都會建立`COleCurrency`新的物件, 並初始化為指定的值。 以下是每個這些函式的簡短描述。 除非另有注明, 否則新`COleCurrency`專案的狀態會設定為 [有效]。

- COleCurrency () 會將`COleCurrency`初始化為 0 (零) 的物件結構化。

- COleCurrency (`cySrc`) 會從`COleCurrency` [貨幣](/windows/win32/api/wtypes/ns-wtypes-cy)值來構造物件。

- COleCurrency (`curSrc`) 會從`COleCurrency`現有`COleCurrency`的物件來構造物件。 新物件的狀態與來源物件相同。

- COleCurrency (`varSrc`) 會`COleCurrency`構造物件。 嘗試將[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)結構或`COleVariant`物件轉換為貨幣 (VT_CY) 值。 如果這種轉換成功, 轉換後的值會複製到新`COleCurrency`的物件中。 如果不是, 則`COleCurrency`物件的值會設定為零 (0), 且其狀態會是 [無效]。

- `COleCurrency(`從`, `指定`) Constructs a `的數值元件 nUnits nFractionalUnits COleCurrency ' 物件。 如果小數部分的絕對值大於 10000, 則會對單位進行適當的調整。 請注意, 單位和分數部分是以帶正負號的長數值來指定。

如需詳細資訊, 請參閱 Windows SDK 中的[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy)和[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)專案。

### <a name="example"></a>範例

下列範例顯示零參數和雙參數函式的效果:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="format"></a>COleCurrency:: Format

呼叫這個成員函式, 以建立貨幣值的格式化標記法。

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
表示地區設定的旗標。 只有下列旗標與貨幣相關:

- LOCALE_NOUSEROVERRIDE 會使用系統預設的地區設定, 而不是自訂的使用者設定。

*lcid*<br/>
表示用於轉換的地區設定識別碼。

### <a name="return-value"></a>傳回值

`CString`包含格式化貨幣值的。

### <a name="remarks"></a>備註

它會使用當地語言規格 (地區設定識別碼) 來格式化值。 貨幣符號不會包含在傳回的值中。 如果這個`COleCurrency`物件的狀態是 null, 則傳回值是空字串。 如果狀態無效, 則傳回字串會由字串資源識別碼S_INVALID_CURRENCY 指定。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="getstatus"></a>COleCurrency:: GetStatus

呼叫這個成員函式以取得給定`COleCurrency`物件的狀態 (有效性)。

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>傳回值

傳回此`COleCurrency`值的狀態。

### <a name="remarks"></a>備註

傳回值是由`CurrencyStatus` `COleCurrency`類別內定義的列舉型別所定義。

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

如需這些狀態值的簡短描述, 請參閱下列清單:

  - `COleCurrency::valid`指出這個`COleCurrency`物件是有效的。

  - `COleCurrency::invalid`指出這個`COleCurrency`物件無效; 也就是說, 它的值可能不正確。

  - `COleCurrency::null`指出這個`COleCurrency`物件是 null, 也就是沒有為這個物件提供任何值。 (這是「沒有值」的資料庫意義中的「null」, 而不是C++ null)。

在下列情況下`COleCurrency` , 物件的狀態無效:

- 如果其值是從無法轉換為貨幣`COleVariant`值的變數或值所設定。

- 如果這個物件具有溢位或反向溢位期間發生算術指派運算，例如`+=`或是 **\*=** 。

- 如果將不正確值指派給這個物件, 則為。

- 如果這個物件的狀態是使用[SetStatus](#setstatus)明確設定為無效, 則為。

如需可能將狀態設定為無效之作業的詳細資訊, 請參閱下列成員函式:

- [COleCurrency](#colecurrency)

- [operator =](#operator_eq)

- [operator +-](#operator_plus_minus)

- [operator + = 和-=](#operator_plus_minus_eq)

- [operator * /](#operator_star)

- [operator * = 和/=](#operator_star_div_eq)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

##  <a name="m_cur"></a>  COleCurrency::m_cur

這個`COleCurrency`物件的基礎[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy)結構。

### <a name="remarks"></a>備註

> [!CAUTION]
>  變更此函式所`CURRENCY`傳回之指標所存取的結構中的值, 將會變更這個`COleCurrency`物件的值。 它不會變更此`COleCurrency`物件的狀態。

如需詳細資訊, 請參閱 Windows SDK 中的[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy)專案。

##  <a name="m_status"></a>COleCurrency:: m_status

這個資料成員的型別是列舉型`CurrencyStatus`別, 它是在`COleCurrency`類別內定義的。

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>備註

如需這些狀態值的簡短描述, 請參閱下列清單:

- `COleCurrency::valid`指出這個`COleCurrency`物件是有效的。

- `COleCurrency::invalid`指出這個`COleCurrency`物件無效; 也就是說, 它的值可能不正確。

- `COleCurrency::null`指出這個`COleCurrency`物件是 null, 也就是沒有為這個物件提供任何值。 (這是「沒有值」的資料庫意義中的「null」, 而不是C++ null)。

在下列情況下`COleCurrency` , 物件的狀態無效:

- 如果其值是從無法轉換為貨幣`COleVariant`值的變數或值所設定。

- 如果這個物件具有溢位或反向溢位期間發生算術指派運算，例如`+=`或是 **\*=** 。

- 如果將不正確值指派給這個物件, 則為。

- 如果這個物件的狀態是使用[SetStatus](#setstatus)明確設定為無效, 則為。

如需可能將狀態設定為無效之作業的詳細資訊, 請參閱下列成員函式:

- [COleCurrency](#colecurrency)

- [operator =](#operator_eq)

- [operator +、-](#operator_plus_minus)

- [operator +=, -=](#operator_plus_minus_eq)

- [operator */](#operator_star)

- [operator *=, /=](#operator_star_div_eq)

> [!CAUTION]
>  此資料成員適用于先進的程式設計情況。 您應該使用內嵌成員函式[GetStatus](#getstatus)和[SetStatus](#setstatus)。 如`SetStatus`需有關明確設定此資料成員的進一步警告, 請參閱。

##  <a name="operator_eq"></a>COleCurrency:: operator =

這些多載指派運算子會將來源貨幣值複製`COleCurrency`到這個物件。

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>備註

每個運算子的簡短說明如下:

- **operator = (** `cySrc` **)** `CURRENCY` 此值會複製到物件中,而且其狀態會設定為有效。`COleCurrency`

- **operator = (** `curSrc` **)** 運算元的值和狀態, 現有`COleCurrency`的物件會複製到這個`COleCurrency`物件中。

- **operator = (** *varSrc* **)** 如果將`VARIANT`值 (或[COleVariant](../../mfc/reference/colevariant-class.md)物件) 轉換為貨幣 ( `VT_CY`) 成功, 轉換的值會複製到這個`COleCurrency`物件, 而且其狀態會設定為有效。 如果轉換不成功, `COleCurrency`物件的值會設定為 0, 且其狀態會是 [無效]。

如需詳細資訊, 請參閱 Windows SDK 中的[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy)和[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="operator_plus_minus"></a>COleCurrency:: operator +,-

這些運算子可讓您在彼此之間或`COleCurrency`彼此之間增加和減少兩個值, 以及變更`COleCurrency`值的正負號。

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>備註

如果其中一個運算元為 null, 則產生`COleCurrency`值的狀態會是 null。

如果算數運算溢位, 則產生`COleCurrency`的值無效。

如果運算元無效, 而另一個不是 null, 則產生`COleCurrency`值的狀態會無效。

如需有效、無效和 null 狀態值的詳細資訊, 請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="operator_plus_minus_eq"></a>COleCurrency:: operator + =、-=

可讓您在此`COleCurrency` `COleCurrency`物件中加上和減去值。

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>備註

如果其中一個運算元為 null, 則此`COleCurrency`物件的狀態會設定為 null。

如果算數運算溢位, 這個`COleCurrency`物件的狀態就會設定為無效。

如果其中一個運算元無效, 而另一個不是 null, 則此`COleCurrency`物件的狀態會設定為無效。

如需有效、無效和 null 狀態值的詳細資訊, 請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="operator_star"></a>COleCurrency:: operator \*和/

可讓您根據整數`COleCurrency`值來調整值。

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>備註

如果運算元是 null, 則產生`COleCurrency`值的狀態會是 null。 `COleCurrency`

如果算數運算溢位或下溢, 則產生`COleCurrency`值的狀態會無效。

如果運算元無效, 結果`COleCurrency`值的狀態就會是不正確。 `COleCurrency`

如需有效、無效和 null 狀態值的詳細資訊, 請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="operator_star_div_eq"></a>COleCurrency:: operator \*=,/=

可讓您以整數`COleCurrency`值來調整此值。

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>備註

如果運算元為 null, 則此`COleCurrency`物件的狀態會設定為 null。 `COleCurrency`

如果算數運算溢位, 這個`COleCurrency`物件的狀態就會設定為無效。

如果運算元無效, 這個`COleCurrency`物件的狀態就會設定為無效。 `COleCurrency`

如需有效、無效和 null 狀態值的詳細資訊, 請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="operator_stream"></a>COleCurrency:: operator &lt;、 &lt;&gt;&gt;

支援將診斷傾印並儲存至封存。

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>備註

「抽取」 **>>** () 運算子支援從封存載入。

##  <a name="operator_currency"></a>COleCurrency:: operator 貨幣

傳回從`CURRENCY`這個`COleCurrency`物件複製其值的結構。

```
operator CURRENCY() const;
```

### <a name="remarks"></a>備註

##  <a name="parsecurrency"></a>COleCurrency::P arseCurrency

呼叫這個成員函式來剖析字串, 以讀取貨幣值。

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>參數

*lpszCurrency*<br/>
要剖析之以 null 終止之字串的指標。

*dwFlags*<br/>
指出地區設定的旗標, 可能是下列旗標:

- LOCALE_NOUSEROVERRIDE 會使用系統預設的地區設定, 而不是自訂的使用者設定。

*lcid*<br/>
表示用於轉換的地區設定識別碼。

### <a name="return-value"></a>傳回值

如果字串已成功轉換為貨幣值, 則為非零, 否則為0。

### <a name="remarks"></a>備註

它會針對來源字串中非數值字元的意義使用當地語言規格 (地區設定識別碼)。

如需地區設定識別碼值的討論, 請參閱[支援多種語言](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages)。

如果字串已成功轉換為貨幣值, 則這個`COleCurrency`物件的值會設定為該值, 而其狀態會設為有效。

如果字串無法轉換成貨幣值, 或如果有數值溢位, 這個`COleCurrency`物件的狀態就會是不正確。

如果字串轉換因記憶體配置錯誤而失敗, 此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。 在任何其他錯誤狀態中, 此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency_relational_operators"></a>COleCurrency 關係運算子

比較兩個貨幣值, 如果條件為 true, 則傳回非零。否則為0。

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>備註

> [!NOTE]
>  如果任一運算元的狀態為 null 或 **<** 無效, **>** 則 **>=** 排序作業 (、 **\< =** 、、) 的傳回值為未定義。 等號比較運算子`==`( `!=`,) 會考慮運算元的狀態。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="setcurrency"></a>COleCurrency:: SetCurrency

呼叫這個成員函式, 以設定這個`COleCurrency`物件的單位和小數部分。

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>參數

*nUnits*, *nFractionalUnits*指出要複製到這個`COleCurrency`物件之值的單位和小數部分 (在 1/10000 中)。

### <a name="remarks"></a>備註

如果小數部分的絕對值大於 10000, 則會對單位進行適當的調整, 如下列範例中的第三個所示。

請注意, 單位和分數部分是以帶正負號的長數值來指定。 下列幾個範例中的第四個示範當參數有不同的符號時, 會發生什麼事。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="setstatus"></a>  COleCurrency::SetStatus

呼叫這個成員函式可設定這個`COleCurrency`物件的狀態 (有效性)。

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>參數

*status*<br/>
這個`COleCurrency`物件的新狀態。

### <a name="remarks"></a>備註

*狀態*參數值是由`CurrencyStatus`列舉型別所定義, 此類型定義于`COleCurrency`類別內。

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

如需這些狀態值的簡短描述, 請參閱下列清單:

- `COleCurrency::valid`指出這個`COleCurrency`物件是有效的。

- `COleCurrency::invalid`指出這個`COleCurrency`物件無效; 也就是說, 它的值可能不正確。

- `COleCurrency::null`指出這個`COleCurrency`物件是 null, 也就是沒有為這個物件提供任何值。 (這是「沒有值」的資料庫意義中的「null」, 而不是C++ null)。

> [!CAUTION]
>  這個函數適用于先進的程式設計情況。 此函式不會改變這個物件中的資料。 最常用來將狀態設定為 null 或無效。 請注意, 指派運算子 ( [operator =](#operator_eq)) 和[SetCurrency](#setcurrency)會根據來源值來設定物件的狀態。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 類別](../../mfc/reference/colevariant-class.md)
