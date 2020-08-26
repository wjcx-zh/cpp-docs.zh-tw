---
title: CStringT 類別
ms.date: 03/27/2019
f1_keywords:
- CStringT
- ATLSTR/ATL::CStringT
- ATLSTR/ATL::CStringT::CStringT
- ATLSTR/ATL::CStringT::AllocSysString
- ATLSTR/ATL::CStringT::AnsiToOem
- ATLSTR/ATL::CStringT::AppendFormat
- ATLSTR/ATL::CStringT::Collate
- ATLSTR/ATL::CStringT::CollateNoCase
- ATLSTR/ATL::CStringT::Compare
- ATLSTR/ATL::CStringT::CompareNoCase
- ATLSTR/ATL::CStringT::Delete
- ATLSTR/ATL::CStringT::Find
- ATLSTR/ATL::CStringT::FindOneOf
- ATLSTR/ATL::CStringT::Format
- ATLSTR/ATL::CStringT::FormatMessage
- ATLSTR/ATL::CStringT::FormatMessageV
- ATLSTR/ATL::CStringT::FormatV
- ATLSTR/ATL::CStringT::GetEnvironmentVariable
- ATLSTR/ATL::CStringT::Insert
- ATLSTR/ATL::CStringT::Left
- ATLSTR/ATL::CStringT::LoadString
- ATLSTR/ATL::CStringT::MakeLower
- ATLSTR/ATL::CStringT::MakeReverse
- ATLSTR/ATL::CStringT::MakeUpper
- ATLSTR/ATL::CStringT::Mid
- ATLSTR/ATL::CStringT::OemToAnsi
- ATLSTR/ATL::CStringT::Remove
- ATLSTR/ATL::CStringT::Replace
- ATLSTR/ATL::CStringT::ReverseFind
- ATLSTR/ATL::CStringT::Right
- ATLSTR/ATL::CStringT::SetSysString
- ATLSTR/ATL::CStringT::SpanExcluding
- ATLSTR/ATL::CStringT::SpanIncluding
- ATLSTR/ATL::CStringT::Tokenize
- ATLSTR/ATL::CStringT::Trim
- ATLSTR/ATL::CStringT::TrimLeft
- ATLSTR/ATL::CStringT::TrimRight
- CSTRINGT/CStringT
- CSTRINGT/CStringT::CStringT
- CSTRINGT/CStringT::AllocSysString
- CSTRINGT/CStringT::AnsiToOem
- CSTRINGT/CStringT::AppendFormat
- CSTRINGT/CStringT::Collate
- CSTRINGT/CStringT::CollateNoCase
- CSTRINGT/CStringT::Compare
- CSTRINGT/CStringT::CompareNoCase
- CSTRINGT/CStringT::Delete
- CSTRINGT/CStringT::Find
- CSTRINGT/CStringT::FindOneOf
- CSTRINGT/CStringT::Format
- CSTRINGT/CStringT::FormatMessage
- CSTRINGT/CStringT::FormatMessageV
- CSTRINGT/CStringT::FormatV
- CSTRINGT/CStringT::GetEnvironmentVariable
- CSTRINGT/CStringT::Insert
- CSTRINGT/CStringT::Left
- CSTRINGT/CStringT::LoadString
- CSTRINGT/CStringT::MakeLower
- CSTRINGT/CStringT::MakeReverse
- CSTRINGT/CStringT::MakeUpper
- CSTRINGT/CStringT::Mid
- CSTRINGT/CStringT::OemToAnsi
- CSTRINGT/CStringT::Remove
- CSTRINGT/CStringT::Replace
- CSTRINGT/CStringT::ReverseFind
- CSTRINGT/CStringT::Right
- CSTRINGT/CStringT::SetSysString
- CSTRINGT/CStringT::SpanExcluding
- CSTRINGT/CStringT::SpanIncluding
- CSTRINGT/CStringT::Tokenize
- CSTRINGT/CStringT::Trim
- CSTRINGT/CStringT::TrimLeft
- CSTRINGT/CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
ms.openlocfilehash: 3e6d61bdf296e85bee5d41ec2131fa3d83122c2b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832083"
---
# <a name="cstringt-class"></a>CStringT 類別

此類別代表 `CStringT` 物件。

## <a name="syntax"></a>語法

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>參數

*BaseType*<br/>
字串類別的字元類型。 可以是下列其中一項：

