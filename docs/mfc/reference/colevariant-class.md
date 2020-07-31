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
ms.openlocfilehash: 63bce4695e4e1142b797f24cfbbae71638177d04
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470897"
---
# <a name="colevariant-class"></a>COleVariant 類別

封裝 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) 資料類型。

## <a name="syntax"></a>語法

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleVariant：： COleVariant](#colevariant)|建構 `COleVariant` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleVariant：： Attach](#attach)|將 VARIANT 附加至 `COleVariant` 。|
|[COleVariant：： ChangeType](#changetype)|變更這個物件的 variant 類型 `COleVariant` 。|
|[COleVariant：： Clear](#clear)|清除這個 `COleVariant` 物件。|
|[COleVariant：:D etach](#detach)|從卸離變數 `COleVariant` ，並傳回 variant。|
|[COleVariant：： GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|從現有的 variant 陣列抓取位元組陣列。|
|[COleVariant：： SetString](#setstring)|將字串設定為特定類型，通常是 ANSI。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[COleVariant：： operator LPCVARIANT](#operator_lpcvariant)|將 `COleVariant` 值轉換成 `LPCVARIANT` 。|
|[COleVariant：： operator LPVARIANT](#operator_lpvariant)|將 `COleVariant` 物件轉換為 `LPVARIANT` 。|
|[COleVariant：： operator =](#operator_eq)|複製 `COleVariant` 值。|
|[COleVariant：： operator = =](#operator_eq_eq)|比較兩個 `COleVariant` 值。|
|[COleVariant：： operator &lt; &lt; 、&gt;&gt;](#operator_lt_lt__gt_gt)|`COleVariant`將值輸出至 `CArchive` 或 `CDumpContext` ，並 `COleVariant` 從輸入物件 `CArchive` 。|

## <a name="remarks"></a>備註

此資料類型用於 OLE automation 中。 具體而言， [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)結構包含 VARIANT 結構陣列的指標。 `DISPPARAMS`結構是用來將參數傳遞給[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

> [!NOTE]
> 這個類別衍生自 `VARIANT` 結構。 這表示您可以 `COleVariant` 在呼叫的參數中傳遞， `VARIANT` 而且結構的資料成員 `VARIANT` 是可存取的資料成員 `COleVariant` 。

[COleCurrency](../../mfc/reference/colecurrency-class.md)和[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)這兩個相關的 MFC 類別會封裝 variant 資料類型 CURRENCY （ `VT_CY` ）和 DATE （ `VT_DATE` ）。 在 `COleVariant` DAO 類別中廣泛使用類別; 如需此類別的一般用法，例如[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)和[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)，請參閱這些類別。

如需詳細資訊，請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy-r1)、 [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)和[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)專案。

如需有關 `COleVariant` 類別及其在 ole automation 中使用之用法的詳細資訊，請參閱[automation](../../mfc/automation.md)一文中的「在 Ole Automation 中傳遞參數」。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COleVariant：： Attach

呼叫此函式可將指定的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)物件附加至目前的 `COleVariant` 物件。

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
`VARIANT`要附加至目前物件的現有物件 `COleVariant` 。

### <a name="remarks"></a>備註

此函式會將*varSrc*的 VARTYPE 設定為 VT_EMPTY。

如需詳細資訊，請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)專案。

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COleVariant：： COleVariant

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
`COleVariant` `VARIANT` 要複製到新物件中的現有或物件 `COleVariant` 。

*.Psrc*<br/>
`VARIANT`將複製到新物件之物件的指標 `COleVariant` 。

*lpszSrc*<br/>
要複製到新物件中的以 null 結束的字串 `COleVariant` 。

*vtSrc*<br/>
`VARTYPE`新 `COleVariant` 物件的。

*strSrc*<br/>
要複製到新物件中的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件 `COleVariant` 。

*nSrc*， *lSrc*要複製到新物件中的數值 `COleVariant` 。

*vtSrc*<br/>
`VARTYPE`新 `COleVariant` 物件的。

*curSrc*<br/>
要複製到新物件中的[COleCurrency](../../mfc/reference/colecurrency-class.md)物件 `COleVariant` 。

*fltSrc*、 *dblSrc*<br/>
要複製到新的 `COleVariant` 物件中的數值。

*timeSrc*<br/>
要複製到新物件中的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件 `COleVariant` 。

*arrSrc*<br/>
要複製到新物件中的[CByteArray](../../mfc/reference/cbytearray-class.md)物件 `COleVariant` 。

*lbSrc*<br/>
要複製到新物件中的[CLongBinary](../../mfc/reference/clongbinary-class.md)物件 `COleVariant` 。

*pidl*<br/>
要複製到新物件中之[ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist)結構的指標 `COleVariant` 。

### <a name="remarks"></a>備註

所有這些函式都會建立新 `COleVariant` 的物件，並初始化為指定的值。 以下是每個這些函式的簡短描述。

- **COleVariant （）** 建立空的 `COleVariant` 物件，VT_EMPTY。

- **COleVariant （** *varSrc* **）** 複製現有 `VARIANT` 的或 `COleVariant` 物件。 variant 類型會保留。

- **COleVariant （** *.psrc* **）** 複製現有 `VARIANT` 的或 `COleVariant` 物件。 variant 類型會保留。

- **COleVariant （** *lpszSrc* **）** 將字串複製到新的物件中，VT_BSTR （UNICODE）。

- **COleVariant （** *lpszSrc* **，** *vtSrc* **）** 將字串複製到新的物件中。 參數*vtSrc*必須是 VT_BSTR （UNICODE）或 VT_BSTRT （ANSI）。

- **COleVariant （** *strSrc* **）** 將字串複製到新的物件中，VT_BSTR （UNICODE）。

- **COleVariant （** *nSrc* **）** 將8位整數複製到新的物件中，VT_UI1。

- **COleVariant （** *nSrc* **，** *vtSrc* **）** 將16位整數（或布林值）複製到新的物件。 參數*vtSrc*必須 VT_I2 或 VT_BOOL。

- **COleVariant （** *lSrc* **，** *vtSrc* **）** 將32位整數（或 SCODE 值）複製到新的物件中。 參數*vtSrc*必須 VT_I4、VT_ERROR 或 VT_BOOL。

- **COleVariant （** *curSrc* **）** 將 `COleCurrency` 值複製到新的物件，VT_CY。

- **COleVariant （** *fltSrc* **）** 將32位浮點值複製到新的物件，VT_R4。

- **COleVariant （** *dblSrc* **）** 將64位浮點值複製到新的物件，VT_R8。

- **COleVariant （** *timeSrc* **）** 將 `COleDateTime` 值複製到新的物件，VT_DATE。

- **COleVariant （** *arrSrc* **）** 將 `CByteArray` 物件複製到新的物件，VT_EMPTY。

- **COleVariant （** *lbSrc* **）** 將 `CLongBinary` 物件複製到新的物件，VT_EMPTY。

如需 SCODE 的詳細資訊，請參閱 Windows SDK 中[COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes)。

## <a name="colevariantchangetype"></a><a name="changetype"></a>COleVariant：： ChangeType

轉換此物件中 variant 值的類型 `COleVariant` 。

```cpp
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>參數

*vartype*<br/>
這個物件的 VARTYPE `COleVariant` 。

*.Psrc*<br/>
要轉換之[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)物件的指標。 如果此值為 Null，則 `COleVariant` 會使用這個物件做為轉換的來源。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype)專案。

## <a name="colevariantclear"></a><a name="clear"></a>COleVariant：： Clear

清除 `VARIANT`。

```cpp
void Clear();
```

### <a name="remarks"></a>備註

這會將此物件的 VARTYPE 設定為 VT_EMPTY。 `COleVariant`此析構函數會呼叫這個函式。

如需詳細資訊，請參閱 `VARIANT` Windows SDK 中的、VARTYPE 和 `VariantClear` 專案。

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant：:D etach

從這個物件卸離基礎[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)物件 `COleVariant` 。

```
VARIANT Detach();
```

### <a name="remarks"></a>備註

此函式會將此物件的 VARTYPE 設定 `COleVariant` 為 VT_EMPTY。

> [!NOTE]
> 呼叫之後，呼叫端必須 `Detach` 負責 `VariantClear` 在產生的結構上呼叫 `VARIANT` 。

如需詳細資訊，請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)、 [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)和[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)專案。

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COleVariant：： GetByteArrayFromVariantArray

從現有的 variant 陣列抓取位元組陣列

```cpp
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>參數

*#a0*<br/>
現有[CByteArray](../../mfc/reference/cbytearray-class.md)物件的參考。

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleVariant：： operator LPCVARIANT

這個轉型運算子 `VARIANT` 會傳回從這個物件複製其值的結構 `COleVariant` 。

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>備註

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleVariant：： operator LPVARIANT

呼叫這個轉型運算子來存取 `VARIANT` 這個物件的基礎結構 `COleVariant` 。

```
operator LPVARIANT();
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 變更此函式 `VARIANT` 所傳回之指標所存取的結構中的值，將會變更這個 `COleVariant` 物件的值。

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant：： operator =

這些多載指派運算子會將來源值複製到這個 `COleVariant` 物件。

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

每個運算子的簡短說明如下：

- **operator = （** *varSrc* **）** 將現有的 VARIANT 或 `COleVariant` 物件複製到這個物件。

- **operator = （** *.psrc* **）** 將 *.psrc*所存取的 VARIANT 物件複製到這個物件。

- **operator = （** *lpszSrc* **）** 將以 null 結束的字串複製到這個物件，並將 VARTYPE 設定為 VT_BSTR。

- **operator = （** *strSrc* **）** 將[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件複製到這個物件，並將 VARTYPE 設定為 VT_BSTR。

- **operator = （** *nSrc* **）** 將8或16位整數值複製到這個物件。 如果*nSrc*是8位的值，則會將這個的 VARTYPE 設定為 VT_UI1。 如果*nSrc*是16位值，而這個的 VARTYPE 是 VT_BOOL，則會保留;否則，它會設定為 VT_I2。

- **operator = （** *lSrc* **）** 將32位整數值複製到這個物件。 如果這是 VT_ERROR 的 VARTYPE，則會保留;否則，它會設定為 VT_I4。

- **operator = （** *curSrc* **）** 將[COleCurrency](../../mfc/reference/colecurrency-class.md)物件複製到這個物件，並將 VARTYPE 設定為 VT_CY。

- **operator = （** *fltSrc* **）** 將32位浮點值複製到這個物件，並將 VARTYPE 設定為 VT_R4。

- **operator = （** *dblSrc* **）** 將64位浮點值複製到這個物件，並將 VARTYPE 設定為 VT_R8。

- **operator = （** *dateSrc* **）** 將[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件複製到這個物件，並將 VARTYPE 設定為 VT_DATE。

- **operator = （** *arrSrc* **）** 將[CByteArray](../../mfc/reference/cbytearray-class.md)物件複製到這個 `COleVariant` 物件。

- **operator = （** *lbSrc* **）** 將[CLongBinary](../../mfc/reference/clongbinary-class.md)物件複製到這個 `COleVariant` 物件。

如需詳細資訊，請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)和[VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)專案。

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COleVariant：： operator = =

這個運算子會比較兩個變體值，如果相等，則傳回非零。否則為0。

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant：： operator &lt; &lt; 、&gt;&gt;

`COleVariant`將值輸出至 `CArchive` 或 `CdumpContext` ，並 `COleVariant` 從輸入物件 `CArchive` 。

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

`COleVariant`插入（ **\<\<**) operator supports diagnostic dumping and storing to an archive. The extraction (**>>** ）運算子支援從封存載入。

## <a name="colevariantsetstring"></a><a name="setstring"></a>COleVariant：： SetString

將字串設定為特定類型。

```cpp
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>參數

*lpszSrc*<br/>
要複製到新物件中的以 null 結束的字串 `COleVariant` 。

*VtSrc*<br/>
新物件的 VARTYPE `COleVariant` 。

### <a name="remarks"></a>備註

參數*vtSrc*必須是 VT_BSTR （UNICODE）或 VT_BSTRT （ANSI）。 `SetString`通常用來將字串設定為 ANSI，因為[COleVariant：： COleVariant](#colevariant)的預設值具有字串或字串指標參數，而且沒有 VARTYPE 為 UNICODE。

非 UNICODE 組建中的 DAO 記錄集會預期字串必須是 ANSI。 因此，對於使用物件的 DAO 函式， `COleVariant` 如果您不是建立 UNICODE 記錄集，則必須使用**COleVariant：： COleVariant （** *lpszSrc* **，** *vtSrc* **）** 形式的函式，並將*vtSrc*設定為 VT_BSTRT （ANSI），或使用 `SetString` with *vtSrc*設定為 VT_BSTRT 來建立 ANSI 字串。 例如， `CDaoRecordset` [CDaoRecordset：： Seek](../../mfc/reference/cdaorecordset-class.md#seek)和[CDaoRecordset：： SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue)函式會使用 `COleVariant` 物件做為參數。 如果 DAO 記錄集不是 UNICODE，則這些物件必須是 ANSI。

## <a name="see-also"></a>請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
