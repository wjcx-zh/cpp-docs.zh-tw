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
ms.openlocfilehash: a411ed54a73a0dee49ebbd9ccacbd7c6f8e69ca5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491633"
---
# <a name="cstringt-class"></a>CStringT 類別

此類別代表`CStringT`物件。

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

- **char**（適用于 ANSI 字元字串）。

- **wchar_t**（適用于 Unicode 字元字串）。

- TCHAR （適用于 ANSI 和 Unicode 字元字串）。

*StringTraits*<br/>
判斷 string 類別是否需要 C 執行時間（CRT）程式庫支援，以及字串資源所在的位置。 可以是下列其中一項：

- **StrTraitATL < wchar_t**&#124; **char** &#124; &#124; TCHAR、ChTraitsCRT < wchar_t char TCHAR > > &#124;

   類別需要 CRT 支援，並在所指定`m_hInstResource`的模組（應用程式的模組類別的成員）中搜尋資源字串。

- **StrTraitATL < wchar_t**&#124; **char** &#124; &#124; TCHAR、ChTraitsOS < wchar_t char TCHAR > > &#124;

   類別不需要 CRT 支援，而且會在所指定`m_hInstResource`的模組（應用程式的模組類別的成員）中搜尋資源字串。

- **StrTraitMFC < wchar_t**&#124; **char** &#124; &#124; TCHAR、ChTraitsCRT < wchar_t char TCHAR > > &#124;

   類別需要 CRT 支援，並使用標準 MFC 搜尋演算法來搜尋資源字串。

- **StrTraitMFC < wchar_t**&#124; **char** &#124; &#124; TCHAR、ChTraitsOS < wchar_t char TCHAR > > &#124;

   類別不需要 CRT 支援，而且會使用標準 MFC 搜尋演算法來搜尋資源字串。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|以各種方式來構造物件。`CStringT`|
