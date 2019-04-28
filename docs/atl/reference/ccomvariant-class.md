---
title: CComVariant 類別
ms.date: 11/04/2016
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
ms.openlocfilehash: 6be05b52b96ada7871f955c687036a83b4e0b493
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259049"
---
# <a name="ccomvariant-class"></a>CComVariant 類別

這個類別會包裝 VARIANT 型別，提供成員，表示儲存的資料類型。

## <a name="syntax"></a>語法

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|建構函式。|
|[CComVariant::~CComVariant](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComVariant::Attach](#attach)|將 VARIANT 以`CComVariant`物件。|
|[CComVariant::ChangeType](#changetype)|將轉換`CComVariant`新類型的物件。|
|[CComVariant::Clear](#clear)|清除`CComVariant`物件。|
|[CComVariant::Copy](#copy)|將複製到 VARIANT`CComVariant`物件。|
|[CComVariant::CopyTo](#copyto)|內容複製`CComVariant`物件。|
|[CComVariant::Detach](#detach)|卸離基礎 VARIANT 從`CComVariant`物件。|
|[CComVariant::GetSize](#getsize)|傳回內容的位元組數的大小`CComVariant`物件。|
|[CComVariant::ReadFromStream](#readfromstream)|從資料流載入變體。|
|[CComVariant::SetByRef](#setbyref)|初始化`CComVariant`物件以及設定`vt`VT_BYREF 的成員。|
|[CComVariant::WriteToStream](#writetostream)|將資料流中的基礎變體。|

### <a name="public-operators"></a>公用運算子

|||
|-|-|
|[CComVariant::operator <](#operator_lt)|指出是否`CComVariant`物件是否小於指定的變數。|
|[CComVariant::operator >](#operator_gt)|指出是否`CComVariant`物件是否大於指定的變數。|
|[operator !=](#operator_neq)|指出是否`CComVariant`物件不等於指定的變數。|
|[operator =](#operator_eq)|將值指派給`CComVariant`物件。|
|[operator ==](#operator_eq_eq)|指出是否`CComVariant`的物件等於指定的變數。|

## <a name="remarks"></a>備註

`CComVariant` 包裝 VARIANT 與 VARIANTARG 類型，其中包含聯集和成員，表示等位中儲存的資料類型。 變數通常用於自動化。

`CComVariant` 自 VARIANT 型別，因此它可用於可使用的變數。 例如，您可以使用 V_VT 巨集擷取的型別`CComVariant`或者您也可以存取`vt`直接一樣您可以使用變數的成員。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>需求

**標頭：** atlcomcli.h

##  <a name="attach"></a>  CComVariant::Attach

安全地清除目前的內容`CComVariant`物件，請將複製的內容*pSrc*成此物件，然後設定的 variant 類型*pSrc*設為 VT_EMPTY。

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>參數

*pSrc*<br/>
[in]指向[VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)附加至物件。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

所儲存的資料的擁有權*pSrc*轉移到`CComVariant`物件。

##  <a name="ccomvariant"></a>  CComVariant::CComVariant

每個建構函式會處理安全初始化`CComVariant`藉由呼叫物件`VariantInit`Win32 函數或藉由設定物件的值和根據傳遞的參數類型。

```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
[in]`CComVariant`或用來初始化的 VARIANT`CComVariant`物件。 來源 variant 的內容複製到目的地，而無需轉換。

*lpszSrc*<br/>
[in]字元字串用來初始化`CComVariant`物件。 您可以傳遞零結束寬 (Unicode) 字元字串的建構函式或 ANSI 字串 LPCSTR 版本 LPCOLESTR 版本。 在任一情況下，此字串會轉換成 BSTR 配置使用 Unicode `SysAllocString`。 型別`CComVariant`物件都會是 VT_BSTR。

*bSrc*<br/>
[in]**Bool**用來初始化`CComVariant`物件。 **Bool**引數時，會轉換成 VARIANT_BOOL 上，然後再儲存。 型別`CComVariant`物件都會是 VT_BOOL。

*nSrc*<br/>
[in]**Int**，**位元組**，**簡短**，**長**，LONGLONG、 ULONGLONG， **unsigned short**， **unsigned long**，或**不帶正負號的 int**用來初始化`CComVariant`物件。 型別`CComVariant`物件將會是 VT_I4、 VT_UI1、 VT_I2、 VT_I4、 VT_I8、 VT_UI8、 VT_UI2、 VT_UI4 或 VT_UI4，分別。

*vtSrc*<br/>
[in]Variant 類型。 當第一個參數是**int**，有效的類型為 VT_I4 和 VT_INT。 當第一個參數是**長**，有效的類型為 VT_I4 和 VT_ERROR。 當第一個參數是**double**，有效的類型為 VT_R8 和 VT_DATE。 當第一個參數是**不帶正負號的 int**，有效的類型為 VT_UI4 和 VT_UINT。

*fltSrc*<br/>
[in]**浮點數**用來初始化`CComVariant`物件。 型別`CComVariant`物件都會是 VT_R4。

*dblSrc*<br/>
[in]**雙**用來初始化`CComVariant`物件。 型別`CComVariant`物件都會是 VT_R8。

*cySrc*<br/>
[in]`CY`用來初始化`CComVariant`物件。 型別`CComVariant`物件都會是 VT_CY。

*pSrc*<br/>
[in]`IDispatch`或是`IUnknown`指標，用來初始化`CComVariant`物件。 `AddRef` 將介面指標上呼叫。 型別`CComVariant`物件都會是 VT_DISPATCH 或 VT_UNKNOWN，分別。

或者，用來初始化 SAFERRAY 指標`CComVariant`物件。 SAFEARRAY 的複本儲存在`CComVariant`物件。 型別`CComVariant`物件將會原始的型別，以及與的 SAFEARRAY VT_ARRAY 組合。

*cSrc*<br/>
[in]**Char**用來初始化`CComVariant`物件。 型別`CComVariant`物件都會是 VT_I1。

*bstrSrc*<br/>
[in]BSTR 用來初始化`CComVariant`物件。 型別`CComVariant`物件都會是 VT_BSTR。

### <a name="remarks"></a>備註

解構函式會藉由呼叫管理清除[CComVariant::Clear](#clear)。

##  <a name="dtor"></a>  CComVariant:: ~ CComVariant

解構函式。

```
~CComVariant() throw();
```

### <a name="remarks"></a>備註

這個方法會藉由呼叫管理清除[CComVariant::Clear](#clear)。

##  <a name="changetype"></a>  CComVariant::ChangeType

將轉換`CComVariant`新類型的物件。

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>參數

*vtNew*<br/>
[in]新類型`CComVariant`物件。

*pSrc*<br/>
[in]其值會轉換成新類型的 variant 的指標。 預設值是 NULL，意義`CComVariant`物件會就地轉換。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果您將值傳給*pSrc*，`ChangeType`做為來源將使用的這個變體來進行轉換。 否則，`CComVariant`物件都會是來源。

##  <a name="clear"></a>  CComVariant::Clear

清除`CComVariant`藉由呼叫物件`VariantClear`Win32 函式。

```
HRESULT Clear();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

解構函式會自動呼叫`Clear`。

##  <a name="copy"></a>  CComVariant::Copy

釋放`CComVariant`物件，然後將它指派一份指定的變數。

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>參數

*pSrc*<br/>
[in]指標[VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)複製。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="copyto"></a>  CComVariant::CopyTo

內容複製`CComVariant`物件。

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>參數

*pstrDest*<br/>
BSTR，其中將會收到一份內容會指向`CComVariant`物件。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`CComVariant` Vt_bstr 類型必須是物件。

##  <a name="detach"></a>  CComVariant::Detach

卸離基礎 VARIANT 從`CComVariant`物件，並將物件的類型設為 VT_EMPTY。

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>參數

*pDest*<br/>
[out]傳回物件的基礎變數值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

請注意，所參考的 VARIANT 的內容*pDest*之前所指派的值和類型的呼叫將會自動清除`CComVariant`物件。

##  <a name="getsize"></a>  CComVariant::GetSize

對於簡單固定的大小變體，此方法會傳回**sizeof**基礎的資料型別加上**sizeof(VARTYPE)**。

```
ULONG GetSize() const;
```

### <a name="return-value"></a>傳回值

以位元組為單位的目前內容的大小`CComVariant`物件。

### <a name="remarks"></a>備註

如果 VARIANT 包含介面指標`GetSize`查詢`IPersistStream`或`IPersistStreamInit`。 如果成功，則傳回值是所傳回之值的低位 32 位元`GetSizeMax`加上**sizeof** CLSID 並**sizeof(VARTYPE)**。 如果介面指標為 NULL，`GetSize`會傳回**sizeof**加號 CLSID **sizeof(VARTYPE)**。 如果大小總計大於 ULONG_MAX，`GetSize`會傳回**sizeof(VARTYPE)** 以表示錯誤。

在其他情況下，VT_BSTR 類型的暫存變數會強制轉型從目前的變數。 此 BSTR 的長度會計算為字串的長度再加上字串本身長度大小加上加號的 null 字元的大小**sizeof(VARTYPE)**。 如果變數不能強制轉型為 VT_BSTR，類型的 VARIANT`GetSize`會傳回**sizeof(VARTYPE)**。

這個方法所傳回的大小符合所使用的位元組數目[CComVariant::WriteToStream](#writetostream)成功的情況下。

##  <a name="operator_eq"></a>  CComVariant::operator =

指派值和對應的型別至`CComVariant`物件。

```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```

### <a name="parameters"></a>參數

*varSrc*<br/>
[in]`CComVariant`或是[VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)指派給`CComVariant`物件。 來源 variant 的內容複製到目的地，而無需轉換。

*bstrSrc*<br/>
[in]若要指派給 BSTR`CComVariant`物件。 型別`CComVariant`物件都會是 VT_BSTR。

*lpszSrc*<br/>
[in]若要指派給字元字串`CComVariant`物件。 您可以傳遞零結束寬 (Unicode) 字元字串至 LPCOLESTR 版本運算子或 LPCSTR 版本的 ANSI 字串。 在任一情況下，此字串會轉換成 BSTR 配置使用 Unicode `SysAllocString`。 型別`CComVariant`物件都會是 VT_BSTR。

*bSrc*<br/>
[in]**Bool**指派給`CComVariant`物件。 **Bool**引數時，會轉換成 VARIANT_BOOL 上，然後再儲存。 型別`CComVariant`物件都會是 VT_BOOL。

*nSrc*<br/>
[in]**Int**，位元組**簡短**，**長**，LONGLONG、 ULONGLONG， **unsigned short**，**不帶正負號長**，或是**不帶正負號的 int**指派給`CComVariant`物件。 型別`CComVariant`物件將會是 VT_I4、 VT_UI1、 VT_I2、 VT_I4、 VT_I8、 VT_UI8、 VT_UI2、 VT_UI4 或 VT_UI4，分別。

*fltSrc*<br/>
[in]**浮點數**指派給`CComVariant`物件。 型別`CComVariant`物件都會是 VT_R4。

*dblSrc*<br/>
[in]**雙**指派給`CComVariant`物件。 型別`CComVariant`物件都會是 VT_R8。

*cySrc*<br/>
[in]`CY`指派給`CComVariant`物件。 型別`CComVariant`物件都會是 VT_CY。

*pSrc*<br/>
[in]`IDispatch`或是`IUnknown`指派給指標`CComVariant`物件。 `AddRef` 將介面指標上呼叫。 型別`CComVariant`物件都會是 VT_DISPATCH 或 VT_UNKNOWN，分別。

或者，若要指派給的 SAFEARRAY 指標`CComVariant`物件。 SAFEARRAY 的複本儲存在`CComVariant`物件。 型別`CComVariant`物件將會原始的型別，以及與的 SAFEARRAY VT_ARRAY 組合。

*cSrc*<br/>
[in]若要指派給 char`CComVariant`物件。 型別`CComVariant`物件都會是 VT_I1。

##  <a name="operator_eq_eq"></a>  CComVariant::operator = =

指出是否`CComVariant`的物件等於指定的變數。

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果為 true 的值和類型*varSrc*相等的值和類型，分別`CComVariant`物件。 否則為 FALSE。 運算子會使用使用者的預設地區設定，以進行比較。

運算子會比較變數的類型值。 它會比較字串、 整數和浮點數，但不是陣列或記錄。

##  <a name="operator_neq"></a>  CComVariant::operator ！ =

指出是否`CComVariant`物件不等於指定的變數。

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果為 true 的值 」 或 「 型別*varSrc*不等於值或型別，分別`CComVariant`物件。 否則為 FALSE。 運算子會使用使用者的預設地區設定，以進行比較。

運算子會比較變數的類型值。 它會比較字串、 整數和浮點數，但不是陣列或記錄。

##  <a name="operator_lt"></a>  CComVariant::operator &lt;

指出是否`CComVariant`物件是否小於指定的變數。

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果為 true 的值`CComVariant`物件是否小於一個的值*varSrc*。 否則為 FALSE。 運算子會使用使用者的預設地區設定，以進行比較。

##  <a name="operator_gt"></a>  CComVariant::operator &gt;

指出是否`CComVariant`物件是否大於指定的變數。

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果為 true 的值`CComVariant`物件的值大於*varSrc*。 否則為 FALSE。 運算子會使用使用者的預設地區設定，以進行比較。

##  <a name="readfromstream"></a>  CComVariant::ReadFromStream

設定基礎的 VARIANT，包含在指定的資料流中的 variant。

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
[in]指標[IStream](/windows/desktop/api/objidl/nn-objidl-istream)上包含資料的資料流介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`ReadToStream` 需要由先前呼叫[WriteToStream](#writetostream)。

##  <a name="setbyref"></a>  CComVariant::SetByRef

初始化`CComVariant`物件以及設定`vt`VT_BYREF 的成員。

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>參數

*T*<br/>
VARIANT，例如 BSTR 類型**int**，或**char**。

*pT*<br/>
用來初始化指標`CComVariant`物件。

### <a name="remarks"></a>備註

`SetByRef` 已初始化的函式樣板`CComVariant`物件的指標*pT* ，並設定`vt`VT_BYREF 的成員。 例如: 

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>  CComVariant::WriteToStream

將資料流中的基礎變體。

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
[in]指標[IStream](/windows/desktop/api/objidl/nn-objidl-istream)資料流上的介面。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
