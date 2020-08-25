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
ms.openlocfilehash: 40315077ceba3d87e12c8ab426560deef4928793
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833604"
---
# <a name="ccomvariant-class"></a>CComVariant 類別

這個類別會包裝 VARIANT 類型，並提供成員來指出儲存的資料類型。

## <a name="syntax"></a>語法

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComVariant：： CComVariant](#ccomvariant)|建構函式。|
|[CComVariant：： ~ CComVariant](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComVariant：： Attach](#attach)|將 VARIANT 附加至 `CComVariant` 物件。|
|[CComVariant：： ChangeType](#changetype)|將 `CComVariant` 物件轉換成新的類型。|
|[CComVariant：： Clear](#clear)|清除 `CComVariant` 物件。|
|[CComVariant：： Copy](#copy)|將 VARIANT 複製到 `CComVariant` 物件。|
|[CComVariant：： CopyTo](#copyto)|複製物件的內容 `CComVariant` 。|
|[CComVariant：:D etach](#detach)|從物件卸離基礎變異 `CComVariant` 。|
|[CComVariant：： GetSize](#getsize)|傳回物件內容的位元組大小 `CComVariant` 。|
|[CComVariant：： ReadFromStream](#readfromstream)|從資料流程載入變異。|
|[CComVariant：： SetByRef](#setbyref)|初始化 `CComVariant` 物件，並將 `vt` 成員設定為 VT_BYREF。|
|[CComVariant：： WriteToStream](#writetostream)|將基礎變異數儲存至資料流程。|

### <a name="public-operators"></a>公用運算子

|運算子|描述|
|-|-|
|[CComVariant：： operator <](#operator_lt)|指出物件是否 `CComVariant` 小於指定的變異數。|
|[CComVariant：： operator >](#operator_gt)|指出物件是否 `CComVariant` 大於指定的變異數。|
|[operator！ =](#operator_neq)|指出物件是否不 `CComVariant` 等於指定的變異數。|
|[運算子 =](#operator_eq)|將值指派給 `CComVariant` 物件。|
|[operator = =](#operator_eq_eq)|指出物件是否 `CComVariant` 等於指定的變異數。|

## <a name="remarks"></a>備註

`CComVariant` 包裝 VARIANT 和 VARIANTARG 類型，其中包含聯集和成員，指出儲存在聯集的資料類型。 變數通常用於自動化中。

`CComVariant` 衍生自 VARIANT 型別，因此可以在可以使用 VARIANT 的任何地方使用它。 例如，您可以使用 V_VT 宏來解壓縮的型別，也可以 `CComVariant` 直接存取成員，就 `vt` 像您可以使用 VARIANT 一樣。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>規格需求

**標頭：** atlcomcli.h。h

## <a name="ccomvariantattach"></a><a name="attach"></a> CComVariant：： Attach

安全地清除物件的目前內容 `CComVariant` 、將 *.psrc* 的內容複寫到此物件中，然後將 *.psrc* 的 variant 類型設定為 VT_EMPTY。

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>參數

*.Psrc*<br/>
在指向要附加至物件的 [變異](/windows/win32/api/oaidl/ns-oaidl-variant) 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

*.Psrc*所持有資料的擁有權會傳輸到 `CComVariant` 物件。

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a> CComVariant：： CComVariant

每個函式會藉 `CComVariant` 由呼叫 Win32 函式， `VariantInit` 或根據傳遞的參數設定物件的值和類型，來處理物件的安全初始化。

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
在 `CComVariant` 用來初始化物件的或變數 `CComVariant` 。 來源變異的內容會複製到目的地，而不會進行轉換。

*lpszSrc*<br/>
在用來初始化物件的字元字串 `CComVariant` 。 您可以將以零結束的寬 (Unicode) 字元字串傳遞至 LPCOLESTR 版本的函式，或將 ANSI 字串傳遞至 LPCSTR 版本。 在任一種情況下，字串都會轉換成使用配置的 Unicode BSTR `SysAllocString` 。 `CComVariant`將 VT_BSTR 物件的型別。

*bSrc*<br/>
在 **`bool`** 用來初始化物件的 `CComVariant` 。 **`bool`** 引數會在儲存之前轉換成 VARIANT_BOOL。 `CComVariant`將 VT_BOOL 物件的型別。

*nSrc*<br/>
在 **`int`** ** **， **`short`** **`long`** **`unsigned short`** **`unsigned long`** **`unsigned int`** 用來初始化 `CComVariant` 物件的、位元組、、、LONGLONG、ULONGLONG、或。 物件的類型 `CComVariant` 將分別為 VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4 或 VT_UI4。

*vtSrc*<br/>
在變異的型別。 當第一個參數是時 **`int`** ，有效的型別會 VT_I4 且 VT_INT。 當第一個參數是時 **`long`** ，有效的型別會 VT_I4 且 VT_ERROR。 當第一個參數是時 **`double`** ，有效的型別會 VT_R8 且 VT_DATE。 當第一個參數是時 **`unsigned int`** ，有效的型別會 VT_UI4 且 VT_UINT。

*fltSrc*<br/>
在 **`float`** 用來初始化物件的 `CComVariant` 。 `CComVariant`將 VT_R4 物件的型別。

*dblSrc*<br/>
在 **`double`** 用來初始化物件的 `CComVariant` 。 `CComVariant`將 VT_R8 物件的型別。

*cySrc*<br/>
在 `CY` 用來初始化物件的 `CComVariant` 。 `CComVariant`將 VT_CY 物件的型別。

*.Psrc*<br/>
在 `IDispatch` `IUnknown` 用來初始化物件的或指標 `CComVariant` 。 `AddRef` 將在介面指標上呼叫。 物件的類型 `CComVariant` 將會分別 VT_DISPATCH 或 VT_UNKNOWN。

或 SAFERRAY 指標，用來初始化 `CComVariant` 物件。 SAFEARRAY 的複本會儲存在 `CComVariant` 物件中。 物件的類型 `CComVariant` 將會是 SAFEARRAY 的原始型別和 VT_ARRAY 的組合。

*證監會*<br/>
在 **`char`** 用來初始化物件的 `CComVariant` 。 `CComVariant`將 VT_I1 物件的型別。

*bstrSrc*<br/>
在用來初始化物件的 BSTR `CComVariant` 。 `CComVariant`將 VT_BSTR 物件的型別。

### <a name="remarks"></a>備註

此函式會藉由呼叫 [CComVariant：： Clear](#clear)來管理清除。

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a> CComVariant：： ~ CComVariant

解構函式。

```
~CComVariant() throw();
```

### <a name="remarks"></a>備註

這個方法會藉由呼叫 [CComVariant：： Clear](#clear)來管理清除。

## <a name="ccomvariantchangetype"></a><a name="changetype"></a> CComVariant：： ChangeType

將 `CComVariant` 物件轉換成新的類型。

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>參數

*vtNew*<br/>
在物件的新類型 `CComVariant` 。

*.Psrc*<br/>
在VARIANT 的指標，其值將會轉換成新的類型。 預設值為 Null，表示 `CComVariant` 物件會就地轉換。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果您傳遞 *.psrc*的值， `ChangeType` 將會使用此變異作為轉換的來源。 否則， `CComVariant` 物件將會是來源。

## <a name="ccomvariantclear"></a><a name="clear"></a> CComVariant：： Clear

藉 `CComVariant` 由呼叫 Win32 函數來清除物件 `VariantClear` 。

```
HRESULT Clear();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此函式會自動呼叫 `Clear` 。

## <a name="ccomvariantcopy"></a><a name="copy"></a> CComVariant：： Copy

釋出 `CComVariant` 物件，然後為它指派一份指定的 VARIANT。

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>參數

*.Psrc*<br/>
在要複製之 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) 的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccomvariantcopyto"></a><a name="copyto"></a> CComVariant：： CopyTo

複製物件的內容 `CComVariant` 。

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>參數

*pstrDest*<br/>
指向將接收物件內容複本的 BSTR `CComVariant` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`CComVariant`物件的類型必須是 VT_BSTR。

## <a name="ccomvariantdetach"></a><a name="detach"></a> CComVariant：:D etach

從物件卸離基礎變異數 `CComVariant` ，並將物件的型別設定為 VT_EMPTY。

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>參數

*pDest*<br/>
擴展傳回物件的基礎變異值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

請注意， *pDest* 所參考的 VARIANT 內容將會在指派呼叫物件的值和類型之前自動清除 `CComVariant` 。

## <a name="ccomvariantgetsize"></a><a name="getsize"></a> CComVariant：： GetSize

針對簡單固定大小的變體，這個方法會傳回 **`sizeof`** 基礎資料類型的值，加上 **SIZEOF (VARTYPE) **。

```
ULONG GetSize() const;
```

### <a name="return-value"></a>傳回值

物件目前內容的大小（以位元組為單位） `CComVariant` 。

### <a name="remarks"></a>備註

如果變數包含介面指標，則 `GetSize` 查詢 `IPersistStream` 或 `IPersistStreamInit` 。 如果成功，則傳回值為 plus 和所傳回值的低序位32位 `GetSizeMax` `sizeof(CLSID)` `sizeof(VARTYPE)` 。 如果介面指標為 Null，則 `GetSize` 傳回 `sizeof(CLSID)` 加號 `sizeof(VARTYPE)` 。 如果總大小大於 ULONG_MAX，會傳回 `GetSize` `sizeof(VARTYPE)` 表示錯誤的。

在所有其他情況下，會從目前的 VARIANT 強制型別 VT_BSTR 的暫時性變異。 此 BSTR 的長度會計算為字串長度的大小加上字串本身的長度加上 null 字元的大小加上 null 字元加上 **sizeof (VARTYPE) **。 如果 VARIANT 無法強制轉型為類型 VT_BSTR 的 VARIANT，則會傳回 `GetSize` **SIZEOF (VARTYPE) **。

這個方法所傳回的大小符合 [CComVariant：： WriteToStream](#writetostream) 在成功的情況下所使用的位元組數目。

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a> CComVariant：： operator =

將值和對應的類型指派給 `CComVariant` 物件。

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
在 `CComVariant` 要指派給物件的或 [變數](/windows/win32/api/oaidl/ns-oaidl-variant) `CComVariant` 。 來源變異的內容會複製到目的地，而不會進行轉換。

*bstrSrc*<br/>
在要指派給物件的 BSTR `CComVariant` 。 `CComVariant`將 VT_BSTR 物件的型別。

*lpszSrc*<br/>
在要指派給物件的字元字串 `CComVariant` 。 您可以將以零結束的寬 (Unicode) 字元字串傳遞給運算子的 LPCOLESTR 版本，或傳遞至 LPCSTR 版本的 ANSI 字串。 在任一種情況下，字串都會轉換成使用配置的 Unicode BSTR `SysAllocString` 。 `CComVariant`將 VT_BSTR 物件的型別。

*bSrc*<br/>
在 **`bool`** 要指派給 `CComVariant` 物件的。 **`bool`** 引數會在儲存之前轉換成 VARIANT_BOOL。 `CComVariant`將 VT_BOOL 物件的型別。

*nSrc*<br/>
在要 **`int`** 指派給物件的、位元組、 **`short`** 、、 **`long`** LONGLONG、ULONGLONG、 **`unsigned short`** **`unsigned long`** 或 **`unsigned int`** `CComVariant` 。 物件的類型 `CComVariant` 將分別為 VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4 或 VT_UI4。

*fltSrc*<br/>
在 **`float`** 要指派給 `CComVariant` 物件的。 `CComVariant`將 VT_R4 物件的型別。

*dblSrc*<br/>
在 **`double`** 要指派給 `CComVariant` 物件的。 `CComVariant`將 VT_R8 物件的型別。

*cySrc*<br/>
在 `CY` 要指派給 `CComVariant` 物件的。 `CComVariant`將 VT_CY 物件的型別。

*.Psrc*<br/>
在 `IDispatch` `IUnknown` 要指派給物件的或指標 `CComVariant` 。 `AddRef` 將在介面指標上呼叫。 物件的類型 `CComVariant` 將會分別 VT_DISPATCH 或 VT_UNKNOWN。

或要指派給物件的 SAFEARRAY 指標 `CComVariant` 。 SAFEARRAY 的複本會儲存在 `CComVariant` 物件中。 物件的類型 `CComVariant` 將會是 SAFEARRAY 的原始型別和 VT_ARRAY 的組合。

*證監會*<br/>
在要指派給物件的字元 `CComVariant` 。 `CComVariant`將 VT_I1 物件的型別。

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a> CComVariant：： operator = =

指出物件是否 `CComVariant` 等於指定的變異數。

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果 *varSrc* 的值和類型分別等於物件的值和類型，則傳回 TRUE `CComVariant` 。 否則，FALSE。 運算子會使用使用者的預設地區設定來執行比較。

運算子只會比較變異類型的值。 它會比較字串、整數和浮點數，但不會比較陣列或記錄。

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a> CComVariant：： operator！ =

指出物件是否不 `CComVariant` 等於指定的變異數。

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果 *varSrc* 的值或類型不等於物件的值或類型，則傳回 TRUE `CComVariant` 。 否則，FALSE。 運算子會使用使用者的預設地區設定來執行比較。

運算子只會比較變異類型的值。 它會比較字串、整數和浮點數，但不會比較陣列或記錄。

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a> CComVariant：： operator &lt;

指出物件是否 `CComVariant` 小於指定的變異數。

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果物件的值小於 VarSrc 的值，則傳回 TRUE `CComVariant` 。 *varSrc* 否則，FALSE。 運算子會使用使用者的預設地區設定來執行比較。

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a> CComVariant：： operator &gt;

指出物件是否 `CComVariant` 大於指定的變異數。

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果物件的值大於 VarSrc 的值，則傳回 TRUE `CComVariant` 。 *varSrc* 否則，FALSE。 運算子會使用使用者的預設地區設定來執行比較。

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a> CComVariant：： ReadFromStream

將基礎變異數設定為指定之資料流程中包含的 VARIANT。

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
在包含資料之資料流程上的 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 介面指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`ReadToStream` 需要先前的 [WriteToStream](#writetostream)呼叫。

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a> CComVariant：： SetByRef

初始化 `CComVariant` 物件，並將 `vt` 成員設定為 VT_BYREF。

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>參數

*T*<br/>
VARIANT 的類型，例如 BSTR、 **`int`** 或 **`char`** 。

*鉑*<br/>
用來初始化物件的指標 `CComVariant` 。

### <a name="remarks"></a>備註

`SetByRef` 是一種函式範本，會將 `CComVariant` 物件初始化為指標的 *pT* ，並將 `vt` 成員設定為 VT_BYREF。 例如：

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a> CComVariant：： WriteToStream

將基礎變異數儲存至資料流程。

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
在資料流程上的 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 介面指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
