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
ms.openlocfilehash: b4c157435aaffab5f1315fd4636f55f9d4e0d5b4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496866"
---
# <a name="ccomvariant-class"></a>CComVariant 類別

這個類別會包裝 VARIANT 型別，並提供成員來指出儲存的資料型別。

## <a name="syntax"></a>語法

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|建構函式。|
|[CComVariant：： ~ CComVariant](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComVariant::Attach](#attach)|將 VARIANT 附加至`CComVariant`物件。|
|[CComVariant::ChangeType](#changetype)|`CComVariant`將物件轉換成新的類型。|
|[CComVariant::Clear](#clear)|`CComVariant`清除物件。|
|[CComVariant::Copy](#copy)|將 VARIANT 複製到`CComVariant`物件。|
|[CComVariant::CopyTo](#copyto)|複製`CComVariant`物件的內容。|
|[CComVariant::Detach](#detach)|從`CComVariant`物件卸離基礎變體。|
|[CComVariant::GetSize](#getsize)|以位元組數傳回`CComVariant`物件內容的大小。|
|[CComVariant::ReadFromStream](#readfromstream)|從資料流程載入變體。|
|[CComVariant::SetByRef](#setbyref)|初始化物件，並將成員設定為 VT_BYREF。 `vt` `CComVariant`|
|[CComVariant::WriteToStream](#writetostream)|將基礎變體儲存至資料流程。|

### <a name="public-operators"></a>公用運算子

|||
|-|-|
|[CComVariant：： operator <](#operator_lt)|指出`CComVariant`物件是否小於指定的 VARIANT。|
|[CComVariant：： operator >](#operator_gt)|指出`CComVariant`物件是否大於指定的 VARIANT。|
|[operator !=](#operator_neq)|指出`CComVariant`物件是否不等於指定的 VARIANT。|
|[operator =](#operator_eq)|將值指派給`CComVariant`物件。|
|[operator ==](#operator_eq_eq)|指出`CComVariant`物件是否等於指定的 VARIANT。|

## <a name="remarks"></a>備註

`CComVariant`包裝 VARIANT 和 VARIANTARG 類型，其中包含 union 和成員，指出儲存在聯集的資料類型。 變數通常用於自動化。

`CComVariant`衍生自 VARIANT 型別，因此可以在任何可使用 VARIANT 的地方使用。 例如，您可以使用 V_VT 宏來解壓縮的類型`CComVariant` ，或者您可以直接存取該`vt`成員，就像您可以使用 VARIANT 一樣。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>需求

**標頭：** atlcomcli.h。h

##  <a name="attach"></a>CComVariant：： Attach

安全地清除`CComVariant`物件的目前內容，將 *.psrc*的內容複寫到這個物件中，然後將 *.psrc*的 variant 類型設定為 VT_EMPTY。

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>參數

*pSrc*<br/>
在指向要附加至物件的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) 。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

*.Psrc*所持有的資料擁有權會傳送至`CComVariant`物件。

##  <a name="ccomvariant"></a>CComVariant：： CComVariant

每個函式都會`CComVariant` `VariantInit`呼叫 Win32 函數，或根據傳遞的參數設定物件的值和類型，以處理物件的安全初始化。

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
在用`CComVariant` 來`CComVariant`初始化物件的或 VARIANT。 來源變異的內容會複製到目的地，而不會進行轉換。

*lpszSrc*<br/>
在用來初始化`CComVariant`物件的字元字串。 您可以將以零結束的寬（Unicode）字元字串傳遞至 LPCOLESTR 版本的函式，或將 ANSI 字串傳遞至 LPCSTR 版本。 在任一情況下，字串都會轉換成使用`SysAllocString`所配置的 Unicode BSTR。 `CComVariant`物件的類型將會是 VT_BSTR。

*bSrc*<br/>
在用來初始化`CComVariant`物件的 bool。 在儲存之前， **bool**引數會轉換成 VARIANT_BOOL。 `CComVariant`物件的類型將會是 VT_BOOL。

*nSrc*<br/>
在用來初始化物件的 int、BYTE、short、long、LONGLONG、ULONGLONG、不帶正負號的簡短、不帶正負號的整數或不帶正負號的 int。 `CComVariant` `CComVariant`物件的類型會分別是 VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4 或 VT_UI4。

*vtSrc*<br/>
在Variant 的類型。 當第一個參數是**int**時，有效的類型為 VT_I4 和 VT_INT。 當第一個參數很**長**時，有效的類型為 VT_I4 和 VT_ERROR。 當第一個參數為**double**時，有效的類型為 VT_R8 和 VT_DATE。 當第一個參數為不**帶正負**號的整數時，有效的類型為 VT_UI4 和 VT_UINT。

*fltSrc*<br/>
在用來初始化`CComVariant`物件的 float。 `CComVariant`物件的類型將會是 VT_R4。

*dblSrc*<br/>
在用來初始化`CComVariant`物件的**雙精度浮點數**。 `CComVariant`物件的類型將會是 VT_R8。

*cySrc*<br/>
在用`CY` 來`CComVariant`初始化物件的。 `CComVariant`物件的類型將會是 VT_CY。

*pSrc*<br/>
在用`IDispatch`來`IUnknown`初始化`CComVariant`物件的或指標。 `AddRef`將在介面指標上呼叫。 `CComVariant`物件的類型會分別是 VT_DISPATCH 或 VT_UNKNOWN。

或者，用來初始化`CComVariant`物件的 SAFERRAY 指標。 SAFEARRAY 的複本會儲存在`CComVariant`物件中。 `CComVariant`物件的類型將會結合 SAFEARRAY 和 VT_ARRAY 的原始類型。

*cSrc*<br/>
在用來初始化`CComVariant`物件的 char。 `CComVariant`物件的類型將會是 VT_I1。

*bstrSrc*<br/>
在用來初始化`CComVariant`物件的 BSTR。 `CComVariant`物件的類型將會是 VT_BSTR。

### <a name="remarks"></a>備註

此函式會藉由呼叫[CComVariant：： Clear](#clear)來管理清除。

##  <a name="dtor"></a>CComVariant：： ~ CComVariant

解構函式。

```
~CComVariant() throw();
```

### <a name="remarks"></a>備註

這個方法會藉由呼叫[CComVariant：： Clear](#clear)來管理清除。

##  <a name="changetype"></a>CComVariant：： ChangeType

`CComVariant`將物件轉換成新的類型。

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>參數

*vtNew*<br/>
在`CComVariant`物件的新類型。

*pSrc*<br/>
在VARIANT 的指標，其值將轉換成新的類型。 預設值為 Null，表示`CComVariant`物件將會就地轉換。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果您傳遞 *.psrc*的值， `ChangeType`將會使用此變體做為轉換的來源。 否則， `CComVariant`物件將會是來源。

##  <a name="clear"></a>CComVariant：： Clear

藉由`VariantClear`呼叫 Win32 函數來清除`CComVariant`物件。

```
HRESULT Clear();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

此析構函式`Clear`會自動呼叫。

##  <a name="copy"></a>CComVariant：： Copy

`CComVariant`釋放物件，然後為它指派指定之 VARIANT 的複本。

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>參數

*pSrc*<br/>
在要複製之[變數](/windows/win32/api/oaidl/ns-oaidl-variant)的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="copyto"></a>CComVariant：： CopyTo

複製`CComVariant`物件的內容。

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>參數

*pstrDest*<br/>
指向會接收`CComVariant`物件內容複本的 BSTR。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`CComVariant`物件的類型必須是 VT_BSTR。

##  <a name="detach"></a>CComVariant：:D etach

從`CComVariant`物件卸離基礎變異數，並將物件的類型設定為 VT_EMPTY。

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>參數

*pDest*<br/>
脫銷傳回物件的基礎變異值。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

請注意， *pDest*所參考的 VARIANT 內容會在指派呼叫`CComVariant`物件的值和類型之前自動清除。

##  <a name="getsize"></a>CComVariant：： GetSize

針對簡單-固定大小變化，這個方法會傳回基礎資料類型加上**sizeof （VARTYPE）** 的**sizeof** 。

```
ULONG GetSize() const;
```

### <a name="return-value"></a>傳回值

`CComVariant`物件目前內容的大小（以位元組為單位）。

### <a name="remarks"></a>備註

如果 VARIANT 包含介面指標， `GetSize`則`IPersistStream`查詢或`IPersistStreamInit`。 如果成功，則傳回值會是所傳回`GetSizeMax`值的低序位32位，加上**sizeof**的 CLSID 和**sizeof （VARTYPE）** 。 如果介面指標是 Null， `GetSize`則會傳回**sizeof**加上**sizeof （VARTYPE）** 。 如果總大小大於 ULONG_MAX， `GetSize`則會傳回表示錯誤的**sizeof （VARTYPE）** 。

在所有其他情況下，VT_BSTR 類型的暫時變體會從目前的 VARIANT 強制轉型。 這個 BSTR 的長度會計算為字串長度加上字串本身長度加上 null 字元加上**sizeof （VARTYPE）** 的大小。 如果 variant 無法強制轉型為 VT_BSTR 類型的 variant， `GetSize`則會傳回**sizeof （VARTYPE）** 。

這個方法所傳回的大小符合成功條件下[CComVariant：： WriteToStream](#writetostream)所使用的位元組數目。

##  <a name="operator_eq"></a>CComVariant：： operator =

將值和對應的`CComVariant`類型指派給物件。

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
在要`CComVariant`指派給物件的或[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)。`CComVariant` 來源變異的內容會複製到目的地，而不會進行轉換。

*bstrSrc*<br/>
在要指派給`CComVariant`物件的 BSTR。 `CComVariant`物件的類型將會是 VT_BSTR。

*lpszSrc*<br/>
在要指派`CComVariant`給物件的字元字串。 您可以將以零結束的寬（Unicode）字元字串傳遞至 LPCOLESTR 版本的運算子，或將 ANSI 字串傳遞至 LPCSTR 版本。 不論是哪一種情況，字串都會轉換成使用`SysAllocString`所配置的 Unicode BSTR。 `CComVariant`物件的類型將會是 VT_BSTR。

*bSrc*<br/>
在要指派給`CComVariant`物件的 bool。 在儲存之前， **bool**引數會轉換成 VARIANT_BOOL。 `CComVariant`物件的類型將會是 VT_BOOL。

*nSrc*<br/>
在要指派`CComVariant`給物件的**int**、BYTE、 **short**、 **long**、LONGLONG、ULONGLONG、不帶正負號的**簡短**、不帶正負**號的** **整數或無符號 int** 。 `CComVariant`物件的類型會分別是 VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4 或 VT_UI4。

*fltSrc*<br/>
在要指派`CComVariant`給物件的 float。 `CComVariant`物件的類型將會是 VT_R4。

*dblSrc*<br/>
在要指派給`CComVariant`物件的**雙精度浮點數**。 `CComVariant`物件的類型將會是 VT_R8。

*cySrc*<br/>
在要`CY` 指派`CComVariant`給物件的。 `CComVariant`物件的類型將會是 VT_CY。

*pSrc*<br/>
在要指派`IUnknown`給`IDispatch`物件的或指標。`CComVariant` `AddRef`將在介面指標上呼叫。 `CComVariant`物件的類型會分別是 VT_DISPATCH 或 VT_UNKNOWN。

或者是要指派給物件的`CComVariant` SAFEARRAY 指標。 SAFEARRAY 的複本會儲存在`CComVariant`物件中。 `CComVariant`物件的類型將會結合 SAFEARRAY 和 VT_ARRAY 的原始類型。

*cSrc*<br/>
在要指派`CComVariant`給物件的 char。 `CComVariant`物件的類型將會是 VT_I1。

##  <a name="operator_eq_eq"></a>CComVariant：： operator = =

指出`CComVariant`物件是否等於指定的 VARIANT。

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果*varSrc*的值和類型分別`CComVariant`等於物件的值和類型，則傳回 TRUE。 否則為 FALSE。 運算子會使用使用者的預設地區設定來執行比較。

運算子只會比較 variant 類型的值。 它會比較字串、整數和浮點數，而不是陣列或記錄。

##  <a name="operator_neq"></a>CComVariant：： operator！ =

指出`CComVariant`物件是否不等於指定的 VARIANT。

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果*varSrc*的值或類型不等於`CComVariant`物件的值或類型，則傳回 TRUE。 否則為 FALSE。 運算子會使用使用者的預設地區設定來執行比較。

運算子只會比較 variant 類型的值。 它會比較字串、整數和浮點數，而不是陣列或記錄。

##  <a name="operator_lt"></a>CComVariant：： operator&lt;

指出`CComVariant`物件是否小於指定的 VARIANT。

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果`CComVariant`物件的值小於*varSrc*的值，則傳回 TRUE。 否則為 FALSE。 運算子會使用使用者的預設地區設定來執行比較。

##  <a name="operator_gt"></a>CComVariant：： operator&gt;

指出`CComVariant`物件是否大於指定的 VARIANT。

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果`CComVariant`物件的值大於*varSrc*的值，則傳回 TRUE。 否則為 FALSE。 運算子會使用使用者的預設地區設定來執行比較。

##  <a name="readfromstream"></a>CComVariant：： ReadFromStream

將基礎變異數設定為包含在指定之資料流程中的 VARIANT。

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
在資料流程上包含資料之[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`ReadToStream`需要先前對[WriteToStream](#writetostream)的呼叫。

##  <a name="setbyref"></a>CComVariant：： SetByRef

初始化物件，並將成員設定為 VT_BYREF。 `vt` `CComVariant`

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>參數

*T*<br/>
VARIANT 的類型，例如 BSTR、 **int**或**char**。

*pT*<br/>
用來初始化`CComVariant`物件的指標。

### <a name="remarks"></a>備註

`SetByRef`是函式樣板，會將`CComVariant`物件初始化為指標*pT* ，並將`vt`成員設定為 VT_BYREF。 例如：

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>CComVariant：： WriteToStream

將基礎變體儲存至資料流程。

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
在資料流程上[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