- **`char`**)  (ANSI 字元字串。

- **`wchar_t`** Unicode 字元字串的 () 。

- TCHAR ANSI 和 Unicode 字元字串的 () 。

*StringTraits*<br/>
判斷字串類別是否需要 C 執行時間 (CRT) 程式庫支援，以及字串資源所在的位置。 可以是下列其中一項：

- **StrTraitATL< wchar_t** &#124; **`char`** &#124; **TCHAR、ChTraitsCRT< wchar_t** &#124; **`char`** &#124; **TCHAR > >**

   類別需要 CRT 支援，並且會在 `m_hInstResource` (應用程式模組類別的成員) 中所指定的模組中搜尋資源字串。

- **StrTraitATL< wchar_t** &#124; **`char`** &#124; **TCHAR、ChTraitsOS< wchar_t** &#124; **`char`** &#124; **TCHAR > >**

   類別不需要 CRT 支援，並且會在 `m_hInstResource` (應用程式模組類別的成員) 所指定的模組中搜尋資源字串。

- **StrTraitMFC< wchar_t** &#124; **`char`** &#124; **TCHAR、ChTraitsCRT< wchar_t** &#124; **`char`** &#124; **TCHAR > >**

   類別需要 CRT 支援，並使用標準 MFC 搜尋演算法來搜尋資源字串。

- **StrTraitMFC< wchar_t** &#124; **`char`** &#124; **TCHAR、ChTraitsOS< wchar_t** &#124; **`char`** &#124; **TCHAR > >**

   類別不需要 CRT 支援，而且會使用標準的 MFC 搜尋演算法來搜尋資源字串。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CStringT：： CStringT](#cstringt)|`CStringT`以各種方式來建立物件。|
|[CStringT：： ~ CStringT](#_dtorcstringt)|終結 `CStringT` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStringT：： AllocSysString](#allocsysstring)|從資料配置 BSTR `CStringT` 。|
|[CStringT：： AnsiToOem](#ansitooem)|進行從 ANSI 字元集到 OEM 字元集的就地轉換。|
|[CStringT：： Stringbuilder.appendformat](#appendformat)|將格式化資料附加至現有的 `CStringT` 物件。|
|[CStringT：： Collate](#collate)|比較兩個字串 (區分大小寫，使用地區設定特有的資訊) 。|
|[CStringT：： CollateNoCase](#collatenocase)|比較兩個字串 (不區分大小寫，使用地區設定特有的資訊) 。|
|[CStringT：： Compare](#compare)|比較兩個字串 (區分大小寫的) 。|
|[CStringT：： CompareNoCase](#comparenocase)|比較兩個字串 (不區分大小寫) 。|
|[CStringT：:D elete](#delete)|從字串中刪除一個或幾個字元。|
|[CStringT：： Find](#find)|在較大的字串中尋找字元或子字串。|
|[CStringT：： FindOneOf](#findoneof)|從集合中尋找第一個相符的字元。|
|[CStringT：： Format](#format)|將字串格式化為 `sprintf` 。|
|[CStringT：： FormatMessage](#formatmessage)|格式化訊息字串。|
|[CStringT：： FormatMessageV](#formatmessagev)|使用變數引數清單來格式化訊息字串。|
|[CStringT：： FormatV](#formatv)|使用引數的變數清單來格式化字串。|
|[CStringT：： GetEnvironmentVariable](#getenvironmentvariable)|將字串設定為指定之環境變數的值。|
|[CStringT：： Insert](#insert)|在字串內的指定索引處插入單一字元或子字串。|
|[CStringT：： Left](#left)|解壓縮字串的左邊部分。|
|[CStringT：： Loadstring 時](#loadstring)|`CStringT`從 Windows 資源載入現有的物件。|
|[CStringT：： MakeLower](#makelower)|將此字串中的所有字元轉換成小寫字元。|
|[CStringT：： MakeReverse](#makereverse)|反轉字串。|
|[CStringT：： MakeUpper](#makeupper)|將此字串中的所有字元轉換成大寫字元。|
|[CStringT：： Mid](#mid)|解壓縮字串的中間部分。|
|[CStringT：： OemToAnsi](#oemtoansi)|進行從 OEM 字元集到 ANSI 字元集的就地轉換。|
|[CStringT：： Remove](#remove)|從字串中移除指定的字元。|
|[CStringT：： Replace](#replace)|以其他字元取代指定的字元。|
|[CStringT：： ReverseFind](#reversefind)|尋找較大字串內的字元;從結尾開始。|
|[CStringT：： Right](#right)|解壓縮字串的右側部分。|
|[CStringT：： SetSysString](#setsysstring)|使用物件的資料，設定現有的 BSTR 物件 `CStringT` 。|
|[CStringT：： SpanExcluding](#spanexcluding)|從字串（開頭為第一個字元）解壓縮字元，而不在所識別的字元集中 `pszCharSet` 。|
|[CStringT：： SpanIncluding](#spanincluding)|解壓縮只包含集合中之字元的子字串。|
|[CStringT：： Token 化](#tokenize)|在目標字串中解壓縮指定的標記。|
|[CStringT：： Trim](#trim)|修剪字串中所有開頭和尾端空白字元。|
|[CStringT：： TrimLeft](#trimleft)|修剪字串中的前置空白字元。|
|[CStringT：： TrimRight](#trimright)|修剪字串中的尾端空白字元。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[CStringT：： operator =](#operator_eq)|將新值指派給 `CStringT` 物件。|
|[CStringT：： operator +](#operator_add)|串連兩個字串或字元和字串。|
|[CStringT：： operator + =](#operator_add_eq)|將新字串串連至現有字串的結尾。|
|[CStringT：： operator = =](#operator_eq_eq)|判斷兩個字串在邏輯上是否相等。|
|[CStringT：： operator！ =](#operator_neq)|判斷兩個字串在邏輯上是否不相等。|
|[CStringT：： operator &lt;](#operator_lt)|判斷運算子左邊的字串是否小於右邊的字串。（）|
|[CStringT：： operator &gt;](#operator_gt)|判斷運算子左邊的字串是否大於右邊的字串。（）|
|[CStringT：： operator &lt;=](#operator_lt_eq)|判斷運算子左邊的字串是否小於或等於右邊的字串。（）|
|[CStringT：： operator &gt;=](#operator_gt_eq)|判斷運算子左邊的字串，是否大於或等於右邊的字串（string）。|

## <a name="remarks"></a>備註

`CStringT` 繼承自 [CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)。 先進的功能（例如字元操作、排序和搜尋）是由所執行 `CStringT` 。

> [!NOTE]
> `CStringT` 物件能夠擲回例外狀況。 當 `CStringT` 物件因為任何原因而用盡記憶體時，就會發生這種情況。

`CStringT`物件是由可變長度的字元序列所組成。 `CStringT` 使用類似于基本的語法提供函數和運算子。 串連和比較運算子以及簡化的記憶體管理，讓 `CStringT` 物件比一般字元陣列更容易使用。

> [!NOTE]
> 雖然可以建立 `CStringT` 包含內嵌 null 字元的實例，但我們還是建議您這樣做。 在包含內嵌 null 字元的物件上呼叫方法和運算子 `CStringT` 可能會產生非預期的結果。

藉由使用不同的 `BaseType` 和 `StringTraits` 參數組合， `CStringT` 物件可以是由 ATL 程式庫預先定義的下列類型。

如果在 ATL 應用程式中使用：

`CString`、 `CStringA` 和 `CStringW` 從 MFC DLL 匯出 ( # A0) ，而不是從使用者 dll。 這樣做的目的是為了避免 `CStringT` 定義乘法。

> [!NOTE]
> 如果您的程式碼包含 [使用 CStringT 匯出字串類別](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)中所述連結器錯誤的因應措施，您應該移除該程式碼。 已不再需要此項目。

下列字串類型可在 MFC 應用程式中使用：

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CStringA`|具有 CRT 支援的 ANSI 字元類型字串。|
|`CStringW`|具有 CRT 支援的 Unicode 字元類型字串。|
|`CString`|ANSI 和 Unicode 字元類型（含 CRT 支援）。|

下列字串類型可在定義 ATL_CSTRING_NO_CRT 的專案中使用：

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CAtlStringA`|不含 CRT 支援的 ANSI 字元類型字串。|
|`CAtlStringW`|不含 CRT 支援的 Unicode 字元類型字串。|
|`CAtlString`|不含 CRT 支援的 ANSI 和 Unicode 字元類型。|

下列字串類型可在未定義 ATL_CSTRING_NO_CRT 的專案中使用：

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CAtlStringA`|具有 CRT 支援的 ANSI 字元類型字串。|
|`CAtlStringW`|具有 CRT 支援的 Unicode 字元類型字串。|
|`CAtlString`|ANSI 和 Unicode 字元類型（含 CRT 支援）。|

`CString` 物件也具有下列特性：

- `CStringT` 由於串連作業的結果，物件可能會成長。

- `CStringT` 物件會遵循「值語義」。 `CStringT`請將物件視為實際字串，而不是字串的指標。

- 您可以自由取代函式 `CStringT` `PCXSTR` 引數的物件。

- 字串緩衝區的自訂記憶體管理。 如需詳細資訊，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="cstringt-predefined-types"></a>CStringT 預先定義的類型

因為 `CStringT` 使用樣板引數來定義 ([wchar_t](../../c-runtime-library/standard-types.md) 或 [char](../../c-runtime-library/standard-types.md)) 的字元類型，所以方法參數類型可能會很複雜。 為了簡化這個問題，我們定義了一組預先定義的類型，並在整個類別中使用 `CStringT` 。 下表列出各種類型：

|名稱|描述|
|----------|-----------------|
|`XCHAR`|單一字元 (**`wchar_t`** 或 **`char`**) 具有與物件相同的字元類型 `CStringT` 。|
|`YCHAR`|單一字元 (**`wchar_t`** 或 **`char`**) 與物件相反的字元類型 `CStringT` 。|
|`PXSTR`|字元字串的指標， (**`wchar_t`** 或 **`char`**) 具有與物件相同的字元類型 `CStringT` 。|
|`PYSTR`|字元字串的指標， (**`wchar_t`** 或 **`char`**) 與物件相反的字元類型 `CStringT` 。|
|`PCXSTR`|字元字串的指標， **`const`** (**`wchar_t`** 或 **`char`**) 具有與物件相同的字元類型 `CStringT` 。|
|`PCYSTR`|字元字串的指標， **`const`** (**`wchar_t`** 或 **`char`**) 與物件相反的字元類型 `CStringT` 。|

> [!NOTE]
> 先前使用未記載之 (（例如) ）方法的程式碼， `CString` `AssignCopy` 必須取代為使用下列 (檔方法的程式碼，例如 `CStringT` `GetBuffer` 或 `ReleaseBuffer`) 。 這些方法都是繼承自 `CSimpleStringT` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>規格需求

|標頭|使用對象|
|------------|-------------|
|cstringt。h|僅限 MFC 的字串物件|
|和 atlstr.h。h|非 MFC 字串物件|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a> CStringT：： AllocSysString

配置類型 BSTR 的自動化相容字串，並將物件的內容複寫到其中 `CStringT` ，包括結束的 null 字元。

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>傳回值

新配置的字串。

### <a name="remarks"></a>備註

在 MFC 程式中，如果沒有足夠的記憶體，則會擲回 [CMemoryException 類別](../../mfc/reference/cmemoryexception-class.md) 。 在 ATL 程式中，會擲回 [CAtlException](../../atl/reference/catlexception-class.md) 。 此函數通常用來傳回自動化的字串。

通常，如果這個字串傳遞至 COM 函式作為 [in] 參數，則需要呼叫者釋放字串。 您可以使用 [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)來完成這項操作，如 Windows SDK 所述。 如需詳細資訊，請參閱為 [BSTR 配置和釋放記憶體](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)。

如需 Windows 中的 OLE 配置函數的詳細資訊，請參閱 Windows SDK 中的 [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) 。

### <a name="example"></a>範例

下列範例示範 `CStringT::AllocSysString` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a> CStringT：： AnsiToOem

將此物件中的所有字元 `CStringT` 從 ANSI 字元集轉換為 OEM 字元集。

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>備註

如果已定義 _UNICODE，則無法使用函數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a> CStringT：： Stringbuilder.appendformat

將格式化資料附加至現有的 `CStringT` 物件。

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
格式控制字元串。

*nFormatID*<br/>
包含格式控制字元串的字串資源識別碼。

*引數*<br/>
選擇性引數。

### <a name="remarks"></a>備註

此函式會格式化並在中附加一系列的字元和值 `CStringT` 。 如果根據 *pszFormat* 中的對應格式規格或 *nFormatID*所識別的字串資源來轉換和附加任何) ，則每個選擇性引數都會 (。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a> CStringT：： Collate

使用泛型文字函數比較兩個字串 `_tcscoll` 。

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
用於比較的另一個字串。

### <a name="return-value"></a>傳回值

如果字串相同，則為零; 如果這個 `CStringT` 物件小於 *psz*，則 < 0; 如果這個 `CStringT` 物件大於 *psz*>，則為0。

### <a name="remarks"></a>備註

TCHAR 中定義的泛型文字函數 `_tcscoll` 。H，會對應到 `strcoll` 、 `wcscoll` 或 `_mbscoll` ，視編譯時期所定義的字元集而定。 每個函式都會根據目前使用的字碼頁來執行字串的區分大小寫比較。 如需詳細資訊，請參閱 [strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a> CStringT：： CollateNoCase

使用泛型文字函數比較兩個字串 `_tcscoll` 。

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
用於比較的另一個字串。

### <a name="return-value"></a>傳回值

如果字串完全相同 (忽略大小寫) ，則為零 <; 如果這個 `CStringT` 物件小於 *psz* (忽略大小寫) ，則為零; 如果這個物件 `CStringT` 大於 *psz* ，> 忽略大小寫 (，則為0。

### <a name="remarks"></a>備註

TCHAR 中定義的泛型文字函數 `_tcscoll` 。H，會對應到 `stricoll` 、 `wcsicoll` 或 `_mbsicoll` ，視編譯時期所定義的字元集而定。 每個函式會根據目前使用中的字碼頁，執行字串的不區分大小寫比較。 如需詳細資訊，請參閱 [strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a> CStringT：： Compare

比較兩個字串 (區分大小寫的) 。

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>參數

*psz*<br/>
用於比較的另一個字串。

### <a name="return-value"></a>傳回值

如果字串相同，則為零; 如果這個 `CStringT` 物件小於 *psz*，則 < 0; 如果這個 `CStringT` 物件大於 *psz*>，則為0。

### <a name="remarks"></a>備註

TCHAR 中定義的泛型文字函數 `_tcscmp` 。H，會對應到 `strcmp` 、 `wcscmp` 或 `_mbscmp` ，視編譯時期所定義的字元集而定。 每個函式都會執行區分大小寫的字串比較，而且不受地區設定影響。 如需詳細資訊，請參閱 [strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)。

如果字串包含內嵌的 null，則在比較時，會將字串視為在第一個內嵌的 null 字元截斷。

### <a name="example"></a>範例

下列範例示範 `CStringT::Compare` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a> CStringT：： CompareNoCase

比較兩個字串 (不區分大小寫) 。

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
用於比較的另一個字串。

### <a name="return-value"></a>傳回值

如果字串完全相同 (忽略大小寫) ，則為零 <; 如果這個 `CStringT` 物件小於 *psz* (忽略大小寫) ，則為零; 如果這個物件 `CStringT` 大於 *psz* ，>忽略大小寫 (，則為0。

### <a name="remarks"></a>備註

TCHAR 中定義的泛型文字函數 `_tcsicmp` 。H，會對應至 `_stricmp` `_wcsicmp` 或 `_mbsicmp` ，視編譯時期所定義的字元集而定。 每個函數都會執行字串的不區分大小寫比較。 比較取決於地區設定的 LC_CTYPE 層面，但不是 LC_COLLATE。 如需詳細資訊，請參閱 [_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a> CStringT：： CStringT

建構 `CStringT` 物件。

```
CStringT() throw() :
    CThisSimpleString(StringTraits::GetDefaultManager());

explicit CStringT(IAtlStringMgr* pStringMgr) throw() :
    CThisSimpleString( pStringMgr);

CStringT(const VARIANT& varSrc);

CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);

CStringT(const CStringT& strSrc) :
    CThisSimpleString( strSrc);

operator CSimpleStringT<
                    BaseType,
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()

template <bool bMFCDLL>
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :
    CThisSimpleString( strSrc);

template <class SystemString>
CStringT(SystemString^ pString) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength) :
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());

CStringT(const YCHAR* pch, int nLength) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :
    CThisSimpleString( pch, nLength, pStringMgr);

CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);
```

### <a name="parameters"></a>參數

*Pch*<br/>
長度 *nLength*字元陣列的指標，不是以 null 結束的字元。

*nLength*<br/>
*Pch*中的字元數計數。

*>ch*<br/>
單一字元。

*pszSrc*<br/>
要複製到這個物件的以 null 終止的字串 `CStringT` 。

*pStringMgr*<br/>
物件的記憶體管理員指標 `CStringT` 。 如需 `IAtlStringMgr` 和記憶體管理的詳細資訊 `CStringT` ，請參閱 [使用 CStringT 進行記憶體管理](../../atl-mfc-shared/memory-management-with-cstringt.md)。

*strSrc*<br/>
`CStringT`要複製到這個物件中的現有物件 `CStringT` 。 如需和的詳細資訊 `CThisString` `CThisSimpleString` ，請參閱「備註」一節。

*varSrc*<br/>
要複製到這個物件的 variant 物件 `CStringT` 。

*BaseType*<br/>
字串類別的字元類型。 可以是下列其中一項：

**`char`**)  (ANSI 字元字串。

**`wchar_t`** Unicode 字元字串的 () 。

TCHAR ANSI 和 Unicode 字元字串的 () 。

*bMFCDLL*<br/>
布林值，指定專案是否為 MFC DLL (TRUE) 或不 (FALSE) 。

*[Systemstring]*<br/>
必須是 `System::String` ，而且必須使用/clr 編譯專案。

*pString*<br/>
物件的控制碼 `CStringT` 。

### <a name="remarks"></a>備註

因為這些函式會將輸入資料複製到新配置的儲存區，所以您應該知道可能會產生記憶體例外狀況。 請注意，其中有些函式會作為轉換函數。 例如，這可讓您替代 `CStringT` 預期物件的 LPTSTR。

- `CStringT` ( `LPCSTR` `lpsz` ) ： `CStringT` 從 ANSI 字串中建立 Unicode。 您也可以使用此函式來載入字串資源，如下列範例所示。

- `CStringT(``LPCWSTR` `lpsz` ) ： `CStringT` 從 Unicode 字串結構。

- `CStringT` ( `const unsigned char*` `psz` ) ：可讓您 `CStringT` 從的指標來建立 **`unsigned char`** 。

> [!NOTE]
> 定義 _CSTRING_DISABLE_NARROW_WIDE_CONVERSION 宏，以關閉 ANSI 和 Unicode 字串之間的隱含字串轉換。 宏從支援轉換的編譯的函式中排除。

請注意， *strSrc* 參數可以是 `CStringT` 或 `CThisSimpleString` 物件。 若為 `CStringT` ，請使用其中一個預設具現化 (`CString` 、 `CStringA` 或 `CStringW`) ; 若是 `CThisSimpleString` ，請使用 **`this`** 指標。 `CThisSimpleString` 宣告 [CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)的實例，這是較小的字串類別，其內建功能比 `CStringT` 類別少。

多載運算子會 `CSimpleStringT<>&()` `CStringT` 從宣告中建立物件 `CSimpleStringT` 。

> [!NOTE]
> 雖然可以建立 `CStringT` 包含內嵌 null 字元的實例，但我們還是建議您這樣做。 在包含內嵌 null 字元的物件上呼叫方法和運算子 `CStringT` 可能會產生非預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a> CStringT：： ~ CStringT

終結 `CStringT` 物件。

```
~CStringT() throw();
```

### <a name="remarks"></a>備註

終結 `CStringT` 物件。

## <a name="cstringtdelete"></a><a name="delete"></a> CStringT：:D elete

從指定索引處的字元開始，刪除字串中的字元。

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
要刪除之物件中第一個字元的以零為基底的索引 `CStringT` 。

*nCount*<br/>
要移除的字元數。

### <a name="return-value"></a>傳回值

已變更之字串的長度。

### <a name="remarks"></a>備註

如果 *nCount* 的長度超過字串，則會移除字串的其餘部分。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a> CStringT：： Find

在此字串中搜尋字元或子字串的第一個相符項。

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>參數

*pszSub*<br/>
要搜尋的子字串。

*iStart*<br/>
字串中要開始搜尋的字元索引，或從開頭開始算起的0。

*>ch*<br/>
要搜尋的單一字元。

### <a name="return-value"></a>傳回值

此物件中第一個字元的以零為起始的索引 `CStringT` ，這個物件符合要求的子字串或字元; 如果找不到子字串或字元，則為-1。

### <a name="remarks"></a>備註

函式已多載，以接受 (類似于執行時間函式 `strchr`) 和字串 (類似) 的單一字元 `strstr` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a> CStringT：： FindOneOf

搜尋此字串中是否有符合 *pszCharSet*中所含任何字元的第一個字元。

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
包含要比對之字元的字串。

### <a name="return-value"></a>傳回值

這個字串中第一個字元的以零為起始的索引，也是在 *pszCharSet*中;如果沒有相符的，則為-1。

### <a name="remarks"></a>備註

尋找 *pszCharSet*中任何字元的第一個出現位置。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a> CStringT：： Format

將格式化的資料以 `CStringT` [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) 將資料格式化成 C 樣式字元陣列的相同方式來寫入。

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>參數

*nFormatID*<br/>
包含格式控制字元串的字串資源識別碼。

*pszFormat*<br/>
格式控制字元串。

*引數*<br/>
選擇性引數。

### <a name="remarks"></a>備註

此函式會在中格式化並儲存一連串的字元和值 `CStringT` 。 每個選擇性引數都會 (是否根據 *pszFormat* 中的對應格式規格，或 *nFormatID*所識別的字串資源來轉換和輸出任何) 。

如果字串物件本身以參數形式提供給，則呼叫會失敗 `Format` 。 例如，下列程式碼會導致無法預期的結果：

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

如需詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a> CStringT：： FormatMessage

格式化訊息字串。

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>參數

*nFormatID*<br/>
字串資源識別碼，包含未格式化的郵件內文。

*pszFormat*<br/>
指向格式控制字元串。 系統會掃描它以進行插入，並據以格式化。 格式字串類似于執行時間函數 *printf*樣式的格式字串，但它允許以任意順序插入參數。

*引數*<br/>
選擇性引數。

### <a name="remarks"></a>備註

函數需要訊息定義做為輸入。 訊息定義取決於 *pszFormat* 或 *nFormatID*所識別的字串資源。 函式會將格式化的郵件內文複製到 `CStringT` 物件，並在要求時處理任何內嵌的插入序列。

> [!NOTE]
> `FormatMessage` 嘗試配置新格式化字串的系統記憶體。 如果嘗試失敗，則會自動擲回記憶體例外狀況。

每個插入在 *pszFormat* 或 *nFormatID* 參數後面都必須有對應的參數。 在郵件內文中，有數個 escape 序列支援動態格式化訊息。 如需詳細資訊，請參閱 Windows SDK 中的 Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 函數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a> CStringT：： FormatMessageV

使用變數引數清單來格式化訊息字串。

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
指向格式控制字元串。 系統會掃描它以進行插入，並據以格式化。 格式字串類似于執行時間函 `printf` 式樣式的格式字串，但它允許以任意順序插入參數。

*pArgList*<br/>
引數清單的指標。

### <a name="remarks"></a>備註

函數需要訊息定義做為輸入（由 *pszFormat*所決定）。 函式會將格式化的郵件內文和引數的變數清單複製到 `CStringT` 物件，並在要求時處理任何內嵌的插入序列。

> [!NOTE]
> `FormatMessageV` 呼叫 [CStringT：： FormatMessage](#formatmessage)，其會嘗試配置新格式化字串的系統記憶體。 如果嘗試失敗，則會自動擲回記憶體例外狀況。

如需詳細資訊，請參閱 Windows SDK 中的 Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 函數。

## <a name="cstringtformatv"></a><a name="formatv"></a> CStringT：： FormatV

使用變數引數清單來格式化訊息字串。

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
指向格式控制字元串。 系統會掃描它以進行插入，並據以格式化。 格式字串類似于執行時間函 `printf` 式樣式的格式字串，但它允許以任意順序插入參數。

*參數*<br/>
引數清單的指標。

### <a name="remarks"></a>備註

以 `CStringT` 將 `vsprintf_s` 資料格式化成 C 樣式字元陣列的相同方式，將格式化字串和引數的變數清單寫入字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a> CStringT：： GetEnvironmentVariable

將字串設定為指定之環境變數的值。

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>參數

*pszVar*<br/>
指定環境變數之以 null 結束的字串指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

從呼叫進程的環境區塊抓取指定之變數的值。 值的格式為以 null 結束的字元字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a> CStringT：： Insert

在字串內的指定索引處插入單一字元或子字串。

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
要在其上進行插入的字元索引。

*psz*<br/>
要插入的子字串指標。

*>ch*<br/>
要插入的字元。

### <a name="return-value"></a>傳回值

已變更之字串的長度。

### <a name="remarks"></a>備註

*IIndex*參數會識別要移動以騰出空間給字元或子字串的第一個字元。 如果 *nIndex* 為零，則會在整個字串之前插入插入。 如果 *nIndex* 大於字串的長度，函數會串連目前的字串和 *ch* 或 *psz*所提供的新資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a> CStringT：： Left

從這個物件中解壓縮最左邊的 *nCount* 字元 `CStringT` ，並傳回已解壓縮之子字串的複本。

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>參數

*nCount*<br/>
要從 `CStringT` 這個物件擷取的字元數。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 傳回的 `CStringT` 物件可以是空的。

### <a name="remarks"></a>備註

如果 *nCount* 超過字串長度，則會解壓縮整個字串。 `Left` 類似於 Basic `Left` 函式。

針對 (MBCS) 的多重位元組字元集， *nCount* 會將每個8位序列視為一個字元，讓 *nCount* 傳回多位元組字元數乘以二。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a> CStringT：： Loadstring 時

讀取由 *nID*識別的 Windows 字串資源至現有的 `CStringT` 物件。

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
模組實例的控制碼。

*nID*<br/>
Windows 字串資源識別碼。

*wLanguageID*<br/>
字串資源的語言。

### <a name="return-value"></a>傳回值

如果資源載入成功，則為非零;否則為0。

### <a name="remarks"></a>備註

使用指定的 language (*wLanguage*) ，從指定的模組載入字串資源 (*NID*)  (*hInstance*) 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a> CStringT：： MakeLower

將 `CStringT` 物件轉換為小寫字串。

```
CStringT& MakeLower();
```

### <a name="return-value"></a>傳回值

產生的小寫字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a> CStringT：： MakeReverse

反轉物件中字元的順序 `CStringT` 。

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>傳回值

產生的反轉字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a> CStringT：： MakeUpper

將 `CStringT` 物件轉換為大寫字串。

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>傳回值

產生的大寫字串。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a> CStringT：： Mid

從這個物件解壓縮長度 *nCount* 字元的子字串 `CStringT` ，從位置 *iFirst* 開始 (以零為基礎的) 。

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>參數

*iFirst*<br/>
此物件中第一個字元的以零為基底的索引，這個 `CStringT` 物件是要包含在解壓縮的子字串中。

*nCount*<br/>
要從 `CStringT` 這個物件擷取的字元數。 如果未提供此參數，則會解壓縮字串的其餘部分。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 請注意，傳回的 `CStringT` 物件可能是空的。

### <a name="remarks"></a>備註

函數會傳回已解壓縮之子字串的複本。 `Mid` 類似于基本的 Mid 函數 (但基本中的索引是以一為基礎的) 。

針對 (MBCS) 的多位元組字元集， *nCount* 指的是每個8位字元;也就是說，一個多位元組字元中的潛在客戶和後隨位元組會計算為兩個字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a> CStringT：： OemToAnsi

將此物件中的所有字元 `CStringT` 從 OEM 字元集轉換為 ANSI 字元集。

```cpp
void OemToAnsi();
```

### <a name="remarks"></a>備註

如果已定義 _UNICODE，則無法使用此函數。

### <a name="example"></a>範例

請參閱 [CStringT：： AnsiToOem](#ansitooem)的範例。

## <a name="cstringtoperator-"></a><a name="operator_eq"></a> CStringT：： operator =

將新值指派給字串。

```
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);

CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>參數

*strSrc*<br/>
`CStringT`要指派給這個字串的。

*str*<br/>
`CThisSimpleString` 物件的參考。

*bMFCDLL*<br/>
布林值，指定專案是否為 MFC DLL。

*BaseType*<br/>
字串基底類型。

*無 功*<br/>
要指派給這個字串的 variant 物件。

*>ch*<br/>
要指派給字串的 ANSI 或 Unicode 字元。

*pszSrc*<br/>
要指派的原始字串指標。

### <a name="remarks"></a>備註

指派運算子接受其他 `CStringT` 物件、字元指標或單一字元。 您應該注意，當您使用此運算子時，可能會發生記憶體例外狀況，因為可以配置新的儲存體。

如需的詳細資訊 `CThisSimpleString` ，請參閱 [CStringT：： CStringT](#cstringt)的備註一節。

> [!NOTE]
> 雖然可以建立 `CStringT` 包含內嵌 null 字元的實例，但我們還是建議您這樣做。 在包含內嵌 null 字元的物件上呼叫方法和運算子 `CStringT` 可能會產生非預期的結果。

## <a name="cstringtoperator-"></a><a name="operator_add"></a> CStringT：： operator +

串連兩個字串或字元和字串。

```
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>參數

*ch1*<br/>
要與字串串連的 ANSI 或 Unicode 字元。

*ch2*<br/>
要與字串串連的 ANSI 或 Unicode 字元。

*str1*<br/>
`CStringT`要與字串或字串連的。

*str2*<br/>
`CStringT`要與字串或字串連的。

*psz1*<br/>
要與字串或字串連之以 null 結束的字串指標。

*psz2*<br/>
要與字串或字串連的字串指標。

### <a name="remarks"></a>備註

函數有七種多載形式 `CStringT::operator+` 。 第一個版本會串連兩個現有 `CStringT` 的物件。 接下來的兩個會串連 `CStringT` 物件和以 null 終止的字串。 接下來的兩個會串連 `CStringT` 物件和 ANSI 字元。 最後兩個會串連 `CStringT` 物件和 Unicode 字元。

> [!NOTE]
> 雖然可以建立 `CStringT` 包含內嵌 null 字元的實例，但我們還是建議您這樣做。 在包含內嵌 null 字元的物件上呼叫方法和運算子 `CStringT` 可能會產生非預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a> CStringT：： operator + =

將字串連到字串的結尾。

```
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```

### <a name="parameters"></a>參數

*str*<br/>
`CThisSimpleString` 物件的參考。

*bMFCDLL*<br/>
布林值，指定專案是否為 MFC DLL。

*BaseType*<br/>
字串基底類型。

*無 功*<br/>
要串連至此字串的 variant 物件。

*>ch*<br/>
要與字串串連的 ANSI 或 Unicode 字元。

*pszSrc*<br/>
要串連的原始字串指標。

*strSrc*<br/>
`CStringT`要串連至此字串的。

### <a name="remarks"></a>備註

運算子接受另一個 `CStringT` 物件、字元指標或單一字元。 您應該要注意，當您使用此串連運算子時，可能會發生記憶體例外狀況，因為可以針對新增至此物件的字元配置新的儲存體 `CStringT` 。

如需的詳細資訊 `CThisSimpleString` ，請參閱 [CStringT：： CStringT](#cstringt)的備註一節。

> [!NOTE]
> 雖然可以建立 `CStringT` 包含內嵌 null 字元的實例，但我們還是建議您這樣做。 在包含內嵌 null 字元的物件上呼叫方法和運算子 `CStringT` 可能會產生非預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a> CStringT：： operator = =

判斷兩個字串在邏輯上是否相等。

```
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>參數

*ch1*<br/>
要進行比較的 ANSI 或 Unicode 字元。

*ch2*<br/>
要進行比較的 ANSI 或 Unicode 字元。

*str1*<br/>
`CStringT`用於比較的。

*str2*<br/>
`CStringT`用於比較的。

*psz1*<br/>
要比較之以 null 結束的字串指標。

*psz2*<br/>
要比較之以 null 結束的字串指標。

### <a name="remarks"></a>備註

測試左邊的字串或字元是否等於右邊的字串或字元，並據以傳回 TRUE 或 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a> CStringT：： operator！ =

判斷兩個字串在邏輯上是否不相等。

```
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>參數

*ch1*<br/>
要與字串串連的 ANSI 或 Unicode 字元。

*ch2*<br/>
要與字串串連的 ANSI 或 Unicode 字元。

*str1*<br/>
`CStringT`用於比較的。

*str2*<br/>
`CStringT`用於比較的。

*psz1*<br/>
要比較之以 null 結束的字串指標。

*psz2*<br/>
要比較之以 null 結束的字串指標。

### <a name="remarks"></a>備註

測試左邊的字串或字元是否不等於右邊的字串或字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a> CStringT：： operator &lt;

判斷運算子左邊的字串是否小於右邊的字串。（string）

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
`CStringT`用於比較的。

*str2*<br/>
`CStringT`用於比較的。

*psz1*<br/>
要比較之以 null 結束的字串指標。

*psz2*<br/>
要比較之以 null 結束的字串指標。

### <a name="remarks"></a>備註

字串、字元和字元之間的字典比較：

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找不到任何差異，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a> CStringT：： operator &gt;

判斷運算子左邊的字串是否大於右邊的字串。（string）

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
`CStringT`用於比較的。

*str2*<br/>
`CStringT`用於比較的。

*psz1*<br/>
要比較之以 null 結束的字串指標。

*psz2*<br/>
要比較之以 null 結束的字串指標。

### <a name="remarks"></a>備註

字串、字元和字元之間的字典比較：

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a> CStringT：： operator &lt;=

判斷位於運算子左邊的字串是否小於或等於右邊的字串（string）。

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
`CStringT`用於比較的。

*str2*<br/>
`CStringT`用於比較的。

*psz1*<br/>
要比較之以 null 結束的字串指標。

*psz2*<br/>
要比較之以 null 結束的字串指標。

### <a name="remarks"></a>備註

字串、字元和字元之間的字典比較：

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a> CStringT：： operator &gt;=

判斷運算子左邊的字串，是否大於或等於右邊的字串（string）。

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
`CStringT`用於比較的。

*str2*<br/>
`CStringT`用於比較的。

*psz1*<br/>
要比較之字串的指標。

*psz2*<br/>
要比較之字串的指標。

### <a name="remarks"></a>備註

字串、字元和字元之間的字典比較：

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a> CStringT：： Remove

從字串中移除指定字元的所有實例。

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>參數

*chRemove*<br/>
要從字串移除的字元。

### <a name="return-value"></a>傳回值

從字串中移除的字元計數。 如果字串未變更，則為零。

### <a name="remarks"></a>備註

字元的比較會區分大小寫。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a> CStringT：： Replace

有兩個版本 `Replace` 。第一個版本會使用另一個子字串來取代子字串的一或多個複本。 這兩個子字串都以 null 終止。 第二個版本會使用另一個字元取代字元的一或多個複本。 這兩個版本都是在所儲存的字元資料上運作 `CStringT` 。

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>參數

*pszOld*<br/>
以 null 結束的字串指標，要由 *pszNew*取代。

*pszNew*<br/>
取代 *pszOld*之以 null 結束的字串指標。

*chOld*<br/>
要由 *chNew*取代的字元。

*chNew*<br/>
取代 *chOld*的字元。

### <a name="return-value"></a>傳回值

傳回已取代的字元或子字串實例數目，如果字串未變更，則為零。

### <a name="remarks"></a>備註

`Replace` 可以變更字串長度，因為 *pszNew* 和 *pszOld* 不一定要有相同的長度，而且可以將舊子字串的數個複本變更為新的子字串。 函數會執行區分大小寫的比對。

實例的範例 `CStringT` 包括 `CString` 、 `CStringA` 和 `CStringW` 。

若是 `CStringA` ，請 `Replace` 使用 ANSI 或多位元組 (MBCS) 個字元。 若是 `CStringW` ，則 `Replace` 適用于寬字元。

若為 `CString` ，則會根據下表中的常數是否已定義，在編譯時期選取字元資料類型。

|定義的常數|字元資料類型|
|----------------------|-------------------------|
|_UNICODE|寬字元|
|_MBCS|多位元組字元|
|兩者皆非|單一位元組字元|
|兩者|未定義|

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a> CStringT：： ReverseFind

搜尋此 `CStringT` 物件中最後一個相符的字元。

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>參數

*>ch*<br/>
要搜尋的字元。

### <a name="return-value"></a>傳回值

此物件中最後一個字元的以零為起始的索引 `CStringT` ，這個物件符合要求的字元，如果找不到字元，則為-1。

### <a name="remarks"></a>備註

函數與執行時間函數類似 `strrchr` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a> CStringT：： Right

解壓縮最後一個 (，也就是最右邊的) 從此物件 *nCount* 字元，並傳回已 `CStringT` 解壓縮之子字串的複本。

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>參數

*nCount*<br/>
要從 `CStringT` 這個物件擷取的字元數。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 請注意，傳回的 `CStringT` 物件可以是空的。

### <a name="remarks"></a>備註

如果 *nCount* 超過字串長度，則會解壓縮整個字串。 `Right` 類似于基本 `Right` 函數 (，但基本中的索引是以零為基底的) 。

針對 (MBCS) 的多位元組字元集， *nCount* 指的是每個8位字元;也就是說，一個多位元組字元中的潛在客戶和後隨位元組會計算為兩個字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a> CStringT：： SetSysString

藉由 *pbstr* 來重新配置所指向的 BSTR，並將物件的內容複寫 `CStringT` 到其中，包括 Null 字元。

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>參數

*pbstr*<br/>
字元字串的指標。

### <a name="return-value"></a>傳回值

新字串。

### <a name="remarks"></a>備註

視物件的內容而定 `CStringT` ， *pbstr* 所參考的 BSTR 值可能會變更。 如果記憶體不足，函數會擲回 `CMemoryException` 。

此函數通常用來變更以傳址方式傳遞的字串值以進行自動化。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a> CStringT：： SpanExcluding

從字串中解壓縮字元（開頭為第一個字元），而不在 *pszCharSet*所識別的字元集中。

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
轉譯為一組字元的字串。

### <a name="return-value"></a>傳回值

包含字串中不是 *pszCharSet*之字元的子字串，以字串中的第一個字元為開頭，並以字串中找到的第一個字元結尾，也就是 *pszCharSet* (也就是從字串中的第一個字元開始，而不是從字串中找到的第一個字元 *pszCharSet*) 。 如果在字串中找不到 *pszCharSet* 中的字元，則會傳回整個字串。

### <a name="remarks"></a>備註

`SpanExcluding` 從 *pszCharSet* 中解壓縮並傳回第一次出現字元之前的所有字元 (換句話說， *pszCharSet* 中的字元和字串後面的所有字元都不會) 傳回。 如果在字串中找不到來自 *pszCharSet* 的字元，則會傳回 `SpanExcluding` 整個字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a> CStringT：： SpanIncluding

從 *pszCharSet*所識別之字元集中的第一個字元開始，解壓縮字串中的字元。

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
轉譯為一組字元的字串。

### <a name="return-value"></a>傳回值

包含 *pszCharSet*字串中字元的子字串，以字串中的第一個字元開頭，並在不在 *pszCharSet*的字串中找到字元時結束。 `SpanIncluding` 如果字串中的第一個字元不在指定的集合中，則傳回空的子字串。

### <a name="remarks"></a>備註

如果字串的第一個字元不在字元集中，則會傳回 `SpanIncluding` 空字串。 否則，它會傳回集合中連續字元的序列。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a> CStringT：： Token 化

在目標字串中尋找下一個 token

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>參數

*pszTokens*<br/>
包含 token 分隔符號的字串。 這些分隔符號的順序並不重要。

*iStart*<br/>
以零為基底的索引，開始搜尋。

### <a name="return-value"></a>傳回值

`CStringT`物件，包含目前的 token 值。

### <a name="remarks"></a>備註

`Tokenize`函數會在目標字串中尋找下一個 token。 *PszTokens*中的一組字元會指定要尋找之標記的可能分隔符號。 在每次呼叫函式 `Tokenize` 時，會在 *iStart*上開始，略過前置分隔符號，並傳回 `CStringT` 包含目前權杖的物件，也就是字元的字串，直到下一個分隔符號為止。 *IStart*的值會更新為結尾分隔符號後面的位置，如果到達字串的結尾，則為-1。 您可以利用一連串的呼叫，將更多的 token 細分為目標字串的其餘部分 `Tokenize` ，並使用 *iStart* 來追蹤在字串中要讀取下一個 token 的位置。 當沒有其他權杖時，函式會傳回空字串，而 *iStart* 會設定為-1。

和 CRT token 化函式（例如 [strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)_mbstok_s_l）不同的是，不 `Tokenize` 會修改目標字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>備註

此範例的輸出如下所示：

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a> CStringT：： Trim

修剪字串中開頭和尾端的字元。

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
字串的指標，其中包含要修剪的目標字元。 *PszTarget*中所有開頭和尾端的字元都將從物件中修剪 `CStringT` 。

### <a name="return-value"></a>傳回值

傳回修剪的字串。

### <a name="remarks"></a>備註

移除下列其中一項的所有開頭和尾端位置：

- *ChTarget*所指定的字元。

- 在 *pszTargets*所指定的字串中找到的所有字元。

- 空白。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>備註

此範例的輸出如下所示：

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a> CStringT：： TrimLeft

從字串修剪開頭的字元。

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
字串的指標，其中包含要修剪的目標字元。 *PszTarget*中所有開頭出現的字元都會從物件中修剪 `CStringT` 。

### <a name="return-value"></a>傳回值

產生的修剪字串。

### <a name="remarks"></a>備註

移除下列其中一項的所有開頭和尾端位置：

- *ChTarget*所指定的字元。

- 在 *pszTargets*所指定的字串中找到的所有字元。

- 空白。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a> CStringT：： TrimRight

修剪字串中的結尾字元。

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
字串的指標，其中包含要修剪的目標字元。 *PszTarget*中所有尾端出現的字元都會從物件中修剪 `CStringT` 。

### <a name="return-value"></a>傳回值

傳回 `CStringT` 包含已修剪字串的物件。

### <a name="remarks"></a>備註

移除下列其中一項的尾端專案：

- *ChTarget*所指定的字元。

- 在 *pszTargets*所指定的字串中找到的所有字元。

- 空白。

`CStringT& TrimRight(XCHAR chTarget)`版本會接受一個字元參數，並從字串資料的結尾移除該字元的所有複本 `CStringT` 。 它會從字串的結尾開始，然後往前處理。 它會在找到不同的字元，或當 `CSTringT` 字元資料用盡時停止。

`CStringT& TrimRight(PCXSTR pszTargets)`版本接受以 null 終止的字串，其中包含要搜尋的所有不同字元。 它會移除物件中這些字元的所有複本 `CStringT` 。 它會從字串的結尾開始，然後往前處理。 當它找到不在目標字串中的字元時，或當字元資料用完時，它就會停止 `CStringT` 。 它不會嘗試比對整個目標字串與結尾的子字串 `CStringT` 。

`CStringT& TrimRight()`版本不需要任何參數。 它會修剪字串結尾的任何尾端空白字元 `CStringT` 。 空白字元可以是分行符號、空格或定位字元。

-

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)
