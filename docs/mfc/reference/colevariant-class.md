---
title: COleVariant 類別
ms.date: 11/04/2016
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
ms.openlocfilehash: 7d8abea39a9baa3f447ca0d5f3ab1183367d531f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753717"
---
# <a name="colevariant-class"></a>COleVariant 類別

封裝 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) 資料類型。

## <a name="syntax"></a>語法

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COle 變數:COle變數](#colevariant)|建構 `COleVariant` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle 變數:附加](#attach)|將 VARIANT`COleVariant`附加到 。|
|[COle 變數:變更類型](#changetype)|更改此`COleVariant`物件的變體類型。|
|[COle 變數:清除](#clear)|清除這個 `COleVariant` 物件。|
|[COleVariant::D](#detach)|從 分離 VARIANT`COleVariant`並從 中返回 VARIANT。|
|[COlevariant:從變數陣列取得位元組](#getbytearrayfromvariantarray)|從現有變數組檢索位元組。|
|[COle 變數::設定字串](#setstring)|將字串設置為特定類型,通常是 ANSI。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COle變數::運算符 LPCVARIANT](#operator_lpcvariant)|轉換`COleVariant`成值轉換`LPCVARIANT`為 。|
|[COle變數::運算符 LPVARIANT](#operator_lpvariant)|將`COleVariant`物件轉換`LPVARIANT`為 。|
|[COleVariant::運算符 |](#operator_eq)|複製值`COleVariant`。|
|[COle變數::運算符 |](#operator_eq_eq)|比較兩`COleVariant`個值。|
|[COleVariant:運算子&lt;&lt;,&gt;&gt;](#operator_lt_lt__gt_gt)|將`COleVariant``CArchive`值輸出到`CDumpContext`或並`COleVariant`從中`CArchive`輸入 物件。|

## <a name="remarks"></a>備註

此數據類型用於 OLE 自動化。 具體而言[,DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)結構包含指向 VARIANT 結構陣列的指標。 結構`DISPPARAMS`用於將參數傳遞給[IDispatch:::invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

> [!NOTE]
> 此類派生自結構`VARIANT`。 這意味著您可以傳遞 調`COleVariant`用`VARIANT`的參數`VARIANT`,並且結構的數據成員`COleVariant`是 可訪問的數據成員。

兩個相關的 MFC 類別[COleCurrency](../../mfc/reference/colecurrency-class.md)和[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)封`VT_CY`裝`VT_DATE`了 變體資料類型貨幣 () 和 DATE ( )。 該`COleVariant`類在 DAO 類中廣泛使用;有關此類的典型用法,請參閱這些類,例如[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

有關詳細資訊,請參閱[變體](/windows/win32/api/oaidl/ns-oaidl-variant)、[貨幣](/windows/win32/api/wtypes/ns-wtypes-cy~r1)[、DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)和[IDispatch:呼叫](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)Windows SDK 中的項目。

有關`COleVariant`該類及其在 OLE 自動化中的使用的詳細資訊,請參閱文章[「在](../../mfc/automation.md)OLE 自動化中傳遞參數」。。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COle 變數:附加

調用此函數以將給定[的 VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)`COleVariant`物件附加到 當前物件。

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
要附加到`VARIANT``COleVariant`當前 物件的現有物件。

### <a name="remarks"></a>備註

此函數將*varSrc*的 VARTYPE 設定為VT_EMPTY。

有關詳細資訊,請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)條目。

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COle 變數:COle變數

建構 `COleVariant` 物件。

```
COleVariant();
COleVariant(const VARIANT& varSrc);
COleVariant(const COleVariant& varSrc);
COleVariant(LPCVARIANT pSrc);
COleVariant(LPCTSTR lpszSrc);
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc);
COleVariant(CString& strSrc);
COleVariant(BYTE nSrc);
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2);
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4);
COleVariant(const COleCurrency& curSrc);
COleVariant(float fltSrc);
COleVariant(double dblSrc);
COleVariant(const COleDateTime& timeSrc);
COleVariant(const CByteArray& arrSrc);
COleVariant(const CLongBinary& lbSrc);
COleVariant(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
要複製到`COleVariant`新`VARIANT``COleVariant`物件的現有或物件。

*pSrc*<br/>
指向將複製到新`VARIANT``COleVariant`物件的物件的指標。

*lpszSrc*<br/>
要複製到新`COleVariant`物件的 null 中止字串。

*弗茨爾克*<br/>
為新`VARTYPE``COleVariant`物件的 。

*斯特斯爾克*<br/>
要複製到新`COleVariant`物件的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

*nSrc,* *lSrc*要複製`COleVariant`到新 物件的數值。

*弗茨爾克*<br/>
為新`VARTYPE``COleVariant`物件的 。

*庫爾斯克*<br/>
要複製到新`COleVariant`物件的[COleCurrency](../../mfc/reference/colecurrency-class.md)物件。

*fltSrc*,*德布爾斯爾*<br/>
要複製到新的 `COleVariant` 物件中的數值。

*時間Src*<br/>
要複製到新`COleVariant`物件的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。

*阿爾斯爾克*<br/>
要複製到新`COleVariant`物件的[CByteArray](../../mfc/reference/cbytearray-class.md)物件。

*磅斯爾*<br/>
要複製到新`COleVariant`物件的[CLongBinary](../../mfc/reference/clongbinary-class.md)物件。

*皮德爾*<br/>
指向要複製到新`COleVariant`物件的[ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist)結構的指標。

### <a name="remarks"></a>備註

所有這些構造函數都創建初始化`COleVariant`為指定值的新物件。 下面簡要介紹了每個構造函數。

- **COleVariant)** 創建空`COleVariant`物件,VT_EMPTY。

- **COlevariant(** *varsrc* **)** 複製現有`VARIANT`物件`COleVariant`或 物件。 variant 類型會保留。

- **COlevariant(** *pSrc* **)** 複製現有`VARIANT`物件`COleVariant`或 物件。 variant 類型會保留。

- **COlevariant(** *lpszSrc* **)** 將字串複製到新物件VT_BSTR (UNICODE)。

- **COlevariant(lpszSrc,** *lpszSrc* **,** *vtSrc* **)** 將字串複製到新物件中。 參數*vtSrc*必須VT_BSTR (UNICODE) 或VT_BSTRT (ANSI)。

- **COlevariant(** *斯特斯克* **)** 將字串複製到新物件VT_BSTR (UNICODE)。

- **COlevariant(** *nSrc* **)** 將 8 位整數複製到新物件,VT_UI1。

- **COlevariant(** *nSrc* **,** *vtSrc* **)** 將 16 位整數(或布林值)複製到新物件中。 參數*vtSrc*必須VT_I2或VT_BOOL。

- **COlevariant(** *lSrc* **,** *vtSrc* **)** 將 32 位整數(或 SCODE 值)複製到新物件中。 參數*vtSrc*必須VT_I4、VT_ERROR 或VT_BOOL。

- **COlevariant(** *函式庫爾斯)* **)** 將`COleCurrency`值複製到新物件,VT_CY。

- **COlevariant(** *fltsrc* **)** 將 32 位浮點值複製到新物件,VT_R4。

- **COlevariant(** *dblSrc* **)** 將 64 位浮點值複製到新物件中,VT_R8。

- **COlevariant(** *時間 Src* **)** 將`COleDateTime`值複製到新物件VT_DATE。

- **COlevariant(** *arrSrc* **)** 將`CByteArray`物件複製到新物件,VT_EMPTY。

- **COlevariant(** *磅Src* **)** 將`CLongBinary`物件複製到新物件,VT_EMPTY。

有關 SCODE 的詳細資訊,請參閱 Windows SDK 中的[COM 錯誤代碼結構](/windows/win32/com/structure-of-com-error-codes)。

## <a name="colevariantchangetype"></a><a name="changetype"></a>COle 變數:變更類型

轉換此`COleVariant`物件中的變體值的類型。

```cpp
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>參數

*vartype*<br/>
此`COleVariant`物件的 VARTYPE。

*pSrc*<br/>
指向要轉換[的 VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)物件的指標。 如果此值為 NULL,`COleVariant`則此物件用作轉換的源。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows [ ](/windows/win32/api/oaidl/ns-oaidl-variant)SDK 中的[VARIANT、VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[變體更改類型](/windows/win32/api/oleauto/nf-oleauto-variantchangetype)條目。

## <a name="colevariantclear"></a><a name="clear"></a>COle 變數:清除

清除 `VARIANT`。

```cpp
void Clear();
```

### <a name="remarks"></a>備註

這將為此物件的 VARTYPE 設置為VT_EMPTY。 析`COleVariant`構函數調用此函數。

有關詳細資訊,請參閱 Windows `VARIANT`SDK 中的`VariantClear`VARTYPE 和 條目。

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant::D

從該`COleVariant`物件分離基礎[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)物件。

```
VARIANT Detach();
```

### <a name="remarks"></a>備註

此函數為此`COleVariant`物件的 VARTYPE 設置為VT_EMPTY。

> [!NOTE]
> 調用`Detach`後,調用者負責調`VariantClear`用`VARIANT`生成的結構。

有關詳細資訊,請參閱 Windows [ ](/windows/win32/api/oaidl/ns-oaidl-variant)SDK 中的[VARIANT、VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[變體清除](/windows/win32/api/oleauto/nf-oleauto-variantclear)條目。

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COlevariant:從變數陣列取得位元組

從現有變數組檢索位元陣列

```cpp
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>參數

*位元組*<br/>
對現有[CByteArray](../../mfc/reference/cbytearray-class.md)物件的引用。

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COle變數::運算符 LPCVARIANT

此強制轉換運算符返回`VARIANT`其值從此`COleVariant`物件複製的結構。

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>備註

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COle變數::運算符 LPVARIANT

呼叫此強制轉換運算符以造訪此`VARIANT``COleVariant`物件的基礎結構。

```
operator LPVARIANT();
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 更改此函數返回的`VARIANT`指標存取的結構中的值將更改此`COleVariant`物件的值。

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant::運算符 |

這些重載賦值運算符將源值複製到此`COleVariant`物件中。

```
const COleVariant& operator=(const VARIANT& varSrc);
const COleVariant& operator=(LPCVARIANT pSrc);
const COleVariant& operator=(const COleVariant& varSrc);
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc);
const COleVariant& operator=(BYTE nSrc);
const COleVariant& operator=(short nSrc);
const COleVariant& operator=(long lSrc);
const COleVariant& operator=(const COleCurrency& curSrc);
const COleVariant& operator=(float fltSrc);
const COleVariant& operator=(double dblSrc);
const COleVariant& operator=(const COleDateTime& dateSrc);
const COleVariant& operator=(const CByteArray& arrSrc);
const COleVariant& operator=(const CLongBinary& lbSrc);
```

### <a name="remarks"></a>備註

每個運算子的簡要描述如下:

- 運算子 **(varSrc* **operator =(** **)** 將現有的 VARIANT`COleVariant`或物件複製到此物件中。

- 運算子 *=(pSrc* **operator =(** **)** 將*pSrc*訪問的 VARIANT 物件複製到此物件中。

- 運算子 *=(lpszSrc* **)** **operator =(** 將 null 終止的字串複製到此物件,並將 VARTYPE 設定到VT_BSTR。

- 運算子 *=(strSrc* **operator =(** **)** 將[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件複製到此物件,並將 VARTYPE 設置到VT_BSTR。

- 運算子 **(nSrc)* **)** **operator =(** 將 8 位元或 16 位元整數值複製到此物件中。 如果*nSrc*是 8 位值,則此值的 VARTYPE 設置為VT_UI1。 如果*nSrc*是 16 位值,並且其 VARTYPE 是VT_BOOL,則保留該值;否則,它將設置為VT_I2。

- 運算子 *=(lSrc* **operator =(** **)** 將 32 位元整數值複製到此物件中。 如果VT_ERROR,則保留它;否則,它將設置為VT_I4。

- 運算子 **(curSrc* **operator =(** **)** 將[COleCurrency](../../mfc/reference/colecurrency-class.md)物件複製到此物件,並將 VARTYPE 設置到VT_CY。

- 運算子 *=(fltSrc)* **)** **operator =(** 將 32 位浮點值複製到此物件,並將 VARTYPE 設置為VT_R4。

- 運算子 *=(dblSrc)* **)** **operator =(** 將 64 位元浮點值複製到此物件,並將 VARTYPE 設置到VT_R8。

- **操作員 *(***dateSrc)* **)** 將[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件複製到此物件,並將 VARTYPE 設置到VT_DATE。

- 運算子 *=(arrSrc)* **)** **operator =(** 將[CByteArray](../../mfc/reference/cbytearray-class.md)物件`COleVariant`複製到 此物件。

- **操作員 *(***磅Src)* **)** 將[CLongBinary](../../mfc/reference/clongbinary-class.md)物件`COleVariant`複製到 此物件。

有關詳細資訊,請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)條目。

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COle變數::運算符 |

此運算元比較兩個變體值,如果它們相等,則返回非零;否則 0。

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant:運算子&lt;&lt;,&gt;&gt;

將`COleVariant``CArchive`值輸出到`CdumpContext`或並`COleVariant`從中`CArchive`輸入 物件。

```
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    OleVariant varSrc);

friend CArchive& AFXAPI operator<<(
    CArchive& ar,
    COleVariant varSrc);

friend CArchive& AFXAPI operator>>(
    CArchive& ar,
    COleVariant& varSrc);
```

### <a name="remarks"></a>備註

插入`COleVariant`**\<**( ) 運算子支援診斷轉印並儲存到存檔。 提取**>>**( ) 運算子支援從存檔載入。

## <a name="colevariantsetstring"></a><a name="setstring"></a>COle 變數::設定字串

將字串設定為特定類型。

```cpp
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>參數

*lpszSrc*<br/>
要複製到新`COleVariant`物件的 null 中止字串。

*VtSrc*<br/>
新`COleVariant`物件的 VARTYPE。

### <a name="remarks"></a>備註

參數*vtSrc*必須VT_BSTR (UNICODE) 或VT_BSTRT (ANSI)。 `SetString`通常用於將字串設置為 ANSI,因為[COleVariant::COleVariant](#colevariant)建構函數的預設值帶有字串或字串指標參數,並且沒有 VARTYPE 是 UNICODE。

非 UNICODE 生成中的 DAO 記錄集希望字串為 ANSI。 因此,`COleVariant`對於使用物件的 DAO 函數,如果不創建 UNICODE 記錄集,則必須使用**COleVariant::COleVariant(lpszSrc、vtSrc)***lpszSrc***,***vtSrc***)** 形式的構造函數 *,vtSrc*設置為VT_BSTRT`SetString`(ANSI),或者與設置為 VT_BSTRT的*vtSrc*一起生成 ANSI 字串。 例如,`CDaoRecordset`函數[CDaoRecordset::seek](../../mfc/reference/cdaorecordset-class.md#seek)和[CDaoRecordset:setFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue)`COleVariant`使用物件作為參數。 如果 DAO 記錄集不是 UNICODE,則這些物件必須是 ANSI。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