|[CStringT::~CStringT](#_dtorcstringt)|終結 `CStringT` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|從`CStringT`資料配置 BSTR。|
|[CStringT::AnsiToOem](#ansitooem)|進行從 ANSI 字元集到 OEM 字元集的就地轉換。|
|[CStringT::AppendFormat](#appendformat)|將格式化的資料附加至`CStringT`現有的物件。|
|[CStringT::Collate](#collate)|比較兩個字串（區分大小寫，使用地區設定特定的資訊）。|
|[CStringT::CollateNoCase](#collatenocase)|比較兩個字串（不區分大小寫，使用地區設定特定的資訊）。|
|[CStringT::Compare](#compare)|比較兩個字串（區分大小寫）。|
|[CStringT::CompareNoCase](#comparenocase)|比較兩個字串（不區分大小寫）。|
|[CStringT::Delete](#delete)|從字串中刪除一個或多個字元。|
|[CStringT::Find](#find)|尋找較大字串中的字元或子字串。|
|[CStringT::FindOneOf](#findoneof)|從集合中尋找第一個相符的字元。|
|[CStringT::Format](#format)|將字串格式化為`sprintf` 。|
|[CStringT::FormatMessage](#formatmessage)|格式化訊息字串。|
|[CStringT::FormatMessageV](#formatmessagev)|使用可變引數清單來格式化訊息字串。|
|[CStringT::FormatV](#formatv)|使用引數的可變清單來格式化字串。|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|將字串設定為所指定環境變數的值。|
|[CStringT::Insert](#insert)|在字串中的指定索引處插入單一字元或子字串。|
|[CStringT::Left](#left)|解壓縮字串的左邊部分。|
|[CStringT::LoadString](#loadstring)|從 Windows 資源`CStringT`載入現有的物件。|
|[CStringT::MakeLower](#makelower)|將此字串中的所有字元轉換成小寫字元。|
|[CStringT::MakeReverse](#makereverse)|反轉字串。|
|[CStringT::MakeUpper](#makeupper)|將此字串中的所有字元轉換成大寫字元。|
|[CStringT::Mid](#mid)|解壓縮字串的中間部分。|
|[CStringT::OemToAnsi](#oemtoansi)|進行從 OEM 字元集到 ANSI 字元集的就地轉換。|
|[CStringT::Remove](#remove)|從字串中移除指定的字元。|
|[CStringT::Replace](#replace)|以其他字元取代指定的字元。|
|[CStringT::ReverseFind](#reversefind)|尋找較大字串中的字元;從結尾開始。|
|[CStringT::Right](#right)|解壓縮字串的右側部分。|
|[CStringT::SetSysString](#setsysstring)|使用來自`CStringT`物件的資料來設定現有的 BSTR 物件。|
|[CStringT::SpanExcluding](#spanexcluding)|從字串中，以第一個字元開頭，而不是由所識別`pszCharSet`的字元集中的字元。|
|[CStringT::SpanIncluding](#spanincluding)|解壓縮只包含集合中之字元的子字串。|
|[CStringT::Tokenize](#tokenize)|在目標字串中解壓縮指定的標記。|
|[CStringT::Trim](#trim)|從字串中修剪所有開頭和尾端空白字元。|
|[CStringT::TrimLeft](#trimleft)|修剪字串中開頭的空白字元。|
|[CStringT::TrimRight](#trimright)|修剪字串中的尾端空白字元。|

### <a name="operators"></a>運算子

|||
|-|-|
|[CStringT::operator =](#operator_eq)|將新值指派給`CStringT`物件。|
|[CStringT：： operator +](#operator_add)|串連兩個字串或一個字元和一個字串。|
|[CStringT：： operator + =](#operator_add_eq)|將新字串串連至現有字串的結尾。|
|[CStringT::operator ==](#operator_eq_eq)|判斷兩個字串是否在邏輯上相等。|
|[CStringT::operator !=](#operator_neq)|判斷兩個字串在邏輯上是否不相等。|
|[CStringT：： operator&lt;](#operator_lt)|判斷運算子左邊的字串是否小於右邊的字串。（& i）|
|[CStringT：： operator&gt;](#operator_gt)|判斷運算子左邊的字串是否大於右邊的字串。（& i）|
|[CStringT：： operator&lt;=](#operator_lt_eq)|判斷運算子左邊的字串是否小於或等於右邊的字串。（& i）|
|[CStringT：： operator&gt;=](#operator_gt_eq)|判斷運算子左邊的字串是否大於或等於右邊的字串。（& i）|

## <a name="remarks"></a>備註

`CStringT`繼承自[CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)。 先進的功能，例如字元操作、排序和搜尋，都是由`CStringT`所執行。

> [!NOTE]
> `CStringT`物件可以擲回例外狀況。 當`CStringT`物件因為任何原因而用盡記憶體時，就會發生這種情況。

`CStringT`物件是由可變長度的字元序列所組成。 `CStringT`使用類似于基本的語法來提供函式和運算子。 串連和比較運算子加上簡化的記憶體管理，讓`CStringT`物件比一般字元陣列更容易使用。

> [!NOTE]
>  雖然您可以建立`CStringT`包含內嵌 null 字元的實例，但我們還是建議您不要這麼做。 在包含內嵌 null 字元`CStringT`的物件上呼叫方法和運算子可能會產生非預期的結果。

藉由使用不同的`BaseType`和`StringTraits`參數組合， `CStringT`物件可以包含下列類型，這些型別已由 ATL 程式庫預先定義。

如果在 ATL 應用程式中使用：

`CString`、 `CStringA`和`CStringW`是從 MFC DLL （MFC90）匯出。DLL），而不是來自使用者 Dll。 這麼做是為了避免`CStringT`定義過多次。

> [!NOTE]
>  如果您的程式碼包含[使用 CStringT 匯出字串類別](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)中所述連結器錯誤的因應措施，您應該移除該程式碼。 不再需要它。

下列字串類型可在以 MFC 為基礎的應用程式中使用：

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CStringA`|具有 CRT 支援的 ANSI 字元類型字串。|
|`CStringW`|具有 CRT 支援的 Unicode 字元類型字串。|
|`CString`|包含 CRT 支援的 ANSI 和 Unicode 字元類型。|

下列字串類型可在定義 ATL_CSTRING_NO_CRT 的專案中使用：

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CAtlStringA`|不含 CRT 支援的 ANSI 字元類型字串。|
|`CAtlStringW`|不含 CRT 支援的 Unicode 字元類型字串。|
|`CAtlString`|不含 CRT 支援的 ANSI 和 Unicode 字元類型。|

下列字串類型適用于未定義 ATL_CSTRING_NO_CRT 的專案：

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CAtlStringA`|具有 CRT 支援的 ANSI 字元類型字串。|
|`CAtlStringW`|具有 CRT 支援的 Unicode 字元類型字串。|
|`CAtlString`|包含 CRT 支援的 ANSI 和 Unicode 字元類型。|

`CString`物件也具有下列特性：

- `CStringT`物件可能會因串連作業而成長。

- `CStringT`物件會遵循「值的語義」。 將`CStringT`物件視為實際的字串，而不是字串的指標。

- 您可以自由地`CStringT`替代函數`PCXSTR`引數的物件。

- 字串緩衝區的自訂記憶體管理。 如需詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="cstringt-predefined-types"></a>CStringT 預先定義的類型

因為`CStringT`使用樣板引數來定義支援的字元類型（ [wchar_t](../../c-runtime-library/standard-types.md)或[char](../../c-runtime-library/standard-types.md)），所以方法參數類型有時可能會很複雜。 為了簡化這個問題，會定義一組預先定義的類型，並在`CStringT`整個類別中使用。 下表列出各種類型：

|名稱|說明|
|----------|-----------------|
|`XCHAR`|與`CStringT`物件具有相同字元類型的單一字元（ **wchar_t**或**char**）。|
|`YCHAR`|與`CStringT`物件相反的字元類型的單一字元（ **wchar_t**或**char**）。|
|`PXSTR`|字元字串（ **wchar_t**或**char**）的指標，與`CStringT`物件具有相同的字元類型。|
|`PYSTR`|字元字串（ **wchar_t**或**char**）的指標，其字元`CStringT`類型與物件相反。|
|`PCXSTR`|與物件`CStringT`具有相同字元類型之**const**字元字串（ **wchar_t**或**char**）的指標。|
|`PCYSTR`|以 相反的字元類型做為物件之const字元字串（wchar_t或char）的`CStringT`指標。|

> [!NOTE]
>  先前`CString`使用未記載的方法（ `AssignCopy`例如）的程式碼，必須以使用下列檔之`CStringT` `GetBuffer`方法（例如或`ReleaseBuffer`）的程式碼取代。 這些方法是從`CSimpleStringT`繼承而來。

## <a name="inheritance-hierarchy"></a>繼承階層

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>需求

|標頭|用於|
|------------|-------------|
|cstringt.h|僅限 MFC 的字串物件|
|atlstr.h|非 MFC 字串物件|

##  <a name="allocsysstring"></a>  CStringT::AllocSysString

配置類型 BSTR 的 Automation 相容字串，並將`CStringT`物件的內容複寫到其中，包括終止的 null 字元。

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>傳回值

新配置的字串。

### <a name="remarks"></a>備註

在 MFC 程式中，如果有足夠的記憶體，就會擲回[CMemoryException 類別](../../mfc/reference/cmemoryexception-class.md)。 在 ATL 程式中，會擲回[CAtlException](../../atl/reference/catlexception-class.md) 。 此函數通常用來傳回自動化的字串。

通常，如果將這個字串當做 [in] 參數傳遞至 COM 函式，則需要呼叫者釋放字串。 這可以使用[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)來完成，如 Windows SDK 中所述。 如需詳細資訊，請參閱為[BSTR 配置和釋放記憶體](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)。

如需 Windows 中 OLE 配置函式的詳細資訊，請參閱 Windows SDK 中的[SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) 。

### <a name="example"></a>範例

下列範例示範 `CStringT::AllocSysString` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

##  <a name="ansitooem"></a>CStringT：： AnsiToOem

將這個`CStringT`物件中的所有字元，從 ANSI 字元集轉換成 OEM 字元集。

```
void AnsiToOem();
```

### <a name="remarks"></a>備註

如果已定義 _UNICODE，則無法使用函數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

##  <a name="appendformat"></a>  CStringT::AppendFormat

將格式化的資料附加至`CStringT`現有的物件。

```
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

此函式會格式化，並在中`CStringT`附加一系列的字元和值。 每個選擇性引數（如果有的話）都會根據*pszFormat*中的對應格式規格，或從*nFormatID*所識別的字串資源進行轉換和附加。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

##  <a name="collate"></a>  CStringT::Collate

使用泛型文字函數`_tcscoll`比較兩個字串。

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
另一個用於比較的字串。

### <a name="return-value"></a>傳回值

如果字串完全相同，則為零; 如果這個`CStringT`物件小於*psz*，則 < 0，如果這個`CStringT`物件大於*psz*，則為 0 >。

### <a name="remarks"></a>備註

在 TCHAR 中定義的`_tcscoll`泛型文字函數。H 會對應至`strcoll`、 `wcscoll`或`_mbscoll`，視編譯時期所定義的字元集而定。 每個函式都會根據目前使用中的字碼頁，執行字串的區分大小寫比較。 如需詳細資訊，請參閱[strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。

##  <a name="collatenocase"></a>  CStringT::CollateNoCase

使用泛型文字函數`_tcscoll`比較兩個字串。

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
另一個用於比較的字串。

### <a name="return-value"></a>傳回值

如果字串相同（忽略大小寫），則為零; 如果這個`CStringT`物件小於*psz* （忽略大小寫） >，則 < 0; 如果`CStringT`這個物件大於*psz* （忽略大小寫），則為0。

### <a name="remarks"></a>備註

在 TCHAR 中定義的`_tcscoll`泛型文字函數。H 會對應至`stricoll`、 `wcsicoll`或`_mbsicoll`，視編譯時期所定義的字元集而定。 每個函式都會根據目前使用中的字碼頁，執行字串的不區分大小寫比較。 如需詳細資訊，請參閱[strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

##  <a name="compare"></a>  CStringT::Compare

比較兩個字串（區分大小寫）。

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>參數

*psz*<br/>
另一個用於比較的字串。

### <a name="return-value"></a>傳回值

如果字串完全相同，則為零; 如果這個`CStringT`物件小於*psz*，則 < 0，如果這個`CStringT`物件大於*psz*，則為 0 >。

### <a name="remarks"></a>備註

在 TCHAR 中定義的`_tcscmp`泛型文字函數。H 會對應至`strcmp`、 `wcscmp`或`_mbscmp`，視編譯時期所定義的字元集而定。 每個函式會執行區分大小寫的字串比較，而且不會受到地區設定的影響。 如需詳細資訊，請參閱[strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)。

如果字串包含內嵌的 null，則在進行比較時，會將字串視為第一個內嵌 null 字元的截斷。

### <a name="example"></a>範例

下列範例示範 `CStringT::Compare` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

##  <a name="comparenocase"></a>  CStringT::CompareNoCase

比較兩個字串（不區分大小寫）。

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
另一個用於比較的字串。

### <a name="return-value"></a>傳回值

如果字串相同（忽略大小寫），則為零; 如果這個`CStringT`物件小於*psz* （忽略大小寫） >，則 < 0; 如果`CStringT`這個物件大於*psz* （忽略大小寫），則為0。

### <a name="remarks"></a>備註

在 TCHAR 中定義的`_tcsicmp`泛型文字函數。H，會對應到`_stricmp` `_wcsicmp`或`_mbsicmp`，視編譯時期所定義的字元集而定。 每個函數都會執行字串的不區分大小寫比較。 比較取決於地區設定的 LC_CTYPE 層面，但不是 LC_COLLATE。 如需詳細資訊，請參閱[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

##  <a name="cstringt"></a>CStringT：： CStringT

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

*pch*<br/>
長度為*nLength*之字元陣列的指標，不是以 null 結束。

*nLength*<br/>
*Pch*中的字元數計數。

*ch*<br/>
單一字元。

*pszSrc*<br/>
要複製到這個`CStringT`物件中以 null 結束的字串。

*pStringMgr*<br/>
`CStringT`物件之記憶體管理員的指標。 如需`IAtlStringMgr`和之記憶體管理的`CStringT`詳細資訊，請參閱[使用 CStringT 的記憶體管理](../../atl-mfc-shared/memory-management-with-cstringt.md)。

*strSrc*<br/>
要複製`CStringT`到這個`CStringT`物件中的現有物件。 如需`CThisString`和`CThisSimpleString`的詳細資訊，請參閱備註一節。

*varSrc*<br/>
要複製到這個`CStringT`物件的 variant 物件。

*BaseType*<br/>
字串類別的字元類型。 可以是下列其中一項：

**char**（適用于 ANSI 字元字串）。

**wchar_t**（適用于 Unicode 字元字串）。

TCHAR （適用于 ANSI 和 Unicode 字元字串）。

*bMFCDLL*<br/>
布林值，指定專案是否為 MFC DLL （TRUE）或不是（FALSE）。

*SystemString*<br/>
必須是`System::String`，而且必須使用/clr 來編譯專案。

*pString*<br/>
`CStringT`物件的控制碼。

### <a name="remarks"></a>備註

因為此函式會將輸入資料複製到新配置的儲存體，所以您應該注意記憶體例外狀況可能會產生。 請注意，其中有些函式會作為轉換函式。 例如，這可讓您以預期的`CStringT`物件取代 LPTSTR。

- `CStringT`( `LPCSTR` `lpsz` ):從 ANSI 字串`CStringT`構造 Unicode。 您也可以使用此函數來載入字串資源，如下列範例所示。

- `CStringT(``LPCWSTR` `lpsz` ):`CStringT`從 Unicode 字串構造。

- `CStringT`( `const unsigned char*` `psz` ):可讓您`CStringT`從不**帶正負號 char**的指標來建立。

> [!NOTE]
>  定義 _CSTRING_DISABLE_NARROW_WIDE_CONVERSION 宏，以關閉 ANSI 和 Unicode 字串之間的隱含字串轉換。 宏會從支援轉換的編譯函數中排除。

請注意， *strSrc*參數可以`CStringT`是或`CThisSimpleString`物件。 針對`CStringT`，請使用其中一個預設的具`CString`現`CStringA`化（ `CStringW`、或） `CThisSimpleString`; 若是，請使用**this**指標。 `CThisSimpleString`宣告[CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)的實例，這是較小的字串類別，其內建功能比`CStringT`類別少。

多載運算子`CSimpleStringT<>&()`會從`CStringT`宣告中`CSimpleStringT`建立物件。

> [!NOTE]
>  雖然您可以建立`CStringT`包含內嵌 null 字元的實例，但我們還是建議您不要這麼做。 在包含內嵌 null 字元`CStringT`的物件上呼叫方法和運算子可能會產生非預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

##  <a name="_dtorcstringt"></a>CStringT：： ~ CStringT

`CStringT`終結物件。

```
~CStringT() throw();
```

### <a name="remarks"></a>備註

`CStringT`終結物件。

##  <a name="delete"></a>  CStringT::Delete

從指定索引處的字元開始，刪除字串中的一個或多個字元。

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
要刪除的`CStringT`物件中第一個字元之以零為基底的索引。

*nCount*<br/>
要移除的字元數。

### <a name="return-value"></a>傳回值

已變更之字串的長度。

### <a name="remarks"></a>備註

如果*nCount*的長度超過字串，則會移除字串的其餘部分。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

##  <a name="find"></a>CStringT：： Find

在這個字串中搜尋字元或子字串的第一個相符項。

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>參數

*pszSub*<br/>
要搜尋的子字串。

*iStart*<br/>
字串中要開始搜尋的字元索引，或0表示從開頭開始。

*ch*<br/>
要搜尋的單一字元。

### <a name="return-value"></a>傳回值

這個`CStringT`物件中符合所要求之子字串的第一個字元之以零為基底的索引，如果找不到子字串或字元，則為-1。

### <a name="remarks"></a>備註

函式會多載以接受單一字元（類似于執行時間`strchr`函式）和字串（ `strstr`類似于）。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

##  <a name="findoneof"></a>CStringT：： FindOneOf

在這個字串中搜尋符合*pszCharSet*中包含之任何字元的第一個字元。

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
包含要比對之字元的字串。

### <a name="return-value"></a>傳回值

這個字串中，第一個字元的以零為基底的索引，也是*pszCharSet*;如果沒有相符項，則為-1。

### <a name="remarks"></a>備註

尋找*pszCharSet*中第一次出現的任何字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

##  <a name="format"></a>  CStringT::Format

以 [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) 將資料格式化`CStringT`成 C 樣式字元陣列的方式，將格式化的資料寫入。

```
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

此函式會將一系列的字元和值格式化並`CStringT`儲存在中。 每個選擇性引數（如果有的話）都會根據*pszFormat*中的對應格式規格，或*nFormatID*所識別的字串資源，進行轉換和輸出。

如果字串物件本身當做參數提供給`Format`，呼叫將會失敗。 例如，下列程式碼會導致無法預期的結果：

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

如需詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

##  <a name="formatmessage"></a>  CStringT::FormatMessage

格式化訊息字串。

```
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>參數

*nFormatID*<br/>
包含未格式化郵件內文的字串資源識別碼。

*pszFormat*<br/>
指向格式控制字元串。 系統會針對插入進行掃描，並據此進行格式化。 格式字串類似于執行時間函式*printf*樣式格式字串，但它允許以任意順序插入參數。

*引數*<br/>
選擇性引數。

### <a name="remarks"></a>備註

函數需要訊息定義做為輸入。 訊息定義取決於*pszFormat*或*nFormatID*所識別的字串資源。 函式會將格式化郵件內文複製到`CStringT`物件，並在要求時處理任何內嵌插入序列。

> [!NOTE]
> `FormatMessage`嘗試為新格式化的字串配置系統記憶體。 如果此嘗試失敗，就會自動擲回記憶體例外狀況。

每個插入都必須在*pszFormat*或*nFormatID*參數後面有對應的參數。 在郵件內文中，有數個逸出序列支援動態格式化訊息。 如需詳細資訊，請參閱 Windows SDK 中的 Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)函數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

##  <a name="formatmessagev"></a>  CStringT::FormatMessageV

使用可變引數清單來格式化訊息字串。

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
指向格式控制字元串。 系統會針對插入進行掃描，並據此進行格式化。 格式字串類似于執行時間`printf`函式樣式格式字串，但它允許以任意順序插入參數。

*pArgList*<br/>
引數清單的指標。

### <a name="remarks"></a>備註

函數需要訊息定義做為輸入，並由*pszFormat*決定。 函式會將格式化的郵件內文和引數的可變清單複製`CStringT`到物件，並在要求時處理任何內嵌的插入序列。

> [!NOTE]
> `FormatMessageV`呼叫[CStringT：： FormatMessage](#formatmessage)，它會嘗試為新格式化的字串配置系統記憶體。 如果此嘗試失敗，就會自動擲回記憶體例外狀況。

如需詳細資訊，請參閱 Windows SDK 中的 Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)函數。

##  <a name="formatv"></a>  CStringT::FormatV

使用可變引數清單來格式化訊息字串。

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
指向格式控制字元串。 系統會針對插入進行掃描，並據此進行格式化。 格式字串類似于執行時間`printf`函式樣式格式字串，但它允許以任意順序插入參數。

*引數*<br/>
引數清單的指標。

### <a name="remarks"></a>備註

以將資料格式化成 C 樣式字元陣列的相同`CStringT` `vsprintf_s`方式，將格式化字串和引數清單寫入字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

##  <a name="getenvironmentvariable"></a>CStringT：： GetEnvironmentVariable

將字串設定為所指定環境變數的值。

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>參數

*pszVar*<br/>
指定環境變數之以 null 終止之字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

從呼叫進程的環境區塊，抓取指定變數的值。 值的格式為以 null 結束的字元字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

##  <a name="insert"></a>  CStringT::Insert

在字串中的指定索引處插入單一字元或子字串。

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
要在其中進行插入的字元索引。

*psz*<br/>
要插入之子字串的指標。

*ch*<br/>
要插入的字元。

### <a name="return-value"></a>傳回值

已變更之字串的長度。

### <a name="remarks"></a>備註

*IIndex*參數會識別要移動以騰出空間給字元或子字串的第一個字元。 如果*nIndex*為零，則插入會在整個字串之前進行。 如果*nIndex*大於字串的長度，函式會串連目前的字串，以及*ch*或*psz*所提供的新資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

##  <a name="left"></a>  CStringT::Left

從這個`CStringT`物件解壓縮最左邊的*nCount*字元，並傳回已解壓縮之子字串的複本。

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>參數

*nCount*<br/>
要從 `CStringT` 這個物件擷取的字元數。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 傳回的 `CStringT` 物件可以是空的。

### <a name="remarks"></a>備註

如果*nCount*超過字串長度，則會解壓縮整個字串。 `Left` 類似於 Basic `Left` 函式。

針對多位元組字元集（MBCS）， *nCount*會將每個8位序列視為一個字元，讓*nCount*傳回多位元組字元數乘以二。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

##  <a name="loadstring"></a>  CStringT::LoadString

將由*nID*識別的 Windows 字串資源讀入現有`CStringT`的物件中。

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

使用指定的語言（*wLanguage*），從指定的模組（*hInstance*）載入字串資源（*nID*）。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

##  <a name="makelower"></a>CStringT：： MakeLower

`CStringT`將物件轉換成小寫字串。

```
CStringT& MakeLower();
```

### <a name="return-value"></a>傳回值

產生的小寫字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

##  <a name="makereverse"></a>CStringT：： MakeReverse

反轉`CStringT`物件中的字元順序。

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>傳回值

產生的反轉字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

##  <a name="makeupper"></a>  CStringT::MakeUpper

`CStringT`將物件轉換為大寫字串。

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>傳回值

產生的大寫字串。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

##  <a name="mid"></a>  CStringT::Mid

從位置*iFirst* （以零為基底`CStringT` ）開始，從這個物件中解壓縮長度*nCount*字元的子字串。

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>參數

*iFirst*<br/>
這個`CStringT`物件中要包含在解壓縮的子字串中，第一個字元之以零為起始的索引。

*nCount*<br/>
要從 `CStringT` 這個物件擷取的字元數。 如果未提供此參數，則會解壓縮字串的其餘部分。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 請注意，傳回`CStringT`的物件可能是空的。

### <a name="remarks"></a>備註

函式會傳回已解壓縮之子字串的複本。 `Mid`類似于基本的 Mid 函數（Basic 中的索引是以一為基礎）。

針對多位元組字元集（MBCS）， *nCount*會參考每個8位字元;也就是說，一個多位元組字元中的潛在客戶和後隨位元組會視為兩個字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

##  <a name="oemtoansi"></a>  CStringT::OemToAnsi

將這個`CStringT`物件中的所有字元，從 OEM 字元集轉換成 ANSI 字元集。

```
void OemToAnsi();
```

### <a name="remarks"></a>備註

如果已定義 _UNICODE，則無法使用此函數。

### <a name="example"></a>範例

請參閱[CStringT：： AnsiToOem](#ansitooem)的範例。

##  <a name="operator_eq"></a>CStringT：： operator =

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
要`CStringT`指派給這個字串的。

*str*<br/>
對 `CThisSimpleString` 物件的參考。

*bMFCDLL*<br/>
布林值，指定專案是否為 MFC DLL。

*BaseType*<br/>
字串基底類型。

*var*<br/>
要指派給這個字串的 variant 物件。

*ch*<br/>
要指派給字串的 ANSI 或 Unicode 字元。

*pszSrc*<br/>
要指派之原始字串的指標。

### <a name="remarks"></a>備註

指派運算子會接受另`CStringT`一個物件、字元指標或單一字元。 請注意，每當您使用此運算子時，都會發生記憶體例外狀況，因為可以配置新的儲存空間。

如需的`CThisSimpleString`詳細資訊，請參閱[CStringT：： CStringT](#cstringt)的「備註」一節。

> [!NOTE]
> 雖然您可以建立`CStringT`包含內嵌 null 字元的實例，但我們還是建議您不要這麼做。 在包含內嵌 null 字元`CStringT`的物件上呼叫方法和運算子可能會產生非預期的結果。

##  <a name="operator_add"></a>CStringT：： operator +

串連兩個字串或一個字元和一個字串。

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
要`CStringT`與字串或字串連的。

*str2*<br/>
要`CStringT`與字串或字串連的。

*psz1*<br/>
要與字串或字串連之以 null 結束的字串指標。

*psz2*<br/>
要與字串或字串連之字串的指標。

### <a name="remarks"></a>備註

`CStringT::operator+`函數有七種多載形式。 第一個版本會串連兩`CStringT`個現有的物件。 接下來的兩個`CStringT`會串連物件和以 null 結束的字串。 接下來的兩個`CStringT`會串連物件和 ANSI 字元。 最後兩個會串連`CStringT`一個物件和一個 Unicode 字元。

> [!NOTE]
>  雖然您可以建立`CStringT`包含內嵌 null 字元的實例，但我們還是建議您不要這麼做。 在包含內嵌 null 字元`CStringT`的物件上呼叫方法和運算子可能會產生非預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

##  <a name="operator_add_eq"></a>CStringT：： operator + =

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
對 `CThisSimpleString` 物件的參考。

*bMFCDLL*<br/>
布林值，指定專案是否為 MFC DLL。

*BaseType*<br/>
字串基底類型。

*var*<br/>
要串連到這個字串的 variant 物件。

*ch*<br/>
要與字串串連的 ANSI 或 Unicode 字元。

*pszSrc*<br/>
要串連之原始字串的指標。

*strSrc*<br/>
要`CStringT`串連到這個字串的。

### <a name="remarks"></a>備註

運算子會接受另`CStringT`一個物件、字元指標或單一字元。 您應該注意，每當您使用這個串連運算子時，就會發生記憶體例外狀況，因為新的儲存空間可以配置`CStringT`給加入此物件的字元。

如需的`CThisSimpleString`詳細資訊，請參閱[CStringT：： CStringT](#cstringt)的「備註」一節。

> [!NOTE]
>  雖然您可以建立`CStringT`包含內嵌 null 字元的實例，但我們還是建議您不要這麼做。 在包含內嵌 null 字元`CStringT`的物件上呼叫方法和運算子可能會產生非預期的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

##  <a name="operator_eq_eq"></a>CStringT：： operator = =

判斷兩個字串是否在邏輯上相等。

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
用於比較的 ANSI 或 Unicode 字元。

*ch2*<br/>
用於比較的 ANSI 或 Unicode 字元。

*str1*<br/>
`CStringT`用於比較的。

*str2*<br/>
`CStringT`用於比較的。

*psz1*<br/>
要進行比較之以 null 終止之字串的指標。

*psz2*<br/>
要進行比較之以 null 終止之字串的指標。

### <a name="remarks"></a>備註

測試左邊的字串或字元是否等於右邊的字串或字元，並據以傳回 TRUE 或 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

##  <a name="operator_neq"></a>CStringT：： operator！ =

判斷兩個字串是否邏輯上不相等。

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
要進行比較之以 null 終止之字串的指標。

*psz2*<br/>
要進行比較之以 null 終止之字串的指標。

### <a name="remarks"></a>備註

測試左邊的字串或字元是否不等於右邊的字串或字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

##  <a name="operator_lt"></a>CStringT：： operator&lt;

判斷運算子左邊的字串是否小於右邊的字串。（& i）

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
要進行比較之以 null 終止之字串的指標。

*psz2*<br/>
要進行比較之以 null 終止之字串的指標。

### <a name="remarks"></a>備註

字串與字元之間的字典比較，直到：

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找不到任何差異，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

##  <a name="operator_gt"></a>CStringT：： operator&gt;

判斷運算子左邊的字串是否大於右邊的字串。（& i）

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
要進行比較之以 null 終止之字串的指標。

*psz2*<br/>
要進行比較之以 null 終止之字串的指標。

### <a name="remarks"></a>備註

字串與字元之間的字典比較，直到：

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

##  <a name="operator_lt_eq"></a>CStringT：： operator&lt;=

判斷運算子左邊的字串，是否小於或等於右邊的字串的位置。

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
要進行比較之以 null 終止之字串的指標。

*psz2*<br/>
要進行比較之以 null 終止之字串的指標。

### <a name="remarks"></a>備註

字串與字元之間的字典比較，直到：

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

##  <a name="operator_gt_eq"></a>CStringT：： operator&gt;=

判斷運算子左邊的字串是否大於或等於右邊的字串。（& i）

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

字串與字元之間的字典比較，直到：

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

##  <a name="remove"></a>  CStringT::Remove

從字串中移除指定之字元的所有實例。

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>參數

*chRemove*<br/>
要從字串中移除的字元。

### <a name="return-value"></a>傳回值

從字串中移除的字元計數。 如果未變更字串，則為零。

### <a name="remarks"></a>備註

字元的比較會區分大小寫。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

##  <a name="replace"></a>  CStringT::Replace

有兩個版本`Replace`。第一個版本會使用另一個子字串來取代子字串的一個或多個複本。 這兩個子字串都是以 null 結束。 第二個版本會使用另一個字元來取代一個或多個字元的複本。 這兩個版本都是針對儲存在`CStringT`中的字元資料進行操作。

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>參數

*pszOld*<br/>
要由*pszNew*取代之以 null 終止之字串的指標。

*pszNew*<br/>
以 null 結束的字串指標，取代*pszOld*。

*chOld*<br/>
要由*chNew*取代的字元。

*chNew*<br/>
取代*chOld*的字元。

### <a name="return-value"></a>傳回值

傳回字元或子字串的已取代實例數目，如果字串未變更，則傳回零。

### <a name="remarks"></a>備註

`Replace`可以變更字串長度，因為*pszNew*和*pszOld*不一定要有相同的長度，而且舊的子字串有數個複本可以變更為新的。 函式會執行區分大小寫的比對。

實例的`CStringT`範例包括`CString`、 `CStringA`和。`CStringW`

若`CStringA`為`Replace` ，則使用 ANSI 或多位元組（MBCS）字元。 針對`CStringW` ，`Replace`適用于寬字元。

若`CString`為，則會在編譯時期選取字元資料類型，這是根據下表中的常數是否已定義而定。

|定義的常數|字元資料類型|
|----------------------|-------------------------|
|_UNICODE|寬字元|
|_MBCS|多位元組字元|
|屬於|單一位元組字元|
|兩者|未定義|

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

##  <a name="reversefind"></a>CStringT：： ReverseFind

在此`CStringT`物件中搜尋字元的最後一個相符項。

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>參數

*ch*<br/>
要搜尋的字元。

### <a name="return-value"></a>傳回值

這個`CStringT`物件中，與所要求的字元相符之最後一個字元的以零為起始的索引，如果找不到該字元，則為-1。

### <a name="remarks"></a>備註

函數與執行時間函數`strrchr`類似。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

##  <a name="right"></a>  CStringT::Right

從這個`CStringT`物件中解壓縮最後一個（也就是最右邊的） *nCount*字元，並傳回已解壓縮之子字串的複本。

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>參數

*nCount*<br/>
要從 `CStringT` 這個物件擷取的字元數。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 請注意，傳回`CStringT`的物件可以是空的。

### <a name="remarks"></a>備註

如果*nCount*超過字串長度，則會解壓縮整個字串。 `Right`類似于基本`Right`函數（basic 中的索引是以零為基底）。

針對多位元組字元集（MBCS）， *nCount*會參考每個8位字元;也就是說，一個多位元組字元中的潛在客戶和後隨位元組會視為兩個字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

##  <a name="setsysstring"></a>  CStringT::SetSysString

重新配置*pbstr*所指向的 BSTR，並將`CStringT`物件的內容複寫到其中，包括 Null 字元。

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>參數

*pbstr*<br/>
字元字串的指標。

### <a name="return-value"></a>傳回值

新字串。

### <a name="remarks"></a>備註

根據`CStringT`物件的內容， *pbstr*所參考的 BSTR 值可能會變更。 如果沒有足夠的`CMemoryException`記憶體存在，函式會擲回。

此函式通常用來變更以傳址方式傳遞的字串值以進行自動化。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

##  <a name="spanexcluding"></a>CStringT：： SpanExcluding

從字串中，以第一個字元開頭，而不是*pszCharSet*所識別的字元集合中的字元。

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
轉譯成一組字元的字串。

### <a name="return-value"></a>傳回值

包含字串中不是*pszCharSet*之字元的子字串，從字串中的第一個字元開始，並以字串中找到的第一個*字元（也*就是從第一個字串中的字元，但不包括在字串中找到的第一個字元*pszCharSet*）。 如果在字串中找不到*pszCharSet*中的任何字元，則會傳回整個字串。

### <a name="remarks"></a>備註

`SpanExcluding`從*pszCharSet*中，解壓縮並傳回字元第一次出現之前的所有字元（換句話說， *pszCharSet*中的字元和字串後面的所有字元都不會傳回）。 如果在字串中找不到*pszCharSet*中的任何字元`SpanExcluding` ，則會傳回整個字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

##  <a name="spanincluding"></a>CStringT：： SpanIncluding

從字串中的第一個字元開始，以*pszCharSet*所識別的字元集合中的字元來解壓縮。

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
轉譯成一組字元的字串。

### <a name="return-value"></a>傳回值

子字串，其中包含字串中的字元（ *pszCharSet*中），從字串中的第一個字元開始，並在字串中找到不在*pszCharSet*的字元時結束。 `SpanIncluding`如果字串中的第一個字元不在指定的集合中，則會傳回空的子字串。

### <a name="remarks"></a>備註

如果字串的第一個字元不在字元集中，則`SpanIncluding`會傳回空字串。 否則，它會傳回集合中連續的字元序列。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

##  <a name="tokenize"></a>CStringT：： Token 化

尋找目標字串中的下一個 token

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>參數

*pszTokens*<br/>
包含標記分隔符號的字串。 這些分隔符號的順序並不重要。

*iStart*<br/>
要開始搜尋的以零起始的索引。

### <a name="return-value"></a>傳回值

`CStringT`物件，包含目前的 token 值。

### <a name="remarks"></a>備註

`Tokenize`函式會尋找目標字串中的下一個 token。 *PszTokens*中的一組字元會指定要尋找之標記的可能分隔符號。 函式的每`Tokenize`個呼叫都會從*iStart*開始，略過前置分隔符號`CStringT` ，並傳回包含目前標記的物件，也就是字元的字串，直到下一個分隔符號為止。 *IStart*的值會更新為結尾分隔符號後面的位置，如果已到達字串的結尾，則為-1。 透過一系列的呼叫`Tokenize`，可以將更多的 token 從目標字串的其餘部分中斷，使用*iStart*追蹤字串中下一個權杖的讀取位置。 當沒有其他權杖時，此函式會傳回空字串，而且*iStart*會設定為-1。

不同于 CRT token 化函數（例如[strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)、_mbstok_s_l `Tokenize` ），不會修改目標字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>備註

此範例的輸出如下所示：

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

##  <a name="trim"></a>CStringT：： Trim

修剪字串的開頭和尾端字元。

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
字串的指標，其中包含要修剪的目標字元。 *PszTarget*中所有開頭和結尾的字元都會從`CStringT`物件中修剪。

### <a name="return-value"></a>傳回值

傳回修剪過的字串。

### <a name="remarks"></a>備註

移除下列其中一項的所有開頭和結尾專案：

- *ChTarget*所指定的字元。

- 在*pszTargets*所指定的字串中找到的所有字元。

- 空白字元.

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>備註

此範例的輸出如下所示：

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

##  <a name="trimleft"></a>  CStringT::TrimLeft

修剪字串中的前置字元。

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
字串的指標，其中包含要修剪的目標字元。 *PszTarget*中所有開頭出現的字元都會從`CStringT`物件中修剪。

### <a name="return-value"></a>傳回值

產生的修剪字串。

### <a name="remarks"></a>備註

移除下列其中一項的所有開頭和結尾專案：

- *ChTarget*所指定的字元。

- 在*pszTargets*所指定的字串中找到的所有字元。

- 空白字元.

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

##  <a name="trimright"></a>  CStringT::TrimRight

修剪字串中的尾端字元。

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
字串的指標，其中包含要修剪的目標字元。 *PszTarget*中所有尾端出現的字元都會從`CStringT`物件中修剪。

### <a name="return-value"></a>傳回值

傳回包含修剪後之字串的物件。`CStringT`

### <a name="remarks"></a>備註

移除下列其中一項的尾端出現專案：

- *ChTarget*所指定的字元。

- 在*pszTargets*所指定的字串中找到的所有字元。

- 空白字元.

版本接受一個字元參數，並從`CStringT`字串資料的結尾移除該字元的所有複本。 `CStringT& TrimRight(XCHAR chTarget)` 它會從字串的結尾開始，一直往前邁進。 當它找到不同的字元或字元資料用盡`CSTringT`時，就會停止。

`CStringT& TrimRight(PCXSTR pszTargets)`版本會接受以 null 終止的字串，其中包含要搜尋的所有不同字元。 它會移除`CStringT`物件中這些字元的所有複本。 它會從字串的結尾開始，一直往前邁進。 當它找到不在目標字串中的字元，或當字元資料用盡時`CStringT` ，就會停止。 它不會嘗試比對整個目標字串與結尾`CStringT`的子字串。

`CStringT& TrimRight()`版本不需要任何參數。 它會修剪`CStringT`字串結尾的任何尾端空白字元。 空白字元可以是分行符號、空格或索引標籤。

-

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)
