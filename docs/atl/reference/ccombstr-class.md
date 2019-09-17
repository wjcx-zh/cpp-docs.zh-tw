---
title: CComBSTR 類別
ms.date: 11/04/2016
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: dd45c2ff9b43148e0fe27ebd410a2390a4d12ce2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497549"
---
# <a name="ccombstr-class"></a>CComBSTR 類別

這個類別是[BSTR](/previous-versions/windows/desktop/automat/bstr)的包裝函式。

## <a name="syntax"></a>語法

```
class CComBSTR
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComBSTR：： CComBSTR](#ccombstr)|建構函式。|
|[CComBSTR：： ~ CComBSTR](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComBSTR::Append](#append)|將字串附加至`m_str`。|
|[CComBSTR::AppendBSTR](#appendbstr)|將 BSTR 附加至`m_str`。|
|[CComBSTR::AppendBytes](#appendbytes)|將指定的位元組數目附加至`m_str`。|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|從 safearray 中每個元素的第一個字元建立 BSTR，並將其附加至`CComBSTR`物件。|
|[CComBSTR：： AssignBSTR](#assignbstr)|將 BSTR 指派給`m_str`。|
|[CComBSTR::Attach](#attach)|將 BSTR 附加至`CComBSTR`物件。|
|[CComBSTR::BSTRToArray](#bstrtoarray)|建立以零為起始的一維 safearray，其中陣列的每個元素都是來自`CComBSTR`物件的字元。|
|[CComBSTR::ByteLength](#bytelength)|傳回的長度（ `m_str`以位元組為單位）。|
|[CComBSTR::Copy](#copy)|傳回的`m_str`複本。|
|[CComBSTR::CopyTo](#copyto)|透過`m_str` **[out]** 參數傳回的複本|
|[CComBSTR::Detach](#detach)|`m_str`卸離物件。`CComBSTR`|
|[CComBSTR::Empty](#empty)|釋放`m_str`。|
|[CComBSTR::Length](#length)|傳回的長度`m_str`。|
|[CComBSTR::LoadString](#loadstring)|載入字串資源。|
|[CComBSTR::ReadFromStream](#readfromstream)|從資料流程載入 BSTR 物件。|
|[CComBSTR::ToLower](#tolower)|將字串轉換成小寫。|
|[CComBSTR::ToUpper](#toupper)|將字串轉換成大寫。|
|[CComBSTR::WriteToStream](#writetostream)|儲存`m_str`至資料流程。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComBSTR：： operator BSTR](#operator_bstr)|`CComBSTR`將物件轉換成 BSTR。|
|[CComBSTR：： operator！](#operator_not)|傳回 TRUE 或 FALSE，取決於是否`m_str`為 Null。|
|[CComBSTR::operator !=](#operator_neq)|`CComBSTR`比較與字串。|
|[CComBSTR：： operator &](#operator_amp)|傳回的位址`m_str`。|
|[CComBSTR：： operator + =](#operator_add_eq)|將附加`CComBSTR`至物件。|
|[CComBSTR：： operator <](#operator_lt)|`CComBSTR`比較與字串。|
|[CComBSTR：： operator =](#operator_eq)|將值指派給`m_str`。|
|[CComBSTR：： operator = =](#operator_eq_eq)|`CComBSTR`比較與字串。|
|[CComBSTR：： operator >](#operator_gt)|`CComBSTR`比較與字串。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|包含與`CComBSTR`物件相關聯的 BSTR。|

## <a name="remarks"></a>備註

`CComBSTR`類別是 bstr 的包裝函式，其長度為首碼的字串。 長度會在字串中的資料前面的記憶體位置儲存為整數。

在最後一個計數位符之後， [BSTR](/previous-versions/windows/desktop/automat/bstr)會以 null 結束，但也可能包含內嵌在字串中的 null 字元。 字串長度取決於字元計數，而不是第一個 null 字元。

> [!NOTE]
>  `CComBSTR`類別會提供一些以 ANSI 或 Unicode 字串做為引數的成員（多個函數、指派運算子和比較運算子）。 這些函式的 ANSI 版本比 Unicode 對應專案更有效率，因為暫時的 Unicode 字串通常會在內部建立。 為求效率，請盡可能使用 Unicode 版本。

> [!NOTE]
>  由於在 Visual Studio .net 中實作為改良的查閱行為，因此， `bstr = L"String2" + bstr;`在舊版中可能已編譯的程式碼（如），應`bstr = CStringW(L"String2") + bstr`改為實作為。

如需使用`CComBSTR`時的警告清單，請參閱[使用 CComBSTR](../../atl/programming-with-ccombstr-atl.md)進行程式設計。

## <a name="requirements"></a>需求

**標頭：** atlbase.h。h

##  <a name="append"></a>CComBSTR：： Append

將*lpsz*或*bstrSrc*的 BSTR 成員附加至[m_str](#m_str)。

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>參數

*bstrSrc*<br/>
在要`CComBSTR`附加的物件。

*ch*<br/>
在要附加的字元。

*lpsz*<br/>
在要附加的以零結束的字元字串。 您可以透過 LPCOLESTR 多載或 ANSI 字串，經由 LPCSTR 版本傳遞 Unicode 字串。

*nLen*<br/>
在從*lpsz*到附加的字元數。

### <a name="return-value"></a>傳回值

成功時為 S_OK，或任何標準 HRESULT 錯誤值。

### <a name="remarks"></a>備註

ANSI 字串會先轉換成 Unicode，然後再附加。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>CComBSTR：： AppendBSTR

將指定的 BSTR 附加至[m_str](#m_str)。

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
在要附加的 BSTR。

### <a name="return-value"></a>傳回值

成功時為 S_OK，或任何標準 HRESULT 錯誤值。

### <a name="remarks"></a>備註

請勿將一般寬字元字串傳遞給這個方法。 編譯器無法攔截錯誤，而且將會發生執行階段錯誤。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>CComBSTR：： AppendBytes

將指定的位元組數目附加至[m_str](#m_str) ，而不進行轉換。

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>參數

*lpsz*<br/>
在要附加之位元組陣列的指標。

*p*<br/>
在要附加的位元組數目。

### <a name="return-value"></a>傳回值

成功時為 S_OK，或任何標準 HRESULT 錯誤值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>CComBSTR：： ArrayToBSTR

釋放物件中保留的`CComBSTR`任何現有字串，然後從 safearray 中每個專案的第一個字元建立 BSTR，並將其附加`CComBSTR`至物件。

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>參數

*pSrc*<br/>
在Safearray，其中包含用來建立字串的元素。

### <a name="return-value"></a>傳回值

成功時為 S_OK，或任何標準 HRESULT 錯誤值。

##  <a name="assignbstr"></a>CComBSTR：： AssignBSTR

將 BSTR 指派給[m_str](#m_str)。

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>參數

*bstrSrc*<br/>
在要指派給目前`CComBSTR`物件的 BSTR。

### <a name="return-value"></a>傳回值

成功時為 S_OK，或任何標準 HRESULT 錯誤值。

##  <a name="attach"></a>CComBSTR：： Attach

藉由將[m_str](#m_str)成員`CComBSTR`設定為*src*，將 BSTR 附加至物件。

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>參數

*src*<br/>
在要附加至物件的 BSTR。

### <a name="remarks"></a>備註

請勿將一般寬字元字串傳遞給這個方法。 編譯器無法攔截錯誤，而且將會發生執行階段錯誤。

> [!NOTE]
>  如果為非 Null， `m_str`這個方法會判斷提示。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>CComBSTR：： BSTRToArray

建立以零為起始的一維 safearray，其中陣列的每個元素都是來自`CComBSTR`物件的字元。

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>參數

*ppArray*<br/>
脫銷用來保存函數結果的 safearray 指標。

### <a name="return-value"></a>傳回值

成功時為 S_OK，或任何標準 HRESULT 錯誤值。

##  <a name="bytelength"></a>CComBSTR：： ByteLength

傳回中`m_str`的位元組數目，不包括終止的 null 字元。

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>傳回值

[M_str](#m_str)成員的長度（以位元組為單位）。

### <a name="remarks"></a>備註

如果`m_str`為 Null，則傳回0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>CComBSTR：： CComBSTR

建構函式。 預設的函式會將[m_str](#m_str)成員設定為 Null。

```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);
CComBSTR(REFGUID  guid);
CComBSTR(int nSize);
CComBSTR(int nSize, LPCOLESTR sz);
CComBSTR(int nSize, LPCSTR sz);
CComBSTR(LPCOLESTR pSrc);
CComBSTR(LPCSTR pSrc);
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*nSize*<br/>
在要從*sz*複製的字元數，或的`CComBSTR`初始大小（以字元為單位）。

