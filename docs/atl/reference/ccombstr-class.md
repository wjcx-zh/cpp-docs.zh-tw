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
ms.openlocfilehash: c1448a5638b263a87403edf0baca170f0f952e26
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748145"
---
# <a name="ccombstr-class"></a>CComBSTR 類別

此類是[BSTR](/previous-versions/windows/desktop/automat/bstr)的包裝。

## <a name="syntax"></a>語法

```
class CComBSTR
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComBSTR:CComBSTR](#ccombstr)|建構函式。|
|[CComBSTR:*CComBSTR](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComBSTR::附錄](#append)|將字串附加到`m_str`。|
|[CComBSTR::附錄BSTR](#appendbstr)|將 BSTR`m_str`新增到 。|
|[CComBSTR::附加位元組](#appendbytes)|將指定數量的位元組附加`m_str`到 。|
|[CComBSTR::ArraytoBSTR](#arraytobstr)|從安全陣列中每個元素的第一個字元創建 BSTR`CComBSTR`並將其 附加到物件。|
|[CComBSTR::配置BSTR](#assignbstr)|將 BSTR`m_str`分配給 。|
|[CComBSTR::附加](#attach)|將 BSTR`CComBSTR`附加到 物件。|
|[CComBSTR:BSTRToarray](#bstrtoarray)|創建基於零的一維安全陣列,其中陣列的每個元素都是物件中的`CComBSTR`字元。|
|[CComBSTR:位元組長度](#bytelength)|返回以位元組為`m_str`單位的長度。|
|[CComBSTR:複製](#copy)|傳回的複`m_str`本 。|
|[CComBSTR::複製到](#copyto)|通過`m_str`**[out]** 參數傳回的複本|
|[CComBSTR::D](#detach)|`m_str`從`CComBSTR`物件分離。|
|[CComBSTR:空](#empty)|自由。 `m_str`|
|[CComBSTR:長度](#length)|傳回的長`m_str`度 。|
|[CComBSTR::載入字串](#loadstring)|載入字串資源。|
|[CComBSTR:從串流讀閱讀](#readfromstream)|從流載入 BSTR 物件。|
|[CComBSTR::到下](#tolower)|將字串轉換為小寫。|
|[CComBSTR::上部](#toupper)|將字串轉換為大寫。|
|[CComBSTR::寫入流](#writetostream)|保存到`m_str`流。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComBSTR::操作員BSTR](#operator_bstr)|將`CComBSTR`物件強制轉換為 BSTR。|
|[CComBSTR::操作員!](#operator_not)|傳回 TRUE 或`m_str`FALSE, 您可以取決於 NULL。|
|[CComBSTR::操作員!*](#operator_neq)|將`CComBSTR`和字串進行比較。|
|[CComBSTR::操作員&](#operator_amp)|傳回的`m_str`位址 。|
|[CComBSTR::操作員 |](#operator_add_eq)|將`CComBSTR`a 追加 到物件。|
|[CComBSTR::操作員<](#operator_lt)|將`CComBSTR`和字串進行比較。|
|[CComBSTR::操作員 |](#operator_eq)|將值配置給`m_str`。|
|[CComBSTR::操作員 |](#operator_eq_eq)|將`CComBSTR`和字串進行比較。|
|[CComBSTR::操作員>](#operator_gt)|將`CComBSTR`和字串進行比較。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComBSTR:m_str](#m_str)|包含與`CComBSTR`物件關聯的 BSTR。|

## <a name="remarks"></a>備註

類`CComBSTR`是 BtR 的包裝器,它是長度預固定字串。 長度以整數儲存在字串中數據之前的記憶體位置。

[BSTR](/previous-versions/windows/desktop/automat/bstr)在最後一個計數字符後為 null 終止,但也可能包含嵌入在字串中的空字元。 字串長度由字元計數(而不是第一個空字元)確定。

> [!NOTE]
> 該`CComBSTR`類提供許多成員(建構函數、賦值運算元和比較運算元),這些成員將ANSI或Unicode字串作為參數。 這些函數的 ANSI 版本的效率低於 Unicode 版本,因為臨時 Unicode 字串通常是在內部創建的。 為提高效率,請盡可能使用 Unicode 版本。

> [!NOTE]
> 由於在 Visual Studio .NET 中實現了改進的`bstr = L"String2" + bstr;`查找行為, 因此,在以前的版本中可能編譯的代碼`bstr = CStringW(L"String2") + bstr`(如 )應作為 實現。

有關使用`CComBSTR`時的注意事項清單,請參閱[使用 CComBSTR 程式設計](../../atl/programming-with-ccombstr-atl.md)。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccombstrappend"></a><a name="append"></a>CComBSTR::附錄

將*lpsz*或*bstrSrc*的 BSTR 成員m_str [。](#m_str)

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>參數

*布斯特施爾*<br/>
[在]要`CComBSTR`追加的物件。

*ch*<br/>
[在]要追加的字元。

*lpsz*<br/>
[在]要追加的零端接字串。 您可以通過 LPCOLESTR 重載傳遞 Unicode 字串,也可以通過 LPCSTR 版本傳遞 ANSI 字串。

*nLen*<br/>
[在]從*lpsz*到追加的字元數。

### <a name="return-value"></a>傳回值

成功S_OK或任何標準的 HRESULT 錯誤值。

### <a name="remarks"></a>備註

在追加之前,ANSI 字串將轉換為 Unicode。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

## <a name="ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR::附錄BSTR

將指定的 BSTR 新增到[m_str](#m_str)。

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
[在]要追加的 BSTR。

### <a name="return-value"></a>傳回值

成功S_OK或任何標準的 HRESULT 錯誤值。

### <a name="remarks"></a>備註

不要將普通寬字元字串傳遞給此方法。 編譯器無法捕獲錯誤,並且將發生運行時錯誤。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

## <a name="ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR::附加位元組

將指定的位元組數追加[到m_str](#m_str)而不進行轉換。

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>參數

*lpsz*<br/>
[在]指向要追加的位元組的指標。

*P*<br/>
[在]要追加的位元組數。

### <a name="return-value"></a>傳回值

成功S_OK或任何標準的 HRESULT 錯誤值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

## <a name="ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR::ArraytoBSTR

釋放`CComBSTR`物件中保留的任何現有字串,然後從安全陣列中每個元素的第一個字元創建一個 BSTR 並將其`CComBSTR`附加到 物件。

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>參數

*pSrc*<br/>
[在]包含用於建立字串的元素的安全陣列。

### <a name="return-value"></a>傳回值

成功S_OK或任何標準的 HRESULT 錯誤值。

## <a name="ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR::配置BSTR

將 BSTR 分配給[m_str](#m_str)。

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>參數

*布斯特施爾*<br/>
[在]要分配給當前`CComBSTR`物件的 BSTR。

### <a name="return-value"></a>傳回值

成功S_OK或任何標準的 HRESULT 錯誤值。

## <a name="ccombstrattach"></a><a name="attach"></a>CComBSTR::附加

通過將`CComBSTR`[m_str](#m_str)成員設定為*src,* 將 BSTR 附加到物件。

```cpp
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>參數

