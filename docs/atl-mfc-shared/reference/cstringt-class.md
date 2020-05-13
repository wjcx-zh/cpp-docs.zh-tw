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
ms.openlocfilehash: 8fcce4c426cd99785d34dc080f238cc78cdfee36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746705"
---
# <a name="cstringt-class"></a>CStringT 類別

此表示物件`CStringT`。

## <a name="syntax"></a>語法

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>參數

*BaseType*<br/>
字串類的字元類型。 可以是下列其中一項：

- **字元**(用於 ANSI 字串)。

- **wchar_t(** 對於 Unicode 字串)。

- TCHAR(適用於 ANSI 和 Unicode 字串)。

*弦樂*<br/>
確定字串類別是否需要 C 執行時 (CRT) 函式庫支援以及字串資源的位置。 可以是下列其中一項：

- **斯特爾特拉特<wchar_t &#124;&#124;****查爾、查克拉茨克拉特 wchar_t<&#124;&#124;** 的 **&#124;&#124;****的查爾**&#124;**查爾 > >**

   該類別需要 CRT 支援並搜尋`m_hInstResource`由(應用程式模組類別的成員)指定的模組中的資源字串。

- **斯特爾特拉特< wchar_t&#124;&#124;****查爾&#124;&#124;,ChTraitsos<wchar_t&#124;&#124;****查爾**&#124;**查爾 > >** **char**

   該類別不需要 CRT 支援並搜尋`m_hInstResource`由(應用程式模組類別的成員)指定的模組中的資源字串。

- **斯特特拉特姆足球俱樂部<wchar_t&#124;&#124;****查爾****&#124;,ChTraitsCRT<wchar_t&#124;&#124;****查爾****&#124;查尔 > >**

   該類需要 CRT 支援並使用標準 MFC 搜尋演演演算法搜索資源字串。