*sz*<br/>
[in] 要複製的字串。 Unicode 版本指定 LPCOLESTR;ANSI 版本會指定 LPCSTR。

*pSrc*<br/>
[in] 要複製的字串。 Unicode 版本指定 LPCOLESTR;ANSI 版本會指定 LPCSTR。

*src*<br/>
[in] `CComBSTR` 物件。

*guid*<br/>
在`GUID`結構的參考。

### <a name="remarks"></a>備註

複製的函式`m_str`會將設定為*src*之 BSTR 成員的複本。此`REFGUID`函式會使用`StringFromGUID2`將 GUID 轉換為字串，並儲存結果。

其他建構函式會將 `m_str` 設為所指定字串的複本。 如果您傳遞*nSize*的值，則只會複製*nSize*字元，後面接著終止的 null 字元。

`CComBSTR` 支援移動語意。 您可以使用移動建構函式 (採用右值參考的建構函式 (`&&`)) 來建立新的物件，其使用的基本資料與您當作引數傳入之舊物件相同，無需額外複製物件。

解構函式會釋放 `m_str` 所指向的字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>CComBSTR：： ~ CComBSTR

解構函式。

```
~CComBSTR();
```

### <a name="remarks"></a>備註

解構函式會釋放 `m_str` 所指向的字串。

