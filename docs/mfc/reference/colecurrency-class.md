---
title: COleCurrency 類別
ms.date: 08/29/2019
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
ms.openlocfilehash: cc69143101c5d00d4f9a689bd02abdd9596e5b53
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753928"
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
|[COle貨幣:COle貨幣](#colecurrency)|建構 `COleCurrency` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle貨幣:格式](#format)|生成`COleCurrency`物件的格式化字串表示形式。|
|[COle 貨幣:取得狀態](#getstatus)|獲取此`COleCurrency`物件的狀態(有效性)。|
|[COle貨幣::P](#parsecurrency)|從字串讀取貨幣值並設定的值`COleCurrency`。|
|[COle 貨幣::設定貨幣](#setcurrency)|設置此`COleCurrency`物件的值。|
|[COle 貨幣::設定狀態](#setstatus)|設置此`COleCurrency`物件的狀態(有效性)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[運算符 |](#operator_eq)|複製值`COleCurrency`。|
|[運算符 +, -](#operator_plus_minus)|新增、減去與變更值符號`COleCurrency`。|
|[運算子 *, -]](#operator_plus_minus_eq)|從該`COleCurrency`物件中`COleCurrency`添加和減去值。|
|[操作員 */](#operator_star)|按整`COleCurrency`數值縮放值。|
|[運算子 *, /*](#operator_star_div_eq)|按整`COleCurrency`數值縮放此值。|
|[運算子 <<](#operator_stream)|將`COleCurrency`值輸出到`CArchive`或`CDumpContext`。|
|[運算子 >>](#operator_stream)|從`CArchive``COleCurrency`輸入物件。|
|[運算子](#operator_currency)|將`COleCurrency`值轉換為貨幣。|
|[運算符 *、<、<等。](#colecurrency_relational_operators)|比較兩`COleCurrency`個值。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COle貨幣:m_cur](#m_cur)|包含此`COleCurrency`物件的基礎貨幣。|
|[COle貨幣:m_status](#m_status)|包含此`COleCurrency`物件的狀態。|

## <a name="remarks"></a>備註

`COleCurrency`沒有基類。

貨幣作為 8 位元組、兩個補數整數值(縮放為 10,000)實現。 這得出一個定點數字，小數點左邊 15 位數，小數點右邊 4 位數。 MONEY 數據類型對於涉及資金的計算或精度很重要的任何定點計算都非常有用。 它是 OLE`VARIANT`自動化資料類型的可能類型之一。

`COleCurrency`還實現此定點類型的一些基本算術運算。 已選擇支援的操作來控制在定點計算期間發生的舍入誤差。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`COleCurrency`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COle貨幣:COle貨幣

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

*西斯爾克*<br/>
要複製到新`COleCurrency`物件的貨幣值。

*庫爾斯克*<br/>
要複製到`COleCurrency`新`COleCurrency`物件的現有物件。

*varSrc*<br/>
要轉換為`VARIANT`貨幣值(VT_CY)`COleVariant`並複製到`COleCurrency`新 物件的現有資料結構(可能是物件)。

*n單位**,n分數單位*指示要複製`COleCurrency`到新 物件的值的單位和小數部分(在 1/10,000 中)。

### <a name="remarks"></a>備註

所有這些構造函數都創建新`COleCurrency`的物件,初始化到指定值。 下面簡要介紹了每個構造函數。 除非另有說明,否則新項目`COleCurrency`的狀態將設置為有效。

- COle貨幣() 建構`COleCurrency`初始 化為 0(零)的物件。

- COle貨幣(`cySrc`)`COleCurrency`從[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy~r1)值建構物件。

- COle貨幣(`curSrc`)`COleCurrency``COleCurrency`從現有 物件建構物件。 新對象的狀態與源物件相同。

- COle貨幣(`varSrc`)`COleCurrency`建構 一個物件。 嘗試將[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)`COleVariant`結構或 物件轉換為貨幣 (VT_CY) 值。 如果此轉換成功,則轉換後的值將複製到`COleCurrency`新 物件中。 如果不是,`COleCurrency`則物件的值設置為零 (0), 其狀態無效。

- COle貨幣`nUnits``nFractionalUnits`()從指定的數值`COleCurrency`分 量構造物件。 如果小數零件的絕對值大於 10,000,則對單位進行適當的調整。 請注意,單位和小數部分由已簽名的長值指定。

有關詳細資訊,請參閱 Windows SDK 中的[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy~r1)和[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)條目。

### <a name="example"></a>範例

以下範例顯示了零參數和雙參數建構函式的效果:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COle貨幣:格式

呼叫此成員函數以創建貨幣值的格式化表示形式。

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
指示區域設置的標誌。 只有以下標誌與貨幣相關:

- LOCALE_NOUSEROVERRIDE 使用系統默認區域設置,而不是自定義用戶設置。

*lcid*<br/>
指示用於轉換區域設置 ID。

### <a name="return-value"></a>傳回值

`CString`包含格式化的貨幣值。

### <a name="remarks"></a>備註

它使用本地語言規範(區域設置的 IT)設定值格式。 貨幣符號不包括在返回的值中。 如果此`COleCurrency`物件的狀態為 null,則傳回值為空字串。 如果狀態無效,則返回字串由字串資源IDS_INVALID_CURRENCY指定。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COle 貨幣:取得狀態

調用此成員函數以獲取給定`COleCurrency`物件的狀態(有效性)。

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>傳回值

返回此值`COleCurrency`的狀態。

### <a name="remarks"></a>備註

返回值由`CurrencyStatus``COleCurrency`類中定義的枚舉類型定義。

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

有關這些狀態值的簡要說明,請參閱以下清單:

- `COleCurrency::valid`指示此`COleCurrency`物件有效。

- `COleCurrency::invalid`指示此物件`COleCurrency`無效;如果表明此物件無效。也就是說,其值可能不正確。

- `COleCurrency::null`指示此`COleCurrency`物件為 null,即未為此物件提供任何值。 (這是"無值"的資料庫意義上的"空",而不是C++ NULL。

在以下情況下,`COleCurrency`物件的狀態無效:

- 如果其值從無法轉換為貨幣值的`COleVariant`VARIANT 或值設置。

- 如果此物件在算術賦值操作期間(例如`+=`或 ) 經歷了**\*** 溢出或 下溢。

- 如果為此物件分配了無效值。

- 如果此物件的狀態被顯式設定為無效使用[SetStatus](#setstatus)。

有關可能將狀態設置為無效的操作的詳細資訊,請參閱以下成員函數:

- [COleCurrency](#colecurrency)

- [運算符 |](#operator_eq)

- [運算子 = -](#operator_plus_minus)

- [運算子 * 與 -}](#operator_plus_minus_eq)

- [運算子 = /](#operator_star)

- [運算子 * 與 /*](#operator_star_div_eq)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COle貨幣:m_cur

此`COleCurrency`物件的基礎[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy~r1)結構。

### <a name="remarks"></a>備註

> [!CAUTION]
> 更改此函數返回的`CURRENCY`指標存取的結構中的值將更改此`COleCurrency`物件的值。 它不會更改此`COleCurrency`物件的狀態。

有關詳細資訊,請參閱 Windows SDK 中的[「貨幣](/windows/win32/api/wtypes/ns-wtypes-cy~r1)」條目。

## <a name="colecurrencym_status"></a><a name="m_status"></a>COle貨幣:m_status

此數據成員的類型是枚舉類型`CurrencyStatus`,在類`COleCurrency`中 定義。

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>備註

有關這些狀態值的簡要說明,請參閱以下清單:

- `COleCurrency::valid`指示此`COleCurrency`物件有效。

- `COleCurrency::invalid`指示此物件`COleCurrency`無效;如果表明此物件無效。也就是說,其值可能不正確。

- `COleCurrency::null`指示此`COleCurrency`物件為 null,即未為此物件提供任何值。 (這是"無值"的資料庫意義上的"空",而不是C++ NULL。

在以下情況下,`COleCurrency`物件的狀態無效:

- 如果其值從無法轉換為貨幣值的`COleVariant`VARIANT 或值設置。

- 如果此物件在算術賦值操作期間(例如`+=`或 ) 經歷了**\*** 溢出或 下溢。

- 如果為此物件分配了無效值。

- 如果此物件的狀態被顯式設定為無效使用[SetStatus](#setstatus)。

有關可能將狀態設置為無效的操作的詳細資訊,請參閱以下成員函數:

- [COleCurrency](#colecurrency)

- [運算符 |](#operator_eq)

- [運算符 +, -](#operator_plus_minus)

- [運算子 *, -]](#operator_plus_minus_eq)

- [操作員 */](#operator_star)

- [運算子 *, /*](#operator_star_div_eq)

> [!CAUTION]
> 此數據成員適用於高級程式設計情況。 應使用內聯成員函數[「獲取狀態」](#getstatus)和[「設定狀態](#setstatus)」 。 有關`SetStatus`顯式設置此數據成員的進一步注意事項,請參閱。

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COle貨幣::運算符 |

這些重載賦值運算符將源幣種值複製到`COleCurrency`此物件中。

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>備註

每個運算子的簡要描述如下:

- **運算子 *(** `cySrc` **)** 該`CURRENCY`值將複製到物件`COleCurrency`中 ,其狀態設置為有效。

- **運算子 *(** `curSrc` **)** 操作數的值和狀態,將現有`COleCurrency`物件複製到`COleCurrency`此 物件中。

- 運算子 **(varSrc* **operator =(** **)** 如果`VARIANT`將值(或[COleVariant](../../mfc/reference/colevariant-class.md)物件)轉換為`VT_CY`貨幣 ( ) 成功,則轉換的`COleCurrency`值將複製到此 物件,其狀態設置為有效。 如果轉換不成功,`COleCurrency`則物件的值設定為 0,其狀態設置為無效。

有關詳細資訊,請參閱 Windows SDK 中的[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy~r1)和[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)條目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COle貨幣::運算符 +, -

這些運算元允許您相互添加和減去兩`COleCurrency`個`COleCurrency`值,並更改值的符號。

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>備註

如果任一操作數為空,則結果`COleCurrency`值的狀態為 null。

如果算術運算溢出,則生成的`COleCurrency`值無效。

如果操作數無效,另一個不為空,則生成的`COleCurrency`值的狀態無效。

有關有效、無效和 null 狀態值的詳細資訊,請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COle貨幣::運算符 *,-*

允許您在此`COleCurrency`物件中添加和減`COleCurrency`去 值。

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>備註

如果任一操作數為空,則此`COleCurrency`物件的狀態設置為 null。

如果算術運算溢出,則此`COleCurrency`物件的狀態設置為無效。

如果任一操作數無效,另一個操作數不為空,則此`COleCurrency`物件的狀態設置為無效。

有關有效、無效和 null 狀態值的詳細資訊,請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COle貨幣::操作員\*和/

允許您按整數值縮放`COleCurrency`值。

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>備註

如果`COleCurrency`操作數為 null,`COleCurrency`則結果值的狀態為 null。

如果算術運算溢出或下溢,則結果`COleCurrency`值的狀態無效。

如果`COleCurrency`操作數無效,則`COleCurrency`結果 值的狀態無效。

有關有效、無效和 null 狀態值的詳細資訊,請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COle貨幣::運算符\*= 、 /=

允許您按整數值縮放`COleCurrency`此值。

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>備註

如果`COleCurrency`操作數為 null,`COleCurrency`則此 物件的狀態設定為 null。

如果算術運算溢出,則此`COleCurrency`物件的狀態設置為無效。

如果`COleCurrency`操作數無效,則`COleCurrency`此 物件的狀態設置為無效。

有關有效、無效和 null 狀態值的詳細資訊,請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COle貨幣:運算符&lt;&lt;,&gt;&gt;

支持診斷轉儲並存儲到存檔。

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

提取**>>**( ) 運算子支援從存檔載入。

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COle貨幣::操作員貨幣

返回其`CURRENCY`值從此`COleCurrency`物件複製的結構。

```
operator CURRENCY() const;
```

### <a name="remarks"></a>備註

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COle貨幣::P

呼叫此成員函數以分析字串以讀取貨幣值。

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>參數

*lpsz貨幣*<br/>
指向要解析的 null 終止字串的指標。

*dwFlags*<br/>
指示區域設定的標誌,可能為以下標誌:

- LOCALE_NOUSEROVERRIDE 使用系統默認區域設置,而不是自定義用戶設置。

*lcid*<br/>
指示用於轉換區域設置 ID。

### <a name="return-value"></a>傳回值

如果字串已成功轉換為貨幣值,則非零,否則為 0。

### <a name="remarks"></a>備註

它使用本地語言規範(區域設置 ID)來表示原始字串中非數位字元的含義。

有關區域設定 ID 值的討論,請參閱[支援多種語言](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages)。

如果字串已成功轉換為貨幣值,則此`COleCurrency`物件的值將設置為該值,其狀態將有效。

如果字串無法轉換為貨幣值,或者存在數位溢出,則此`COleCurrency`物件的狀態無效。

如果字串轉換由於記憶體配置錯誤而失敗,此函數將引發[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。 在任何其他錯誤狀態下,此函數將引發[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>COle 貨幣關係運算子

比較兩個貨幣值,如果條件為 true,則返回非零;否則 0。

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
> 如果操作數的狀態為**<** null**\<****>** 或無效 ,則排序操作**>=**(、、、、) 的返回值未定義。 相等運算子 ( `==` `!=`、 ) 考慮操作數的狀態。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COle 貨幣::設定貨幣

調用此成員函數以設置此`COleCurrency`物件的單位和小數部分。

```cpp
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>參數

*n單位**,n分數單位*指示要複製`COleCurrency`到此 物件的值的單位和小數部分(在 1/10,000 中)。

### <a name="remarks"></a>備註

如果小數部分的絕對值大於 10,000,則對單位進行適當的調整,如以下示例的第三個所示。

請注意,單位和小數部分由已簽名的長值指定。 以下範例的第四個範例顯示了參數具有不同符號時發生的情況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COle 貨幣::設定狀態

調用此成員函數以設置此`COleCurrency`物件的狀態(有效性)。

```cpp
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>參數

*status*<br/>
此`COleCurrency`物件的新狀態。

### <a name="remarks"></a>備註

*狀態*參數值`CurrencyStatus`由 枚舉類型定義,該類型在`COleCurrency`類中 定義。

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

有關這些狀態值的簡要說明,請參閱以下清單:

- `COleCurrency::valid`指示此`COleCurrency`物件有效。

- `COleCurrency::invalid`指示此物件`COleCurrency`無效;如果表明此物件無效。也就是說,其值可能不正確。

- `COleCurrency::null`指示此`COleCurrency`物件為 null,即未為此物件提供任何值。 (這是"無值"的資料庫意義上的"空",而不是C++ NULL。

> [!CAUTION]
> 此功能適用於高級程式設計情況。 此函數不會更改此物件中的數據。 它最常用於將狀態設置為 null 或無效。 請注意,賦值運算子 ([運算符 =](#operator_eq)) 和[SetCurrency](#setcurrency)會根據來源值將物件的狀態設定為 。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 類別](../../mfc/reference/colevariant-class.md)
