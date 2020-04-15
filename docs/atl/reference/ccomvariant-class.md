---
title: CCom 變數類別
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
ms.openlocfilehash: 9a84d91e20242fb206d1d3f71fcb3dd207561f62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327220"
---
# <a name="ccomvariant-class"></a>CCom 變數類別

此類包裝 VARIANT 類型,提供一個成員,指示存儲的數據類型。

## <a name="syntax"></a>語法

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom變數:Ccom變數](#ccomvariant)|建構函式。|
|[CCom變數:*Ccom變數](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom 變數:附加](#attach)|將 VARIANT`CComVariant`附加到 物件。|
|[CCom 變數:變更類型](#changetype)|將`CComVariant`物件轉換為新類型。|
|[CCom 變數:清除](#clear)|清除`CComVariant`物件。|
|[CCom 變數:複製](#copy)|將 VARIANT`CComVariant`複製到 物件。|
|[Ccom 變數::複製到](#copyto)|複製`CComVariant`物件的內容。|
|[CComVariant::Detach](#detach)|從`CComVariant`物件分離基礎 VARIANT。|
|[CCom 變數:取得 Size](#getsize)|返回`CComVariant`物件內容的大小(以位元組數為單位)。|
|[Ccom 變數::從流中讀取](#readfromstream)|從流載入 VARIANT。|
|[Ccom 變數::設定ByRef](#setbyref)|初始化物件並將`CComVariant``vt`成員設置為VT_BYREF。|
|[Ccom 變數::寫入流](#writetostream)|將基礎 VARIANT 保存到流中。|

### <a name="public-operators"></a>公用運算子

|||
|-|-|
|[CComVariant::操作員<](#operator_lt)|指示`CComVariant`物件是否小於指定的 VARIANT。|
|[CComVariant::操作員>](#operator_gt)|指示`CComVariant`物件是否大於指定的 VARIANT。|
|[操作員 !]](#operator_neq)|指示`CComVariant`物件是否等於指定的 VARIANT。|
|[運算符 |](#operator_eq)|向`CComVariant`物件分配值。|
|[運算符 |](#operator_eq_eq)|指示`CComVariant`物件是否等於指定的 VARIANT。|

## <a name="remarks"></a>備註

`CComVariant`包裝 VARIANT 和 VARIANTARG 類型,該類型由一個聯合和一個成員組成,指示聯盟中存儲的數據類型。 VARIANT 通常用於自動化。

`CComVariant`派生自 VARIANT 類型,因此可以在可以使用 VARIANT 的任何位置使用。 例如,可以使用V_VT宏提取 類型`CComVariant`, 也可以像使用 VARIANT`vt`一樣直接訪問 成員。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>需求

**標題:** atlcomcli.h

## <a name="ccomvariantattach"></a><a name="attach"></a>CCom 變數:附加

安全地清除`CComVariant`物件的當前內容,將*pSrc*的內容複製到此物件中,然後將*pSrc*的變體類型設置為VT_EMPTY。

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>參數

*pSrc*<br/>
[在]指向要附加到物件的[VARIANT。](/windows/win32/api/oaidl/ns-oaidl-variant)

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

*pSrc*持有的數據的擁有權將轉移到`CComVariant`物件。

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a>CCom變數:Ccom變數

每個構造函數通過調用`CComVariant``VariantInit`Win32 函數或根據傳遞的參數設置物件的值和類型來處理物件的安全初始化。

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
[在]用於`CComVariant`初始化`CComVariant`物件的或 VARIANT。 源變體的內容將複製到目標,無需轉換。

*lpszSrc*<br/>
[在]用於初始化`CComVariant`物件的字串。 您可以將零端端寬(Unicode)字串傳遞給建構函數的 LPCOLESTR 版本,也可以將 ANSI 字串傳遞給 LPCSTR 版本。 在這兩種情況下,字串都將轉換為使用`SysAllocString`分配的 Unicode BSTR。 `CComVariant`對象的類型將VT_BSTR。

*bSrc*<br/>
[在]用於**bool**初始化`CComVariant`物件的布爾。 在存儲之前 **,bool**參數將轉換為VARIANT_BOOL。 `CComVariant`對象的類型將VT_BOOL。

*恩斯爾克*<br/>
[在]**int,** **BYTE,****短**,**長**, 龍, ULONGLONG,**無符號短**,**無符號長**, 或**無符號的 int**用於初始`CComVariant`化物件. `CComVariant`對象的類型將分別為VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4或VT_UI4。

*弗茨爾克*<br/>
[在]變體的類型。 當第一個參數為**int**時,有效類型VT_I4並VT_INT。 當第一個參數**長**時,有效類型VT_I4並VT_ERROR。 當第一個參數**為雙精度**時,有效類型VT_R8,並VT_DATE。 當第一個參數**為無符號 int**時,有效類型VT_UI4和VT_UINT。

*fltSrc*<br/>
[在]初始化`CComVariant`物件的**浮點**。 `CComVariant`對象的類型將VT_R4。

*德布爾斯克*<br/>
[在]初始化`CComVariant`物件**的雙精度值**。 `CComVariant`對象的類型將VT_R8。

*西斯爾克*<br/>
[在]`CY`用於初始化物件。 `CComVariant` `CComVariant`對象的類型將VT_CY。

*pSrc*<br/>
[在]用於`IDispatch`初始`IUnknown`化`CComVariant`物件的或指標。 `AddRef`將在介面指標上調用。 `CComVariant`對象的類型將分別VT_DISPATCH或VT_UNKNOWN。

或者,用於初始化`CComVariant`物件的 SAFERRAY 指標。 SAFEARRAY 的複本儲存在物件`CComVariant`中 。 `CComVariant`對象的類型將是 SAFEARRAY 的原始類型和VT_ARRAY的組合。

*證監會*<br/>
[在]用於**char**初始`CComVariant`化 物件的字元。 `CComVariant`對象的類型將VT_I1。

*布斯特施爾*<br/>
[在]用於初始化`CComVariant`物件的 BSTR。 `CComVariant`對象的類型將VT_BSTR。

### <a name="remarks"></a>備註

析構函數通過調用[CComvariant:::Clear](#clear)來管理清理。

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a>CCom變數:*Ccom變數

解構函式。

```
~CComVariant() throw();
```

### <a name="remarks"></a>備註

此方法通過調用[CComvariant:::Clear](#clear)來管理清理。

## <a name="ccomvariantchangetype"></a><a name="changetype"></a>CCom 變數:變更類型

將`CComVariant`物件轉換為新類型。

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>參數

*vtNew*<br/>
[在]`CComVariant`物件的新類型。

*pSrc*<br/>
[在]指向 VARIANT 的指標,其值將轉換為新類型。 預設值為 NULL,`CComVariant`這意味著 物件將就地轉換。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果傳遞*pSrc*的`ChangeType`值, 將使用此 VARIANT 作為轉換的來源。 否則,`CComVariant`物件將是源。

## <a name="ccomvariantclear"></a><a name="clear"></a>CCom 變數:清除

通過調用`CComVariant``VariantClear`Win32 函數清除物件。

```
HRESULT Clear();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

解音音函數自動呼`Clear`叫 。

## <a name="ccomvariantcopy"></a><a name="copy"></a>CCom 變數:複製

釋放物件,`CComVariant`然後分配給指定的 VARIANT 的複本。

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>參數

*pSrc*<br/>
[在]指向要複製[的 VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccomvariantcopyto"></a><a name="copyto"></a>Ccom 變數::複製到

複製`CComVariant`物件的內容。

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>參數

*普斯特德斯特*<br/>
指向將收到`CComVariant`物件內容副本的 BSTR。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

對`CComVariant`象必須為VT_BSTR類型。

## <a name="ccomvariantdetach"></a><a name="detach"></a>CComVariant::Detach

從`CComVariant`物件分離基礎 VARIANT 並將對象的類型設置為VT_EMPTY。

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>參數

*pDest*<br/>
[出]返回物件的基礎 VARIANT 值。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

請注意,在分配調用`CComVariant`物件的值和類型之前,將自動清除*pDest*引用的 VARIANT 的內容。

## <a name="ccomvariantgetsize"></a><a name="getsize"></a>CCom 變數:取得 Size

對於簡單固定大小 VARIANTs,此方法返回基礎數據類型**的大小**加上**大小(VARTYPE)。**

```
ULONG GetSize() const;
```

### <a name="return-value"></a>傳回值

`CComVariant`物件當前內容的大小(以位元組為單位)。

### <a name="remarks"></a>備註

如果 VARIANT 包含介面指標,`GetSize`則`IPersistStream`查詢`IPersistStreamInit`或 。 如果成功,則返回值是返回`GetSizeMax`的值的低階 32 位元,加上 CLSID**的大小**和大小 **(VARTYPE)。** 如果介面指標為 NULL,`GetSize`則傳回 CLSID**的大小**加上 **(VARTYPE) 的大小**。 如果總大小大於ULONG_MAX,`GetSize`則傳回表示錯誤的 **(VARTYPE) 大小**。

在所有其他情況下,從當前 VARIANT 強制使用VT_BSTR類型的臨時 VARIANT。 此 BSTR 的長度計算為字串的長度加上字串本身的長度加上空字元的大小加上**大小(VARTYPE)。** 如果無法強制將 VARIANT 強制到類型VT_BSTR的 VARIANT,則`GetSize`返回**大小(VARTYPE)。**

此方法返回的大小與[CComVariant:writeToStream](#writetostream)在成功條件下使用的位元組數匹配。

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a>CComVariant::運算符 |

為`CComVariant`物件分配值和相應的類型。

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
[在]要`CComVariant`配置給`CComVariant`物件的[或變數](/windows/win32/api/oaidl/ns-oaidl-variant)。 源變體的內容將複製到目標,無需轉換。

*布斯特施爾*<br/>
[在]要分配給`CComVariant`物件的 BSTR。 `CComVariant`對象的類型將VT_BSTR。

*lpszSrc*<br/>
[在]要分配給`CComVariant`物件的字串。 您可以將零端接寬(Unicode)字串傳遞給運算元的 LPCOLESTR 版本,將 ANSI 字串傳遞給 LPCSTR 版本。 在這兩種情況下,字串都將轉換為使用`SysAllocString`分配的 Unicode BSTR。 `CComVariant`對象的類型將VT_BSTR。

*bSrc*<br/>
[在]要**bool**分配給`CComVariant`物件的布爾。 在存儲之前 **,bool**參數將轉換為VARIANT_BOOL。 `CComVariant`對象的類型將VT_BOOL。

*恩斯爾克*<br/>
[在]**int、** BYTE、**短**、**長**、 龍、 ULONGLONG、**未簽署短**、**無符號長**或**未簽名的 int**分配給`CComVariant`物件。 `CComVariant`對象的類型將分別為VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4或VT_UI4。

*fltSrc*<br/>
[在]要分配給`CComVariant`物件的**float。** `CComVariant`對象的類型將VT_R4。

*德布爾斯克*<br/>
[在]要分配給`CComVariant`物件的**Double。** `CComVariant`對象的類型將VT_R8。

*西斯爾克*<br/>
[在]`CY`要分配給物件。 `CComVariant` `CComVariant`對象的類型將VT_CY。

*pSrc*<br/>
[在]要`IDispatch`分配給`IUnknown``CComVariant`物件的 或指標。 `AddRef`將在介面指標上調用。 `CComVariant`對象的類型將分別VT_DISPATCH或VT_UNKNOWN。

或者,要分配給`CComVariant`物件的 SAFEARRAY 指標。 SAFEARRAY 的複本儲存在物件`CComVariant`中 。 `CComVariant`對象的類型將是 SAFEARRAY 的原始類型和VT_ARRAY的組合。

*證監會*<br/>
[在]要分配給`CComVariant`物件的字元。 `CComVariant`對象的類型將VT_I1。

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a>CComVariant::運算符 |

指示`CComVariant`物件是否等於指定的 VARIANT。

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果*varSrc*的值和類型分別`CComVariant`等於 物件的值和類型,則返回 TRUE。 否則，FALSE。 操作員使用使用者的預設區域設置執行比較。

運算碼僅比較變體類型的值。 它比較字串、整數和浮點,但不比較陣列或記錄。

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a>CComVariant::操作員!*

指示`CComVariant`物件是否等於指定的 VARIANT。

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果*varSrc*的值或類型不分別`CComVariant`等於 物件的值或類型,則返回 TRUE。 否則，FALSE。 操作員使用使用者的預設區域設置執行比較。

運算碼僅比較變體類型的值。 它比較字串、整數和浮點,但不比較陣列或記錄。

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a>CCom變數::運算子&lt;

指示`CComVariant`物件是否小於指定的 VARIANT。

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果`CComVariant`物件的值小於*varSrc*的值,則返回 TRUE。 否則，FALSE。 操作員使用使用者的預設區域設置執行比較。

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a>CCom變數::運算子&gt;

指示`CComVariant`物件是否大於指定的 VARIANT。

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>備註

如果`CComVariant`物件的值大於*varSrc*的值,則返回 TRUE。 否則，FALSE。 操作員使用使用者的預設區域設置執行比較。

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a>Ccom 變數::從流中讀取

將基礎 VARIANT 設置到指定流中包含的 VARIANT。

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
[在]指向流中包含數據的[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`ReadToStream`需要之前呼叫[WriteToStream](#writetostream)。

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a>Ccom 變數::設定ByRef

初始化物件並將`CComVariant``vt`成員設置為VT_BYREF。

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>參數

*T*<br/>
變數的類型,例如 BSTR、int**int**或**字元**。

*鉑*<br/>
用於初始化`CComVariant`物件的指標。

### <a name="remarks"></a>備註

`SetByRef`是一個函數範本,用於將`CComVariant`物件初始化到指標*pT*並將`vt`成員設置到VT_BYREF。 例如：

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a>Ccom 變數::寫入流

將基礎 VARIANT 保存到流中。

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>參數

*pStream*<br/>
[在]指向流上的[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