##  <a name="copy"></a>CComBSTR：： Copy

配置並傳回的`m_str`複本。

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>傳回值

[M_str](#m_str)成員的複本。 如果`m_str`為 null，則會傳回 null。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>CComBSTR：： CopyTo

透過參數配置並傳回[m_str](#m_str)的複本。

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>參數

*pbstr*<br/>
脫銷要傳回這個方法所配置的字串之 BSTR 的位址。

*pvarDest*<br/>
脫銷傳回此方法所配置之字串的變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值，指出複本的成功或失敗。

### <a name="remarks"></a>備註

呼叫這個方法之後， *pvarDest*所指向的 VARIANT 將屬於 VT_BSTR 類型。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>CComBSTR：:D etach

`m_str`從`CComBSTR` 物件卸離 [m_str](#m_str)，並將設定為 Null。

```
BSTR Detach() throw();
```

### <a name="return-value"></a>傳回值

與`CComBSTR`物件相關聯的 BSTR。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>CComBSTR：： Empty

釋放[m_str](#m_str)成員。

```
void Empty() throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>CComBSTR：： Length

傳回中`m_str`的字元數，不包括終止的 null 字元。

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>傳回值

[M_str](#m_str)成員的長度。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>CComBSTR：： Loadstring 時

載入*nID*指定的字串資源，並將它儲存在此物件中。

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>參數

請參閱 Windows SDK 中的[loadstring 時](/windows/win32/api/winuser/nf-winuser-loadstringw)。

### <a name="return-value"></a>傳回值

如果成功載入字串，則傳回 TRUE;否則，會傳回 FALSE。

### <a name="remarks"></a>備註

第一個函式會透過*hInst*參數，從您所識別的模組載入資源。 第二個函式會從與此專案中所使用之[CComModule](../../atl/reference/ccommodule-class.md)衍生物件相關聯的資源模組載入資源。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>  CComBSTR::m_str

包含與`CComBSTR`物件相關聯的 BSTR。

```
BSTR m_str;
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>CComBSTR：： operator BSTR

`CComBSTR`將物件轉換成 BSTR。

```
operator BSTR() const throw();
```

### <a name="remarks"></a>備註

可讓您將`CComBSTR`物件傳遞給具有 **[in] BSTR**參數的函式。

### <a name="example"></a>範例

請參閱[CComBSTR：： m_str](#m_str)的範例。

##  <a name="operator_not"></a>CComBSTR：： operator！

檢查 BSTR 字串是否為 Null。

```
bool operator!() const throw();
```

### <a name="return-value"></a>傳回值

如果[m_str](#m_str)成員是 Null，則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個運算子只會檢查是否有 Null 值，而不是空字串的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>CComBSTR：： operator！ =

傳回[operator = =](#operator_eq_eq)的邏輯相反。

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>參數

*bstrSrc*<br/>
[in] `CComBSTR` 物件。

*pszSrc*<br/>
在以零結束的字串。

*nNull*<br/>
在必須是 Null。

### <a name="return-value"></a>傳回值

如果要比較的專案不等於`CComBSTR`物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

`CComBSTR`在使用者的預設地區設定內容中，會以每秒的方式進行比較。 最後一個比較運算子只會比較包含的字串與 Null。

##  <a name="operator_amp"></a>CComBSTR：： operator&amp;

傳回儲存在[m_str](#m_str)成員中的 BSTR 位址。

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>備註

`CComBstr operator &`具有與其相關聯的特殊判斷提示，以協助找出記憶體流失。 程式將在初始化`m_str`成員時判斷提示。 建立此判斷提示的目標，是為了識別程式設計`& operator`人員使用將新值指派`m_str`給成員，而不需釋放`m_str`第一次配置的情況。 如果`m_str`等於 Null，程式會假設尚未配置 m_str。 在此情況下，程式將不會判斷提示。

預設不會啟用此判斷提示。 定義 ATL_CCOMBSTR_ADDRESS_OF_ASSERT 以啟用此判斷提示。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>CComBSTR：： operator + =

將字串附加至`CComBSTR`物件。

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>參數

*bstrSrc*<br/>
在要`CComBSTR`附加的物件。

*pszSrc*<br/>
在要附加之以零為結尾的字串。

### <a name="remarks"></a>備註

`CComBSTR`在使用者的預設地區設定內容中，會以每秒的方式進行比較。 LPCOLESTR 比較是在每個`memcmp`字串中的原始資料上使用來完成。 建立*pszSrc*的暫存 Unicode 複本之後，就會以相同的方式執行 LPCSTR 比較。 最後一個比較運算子只會比較包含的字串與 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>CComBSTR：： operator&lt;

`CComBSTR`比較與字串。

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>傳回值

如果要比較的專案小於`CComBSTR`物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

比較是使用使用者的預設地區設定來執行。

##  <a name="operator_eq"></a>CComBSTR：： operator =

將[m_str](#m_str)成員設定為 *.psrc*的複本或*src*的 BSTR 成員複本。移動指派運算子會移動`src` ，而不會進行複製。

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>備註

*.Psrc*參數會指定 Unicode 版本的 LPCOLESTR 或 ANSI 版本的 LPCSTR。

### <a name="example"></a>範例

請參閱[CComBSTR：： Copy](#copy)的範例。

##  <a name="operator_eq_eq"></a>CComBSTR：： operator = =

`CComBSTR`比較與字串。 `CComBSTR`在使用者的預設地區設定內容中，會以每秒的方式進行比較。

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>參數

*bstrSrc*<br/>
[in] `CComBSTR` 物件。

*pszSrc*<br/>
在以零結束的字串。

*nNull*<br/>
在必須是 Null。

### <a name="return-value"></a>傳回值

如果要比較的專案等於`CComBSTR`物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

最後一個比較運算子只會比較包含的字串與 Null。

##  <a name="operator_gt"></a>CComBSTR：： operator&gt;

`CComBSTR`比較與字串。

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>傳回值

如果要比較的專案大於`CComBSTR`物件，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

比較是使用使用者的預設地區設定來執行。

##  <a name="readfromstream"></a>CComBSTR：： ReadFromStream

將[m_str](#m_str)成員設定為包含在指定之資料流程中的 BSTR。

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>參數

*pStream*<br/>
在資料流程上包含資料之[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`ReadToStream`要求目前位置的資料流程內容，與呼叫[WriteToStream](#writetostream)所寫出的資料格式相容。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>CComBSTR：： ToLower

將包含的字串轉換為小寫。

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如`CharLowerBuff`需如何執行轉換的詳細資訊，請參閱。

##  <a name="toupper"></a>CComBSTR：： ToUpper

將包含的字串轉換成大寫。

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如`CharUpperBuff`需如何執行轉換的詳細資訊，請參閱。

##  <a name="writetostream"></a>CComBSTR：： WriteToStream

將[m_str](#m_str)成員儲存至資料流程。

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>參數

*pStream*<br/>
在資料流程上[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

您可以使用[ReadFromStream](#readfromstream)函數，從資料流程的內容重新建立 BSTR。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[ATL 和 MFC 字串轉換宏](string-conversion-macros.md)
