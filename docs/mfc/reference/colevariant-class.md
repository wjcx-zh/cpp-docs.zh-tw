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
ms.openlocfilehash: 0676f4896401ab777570666236c4639ad94c3a05
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503056"
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
|[COleVariant::COleVariant](#colevariant)|建構 `COleVariant` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleVariant::Attach](#attach)|將 VARIANT 附加至`COleVariant`。|
|[COleVariant::ChangeType](#changetype)|變更這個`COleVariant`物件的 variant 類型。|
|[COleVariant::Clear](#clear)|清除這個`COleVariant`物件。|
|[COleVariant::Detach](#detach)|從卸離變數`COleVariant` , 並傳回 variant。|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|從現有的 variant 陣列抓取位元組陣列。|
|[COleVariant::SetString](#setstring)|將字串設定為特定類型, 通常是 ANSI。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleVariant:: operator LPCVARIANT](#operator_lpcvariant)|將值轉換成`LPCVARIANT`。 `COleVariant`|
|[COleVariant:: operator LPVARIANT](#operator_lpvariant)|將物件轉換為`LPVARIANT`。 `COleVariant`|
|[COleVariant:: operator =](#operator_eq)|`COleVariant`複製值。|
|[COleVariant:: operator = =](#operator_eq_eq)|比較兩`COleVariant`個值。|
|[COleVariant:: operator &lt;、 &lt;&gt;&gt;](#operator_lt_lt__gt_gt)|`CArchive` `CDumpContext`將值輸出至或, 並從`COleVariant` `CArchive`輸入物件。 `COleVariant`|

## <a name="remarks"></a>備註

此資料類型用於 OLE automation 中。 具體而言, [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-tagdispparams)結構包含 VARIANT 結構陣列的指標。 結構是用來將參數傳遞給[IDispatch:: Invoke。](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) `DISPPARAMS`

> [!NOTE]
> 這個類別衍生自`VARIANT`結構。 這`COleVariant`表示您可以在呼叫`VARIANT`的參數中傳遞, 而且`VARIANT`結構的資料成員是可存取的資料成員`COleVariant`。

[COleCurrency](../../mfc/reference/colecurrency-class.md)和[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)這兩個相關的 MFC 類別會封裝 variant 資料類型`VT_CY`CURRENCY () 和`VT_DATE`DATE ()。 在 DAO 類別中廣泛使用類別;如需此類別的一般用法,例如 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 和 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)，請參閱這些`COleVariant`類別。

如需詳細資訊, 請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy)、 [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-tagdispparams)和[IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)專案。

如需有關`COleVariant`類別及其在 ole automation 中使用之用法的詳細資訊, 請參閱[automation](../../mfc/automation.md)一文中的「在 ole automation 中傳遞參數」。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="attach"></a>COleVariant:: Attach

呼叫此函式可將指定的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)物件附加至`COleVariant`目前的物件。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
要附加`VARIANT`至目前`COleVariant`物件的現有物件。

### <a name="remarks"></a>備註

此函式會將*varSrc*的 VARTYPE 設定為 VT_EMPTY。

如需詳細資訊, 請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)專案。

##  <a name="colevariant"></a>COleVariant:: COleVariant

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
要複製`COleVariant`到`VARIANT` 新`COleVariant`物件中的現有或物件。

*pSrc*<br/>
將複製到新`VARIANT` `COleVariant`物件之物件的指標。

*lpszSrc*<br/>
要複製到新`COleVariant`物件中的以 null 結束的字串。

*vtSrc*<br/>
`VARTYPE` 新`COleVariant`物件的。

*strSrc*<br/>
要複製到新`COleVariant`物件中的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 物件。

*nSrc*, *lSrc*要複製到新`COleVariant`物件中的數值。

*vtSrc*<br/>
`VARTYPE` 新`COleVariant`物件的。

*curSrc*<br/>
要複製到新`COleVariant`物件中的 [COleCurrency](../../mfc/reference/colecurrency-class.md) 物件。

*fltSrc*、 *dblSrc*<br/>
要複製到新的 `COleVariant` 物件中的數值。

*timeSrc*<br/>
要複製到新`COleVariant`物件中的 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 物件。

*arrSrc*<br/>
要複製到新`COleVariant`物件中的 [CByteArray](../../mfc/reference/cbytearray-class.md) 物件。

*lbSrc*<br/>
要複製到新`COleVariant`物件中的 [CLongBinary](../../mfc/reference/clongbinary-class.md) 物件。

*pidl*<br/>
要複製到新 `COleVariant`物件中之 [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) 結構的指標。

### <a name="remarks"></a>備註

所有這些函式都會`COleVariant`建立新的物件, 並初始化為指定的值。 以下是每個這些函式的簡短描述。

- **COleVariant ()** 建立空`COleVariant`的物件 VT_EMPTY。

- **COleVariant (** *varSrc* **)** 複製現有`VARIANT`的或`COleVariant`物件。 variant 類型會保留。

- **COleVariant (** *.psrc* **)** 複製現有`VARIANT`的或`COleVariant`物件。 variant 類型會保留。

- **COleVariant (** *lpszSrc* **)** 將字串複製到新的物件 VT_BSTR (UNICODE)。

- **COleVariant (** *lpszSrc* **,** *vtSrc* **)** 將字串複製到新的物件中。 參數*vtSrc*必須是 VT_BSTR (UNICODE) 或 VT_BSTRT (ANSI)。

- **COleVariant (** *strSrc* **)** 將字串複製到新的物件 VT_BSTR (UNICODE)。

- **COleVariant (** *nSrc* **)** 將8位整數複製到新的物件 VT_UI1。

- **COleVariant (** *nSrc* **,** *vtSrc* **)** 將16位整數 (或布林值) 複製到新的物件。 參數*vtSrc*必須是 VT_I2 或 VT_BOOL。

- **COleVariant (** *lSrc* **,** *vtSrc* **)** 將32位整數 (或 SCODE 值) 複製到新的物件中。 參數*vtSrc*必須是 VT_I4、VT_ERROR 或 VT_BOOL。

- **COleVariant (** *curSrc* **)** `COleCurrency`將值複製到新的物件 VT_CY。

- **COleVariant (** *fltSrc* **)** 將32位浮點值複製到新的物件 VT_R4。

- **COleVariant (** *dblSrc* **)** 將64位浮點值複製到新的物件 VT_R8。

- **COleVariant (** *timeSrc* **)** `COleDateTime`將值複製到新的物件 VT_DATE。

- **COleVariant (** *arrSrc* **)** `CByteArray`將物件複製到新的物件 VT_EMPTY。

- **COleVariant (** *lbSrc* **)** `CLongBinary`將物件複製到新的物件 VT_EMPTY。

如需 SCODE 的詳細資訊, 請參閱 Windows SDK 中[COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes)。

##  <a name="changetype"></a>COleVariant:: ChangeType

轉換此`COleVariant`物件中 variant 值的類型。

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>參數

*vartype*<br/>
這個`COleVariant`物件的 VARTYPE。

*pSrc*<br/>
要轉換之[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)物件的指標。 如果此值為 Null, 則`COleVariant`會使用這個物件做為轉換的來源。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype)專案。

##  <a name="clear"></a>COleVariant:: Clear

`VARIANT`清除。

```
void Clear();
```

### <a name="remarks"></a>備註

這會將此物件的 VARTYPE 設定為 VT_EMPTY。 此`COleVariant`析構函數會呼叫這個函式。

如需詳細資訊, 請`VARIANT`參閱 Windows SDK 中的`VariantClear` 、VARTYPE 和專案。

##  <a name="detach"></a>COleVariant::D etach

從這個`COleVariant`物件卸離基礎[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)物件。

```
VARIANT Detach();
```

### <a name="remarks"></a>備註

此函式會將此`COleVariant`物件的 VARTYPE 設定為 VT_EMPTY。

> [!NOTE]
>  呼叫之後`VariantClear` `VARIANT` , 呼叫端必須負責在產生的結構上呼叫。 `Detach`

如需詳細資訊, 請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)專案。

##  <a name="getbytearrayfromvariantarray"></a>COleVariant:: GetByteArrayFromVariantArray

從現有的 variant 陣列抓取位元組陣列

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>參數

*#a0*<br/>
現有[CByteArray](../../mfc/reference/cbytearray-class.md)物件的參考。

##  <a name="operator_lpcvariant"></a>COleVariant:: operator LPCVARIANT

這個轉型運算子會`VARIANT`傳回從這個`COleVariant`物件複製其值的結構。

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>備註

##  <a name="operator_lpvariant"></a>COleVariant:: operator LPVARIANT

呼叫這個轉型運算子來存取這個`VARIANT` `COleVariant`物件的基礎結構。

```
operator LPVARIANT();
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 變更此函式所`VARIANT`傳回之指標所存取的結構中的值, 將會變更這個`COleVariant`物件的值。

##  <a name="operator_eq"></a>COleVariant:: operator =

這些多載指派運算子會將來源值複製`COleVariant`到這個物件。

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

每個運算子的簡短說明如下:

- **operator = (** *varSrc* **)** 將現有的 VARIANT 或`COleVariant`物件複製到這個物件。

- **operator = (** *.psrc* **)** 將 *.psrc*所存取的 VARIANT 物件複製到這個物件。

- **operator = (** *lpszSrc* **)** 將以 null 結束的字串複製到這個物件, 並將 VARTYPE 設定為 VT_BSTR。

- **operator = (** *strSrc* **)** 將[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件複製到這個物件, 並將 VARTYPE 設定為 VT_BSTR。

- **operator = (** *nSrc* **)** 將8或16位整數值複製到這個物件。 如果*nSrc*是8位值, 則這個的 VARTYPE 會設定為 VT_UI1。 如果*nSrc*是16位值, 而這個的 VARTYPE 是 VT_BOOL, 則會保留;否則, 它會設定為 VT_I2。

- **operator = (** *lSrc* **)** 將32位整數值複製到這個物件。 如果這個的 VARTYPE 是 VT_ERROR, 則會保留;否則, 它會設定為 VT_I4。

- **operator = (** *curSrc* **)** 將[COleCurrency](../../mfc/reference/colecurrency-class.md)物件複製到這個物件, 並將 VARTYPE 設定為 VT_CY。

- **operator = (** *fltSrc* **)** 將32位浮點值複製到這個物件, 並將 VARTYPE 設定為 VT_R4。

- **operator = (** *dblSrc* **)** 將64位浮點值複製到這個物件, 並將 VARTYPE 設定為 VT_R8。

- **operator = (** *dateSrc* **)** 將[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件複製到這個物件, 並將 VARTYPE 設定為 VT_DATE。

- **operator = (** *arrSrc* **)** 將[CByteArray](../../mfc/reference/cbytearray-class.md)物件複製到這個`COleVariant`物件。

- **operator = (** *lbSrc* **)** 將[CLongBinary](../../mfc/reference/clongbinary-class.md)物件複製到這個`COleVariant`物件。

如需詳細資訊, 請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)專案。

##  <a name="operator_eq_eq"></a>COleVariant:: operator = =

這個運算子會比較兩個變體值, 如果相等, 則傳回非零。否則為0。

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>COleVariant:: operator &lt;、 &lt;&gt;&gt;

`CArchive` `CdumpContext`將值輸出至或, 並從`COleVariant` `CArchive`輸入物件。 `COleVariant`

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

`COleVariant`插入 **()運算子\<支援將診斷傾印並儲存至封存。\<** 「抽取」 **>>** () 運算子支援從封存載入。

##  <a name="setstring"></a>  COleVariant::SetString

將字串設定為特定類型。

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>參數

*lpszSrc*<br/>
要複製到新`COleVariant`物件中的以 null 結束的字串。

*VtSrc*<br/>
新`COleVariant`物件的 VARTYPE。

### <a name="remarks"></a>備註

參數*vtSrc*必須是 VT_BSTR (UNICODE) 或 VT_BSTRT (ANSI)。 `SetString`通常用來將字串設定為 ANSI, 因為[COleVariant:: COleVariant](#colevariant)的預設值具有字串或字串指標參數, 而且沒有 VARTYPE 為 UNICODE。

非 UNICODE 組建中的 DAO 記錄集會預期字串必須是 ANSI。 因此，適用於 DAO 函式使用`COleVariant`物件，如果您不想要建立的 UNICODE 資料錄集，您必須使用 **COleVariant::COleVariant (** *lpszSrc* **，** *vtSrc* **)** 形式的建構函式*vtSrc*設定至 VT_BSTRT (ANSI)，或使用`SetString`具有*vtSrc*設 VT將 ANSI 字串 _BSTRT。 `CDaoRecordset`例如, [CDaoRecordset:: Seek](../../mfc/reference/cdaorecordset-class.md#seek)和[CDaoRecordset:: SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue)函式會使用`COleVariant`物件做為參數。 如果 DAO 記錄集不是 UNICODE, 則這些物件必須是 ANSI。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