*src*<br/>
[在]要附加到物件的 BSTR。

### <a name="remarks"></a>備註

不要將普通寬字元字串傳遞給此方法。 編譯器無法捕獲錯誤,並且將發生運行時錯誤。

> [!NOTE]
> 如果`m_str`為非 NULL,則此方法將斷言。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR:BSTRToarray

創建基於零的一維安全陣列,其中陣列的每個元素都是物件中的`CComBSTR`字元。

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>參數

*ppArray*<br/>
[出]指向用於保存函數結果的安全陣組的指標。

### <a name="return-value"></a>傳回值

成功S_OK或任何標準的 HRESULT 錯誤值。

## <a name="ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR:位元組長度

返回`m_str`中的 位元組數,不包括終止空字元。

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>傳回值

[m_str](#m_str)成員的長度(以位元組為單位)。

### <a name="remarks"></a>備註

如果為`m_str`NULL,則返回 0。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

## <a name="ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR:CComBSTR

建構函式。 預設建構函數將[m_str](#m_str)成員設定為 NULL。

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
[在]要從*sz*複製的字元數`CComBSTR`或 以 字元 表示的初始大小。

*深圳*<br/>
[in] 要複製的字串。 Unicode 版本指定 LPCOLESTR;ANSI 版本指定 LPCSTR。

*pSrc*<br/>
[in] 要複製的字串。 Unicode 版本指定 LPCOLESTR;ANSI 版本指定 LPCSTR。

*src*<br/>
[in] `CComBSTR` 物件。

*guid*<br/>
[在]對結構的`GUID`引用。

### <a name="remarks"></a>備註

複製建構函數將設置`m_str`到*src*的 BSTR 成員的副本。 建構`REFGUID`函數使用 並將 GUID 轉換`StringFromGUID2`為字串 並儲存結果。

其他建構函式會將 `m_str` 設為所指定字串的複本。 如果傳遞*nSize 的值*,則只複製*nSize*字元,後跟終止空字元。

`CComBSTR` 支援移動語意。 您可以使用移動建構函式 (採用右值參考的建構函式 (`&&`)) 來建立新的物件，其使用的基本資料與您當作引數傳入之舊物件相同，無需額外複製物件。

解構函式會釋放 `m_str` 所指向的字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

## <a name="ccombstrccombstr"></a><a name="dtor"></a>CComBSTR:*CComBSTR

解構函式。

```
~CComBSTR();
```

### <a name="remarks"></a>備註

解構函式會釋放 `m_str` 所指向的字串。

## <a name="ccombstrcopy"></a><a name="copy"></a>CComBSTR:複製

分配並傳回 的`m_str`複本 。

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>傳回值

[m_str](#m_str)成員的副本。 如果`m_str`為 NULL,則傳回 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

## <a name="ccombstrcopyto"></a><a name="copyto"></a>CComBSTR::複製到

通過 參數分配並返回[m_str](#m_str)的副本。

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>參數

*pbstr*<br/>
[出]傳回此方法分配的字串的 BSTR 的位址。

*普瓦爾德斯特*<br/>
[出]要返回此方法分配的字串的 VARIANT 的位址。

### <a name="return-value"></a>傳回值

指示副本成功或失敗的標準 HRESULT 值。

### <a name="remarks"></a>備註

呼叫此方法後 *,pvarDest*指向的 VARIANT 將稱為類型VT_BSTR。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

## <a name="ccombstrdetach"></a><a name="detach"></a>CComBSTR::D

從`CComBSTR`物件`m_str`分離[m_str](#m_str)並設定為 NULL。

```
BSTR Detach() throw();
```

### <a name="return-value"></a>傳回值

與`CComBSTR`物件關聯的 BSTR。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

## <a name="ccombstrempty"></a><a name="empty"></a>CComBSTR:空

釋放[m_str](#m_str)成員。

```cpp
void Empty() throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

## <a name="ccombstrlength"></a><a name="length"></a>CComBSTR:長度

傳回`m_str`的字元數,不包括終止空字元。

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>傳回值

[m_str](#m_str)成員的長度。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

## <a name="ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR::載入字串

載入*nID*指定的字串資源並將其儲存在此物件中。

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>參數

請參考 Windows SDK 中[載入字串](/windows/win32/api/winuser/nf-winuser-loadstringw)。

### <a name="return-value"></a>傳回值

如果已成功載入字串,則返回 TRUE;如果字串已成功載入,則返回 TRUE。否則,返回 FALSE。

### <a name="remarks"></a>備註

第一個函數通過*hInst*參數從您識別的模組載入資源。 第二個函數從與本專案中使用的[CComModule](../../atl/reference/ccommodule-class.md)派生物件關聯的資源模組中載入資源。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

## <a name="ccombstrm_str"></a><a name="m_str"></a>CComBSTR:m_str

包含與`CComBSTR`物件關聯的 BSTR。

```
BSTR m_str;
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

## <a name="ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR::操作員BSTR

將`CComBSTR`物件強制轉換為 BSTR。

```
operator BSTR() const throw();
```

### <a name="remarks"></a>備註

允許您將物件傳遞給`CComBSTR`具有 **[in] BSTR**參數的函數。

### <a name="example"></a>範例

請參閱[CComBSTR 的範例::m_str](#m_str)。

## <a name="ccombstroperator-"></a><a name="operator_not"></a>CComBSTR::操作員!

檢查 BSTR 字串是否為 NULL。

```
bool operator!() const throw();
```

### <a name="return-value"></a>傳回值

如果[m_str](#m_str)成員為 NULL,則返回 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此運算元僅檢查 NULL 值,而不是檢查空字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR::操作員!*

返回[運算子 #](#operator_eq_eq)的邏輯相反。

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>參數

*布斯特施爾*<br/>
[in] `CComBSTR` 物件。

*皮茨斯爾克*<br/>
[在]零端接字串。

*nNull*<br/>
[在]必須為 NULL。

### <a name="return-value"></a>傳回值

如果要比較的項不等於物件,`CComBSTR`則返回 TRUE;否則,返回 FALSE。

### <a name="remarks"></a>備註

`CComBSTR`在使用者的預設區域設置的上下文中以文本方式進行比較。 最後的比較運算子只是將包含的字串與 NULL 進行比較。

## <a name="ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR::操作員&amp;

返回存儲在[m_str](#m_str)成員中的 BSTR 位址。

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>備註

`CComBstr operator &`具有與其關聯的特殊斷言,以幫助識別記憶體洩漏。 當成員初始化時,`m_str`程式將斷言。 創建此斷言是為了識別程式師使用`& operator`在不釋放 的第一個分配`m_str`的情況下向 成員分配新`m_str`值的情況。 如果`m_str`等於 NULL,則程式假定尚未分配m_str。 在這種情況下,程式不會斷言。

默認情況下,未啟用此斷言。 定義ATL_CCOMBSTR_ADDRESS_OF_ASSERT以啟用此斷言。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR::操作員 |

將字串追加到物件。 `CComBSTR`

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>參數

*布斯特施爾*<br/>
[在]要`CComBSTR`追加的物件。

*皮茨斯爾克*<br/>
[在]要追加的零端接字串。

### <a name="remarks"></a>備註

`CComBSTR`在使用者的預設區域設置的上下文中以文本方式進行比較。 LPCOLESTR 比較`memcmp`使用 每個字串中的原始數據來完成。 創建*pszSrc*的臨時 Unicode 副本後,以相同的方式執行 LPCSTR 比較。 最後的比較運算子只是將包含的字串與 NULL 進行比較。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

## <a name="ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR::操作員&lt;

將`CComBSTR`和字串進行比較。

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>傳回值

如果要比較的項小於物件,`CComBSTR`則返回 TRUE;否則,返回 FALSE。

### <a name="remarks"></a>備註

比較使用使用者的預設區域設置執行。

## <a name="ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR::操作員 |

將[m_str](#m_str)成員設定為*pSrc*的副本或*src*的 BSTR 成員的副本。 移動分配運算符移動`src`而不複製它。

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>備註

*pSrc*參數為 Unicode 版本指定 LPCOLESTR,為 ANSI 版本指定 LPCSTR。

### <a name="example"></a>範例

請參考[CComBSTR 的範例:複製](#copy)。

## <a name="ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR::操作員 |

將`CComBSTR`和字串進行比較。 `CComBSTR`在使用者的預設區域設置的上下文中以文本方式進行比較。

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>參數

*布斯特施爾*<br/>
[in] `CComBSTR` 物件。

*皮茨斯爾克*<br/>
[在]零端接字串。

*nNull*<br/>
[在]必須為 NULL。

### <a name="return-value"></a>傳回值

如果要比較的項等於物件,`CComBSTR`則返回 TRUE;否則,返回 FALSE。

### <a name="remarks"></a>備註

最後的比較運算子只是將包含的字串與 NULL 進行比較。

## <a name="ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR::操作員&gt;

將`CComBSTR`和字串進行比較。

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>傳回值

如果要比較的項大於物件,`CComBSTR`則返回 TRUE;否則,返回 FALSE。

### <a name="remarks"></a>備註

比較使用使用者的預設區域設置執行。

## <a name="ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR:從串流讀閱讀

將[m_str](#m_str)成員設定到指定流中包含的 BSTR。

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>參數

*pStream*<br/>
[在]指向流中包含數據的[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`ReadToStream`要求當前位置的流內容與[WriteToStream](#writetostream)呼叫時寫入的資料格式相容。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

## <a name="ccombstrtolower"></a><a name="tolower"></a>CComBSTR::到下

將包含的字串轉換為小寫。

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

有關如何`CharLowerBuff`執行轉換的詳細資訊,請參閱。

## <a name="ccombstrtoupper"></a><a name="toupper"></a>CComBSTR::上部

將包含的字串轉換為大寫。

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

有關如何`CharUpperBuff`執行轉換的詳細資訊,請參閱。

## <a name="ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR::寫入流

將[m_str](#m_str)成員保存到流中。

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>參數

*pStream*<br/>
[在]指向流上的[IStream](/windows/win32/api/objidl/nn-objidl-istream)介面的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

您可以使用[ReadFromStream](#readfromstream)函數從流的內容中重新創建 BSTR。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[ATL 與 MFC 字串轉換巨集](string-conversion-macros.md)
