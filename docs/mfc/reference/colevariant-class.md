---
title: COleVariant 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 825e534f7cf75f693293931b20e8b982e4bbc6a8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220251"
---
# <a name="colevariant-class"></a>COleVariant 類別
封裝[VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)資料型別。

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
|[COleVariant::Attach](#attach)|將 VARIANT 以`COleVariant`。|
|[COleVariant::ChangeType](#changetype)|變更的 variant 類型`COleVariant`物件。|
|[COleVariant::Clear](#clear)|清除這個`COleVariant`物件。|
|[COleVariant::Detach](#detach)|卸離的 VARIANT 從`COleVariant`，並傳回 VARIANT。|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|從現有的變數陣列中擷取的位元組陣列。|
|[COleVariant::SetString](#setstring)|設定特定的型別，通常為 ANSI 字串。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|將轉換`COleVariant`值貼`LPCVARIANT`。|
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|將轉換`COleVariant`物件插入`LPVARIANT`。|
|[COleVariant::operator =](#operator_eq)|複製`COleVariant`值。|
|[COleVariant::operator = =](#operator_eq_eq)|比較兩個`COleVariant`值。|
|[COleVariant::operator &lt; &lt;， &gt;&gt;](#operator_lt_lt__gt_gt)|輸出`COleVariant`值`CArchive`或是`CDumpContext`並輸入`COleVariant`物件`CArchive`。|

## <a name="remarks"></a>備註

此資料型別使用 OLE automation 中。 具體而言， [DISPPARAMS](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagdispparams)結構包含的 VARIANT 結構陣列的指標。 A`DISPPARAMS`結構用來將參數傳遞給[idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)。

> [!NOTE]
> 此類別衍生自`VARIANT`結構。 這表示您可以傳遞`COleVariant`中的參數，呼叫`VARIANT`且的資料成員`VARIANT`結構是否可存取資料成員`COleVariant`。

兩個相關的 MFC 類別[COleCurrency](../../mfc/reference/colecurrency-class.md)並[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)封裝 variant 資料型別貨幣 ( `VT_CY`) 和日期 ( `VT_DATE`)。 `COleVariant`類別在 DAO 類別中廣泛使用，請參閱一般的使用情況的這個類別，這些類別時，例如[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)並[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

如需詳細資訊，請參閱 < [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)，[貨幣](/windows/desktop/api/wtypes/ns-wtypes-tagcy)， [DISPPARAMS](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagdispparams)，以及[idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) Windows SDK 中的項目。

如需詳細資訊`COleVariant`類別和它的用法，在 OLE 自動化中，請參閱 「 傳遞參數中 OLE 自動化 」 一文中[自動化](../../mfc/automation.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="attach"></a>  COleVariant::Attach

呼叫此函式，將給定[VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)物件與目前`COleVariant`物件。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
將現有`VARIANT`附加至目前的物件`COleVariant`物件。

### <a name="remarks"></a>備註

此函式設定的 VARTYPE *varSrc*設為 VT_EMPTY。

如需詳細資訊，請參閱 < [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)並[VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum) Windows SDK 中的項目。

##  <a name="colevariant"></a>  COleVariant::COleVariant

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
將現有`COleVariant`或是`VARIANT`複製到新的物件`COleVariant`物件。

*pSrc*<br/>
指標`VARIANT`將會複製到新的物件`COleVariant`物件。

*lpszSrc*<br/>
以 null 結束的字串，要複製到新`COleVariant`物件。

*vtSrc*<br/>
`VARTYPE`新`COleVariant`物件。

*strSrc*<br/>
A [CString](../../atl-mfc-shared/reference/cstringt-class.md)複製到新的物件`COleVariant`物件。

*nSrc*， *lSrc*複製到新的數值`COleVariant`物件。

*vtSrc*<br/>
`VARTYPE`新`COleVariant`物件。

*curSrc*<br/>
A [COleCurrency](../../mfc/reference/colecurrency-class.md)複製到新的物件`COleVariant`物件。

*fltSrc*， *dblSrc*<br/>
要複製到新的 `COleVariant` 物件中的數值。

*timeSrc*<br/>
A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)複製到新的物件`COleVariant`物件。

*arrSrc*<br/>
A [CByteArray](../../mfc/reference/cbytearray-class.md)複製到新的物件`COleVariant`物件。

*lbSrc*<br/>
A [CLongBinary](../../mfc/reference/clongbinary-class.md)複製到新的物件`COleVariant`物件。

*pidl*<br/>
指標[ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-_itemidlist)複製到新的結構`COleVariant`物件。

### <a name="remarks"></a>備註

所有這些建構函式建立新`COleVariant`物件初始化為指定的值。 遵循每個這些建構函式的簡短描述。

- **COleVariant （)** 建立空白`COleVariant`物件，為 VT_EMPTY。

- **COleVariant (** *varSrc* **)** 複製現有`VARIANT`或`COleVariant`物件。 variant 類型會保留。

- **COleVariant (** *pSrc* **)** 複製現有`VARIANT`或`COleVariant`物件。 variant 類型會保留。

- **COleVariant (** *lpszSrc* **)** 將字串複製到新物件，也就是 VT_BSTR (UNICODE)。

- **COleVariant (** *lpszSrc* **，** *vtSrc* **)** 將字串複製到新的物件。 參數*vtSrc*必須 VT_BSTR (UNICODE) 或 VT_BSTRT (ANSI)。

- **COleVariant (** *strSrc* **)** 將字串複製到新物件，也就是 VT_BSTR (UNICODE)。

- **COleVariant (** *nSrc* **)** 複製到新的物件，VT_UI1 的 8 位元整數。

- **COleVariant (** *nSrc* **，** *vtSrc* **)** 將 16 位元整數 （或布林值） 複製到新的物件。 參數*vtSrc*必須 VT_I2 或 VT_BOOL。

- **COleVariant (** *lSrc* **，** *vtSrc* **)** 將 32 位元整數 （或 SCODE 值） 複製到新的物件。 參數*vtSrc*必須 VT_I4、 VT_ERROR 或 VT_BOOL。

- **COleVariant (** *curSrc* **)** 複本`COleCurrency`成新的物件，VT_CY 的值。

- **COleVariant (** *fltSrc* **)** 將 32 位元浮點值複製到新的物件，VT_R4。

- **COleVariant (** *dblSrc* **)** 將 64 位元浮點值複製到新的物件，VT_R8。

- **COleVariant (** *timeSrc* **)** 複本`COleDateTime`成新的物件，VT_DATE 值。

- **COleVariant (** *arrSrc* **)** 複本`CByteArray`物件插入新的物件，為 VT_EMPTY。

- **COleVariant (** *lbSrc* **)** 複本`CLongBinary`物件插入新的物件，為 VT_EMPTY。

如需有關 SCODE 的詳細資訊，請參閱[錯誤碼的結構 COM](/windows/desktop/com/structure-of-com-error-codes) Windows SDK 中。

##  <a name="changetype"></a>  COleVariant::ChangeType

將 variant 的值，在這種`COleVariant`物件。

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>參數

*vartype*<br/>
這個 VARTYPE`COleVariant`物件。

*pSrc*<br/>
指標[VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)来轉換的物件。 如果這個值是 NULL，這`COleVariant`物件做為來源用來進行轉換。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)， [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum)，並[VariantChangeType](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantchangetype) Windows SDK 中的項目。

##  <a name="clear"></a>  COleVariant::Clear

清除`VARIANT`。

```
void Clear();
```

### <a name="remarks"></a>備註

這會設定這個物件 VARTYPE 設為 VT_EMPTY。 `COleVariant`解構函式呼叫此函式。

如需詳細資訊，請參閱 < `VARIANT`，VARTYPE，和`VariantClear`Windows SDK 中的項目。

##  <a name="detach"></a>  COleVariant::Detach

卸離的基礎[VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)物件，這個`COleVariant`物件。

```
VARIANT Detach();
```

### <a name="remarks"></a>備註

此函式設定這個 VARTYPE`COleVariant`物件設為 VT_EMPTY。

> [!NOTE]
>  之後呼叫`Detach`，呼叫的呼叫者必須負責`VariantClear`上產生`VARIANT`結構。

如需詳細資訊，請參閱 < [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)， [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum)，並[VariantClear](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantclear) Windows SDK 中的項目。

##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray

從現有的變數陣列中擷取的位元組陣列

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>參數

*位元組*<br/>
若要將現有的參考[CByteArray](../../mfc/reference/cbytearray-class.md)物件。

##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT

這個轉型運算子會傳回`VARIANT`結構，其值會複製從此`COleVariant`物件。

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>備註

##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT

呼叫此轉型運算子，來存取基礎`VARIANT`這個結構`COleVariant`物件。

```
operator LPVARIANT();
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 變更中的值`VARIANT`存取此函式所傳回的指標，結構會變更這個值`COleVariant`物件。

##  <a name="operator_eq"></a>  COleVariant::operator =

這些多載的指派運算子會將來源值複製到這個`COleVariant`物件。

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

每個運算子的簡短描述如下：

- **運算子 = (** *varSrc* **)** 複製現有的變數或`COleVariant`成為這個物件的物件。

- **運算子 = (** *pSrc* **)** 複製存取的 VARIANT 物件*pSrc*到這個物件。

- **運算子 = (** *lpszSrc* **)** 將以 null 結束的字串複製到這個物件，並將 VARTYPE 設定為 VT_BSTR。

- **運算子 = (** *strSrc* **)** 複本[CString](../../atl-mfc-shared/reference/cstringt-class.md)成為這個物件以及設定為 VT_BSTR VARTYPE 物件。

- **運算子 = (** *nSrc* **)** 將 8 位元或 16 位元整數值複製到這個物件。 如果*nSrc*是 8 位元值，這個 VARTYPE 設 VT_UI1。 如果*nSrc*是 16 位元值，這個 VARTYPE 為 VT_BOOL，它是已保留，否則為，設為 VT_I2。

- **運算子 = (** *lSrc* **)** 將 32 位元整數值複製到這個物件。 如果這個 VARTYPE VT_ERROR，會將它保持;否則，它設為 VT_I4。

- **運算子 = (** *curSrc* **)** 複本[COleCurrency](../../mfc/reference/colecurrency-class.md)成為這個物件以及設定至 VT_CY VARTYPE 物件。

- **運算子 = (** *fltSrc* **)** 將 32 位元浮點值複製到這個物件，並將 VARTYPE 設為 VT_R4。

- **運算子 = (** *dblSrc* **)** 將 64 位元浮點值複製到這個物件，並將 VARTYPE 設為 VT_R8。

- **運算子 = (** *dateSrc* **)** 複本[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)成為這個物件以及設定至 VT_DATE VARTYPE 物件。

- **運算子 = (** *arrSrc* **)** 複本[CByteArray](../../mfc/reference/cbytearray-class.md)到這個物件`COleVariant`物件。

- **運算子 = (** *lbSrc* **)** 複本[CLongBinary](../../mfc/reference/clongbinary-class.md)到這個物件`COleVariant`物件。

如需詳細資訊，請參閱 < [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)並[VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum) Windows SDK 中的項目。

##  <a name="operator_eq_eq"></a>  COleVariant::operator = =

此運算子比較兩個變數的值，並傳回非零值，兩者是否相等;否則為 0。

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;， &gt;&gt;

輸出`COleVariant`值`CArchive`或是`CdumpContext`並輸入`COleVariant`物件`CArchive`。

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

`COleVariant`插入 (**\<\<**) 運算子支援診斷傾印，並儲存至封存。 擷取 (**>>**) 運算子可支援從封存的載入。

##  <a name="setstring"></a>  COleVariant::SetString

設定特定類型的字串。

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>參數

*lpszSrc*<br/>
以 null 結束的字串，要複製到新`COleVariant`物件。

*vtSrc*<br/>
新的 VARTYPE`COleVariant`物件。

### <a name="remarks"></a>備註

參數*vtSrc*必須 VT_BSTR (UNICODE) 或 VT_BSTRT (ANSI)。 `SetString` 通常用來為 ANSI，設定字串，因為預設值[COleVariant::COleVariant](#colevariant)建構函式的字串或字串指標參數，並沒有 VARTYPE 為 UNICODE。

DAO 資料錄集的非 UNICODE 組建中預期為 ANSI 字串。 因此，適用於 DAO 函式使用`COleVariant`物件，如果您不想要建立的 UNICODE 資料錄集，您必須使用**COleVariant::COleVariant (** *lpszSrc* **，***vtSrc* **)** 形式的建構函式*vtSrc*設定至 VT_BSTRT (ANSI)，或使用`SetString`具有*vtSrc*設 VT將 ANSI 字串 _BSTRT。 例如，`CDaoRecordset`函式[CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek)並[CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue)使用`COleVariant`物件做為參數。 如果 DAO 資料錄集不是 UNICODE，這些物件必須是 ANSI。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