- **斯特特拉特姆足球俱樂部<wchar_t&#124;&#124;****查爾、ChTraitsos<wchar_t&#124;&#124;****查爾****&#124;TCHAR > >** **char**

   該類不需要 CRT 支援並使用標準 MFC 搜尋演演演算法搜索資源字串。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[弦樂::CStringT](#cstringt)|以各種方式構造`CStringT`物件。|
|[弦樂::*CStringT](#_dtorcstringt)|終結 `CStringT` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStringT:allocSysString](#allocsysstring)|從`CStringT`資料分配 BSTR。|
|[弦樂::安西托姆](#ansitooem)|從 ANSI 字元集到 OEM 字元集進行就地轉換。|
|[CStringT::附加格式](#appendformat)|將格式化的數據追加到現有`CStringT`物件。|
|[CStringT::整理](#collate)|比較兩個字串(區分大小寫,使用特定於區域設置的資訊)。|
|[CStringT::克拉特諾凱斯](#collatenocase)|比較兩個字串(區分大小寫,使用特定於區域設置的資訊)。|
|[CStringT:比較](#compare)|比較兩個字串(區分大小寫)。|
|[CStringT:比較無案例](#comparenocase)|比較兩個字串(不區分大小寫)。|
|[CStringT::D埃萊特](#delete)|從字串中刪除字元或字元。|
|[CStringT:尋找](#find)|在較大的字串中尋找字元或子字串。|
|[弦樂::尋找](#findoneof)|從集中查找第一個匹配字元。|
|[CStringT:格式](#format)|使字串的格式`sprintf`與字串一樣。|
|[CStringT::格式訊息](#formatmessage)|設定消息字串的格式。|
|[CStringT::格式訊息V](#formatmessagev)|使用變數參數清單設定訊息字串的格式。|
|[CStringT::格式V](#formatv)|使用參數的變數清單設定字串的格式。|
|[CStringT:抓取環境變數](#getenvironmentvariable)|將字串設定為指定環境變數的值。|
|[CStringT:插入](#insert)|在字串中的給定索引上插入單個字元或子字串。|
|[CStringT:左](#left)|提取字串的左側部分。|
|[CStringT::載入字串](#loadstring)|從 Windows`CStringT`資源載入現有物件。|
|[CStringT::製作下](#makelower)|將此字串中的所有字元轉換為小寫字元。|
|[CStringT::使反向](#makereverse)|反轉字串。|
|[CStringT::製作上](#makeupper)|將此字串中的所有字元轉換為大寫字元。|
|[CStringT:中](#mid)|提取字串的中間部分。|
|[弦樂::OemToansi](#oemtoansi)|從 OEM 字元集到 ANSI 字元集進行就地轉換。|
|[CStringT::刪除](#remove)|從字串中刪除指示的字元。|
|[CStringT:取代](#replace)|將指示的字元替換為其他字元。|
|[CStringT::反向查找](#reversefind)|在較大的字串中查找字元;從結束開始。|
|[CStringT:右](#right)|提取字串的右側部分。|
|[CStringT::SetSysString](#setsysstring)|使用`CStringT`來自物件的數據設置現有的 BSTR 物件。|
|[CStringT::範圍排除](#spanexcluding)|從字串中提取字元,從第一個字元開始,這些字元不在標識`pszCharSet`的字元集中。|
|[CStringT::跨欄包括](#spanincluding)|提取僅包含集中字元的子字串。|
|[CStringT::權杖化](#tokenize)|提取目標字串中指定的權杖。|
|[CStringT:修剪](#trim)|從字串中修剪所有前導和尾隨空格字元。|
|[CStringT::修剪左](#trimleft)|修剪字串中領先的空格字元。|
|[CStringT::修剪權](#trimright)|修剪字串中尾隨空格字元。|

### <a name="operators"></a>操作員

|||
|-|-|
|[CStringT::運算符 |](#operator_eq)|為`CStringT`物件分配新值。|
|[CStringT:運算符 |](#operator_add)|串聯兩個字串或一個字元和一個字串。|
|[CStringT::運算符 |](#operator_add_eq)|將新字串串聯到現有字串的末尾。|
|[CStringT::運算符 |](#operator_eq_eq)|確定兩個字串在邏輯上是否相等。|
|[CStringT::操作員!]](#operator_neq)|確定兩個字串在邏輯上是否不相等。|
|[CStringT::運算子&lt;](#operator_lt)|確定運算元左側的字串是否小於右側的字串。|
|[CStringT::運算子&gt;](#operator_gt)|確定運算元左側的字串是否大於右側的字串。|
|[CStringT::運算子&lt;=](#operator_lt_eq)|確定運算元左側的字串是否小於或等於右側的字串。|
|[CStringT::運算子&gt;=](#operator_gt_eq)|確定運算元左側的字串是否大於或等於右側的字串。|

## <a name="remarks"></a>備註

`CStringT`繼承自[CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)。 進階功能(如字元操作、排序與搜尋)由`CStringT`。

> [!NOTE]
> `CStringT`對象能夠引發異常。 當`CStringT`對象由於任何原因耗盡記憶體時,就會發生這種情況。

對`CStringT`象 由可變長度的字元序列組成。 `CStringT`使用類似於 Basic 的語法提供函數和運算符。 串聯和比較運算符,以及簡化的記憶體管理,使`CStringT`物件比普通字元陣列更易於使用。

> [!NOTE]
> 儘管可以創建`CStringT`包含嵌入的空字元的實例,但我們建議不要這樣做。 對`CStringT`包含嵌入的空字元的物件呼叫方法和運算元可以產生意外的結果。

通過使用`BaseType``StringTraits`和 參數的不同`CStringT`組合, 物件可以採用以下類型,這些類型已由 ATL 庫預定義。

如果在 ATL 應用程式中使用:

`CString``CStringA`,`CStringW`並從 MFC DLL (MFC90) 匯出。DLL),從不從使用者 DLL。 這樣做是為了防止`CStringT`被乘以定義。

> [!NOTE]
> 如果代碼包含[使用 CStringT 匯出字串類](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)中所述的連結器錯誤的解決方法,則應刪除該代碼。 已不再需要此項目。

以下字串型態在基於 MFC 的應用程式中可用:

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CStringA`|支援 CRT 的 ANSI 字元類型字串。|
|`CStringW`|支援 CRT 的 Unicode 字元類型字串。|
|`CString`|支援 CRT 的 ANSI 和 Unicode 字元類型。|

定義ATL_CSTRING_NO_CRT的項目中可以使用以下字串型態:

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CAtlStringA`|不支援 CRT 的 ANSI 字元類型字串。|
|`CAtlStringW`|不支援 CRT 的 Unicode 字元類型字串。|
|`CAtlString`|ANSI 和 Unicode 字元類型均無 CRT 支援。|

未定義ATL_CSTRING_NO_CRT的項目中可以使用以下字串型態:

|CStringT 類型|宣告|
|-------------------|-----------------|
|`CAtlStringA`|支援 CRT 的 ANSI 字元類型字串。|
|`CAtlStringW`|支援 CRT 的 Unicode 字元類型字串。|
|`CAtlString`|支援 CRT 的 ANSI 和 Unicode 字元類型。|

`CString`物件還具有以下特徵:

- `CStringT`對象可以由於串聯操作而增大。

- `CStringT`物件遵循"值語義"。 將`CStringT`對象視為實際字串,而不是指向字串的指標。

- 您可以自由地將`CStringT`物件替換`PCXSTR`為函數參數。

- 字串緩衝區的自定義記憶體管理。 有關詳細資訊,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="cstringt-predefined-types"></a>CStringT 預先定義類型

由於`CStringT`使用範本參數定義受支援的字元類型[(wchar_t](../../c-runtime-library/standard-types.md)或[char),](../../c-runtime-library/standard-types.md)因此方法參數類型有時可能很複雜。 為了簡化此問題,在整個`CStringT`類中定義和使用一組預定義類型。 下表列出了各種類型:

|名稱|描述|
|----------|-----------------|
|`XCHAR`|與`CStringT`物件具有相同字元類型的單個字元 **(wchar_t**或**字元**)。|
|`YCHAR`|具有相反字元類型的單個字元 **(wchar_t**或**字元**)作為`CStringT`物件。|
|`PXSTR`|指向與物件具有相同字元類型的字串 **(wchar_t**或**字元**)`CStringT`的指標。|
|`PYSTR`|指向字串 **(wchar_t**或**字元**)的指標,該指標的字元類型為`CStringT`物件。|
|`PCXSTR`|指向與物件具有相同字元類型的**const**字串 **(wchar_t**或**字元**)的`CStringT`指標。|
|`PCYSTR`|指向**const**字串 **(wchar_t**或**字元**)的指標,該指標具有相反的字`CStringT`元類型 作為物件。|

> [!NOTE]
> 以前`CString`使用`AssignCopy`(如 ) 的未記錄方法的代碼必須取代為使用`CStringT`以下文件`GetBuffer`記錄`ReleaseBuffer`的方法 (如或 ) 的代碼。 這些方法是從 繼承`CSimpleStringT`的 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>需求

|頁首|使用對象|
|------------|-------------|
|cstringt.h|只限 MFC 的字串物件|
|atlstr.h|非 MFC 字串物件|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT:allocSysString

分配 BSTR 類型的自動化相容字串,`CStringT`並將 物件的內容複製到該字串中,包括終止空字元。

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>傳回值

新分配的字串。

### <a name="remarks"></a>備註

在 MFC 程式中,如果記憶體不足,將引發[CMemoryexception 類別](../../mfc/reference/cmemoryexception-class.md)。 在 ATL 程式中,將拋出一個[CAtlException。](../../atl/reference/catlexception-class.md) 此函數通常用於返回自動化的字串。

通常,如果此字串作為 [in] 參數傳遞給 COM 函數,則這需要呼叫方釋放該字串。 這可以通過使用[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)來實現,如 Windows SDK 中所述。 有關詳細資訊,請參閱為[BSTR 分配和釋放記憶體](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)。

有關 Windows 中的 OLE 分配功能的詳細資訊,請參閱 Windows SDK 中的[SysAllocString。](/windows/win32/api/oleauto/nf-oleauto-sysallocstring)

### <a name="example"></a>範例

下列範例示範 `CStringT::AllocSysString` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a>弦樂::安西托姆

將此`CStringT`物件中的所有字元從 ANSI 字元集轉換為 OEM 字元集。

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>備註

如果定義了_UNICODE,則該函數不可用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a>CStringT::附加格式

將格式化的數據追加到現有`CStringT`物件。

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>參數

*psz格式*<br/>
格式控制字串。

*nFormatID*<br/>
包含格式控制字串的字串資源識別碼。

*引數*<br/>
選擇性引數。

### <a name="remarks"></a>備註

此函數在 中設定與附加字元和值`CStringT`。 每個可選參數(如果有)根據*pszFormat 中的*相應格式規範或*nFormatID*標識的字串資源進行轉換和追加。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a>CStringT::整理

使用泛文字函數`_tcscoll`比較兩個字串。

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
用於比較的另一個字串。

### <a name="return-value"></a>傳回值

如果字串相同,則為零,如果`CStringT`此物件 小於*psz,* 則< 0;如果此`CStringT`物件大於*psz,* 則> 0。

### <a name="remarks"></a>備註

泛文字函數`_tcscoll`, 在 TCHAR 中定義.H, 映射`strcoll`到`wcscoll``_mbscoll`, 或 , 取決於編譯時定義的字元集。 每個函數根據當前使用的代碼頁對字串執行區分大小寫的比較。 有關詳細資訊,請參閱[斯特科爾、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l。](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT::克拉特諾凱斯

使用泛文字函數`_tcscoll`比較兩個字串。

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
用於比較的另一個字串。

### <a name="return-value"></a>傳回值

如果字串相同(忽略大小寫),則< 0(如果此`CStringT`物件小於*psz(* 忽略大小寫),則>如果此`CStringT`物件大於*psz(* 忽略大小寫)。

### <a name="remarks"></a>備註

泛文字函數`_tcscoll`, 在 TCHAR 中定義.H, 映射`stricoll`到`wcsicoll``_mbsicoll`, 或 , 取決於編譯時定義的字元集。 每個函數根據當前使用的代碼頁對字串執行不區分大小寫的比較。 有關詳細資訊,請參閱[斯特科爾、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l。](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a>CStringT:比較

比較兩個字串(區分大小寫)。

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>參數

*psz*<br/>
用於比較的另一個字串。

### <a name="return-value"></a>傳回值

如果字串相同,則為零,如果`CStringT`此物件 小於*psz,* 則< 0;如果此`CStringT`物件大於*psz,* 則> 0。

### <a name="remarks"></a>備註

泛文字函數`_tcscmp`, 在 TCHAR 中定義.H, 映射`strcmp`到`wcscmp``_mbscmp`, 或 , 取決於編譯時定義的字元集。 每個函數執行字串的區分大小寫比較,不受區域設置的影響。 有關詳細資訊,請參閱[strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)。

如果字串包含嵌入的 null,為了比較,字串被視為在第一個嵌入的 null 字元處被截斷。

### <a name="example"></a>範例

下列範例示範 `CStringT::Compare` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT:比較無案例

比較兩個字串(不區分大小寫)。

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>參數

*psz*<br/>
用於比較的另一個字串。

### <a name="return-value"></a>傳回值

如果字串相同(忽略大小寫),則<0(如果此`CStringT`物件小於*psz(* 忽略大小寫),則>如果此`CStringT`物件大於*psz(* 忽略大小寫)。

### <a name="remarks"></a>備註

泛文字函數`_tcsicmp`, 在 TCHAR 中定義.H,映射到`_stricmp``_wcsicmp``_mbsicmp`或 ,具體取決於編譯時定義的字元集。 每個函數執行不區分大小寫的字串比較。 比較取決於區域設置LC_CTYPE方面,而不是LC_COLLATE。 有關詳細資訊,請參閱[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l_mbsicmp_l。](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a>弦樂::CStringT

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
指向長度*nLength*的字元陣列的指標,而不是 null 終止。

*N 長度*<br/>
*pch*中字元數的計數。

*ch*<br/>
單個字元。

*皮茨斯爾克*<br/>
要複製到此`CStringT`物件的 null 中止字串。

*普斯特林姆格*<br/>
指向物件的記憶體管理器的`CStringT`指標。 有關 的詳細`IAtlStringMgr`資訊 和記憶體`CStringT`管理 ,請參閱使用[CStringT 的記憶體管理](../../atl-mfc-shared/memory-management-with-cstringt.md)。

*斯特斯爾克*<br/>
要複製到`CStringT``CStringT`此物件的現有物件。 有關`CThisString``CThisSimpleString`和 的詳細資訊,請參閱備註部分。

*varSrc*<br/>
要複製到此`CStringT`物件的變體物件。

*BaseType*<br/>
字串類的字元類型。 可以是下列其中一項：

**字元**(用於 ANSI 字串)。

**wchar_t(** 對於 Unicode 字串)。

TCHAR(適用於 ANSI 和 Unicode 字串)。

*bMFCDLL*<br/>
布爾,用於指定專案是否為 MFC DLL (TRUE) (FALSE)。

*系統字串*<br/>
必須`System::String`為 ,並且項目必須使用 /clr 編譯。

*pString*<br/>
`CStringT`物件的句柄。

### <a name="remarks"></a>備註

由於建構函數將輸入資料複製到新的分配存儲中,因此您應該注意可能會出現記憶體異常。 請注意,其中一些構造函數充當轉換函數。 例如,這允許您替換需要`CStringT`物件的 LPTSTR。

- `CStringT`:`LPCSTR``lpsz`從`CStringT`ANSI 字串建構 Unicode。 您還可以使用此建構函數載入字串資源,如下例所示。

- `CStringT(`: 從 Unicode 字串建構`CStringT``LPCWSTR``lpsz`a。

- `CStringT`( `const unsigned char*` `psz` ): 允許您`CStringT`建構 從指標到**未簽署的字元**。

> [!NOTE]
> 定義_CSTRING_DISABLE_NARROW_WIDE_CONVERSION巨集以關閉 ANSI 和 Unicode 字串之間的隱式字串轉換。 宏從支援轉換的編譯構造函數中排除。

請注意 *,strSrc*參數可以`CStringT``CThisSimpleString`是 或 物件。 對於`CStringT`,使用其預設實例化之`CString`一`CStringA`(、 或`CStringW`)。for `CThisSimpleString`,使用此**指標。** `CThisSimpleString`聲明[CSimpleStringT 類](../../atl-mfc-shared/reference/csimplestringt-class.md)的實體 ,它是一個較小的字串類,其內置`CStringT`功能比 類少。

重載運算符`CSimpleStringT<>&()`從`CSimpleStringT`聲明建`CStringT`構 物件。

> [!NOTE]
> 儘管可以創建`CStringT`包含嵌入的空字元的實例,但我們建議不要這樣做。 對`CStringT`包含嵌入的空字元的物件呼叫方法和運算元可以產生意外的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a>弦樂::*CStringT

銷毀`CStringT`物件。

```
~CStringT() throw();
```

### <a name="remarks"></a>備註

銷毀`CStringT`物件。

## <a name="cstringtdelete"></a><a name="delete"></a>CStringT::D埃萊特

從字串中刪除以給定索引中的字元開頭的字元。

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
要刪除`CStringT`的物件中第一個字元的零基索引。

*n( N) Count*<br/>
要刪除的字元數。

### <a name="return-value"></a>傳回值

已更改字串的長度。

### <a name="remarks"></a>備註

如果*nCount*長於字串,則將刪除字串的其餘部分。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a>CStringT:尋找

搜尋此字串以搜索字元或子字串的第一個匹配項。

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>參數

*pszSub*<br/>
要搜索的子字串。

*i 開始*<br/>
字串中要開始搜索的字元的索引,或從開頭開始的 0。

*ch*<br/>
要搜索的單個字元。

### <a name="return-value"></a>傳回值

此`CStringT`物件中第一個字元的零基索引,與請求的子字串或字元匹配;-1 如果未找到子字串或字元。

### <a name="remarks"></a>備註

函數重載以接受單個字元(類似於運行時函數`strchr`)和字串(類似於`strstr`)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a>弦樂::尋找

搜索此字串的第一個字元,該字元與*pszCharSet*中包含的任何字元匹配。

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
包含用於匹配的字元的字串。

### <a name="return-value"></a>傳回值

此字串中第一個字元的零基索引,該索引也位於*pszCharSet 中*;-1 如果沒有匹配項。

### <a name="remarks"></a>備註

尋找*pszCharSet*中任何字元的第一次出現。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a>CStringT:格式

以sprintf_s將資料格式轉換為`CStringT`C 樣式字元[sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)陣列 的方式將格式化資料寫入 。

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>參數

*nFormatID*<br/>
包含格式控制字串的字串資源識別碼。

*psz格式*<br/>
格式控制字串。

*引數*<br/>
選擇性引數。

### <a name="remarks"></a>備註

此函數在 中設定與儲存字元和值`CStringT`。 每個可選參數(如果有)根據*pszFormat 中的*相應格式規範或*nFormatID*標識的字串資源進行轉換和輸出。

如果字串物件本身作為 參數提供給`Format`,則調用將失敗。 例如,以下代碼將導致不可預知的結果:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

如需詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a>CStringT::格式訊息

設定消息字串的格式。

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>參數

*nFormatID*<br/>
包含未格式化訊息文字的字串資源識別碼。

*psz格式*<br/>
指向格式控制字串。 它將被掃描為插入和相應的格式。 格式字串類似於運行時函數*printf-style*格式字串,只不過它允許以任意順序插入參數。

*引數*<br/>
選擇性引數。

### <a name="remarks"></a>備註

函數需要消息定義作為輸入。 消息定義由*pszFormat*或*nFormatID*標識的字串資源確定。 該函數將格式化的消息文本複製到物件,`CStringT`並處理任何嵌入的插入序列(如果請求)。

> [!NOTE]
> `FormatMessage`嘗試為新格式化的字串分配系統記憶體。 如果此嘗試失敗,將自動引發記憶體異常。

每個插入必須具有遵循*pszFormat*或*nFormatID*參數的相應參數。 在消息文本中,支援多個轉義序列來動態格式化消息。 有關詳細資訊,請參閱 Windows SDK 中的 Windows[格式訊息](/windows/win32/api/winbase/nf-winbase-formatmessage)功能。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT::格式訊息V

使用變數參數清單設定訊息字串的格式。

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>參數

*psz格式*<br/>
指向格式控制字串。 它將被掃描為插入和相應的格式。 格式字串類似於運行時函數`printf`樣式格式字串,只不過它允許以任意順序插入參數。

*pArglist*<br/>
指向參數清單的指標。

### <a name="remarks"></a>備註

該函數需要消息定義作為輸入,由*pszFormat*確定。 函數將格式化的消息文本和參數的變數列表複製到`CStringT`物件,如果請求,處理任何嵌入的插入序列。

> [!NOTE]
> `FormatMessageV`呼叫[CStringT::FormatMessage](#formatmessage),它嘗試為新格式化的字串分配系統記憶體。 如果此嘗試失敗,將自動引發記憶體異常。

有關詳細資訊,請參閱 Windows SDK 中的 Windows[格式訊息](/windows/win32/api/winbase/nf-winbase-formatmessage)功能。

## <a name="cstringtformatv"></a><a name="formatv"></a>CStringT::格式V

使用變數參數清單設定訊息字串的格式。

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>參數

*psz格式*<br/>
指向格式控制字串。 它將被掃描為插入和相應的格式。 格式字串類似於運行時函數`printf`樣式格式字串,只不過它允許以任意順序插入參數。

*阿格斯*<br/>
指向參數清單的指標。

### <a name="remarks"></a>備註

以將資料`vsprintf_s`格式化為 C 樣式字元陣列的方式將格式化`CStringT`字串 和參數的變數清單寫入字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT:抓取環境變數

將字串設定為指定環境變數的值。

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>參數

*pszVar*<br/>
指定環境變數的 null 連接字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

從調用進程的環境塊檢索指定變數的值。 該值以 null 終止字串的形式出現。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a>CStringT:插入

在字串中的給定索引上插入單個字元或子字串。

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>參數

*iIndex*<br/>
將發生插入的字元的索引。

*psz*<br/>
指向要插入的子字串的指標。

*ch*<br/>
要插入的字元。

### <a name="return-value"></a>傳回值

已更改字串的長度。

### <a name="remarks"></a>備註

*iIndex*參數標識將移動的第一個字元,以便為字元或子字串騰出空間。 如果*nIndex*為零,則插入將在整個字串之前進行。 如果*nIndex*高於字串的長度,則函數將串聯當前字串和*ch*或*psz*提供的新材料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a>CStringT:左

從該`CStringT`物件中提取最左側的*nCount*字元,並返回提取的子字串的副本。

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>參數

*n( N) Count*<br/>
要從 `CStringT` 這個物件擷取的字元數。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 傳回的 `CStringT` 物件可以是空的。

### <a name="remarks"></a>備註

如果*nCount*超過字串長度,則提取整個字串。 `Left` 類似於 Basic `Left` 函式。

對於多位元組位元集 (MBCS),nCount將每個 8 位元序列視為字元,以便*nCount*將多位元*nCount*元元數乘以 2。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a>CStringT::載入字串

將*由 nID*識別的 Windows 字串`CStringT`資源讀取 到現有物件中。

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
模組實例的句柄。

*nID*<br/>
Windows 字串資源 ID。

*w語言識別碼*<br/>
字串資源的語言。

### <a name="return-value"></a>傳回值

如果資源負載成功,則非零;否則 0。

### <a name="remarks"></a>備註

使用指定的語言 *(w語言*) 從指定的模組 *(hA)* 載入字串資源 (*nID*)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a>CStringT::製作下

將`CStringT`物件轉換為小寫字串。

```
CStringT& MakeLower();
```

### <a name="return-value"></a>傳回值

生成的小寫字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a>CStringT::使反向

反轉`CStringT`物件中字元的順序。

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>傳回值

生成的反向字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a>CStringT::製作上

將`CStringT`物件轉換為大寫字串。

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>傳回值

生成的大寫字串。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a>CStringT:中

從該`CStringT`物件中提取長度*nCount*字元的子字串,從位置*iFirst*開始(基於零)。

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>參數

*i第一*<br/>
此`CStringT`物件中第一個字元的零點索引,該索引將包含在提取的子字串中。

*n( N) Count*<br/>
要從 `CStringT` 這個物件擷取的字元數。 如果未提供此參數,則提取字串的其餘部分。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 請注意,返回`CStringT`的物件可能為空。

### <a name="remarks"></a>備註

函數返回提取的子字串的副本。 `Mid`與基本中間函數類似(Basic 中的索引是一個基的除外)。

對於多位元組位元集 *(MBCS),nCount*表示每個 8 位元字元;也就是說,一個多位元組位元中的引線和跟蹤位元組計為兩個字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a>弦樂::OemToansi

將此`CStringT`物件中的所有字元從 OEM 字元集轉換為 ANSI 字元集。

```cpp
void OemToAnsi();
```

### <a name="remarks"></a>備註

如果定義了_UNICODE,則此功能不可用。

### <a name="example"></a>範例

請參閱[CStringT 範例:AnsiToOem](#ansitooem)。

## <a name="cstringtoperator-"></a><a name="operator_eq"></a>CStringT::運算符 |

為字串分配一個新值。

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

*斯特斯爾克*<br/>
要`CStringT`指定此字串 。

*Str*<br/>
`CThisSimpleString` 物件的參考。

*bMFCDLL*<br/>
指定專案是否為 MFC DLL 的布林。

*BaseType*<br/>
字串基類型。

*var*<br/>
要分配給此字串的變體物件。

*ch*<br/>
要分配給字串的 ANSI 或 Unicode 字元。

*皮茨斯爾克*<br/>
指向要分配的原始字串的指標。

### <a name="remarks"></a>備註

賦值運算元接受另`CStringT`一個物件、字元指標或單個字元。 您應該注意,每當使用此運算符時,都會發生記憶體異常,因為可以分配新的存儲。

有關`CThisSimpleString`的資訊 ,請參閱[CStringT::CStringT](#cstringt)的備註部分。

> [!NOTE]
> 儘管可以創建`CStringT`包含嵌入的空字元的實例,但我們建議不要這樣做。 對`CStringT`包含嵌入的空字元的物件呼叫方法和運算元可以產生意外的結果。

## <a name="cstringtoperator-"></a><a name="operator_add"></a>CStringT:運算符 |

串聯兩個字串或一個字元和一個字串。

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
要與字串串聯的 ANSI 或 Unicode 字元。

*ch2*<br/>
要與字串串聯的 ANSI 或 Unicode 字元。

*str1*<br/>
與`CStringT`字串或字串的聯的 。

*str2*<br/>
與`CStringT`字串或字串的聯的 。

*psz1*<br/>
指向 null 連接端接字串的指標,用於與字串或字串聯。

*psz2*<br/>
指向字串的指標,用於與字串或字串聯。

### <a name="remarks"></a>備註

`CStringT::operator+`函數有七種重載形式。 第一個版本串聯兩個現有`CStringT`物件。 接下來的兩個連接了一個`CStringT`物件和一個 null 終止的字串。 接下來的兩個連接了一個`CStringT`物件和一個ANSI字元。 最後兩個連接物件`CStringT`和 Unicode 字元。

> [!NOTE]
> 儘管可以創建`CStringT`包含嵌入的空字元的實例,但我們建議不要這樣做。 對`CStringT`包含嵌入的空字元的物件呼叫方法和運算元可以產生意外的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT::運算符 |

將字串聯到字串的末尾。

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

*Str*<br/>
`CThisSimpleString` 物件的參考。

*bMFCDLL*<br/>
指定專案是否為 MFC DLL 的布林。

*BaseType*<br/>
字串基類型。

*var*<br/>
要串聯到此字串的變體物件。

*ch*<br/>
要與字串串聯的 ANSI 或 Unicode 字元。

*皮茨斯爾克*<br/>
指向要串聯的原始字串的指標。

*斯特斯爾克*<br/>
要`CStringT`串聯到此字串。

### <a name="remarks"></a>備註

運算子接受另一`CStringT`個物件、字元指標或單個字元。 您應該注意,每當使用此串聯運算元時,都可能發生記憶體異常,因為可以為添加到此`CStringT`物件的字元分配新的存儲。

有關`CThisSimpleString`的資訊 ,請參閱[CStringT::CStringT](#cstringt)的備註部分。

> [!NOTE]
> 儘管可以創建`CStringT`包含嵌入的空字元的實例,但我們建議不要這樣做。 對`CStringT`包含嵌入的空字元的物件呼叫方法和運算元可以產生意外的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT::運算符 |

確定兩個字串在邏輯上是否相等。

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
A`CStringT`表示比較。

*str2*<br/>
A`CStringT`表示比較。

*psz1*<br/>
指向 null 終止字串的指標,用於比較。

*psz2*<br/>
指向 null 終止字串的指標,用於比較。

### <a name="remarks"></a>備註

測試左側的字串或字元是否等於右側的字串或字元,並相應地返回 TRUE 或 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a>CStringT::操作員!]

確定兩個字串在邏輯上是否不相等。

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
要與字串串聯的 ANSI 或 Unicode 字元。

*ch2*<br/>
要與字串串聯的 ANSI 或 Unicode 字元。

*str1*<br/>
A`CStringT`表示比較。

*str2*<br/>
A`CStringT`表示比較。

*psz1*<br/>
指向 null 終止字串的指標,用於比較。

*psz2*<br/>
指向 null 終止字串的指標,用於比較。

### <a name="remarks"></a>備註

測試左側的字串或字元是否不等於右側的字串或字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT::運算子&lt;

確定運算元左側的字串是否小於右側的字串。

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
A`CStringT`表示比較。

*str2*<br/>
A`CStringT`表示比較。

*psz1*<br/>
指向 null 終止字串的指標,用於比較。

*psz2*<br/>
指向 null 終止字串的指標,用於比較。

### <a name="remarks"></a>備註

字串之間的字典比較,按字元進行,直到:

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找不到任何差異，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT::運算子&gt;

確定運算元左側的字串是否大於右側的字串。

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
A`CStringT`表示比較。

*str2*<br/>
A`CStringT`表示比較。

*psz1*<br/>
指向 null 終止字串的指標,用於比較。

*psz2*<br/>
指向 null 終止字串的指標,用於比較。

### <a name="remarks"></a>備註

字串之間的字典比較,按字元進行,直到:

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT::運算子&lt;=

確定運算元左側的字串是否小於或等於右側的字串。

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
A`CStringT`表示比較。

*str2*<br/>
A`CStringT`表示比較。

*psz1*<br/>
指向 null 終止字串的指標,用於比較。

*psz2*<br/>
指向 null 終止字串的指標,用於比較。

### <a name="remarks"></a>備註

字串之間的字典比較,按字元進行,直到:

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT::運算子&gt;=

確定運算元左側的字串是大於還是等於右側的字串。

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>參數

*str1*<br/>
A`CStringT`表示比較。

*str2*<br/>
A`CStringT`表示比較。

*psz1*<br/>
指向字串的指標進行比較。

*psz2*<br/>
指向字串的指標進行比較。

### <a name="remarks"></a>備註

字串之間的字典比較,按字元進行,直到:

- 發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。

- 找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。

- 找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a>CStringT::刪除

從字串中刪除指定字元的所有實例。

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>參數

*ch 刪除*<br/>
要從字串中刪除的字元。

### <a name="return-value"></a>傳回值

從字串中刪除的字元計數。 如果字串未更改,則為零。

### <a name="remarks"></a>備註

字元的比較區分大小寫。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a>CStringT:取代

有兩個版本`Replace`。第一個版本使用另一個子字串替換子字串的一個或多個副本。 兩個子字串都是 null 終止的。 第二個版本使用另一個字元替換字元的一個或多個副本。 兩個版本都對存儲在中的`CStringT`字元數據進行操作。

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>參數

*pszOld*<br/>
指向 null 結束字串的指標,要取代為*pszNew*。

*pszNew*<br/>
指向 null 結束字串的指標,該指標取代*pszOld*。

*chOld*<br/>
要取代為*chNew*的字元 。

*ch New*<br/>
字元替代*chOld*。

### <a name="return-value"></a>傳回值

返回字元或子字串的替換實例數,如果字串未更改,則返回零。

### <a name="remarks"></a>備註

`Replace`可以更改字串長度,因為*pszNew*和*pszOld*不必具有相同的長度,並且舊子字串的幾個副本可以更改為新的子字串。 函數執行區分大小寫的匹配。

實體的`CStringT`範例 包括`CString`、`CStringA``CStringW`與 。

對於`CStringA``Replace`,使用 ANSI 或多位元組 (MBCS) 字元。 對於`CStringW``Replace`,使用寬字元。

對於`CString`,根據是否定義了下表中的常量,在編譯時選擇了字元數據類型。

|定義的常數|字元資料類型|
|----------------------|-------------------------|
|_UNICODE|寬字元|
|_MBCS|多位元組|
|兩者皆非|單位元組|
|兩者|未定義|

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a>CStringT::反向查找

搜尋此`CStringT`物件以搜索字元的最後一個匹配項。

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>參數

*ch*<br/>
要搜索的字元。

### <a name="return-value"></a>傳回值

此`CStringT`物件中最後一個字元與請求的字元匹配的零基索引,如果未找到該字元,則為 -1。

### <a name="remarks"></a>備註

此函數以執行時函數`strrchr`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a>CStringT:右

從該`CStringT`物件中提取最後一個(即最右 *)nCount*字元,並返回提取的子字串的副本。

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>參數

*n( N) Count*<br/>
要從 `CStringT` 這個物件擷取的字元數。

### <a name="return-value"></a>傳回值

`CStringT` 物件，該物件中包含所指定字元範圍的複本。 請注意,返回`CStringT`的物件可以為空。

### <a name="remarks"></a>備註

如果*nCount*超過字串長度,則提取整個字串。 `Right`與基本`Right`函數類似(Basic 中的索引為零除外)。

對於多位元組位元集 *(MBCS),nCount*表示每個 8 位元字元;也就是說,一個多位元組位元中的引線和跟蹤位元組計為兩個字元。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT::SetSysString

重新配置*pbstr*指向的 BSTR,並將`CStringT`物件的內容複製到其中,包括 NULL 字元。

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>參數

*pbstr*<br/>
指向字串的指標。

### <a name="return-value"></a>傳回值

新字串。

### <a name="remarks"></a>備註

根據`CStringT`物件的內容 *,pbstr*引用的 BSTR 值可能會更改。 如果記憶體不足,`CMemoryException`則函數會引發 。

此函數通常用於更改透過引用傳遞的用於自動化的字串的值。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT::範圍排除

從字串中提取字元,從第一個字元開始,這些字元不在*pszCharSet*標識的字元集中。

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
被解釋為一組字元的字串。

### <a name="return-value"></a>傳回值

包含字串中不在*pszCharSet*中的字元的子字串,從字串中的第一個字元開始,到在字串中找到的第一個字元結束,該字元也位於*pszCharSet*中(即,從字元串中的第一個字元開始,最多到但不包括找到*pszCharSet*的字串中的第一個字元)。 如果在字串中找不到*pszCharSet*中的字元,則返回整個字串。

### <a name="remarks"></a>備註

`SpanExcluding`從*pszCharSet*提取並返回字元第一次出現之前的所有字元(換句話說,不會返回*pszCharSet*中的字元及其後的所有字元)。 如果在字串中找不到*pszCharSet*中的字元,`SpanExcluding`則傳回整個字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a>CStringT::跨欄包括

從字串中提取字元,從第一個字元開始,這些字元位於*pszCharSet*標識的字元集中。

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>參數

*pszCharSet*<br/>
被解釋為一組字元的字串。

### <a name="return-value"></a>傳回值

包含*pszCharSet*中字串中的字元的子字串,從字串中的第一個字元開始,到在字串中找不到不在*pszCharSet*中的字元時結束。 `SpanIncluding`如果字串中的第一個字元不在指定的集中,則返回一個空子字串。

### <a name="remarks"></a>備註

如果字串的第一個字元不在字元集中,則`SpanIncluding`返回一個空字串。 否則,它將返回集中的連續字元序列。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a>CStringT::權杖化

在目標字串中尋找下一個權杖

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>參數

*pszTokens*<br/>
包含權杖分隔符的字串。 這些分隔符的順序並不重要。

*i 開始*<br/>
開始搜索的零基索引。

### <a name="return-value"></a>傳回值

包含`CStringT`當前權杖值的物件。

### <a name="remarks"></a>備註

函數`Tokenize`在目標字串中尋找下一個權杖。 *pszTokens*中的字元集指定要找到的權杖的可能分隔元。 對函數的每個調用`Tokenize`從*iStart*開始,跳過前導分隔符,`CStringT`並返回包含 當前令牌的物件,該標記是下一個分隔符字元的字串。 *iStart*的值將更新為結束分隔符字元之後的位置,如果達到字串的末尾,則為 -1。 以一系列呼叫`Tokenize`,可以使用*iStart*追蹤要讀取下一個權杖在字串中的位置,從而從目標字串的其餘部分中分解更多權杖。 當沒有更多的權杖時,函數將返回一個空字串 *,iStart*將設置為 -1。

與 CRT 標記strtok_s等函數不同[,_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)等函數`Tokenize`不會修改目標字串。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>備註

此範例的輸出如下所示:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a>CStringT:修剪

修剪字串中前導字元和尾隨字元。

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
指向包含要修剪的目標字元的字串的指標。 *pszTarget*中字元的所有前導和尾隨事件都將從物件`CStringT`中 修剪。

### <a name="return-value"></a>傳回值

返回修剪的字串。

### <a name="remarks"></a>備註

刪除以下一個所有前導和尾隨事件:

- *chTarget*指定的字元。

- 在*pszTargets*指定的字串中找到的所有字元。

- 空白。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>備註

此範例的輸出如下所示:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a>CStringT::修剪左

從字串修剪前導字元。

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
指向包含要修剪的目標字元的字串的指標。 *pszTarget*中字元的所有前導匹配項都將從物件`CStringT`中 修剪。

### <a name="return-value"></a>傳回值

產生的修剪字串。

### <a name="remarks"></a>備註

刪除以下一個所有前導和尾隨事件:

- *chTarget*指定的字元。

- 在*pszTargets*指定的字串中找到的所有字元。

- 空白。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a>CStringT::修剪權

從字串中修剪尾隨字元。

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>參數

*chTarget*<br/>
要修剪的目標字元。

*pszTargets*<br/>
指向包含要修剪的目標字元的字串的指標。 *pszTarget*中字元的所有尾隨發生都將`CStringT`從 物件中修剪。

### <a name="return-value"></a>傳回值

返回包含`CStringT`修剪的字串的物件。

### <a name="remarks"></a>備註

刪除以下一個的尾隨事件:

- *chTarget*指定的字元。

- 在*pszTargets*指定的字串中找到的所有字元。

- 空白。

版本`CStringT& TrimRight(XCHAR chTarget)`接受一個字元參數,並`CStringT`從字串數據末尾刪除該字元的所有副本。 它從字串的末尾開始,朝向前面工作。 當它找到不同的字元或字元數據用完時`CSTringT`,它將停止。

版本`CStringT& TrimRight(PCXSTR pszTargets)`接受一個 null 終止的字串,其中包含要搜索的所有不同字元。 它刪除`CStringT`物件中這些字元的所有副本。 它從字串的末尾開始,朝向前面工作。 當它找到不在目標字串中的字元或字元數據用完時`CStringT`,它將停止。 它不嘗試將整個目標字串匹配到 的末尾的`CStringT`子字串。

該`CStringT& TrimRight()`版本不需要參數。 它會從`CStringT`字串的末尾修剪任何尾隨的空白字元。 空白字元可以是換行元、空格或製表元。

-

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)
