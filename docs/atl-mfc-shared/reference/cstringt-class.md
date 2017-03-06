---
title: "CStringT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CString
- CStringT
- ATL::CStringT
- ATL.CStringT
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
caps.latest.revision: 33
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: 961dc75623ec04993d118e46e1d4ba73a9aadcec
ms.lasthandoff: 02/28/2017

---
# <a name="cstringt-class"></a>CStringT 類別
此類別代表`CStringT`物件。  
  
## <a name="syntax"></a>語法  
  
```  
 
template<typename BaseType, class StringTraits>  
class CStringT :   
public CSimpleStringT<BaseType,
                      _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                      ::c_bIsMFCDLLTraits>  
 
```  
  
#### <a name="parameters"></a>參數  
 `BaseType`  
 字串類別的字元類型。 可以是下列其中一項：  
  
- `char`（適用於 ANSI 字元字串）。  
  
- `wchar_t`（如需 Unicode 字元字串）。  
  
- **TCHAR** （適用於 ANSI 和 Unicode 字元字串）。  
  
 `StringTraits`  
 判斷字串類別是否需要 C 執行階段 (CRT) 程式庫支援和字串資源的位置。 可以是下列其中一項：  
  
- **StrTraitATL<> </> ** |`char` |**TCHAR、 ChTraitsCRT<> </> ** |`char` |**TCHAR > >**  
  
     此類別需要使用 CRT 支援並搜尋所指定的模組中的資源字串`m_hInstResource`（應用程式的模組類別的成員）。  
  
- **StrTraitATL<> </> ** |`char` |**TCHAR、 ChTraitsOS<> </> ** |`char` |**TCHAR > >**  
  
     此類別不需要 CRT 支援及尋找所指定的模組中的資源字串`m_hInstResource`（應用程式的模組類別的成員）。  
  
- **StrTraitMFC<> </> ** |`char` |**TCHAR、 ChTraitsCRT<> </> ** |`char` |**TCHAR > >**  
  
     此類別需要 CRT 支援，並使用標準的 MFC 搜尋演算法的資源字串的搜尋。  
  
- **StrTraitMFC<> </> ** |`char` |**TCHAR、 ChTraitsOS<> </> ** |`char` |**TCHAR > >**  
  
     此類別不需要 CRT 支援，並使用標準的 MFC 搜尋演算法的資源字串的搜尋。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CStringT::CStringT](#cstringt)|建構`CStringT`物件以各種方式。|  
|[CStringT:: ~ CStringT](#_dtorcstringt)|終結 `CStringT` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CStringT::AllocSysString](#allocsysstring)|配置`BSTR`從`CStringT`資料。|  
|[CStringT::AnsiToOem](#ansitooem)|可讓 OEM 字元集的 ANSI 字元集的就地轉換。|  
|[CStringT::AppendFormat](#appendformat)|將格式化的資料附加至現有`CStringT`物件。|  
|[CStringT::Collate](#collate)|比較兩個字串 （敏感的案例中，使用特定地區設定資訊）。|  
|[CStringT::CollateNoCase](#collatenocase)|比較兩個字串 （不區分大小寫，會使用地區設定特有的資訊）。|  
|[CStringT::Compare](#compare)|比較兩個字串 （區分大小寫）。|  
|[CStringT::CompareNoCase](#comparenocase)|比較兩個字串 （不區分大小寫）。|  
|[CStringT::Delete](#delete)|刪除從字串的字元。|  
|[CStringT::Find](#find)|尋找字元或更大的字串內子字串。|  
|[CStringT::FindOneOf](#findoneof)|尋找第一個比對從一組字元。|  
|[CStringT::Format](#format)|格式字串做為`sprintf`沒有。|  
|[CStringT::FormatMessage](#formatmessage)|格式化訊息字串。|  
|[CStringT::FormatMessageV](#formatmessagev)|格式化的訊息字串，使用變數引數清單。|  
|[CStringT::FormatV](#formatv)|使用變數引數清單的字串來格式化。|  
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|設定指定的環境變數的值的字串。|  
|[CStringT::Insert](#insert)|字串內的指定索引處插入單一字元或子字串。|  
|[CStringT::Left](#left)|擷取字串的左側的部分。|  
|[CStringT::LoadString](#loadstring)|載入現有`CStringT`從 Windows 資源的物件。|  
|[CStringT::MakeLower](#makelower)|轉換為小寫字元，這個字串中的所有字元。|  
|[CStringT::MakeReverse](#makereverse)|反轉字串。|  
|[CStringT::MakeUpper](#makeupper)|將轉換成大寫字元這個字串中的所有字元。|  
|[CStringT::Mid](#mid)|擷取字串的中間部分。|  
|[CStringT::OemToAnsi](#oemtoansi)|進行就地轉換從 ANSI 字元集的 OEM 字元集。|  
|[CStringT::Remove](#remove)|移除指定字串的字元。|  
|[CStringT::Replace](#replace)|取代指定使用其他字元的字元。|  
|[CStringT::ReverseFind](#reversefind)|尋找更大的字串; 內的字元會從結尾開始。|  
|[CStringT::Right](#right)|擷取字串的右側部分。|  
|[CStringT::SetSysString](#setsysstring)|設定現有`BSTR`物件從資料`CStringT`物件。|  
|[CStringT::SpanExcluding](#spanexcluding)|從字串中，不在所識別的字元集中的第一個字元開始擷取字元`pszCharSet`。|  
|[CStringT::SpanIncluding](#spanincluding)|擷取子字串，其中包含集合中的字元。|  
|[CStringT::Tokenize](#tokenize)|擷取目標字串中指定語彙基元。|  
|[CStringT::Trim](#trim)|會修剪所有開頭和尾端空白字元的字串。|  
|[CStringT::TrimLeft](#trimleft)|修剪前置空格字元的字串。|  
|[CStringT::TrimRight](#trimright)|修剪尾端空格字元字串。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 =](#operator_eq)|新值指派給`CStringT`物件。|  
|[CStringT::operator +](#operator_add)|串連兩個字串或字元和字串。|  
|[CStringT::operator + =](#operator_add_eq)|將新增至現有字串的結尾字串的串連。|  
|[CStringT::operator = =](#operator_eq_eq)|判斷兩個字串是否以邏輯方式相等。|  
|[CStringT::operator ！ =](#operator_neq)|判斷兩個字串是否以邏輯方式不相等。|  
|[CStringT::operator&lt;](#operator_lt)|判斷運算子左邊的字串是否小於右邊的字串。|  
|[CStringT::operator&gt;](#operator_gt)|判斷是否大於右邊的字串運算子左邊的字串。|  
|[CStringT::operator&lt;=](#operator_lt_eq)|判斷運算子左邊的字串是否小於或等於右邊的字串。|  
|[CStringT::operator&gt;=](#operator_gt_eq)|判斷運算子左邊的字串是否大於或等於右邊的字串。|  
  
## <a name="remarks"></a>備註  
 `CStringT`繼承自[CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)。 進階的功能，例如字元操作、 排序和搜尋，由實作`CStringT`。  
  
> [!NOTE]
> `CStringT`物件是能夠擲回例外狀況。 發生這種情況時`CStringT`物件因故用盡記憶體。  
  
 A`CStringT`物件包含可變長度的一連串字元。 `CStringT`提供函式和運算子使用類似的基本語法。 串連運算子和比較運算子，以及簡化的記憶體管理、 製作`CStringT`更輕鬆地使用比一般字元陣列的物件。  
  
> [!NOTE]
>  雖然您可以建立`CStringT`執行個體包含內嵌 null 字元時，我們建議您不要它。 在呼叫方法和運算子`CStringT`包含內嵌的 null 字元的物件可能會產生非預期的結果。  
  
 所使用的不同組合`BaseType`和`StringTraits`參數，`CStringT`物件可以在下列類型，也就是隨附已預先定義的 ATL 程式庫。  
  
 如果使用 ATL 應用程式中︰  
  
 `CString``CStringA`，和`CStringW`匯出從 MFC DLL (MFC90。DLL)，絕不會從使用者 Dll。 這為了避免`CStringT`從正在定義多次。  
  
> [!NOTE]
>  如果您在匯出時遇到連結器錯誤`CString`-MFC 擴充 DLL 中 Visual c + +.NET 2002年從衍生類別，並套用因應措施述知識庫文件 < 連結錯誤當您匯入 CString-Derived 類別 > (Q309801)，您應該移除因應措施的程式碼，因為這個問題已經修正在 Visual c + +.NET 2003年。 您可以找到知識庫文件，在 MSDN Library CD-ROM 或是在[http://support.microsoft.com/support](http://support.microsoft.com/support)。  
  
 在 MFC 應用程式中有下列的字串類型︰  
  
|CStringT 類型|宣告|  
|-------------------|-----------------|  
|`CStringA`|ANSI 字元輸入具有 CRT 支援字串。|  
|`CStringW`|Unicode 字元輸入具有 CRT 支援字串。|  
|`CString`|ANSI 和 Unicode 字元類型具有 CRT 支援。|  
  
 下列字串型別可用在專案位置**ATL_CSTRING_NO_CRT**定義︰  
  
|CStringT 類型|宣告|  
|-------------------|-----------------|  
|**CAtlStringA**|ANSI 字元輸入不具有 CRT 支援的字串。|  
|**CAtlStringW**|Unicode 字元輸入不具有 CRT 支援的字串。|  
|**CAtlString**|ANSI 和 Unicode 字元類型不具有 CRT 支援。|  
  
 下列字串型別可用在專案位置**ATL_CSTRING_NO_CRT**未定義︰  
  
|CStringT 類型|宣告|  
|-------------------|-----------------|  
|**CAtlStringA**|ANSI 字元輸入具有 CRT 支援字串。|  
|**CAtlStringW**|Unicode 字元輸入具有 CRT 支援字串。|  
|**CAtlString**|ANSI 和 Unicode 字元類型具有 CRT 支援。|  
  
 `CString`物件也具有下列特性︰  
  
- `CStringT`物件所能成長的串連作業的結果。  
  
- `CStringT`物件會遵循 < 值語意 （semantics） >。 想像成`CStringT`物件做為實際的字串，而非字串的指標。  
  
-   您可以自由取代`CStringT`物件`PCXSTR`函式引數。  
  
-   字串緩衝區的自訂記憶體管理。 如需詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## <a name="cstringt-predefined-types"></a>CStringT 預先定義的類型  
 因為`CStringT`用於定義字元類型的樣板引數 (任一[wchar_t](../../c-runtime-library/standard-types.md)或[char](../../c-runtime-library/standard-types.md)) 支援，方法參數型別可能很複雜情況下。 若要簡化此問題，一組預先定義的型別定義和使用整個`CStringT`類別。 下表列出各種類型︰  
  
|名稱|說明|  
|----------|-----------------|  
|`XCHAR`|單一字元 (可能是`wchar_t`或`char`) 與相同的字元類型`CStringT`物件。|  
|**YCHAR**|單一字元 (可能是`wchar_t`或`char`) 相反的字元類型`CStringT`物件。|  
|`PXSTR`|字元字串的指標 (可能是`wchar_t`或`char`) 與相同的字元類型`CStringT`物件。|  
|**PYSTR**|字元字串的指標 (可能是`wchar_t`或`char`) 相反的字元類型`CStringT`物件。|  
|`PCXSTR`|指標**const**字元字串 (可能是`wchar_t`或`char`) 與相同的字元類型`CStringT`物件。|  
|**PCYSTR**|指標**const**字元字串 (可能是`wchar_t`或`char`) 相反的字元類型`CStringT`物件。|  
  
> [!NOTE]
>  先前使用未記載之的方法的程式碼`CString`(例如**AssignCopy**) 必須使用下列的記錄的方法的程式碼，以取代`CStringT`(例如`GetBuffer`或`ReleaseBuffer`)。 這些方法都繼承自`CSimpleStringT`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## <a name="requirements"></a>需求  
  
|頁首|用於|  
|------------|-------------|  
|cstringt.h|僅限 MFC 的字串物件|  
|atlstr.h|非 MFC 字串物件|  
  
##  <a name="a-nameallocsysstringa--cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT::AllocSysString  
 配置類型的 Automation 相容字串`BSTR`複製的內容和`CStringT`物件，包括結束的 null 字元。  
  
```  
BSTR AllocSysString() const;  
```  
  
### <a name="return-value"></a>傳回值  
 新配置的字串。  
  
### <a name="remarks"></a>備註  
 在 MFC 程式中， [Afxthrowmemoryexception 類別](../../mfc/reference/cmemoryexception-class.md)存在記憶體不足，則會擲回。 在 ATL 程式[CAtlException](../../atl/reference/catlexception-class.md)就會擲回。 此函式通常用來自動化傳回的字串。  
  
 一般而言，如果這個字串會傳遞至 COM 函式做為 [in] 參數，則這樣要求呼叫者釋放字串。 這可以經由使用[SysFreeString](http://msdn.microsoft.com/en-us/8f230ee3-5f6e-4cb9-a910-9c90b754dcd3)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需詳細資訊，請參閱[Allocating 和釋放記憶體 BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)。  
  
 如需 Windows 中的 OLE 配置函式的詳細資訊，請參閱[SysAllocString](http://msdn.microsoft.com/en-us/9e0437a2-9b4a-4576-88b0-5cb9d08ca29b)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列範例示範 `CStringT::AllocSysString` 的用法。  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&105;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]  
  
##  <a name="a-nameansitooema--cstringtansitooem"></a><a name="ansitooem"></a>CStringT::AnsiToOem  
 將在此的所有字元都轉換`CStringT`OEM 字元集 ANSI 字元集中的物件。  
  
```  
void AnsiToOem();
```  
  
### <a name="remarks"></a>備註  
 函式不存在如果`_UNICODE`定義。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&106;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]  
  
##  <a name="a-nameappendformata--cstringtappendformat"></a><a name="appendformat"></a>CStringT::AppendFormat  
 將格式化的資料附加至現有`CStringT`物件。  
  
```  
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```  
  
### <a name="parameters"></a>參數  
 `pszFormat`  
 格式控制字串。  
  
 `nFormatID`  
 包含控制項的格式字串的字串資源識別碼。  
  
 `argument`  
 選擇性引數。  
  
### <a name="remarks"></a>備註  
 此函式格式，並將一系列字元和值在`CStringT`。 每個選擇性引數 （如果有的話） 會轉換並根據對應格式規格中附加`pszFormat`或從所識別的字串資源`nFormatID`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&107;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]  
  
##  <a name="a-namecollatea--cstringtcollate"></a><a name="collate"></a>CStringT::Collate  
 比較兩個字串使用泛用文字的函式`_tcscoll`。  
  
```  
int Collate(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 另一個字串用來做比較。  
  
### <a name="return-value"></a>傳回值  
 零的字串完全相同，如果< 0="" if="" this="">`CStringT`物件是小於`psz`，或 > 0，表示此`CStringT`物件是否大於`psz`。  
  
### <a name="remarks"></a>備註  
 一般文字函式`_tcscoll`，定義在 TCHAR。H，對應至`strcoll`， `wcscoll`，或`_mbscoll`，取決於編譯時期定義的字元集。 每個函式執行根據字碼頁字串的區分大小寫比較目前使用中。 如需詳細資訊，請參閱[strcoll、 wcscoll、 _mbscoll、 _strcoll_l、 _wcscoll_l、 _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。  
  
##  <a name="a-namecollatenocasea--cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT::CollateNoCase  
 比較兩個字串使用泛用文字的函式`_tcscoll`。  
  
```  
int CollateNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 另一個字串用來做比較。  
  
### <a name="return-value"></a>傳回值  
 零，如果相同的字串 （忽略大小寫） < 0="" if="" this=""> `CStringT`物件是小於`psz`（忽略大小寫） 或 > 0，表示此`CStringT`物件是否大於`psz`（忽略大小寫）。  
  
### <a name="remarks"></a>備註  
 一般文字函式`_tcscoll`，定義在 TCHAR。H，對應至`stricoll`， `wcsicoll`，或`_mbsicoll`，取決於編譯時期定義的字元集。 每個函式會執行不區分大小寫比較的字串，根據目前使用中的字碼頁。 如需詳細資訊，請參閱[strcoll、 wcscoll、 _mbscoll、 _strcoll_l、 _wcscoll_l、 _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&109;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]  
  
##  <a name="a-namecomparea--cstringtcompare"></a><a name="compare"></a>CStringT::Compare  
 比較兩個字串 （區分大小寫）。  
  
```  
int Compare(PCXSTR psz) const; 
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 另一個字串用來做比較。  
  
### <a name="return-value"></a>傳回值  
 零的字串完全相同，如果< 0="" if="" this="">`CStringT`物件是小於`psz`，或 > 0，表示此`CStringT`物件是否大於`psz`。  
  
### <a name="remarks"></a>備註  
 一般文字函式`_tcscmp`，定義在 TCHAR。H，對應至`strcmp`， `wcscmp`，或`_mbscmp`，取決於編譯時期定義的字元集。 每個函式執行區分大小寫的字串比較，並不會受到地區設定。 如需詳細資訊，請參閱[strcmp、 wcscmp、 _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)。  
  
 如果字串包含內嵌的 null，以供比較用，字串會視為在第一個內嵌的 null 字元會被截斷。  
  
### <a name="example"></a>範例  
 下列範例示範 `CStringT::Compare` 的用法。  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&110;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]  
  
##  <a name="a-namecomparenocasea--cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT::CompareNoCase  
 比較兩個字串 （不區分大小寫）。  
  
```  
int CompareNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>參數  
 `psz`  
 另一個字串用來做比較。  
  
### <a name="return-value"></a>傳回值  
 零，如果相同的字串 （忽略大小寫） <0 if="" this=""></0> `CStringT`物件是小於`psz`（忽略大小寫） 或 >&0;，表示此`CStringT`物件是否大於`psz`（忽略大小寫）。  
  
### <a name="remarks"></a>備註  
 一般文字函式`_tcsicmp`，定義在 TCHAR。H，對應至`_stricmp`，`_wcsicmp`或是`_mbsicmp`，取決於編譯時期定義的字元集。 每個函式執行不區分大小寫的字串比較。 比較取決於`LC_CTYPE`方面的地區設定，但不是`LC_COLLATE`。 如需詳細資訊，請參閱[_stricmp、 _wcsicmp、 _mbsicmp、 _stricmp_l、 _wcsicmp_l、 _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&111;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]  
  
##  <a name="a-namecstringta--cstringtcstringt"></a><a name="cstringt"></a>CStringT::CStringT  
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
 `pch`  
 長度的字元陣列的指標`nLength`、 無法以 null 結束。  
  
 `nLength`  
 中的字元數的計數`pch`。  
  
 `ch`  
 單一字元。  
  
 `pszSrc`  
 以 null 結束字串複製到這`CStringT`物件。  
  
 `pStringMgr`  
 指標的記憶體管理員`CStringT`物件。 如需有關`IAtlStringMgr`和記憶體管理`CStringT`，請參閱[記憶體管理與 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
 `strSrc`  
 將現有`CStringT`物件複製到這`CStringT`物件。 如需有關`CThisString`和`CThisSimpleString`，請參閱 < 備註 > 一節。  
  
 `varSrc`  
 Variant 物件複製到這`CStringT`物件。  
  
 `BaseType`  
 字串類別的字元類型。 可以是下列其中一項：  
  
 `char`（適用於 ANSI 字元字串）。  
  
 `wchar_t`（如需 Unicode 字元字串）。  
  
 `TCHAR`（適用於 ANSI 和 Unicode 字元字串）。  
  
 `bMFCDLL`  
 布林值，指定專案是否 MFC DLL (TRUE) 與否 (FALSE)。  
  
 `SystemString`  
 必須是`System::String`，以及必須使用 /clr 編譯專案。  
  
 `pString`  
 控制代碼`CStringT`物件。  
  
### <a name="remarks"></a>備註  
 因為建構函式會將輸入的資料複製到新配置的儲存體，您應該注意可能會造成例外狀況的記憶體。 請注意，某些這些建構函式做為轉換函式。 這可讓您以取代，比方說，`LPTSTR`其中`CStringT`預期物件。  
  
- `CStringT`( `LPCSTR` `lpsz` ): 建構 Unicode`CStringT`從 ANSI 字串。 您也可以使用這個建構函式載入字串資源，如下列範例所示。  
  
- `CStringT(``LPCWSTR` `lpsz` ): 建構`CStringT`從 Unicode 字串。  
  
- `CStringT`( `const unsigned char*` `psz` ): 可讓您建構`CStringT`指標從`unsigned char`。  
  
> [!NOTE]
>  定義**_CSTRING_DISABLE_NARROW_WIDE_CONVERSION**關閉之間進行隱含的字串轉換巨集[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]和[!INCLUDE[TLA#tla_unicode](../../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]字串。 從編譯建構函式支援轉換的排除巨集。  
  
 請注意，`strSrc`參數可以是`CStringT`或`CThisSimpleString`物件。 如`CStringT`，使用其中一個預設執行個體化 ( `CString`， `CStringA`，或`CStringW`); 如`CThisSimpleString`，使用`this`指標。 `CThisSimpleString`宣告的執行個體[CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)，這是較小的字串類別使用內建的功能比`CStringT`類別。  
  
 多載運算子`CSimpleStringT<>&()`建構`CStringT`物件從`CSimpleStringT`宣告。  
  
> [!NOTE]
>  雖然您可以建立`CStringT`執行個體包含內嵌 null 字元時，我們建議您不要它。 在呼叫方法和運算子`CStringT`包含內嵌的 null 字元的物件可能會產生非預期的結果。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&112;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]  
  
##  <a name="a-namedtorcstringta--cstringtcstringt"></a><a name="_dtorcstringt"></a>CStringT:: ~ CStringT  
 終結`CStringT`物件。  
  
```  
~CStringT() throw();
```  
  
### <a name="remarks"></a>備註  
 終結`CStringT`物件。  
  
##  <a name="a-namedeletea--cstringtdelete"></a><a name="delete"></a>CStringT::Delete  
 刪除與指定索引處的字元字串的字元。  
  
```  
int Delete(int iIndex, int nCount = 1);
```  
  
### <a name="parameters"></a>參數  
 `iIndex`  
 以零起始的索引中的第一個字元`CStringT`若要刪除的物件。  
  
 `nCount`  
 要移除的字元數。  
  
### <a name="return-value"></a>傳回值  
 變更字串的長度。  
  
### <a name="remarks"></a>備註  
 如果`nCount`超過字串，字串的其餘部分將會移除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&113;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]  
  
```Output  
Before: Soccer is best,
    but hockey is quicker!  
After: Soccer best,
    but hockey is quicker!  
```  
  
##  <a name="a-namefinda--cstringtfind"></a><a name="find"></a>CStringT::Find  
 這個字串中搜尋的字元或子字串的第一個相符項目。  
  
```  
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pszSub`  
 要搜尋的子字串。  
  
 `iStart`  
 若要開始，搜尋字串或 0 表示從頭開始的字元索引。  
  
 `ch`  
 要搜尋的單一字元。  
  
### <a name="return-value"></a>傳回值  
 在此第一個字元以零起始的索引`CStringT`符合要求的子字串或字元的物件; 如果沒有找到的子字串或字元的-1。  
  
### <a name="remarks"></a>備註  
 函式多載之後可接受這兩個單一字元 (類似於執行階段函式`strchr`) 和字串 (類似於`strstr`)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&114;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]  
  
##  <a name="a-namefindoneofa--cstringtfindoneof"></a><a name="findoneof"></a>CStringT::FindOneOf  
 此比對中所包含的任何字元的第一個字元字串中搜尋`pszCharSet`。  
  
```  
int FindOneOf(PCXSTR pszCharSet) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pszCharSet`  
 字串，包含用於比對的字元。  
  
### <a name="return-value"></a>傳回值  
 以零起始的索引也會在這個字串中的第一個字元`pszCharSet`; 如果沒有符合的結果為 –&1;。  
  
### <a name="remarks"></a>備註  
 尋找第一個字元的任何`pszCharSet`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&115;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]  
  
##  <a name="a-nameformata--cstringtformat"></a><a name="format"></a>CStringT::Format  
 格式化資料寫入`CStringT`在相同的方式來[sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)資料格式化成 C 樣式的字元陣列。  
  
```  
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```  
  
### <a name="parameters"></a>參數  
 `nFormatID`  
 包含控制項的格式字串的字串資源識別碼。  
  
 `pszFormat`  
 格式控制字串。  
  
 `argument`  
 選擇性引數。  
  
### <a name="remarks"></a>備註  
 此函式格式化，並儲存一連串字元和值`CStringT`。 每個選擇性引數 （如果有的話） 會轉換和輸出中的對應格式規格根據`pszFormat`或從所識別的字串資源`nFormatID`。  
  
 如果字串物件本身提供做為參數，將會失敗呼叫`Format`。 例如，下列程式碼將會造成無法預期的結果︰  
  
 [!code-cpp[NVC_ATLMFC_Utilities&116;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]  
  
 如需詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&117;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]  
  
##  <a name="a-nameformatmessagea--cstringtformatmessage"></a><a name="formatmessage"></a>CStringT::FormatMessage  
 格式化訊息字串。  
  
```  
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```  
  
### <a name="parameters"></a>參數  
 `nFormatID`  
 包含未格式化的訊息文字的字串資源識別碼。  
  
 `pszFormat`  
 格式控制字串的指標。 它會掃描插入並且據以格式化。 格式字串是類似於執行階段函式`printf`-樣式格式字串，但它可讓您插入任意順序的參數。  
  
 `argument`  
 選擇性引數。  
  
### <a name="remarks"></a>備註  
 函式需要訊息定義做為輸入。 訊息定義由`pszFormat`或是從所識別的字串資源`nFormatID`。 函式格式化的訊息將文字複製到`CStringT`處理任何內嵌的物件，如果要求的話，插入順序。  
  
> [!NOTE]
> `FormatMessage`嘗試配置系統記憶體最近格式化的字串。 如果此嘗試失敗，會自動擲回記憶體例外狀況。  
  
 每個插入必須有對應的參數下列`pszFormat`或是`nFormatID`參數。 訊息文字中支援數個逸出序列以動態方式格式化訊息。 如需詳細資訊，請參閱 Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&118;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]  
  
##  <a name="a-nameformatmessageva--cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT::FormatMessageV  
 格式化的訊息字串，使用變數引數清單。  
  
```  
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```  
  
### <a name="parameters"></a>參數  
 `pszFormat`  
 格式控制字串的指標。 它會掃描插入並且據以格式化。 格式字串是類似於執行階段函式`printf`-樣式格式字串，但它可讓您插入任意順序的參數。  
  
 `pArgList`  
 引數清單的指標。  
  
### <a name="remarks"></a>備註  
 函式需要訊息定義做為輸入，取決於`pszFormat`。 函式會將格式化的訊息文字和變數的引數清單複製`CStringT`處理任何內嵌的物件，如果要求的話，插入順序。  
  
> [!NOTE]
> `FormatMessageV`呼叫[CStringT::FormatMessage](#formatmessage)，嘗試為新格式的字串配置系統記憶體。 如果此嘗試失敗，會自動擲回記憶體例外狀況。  
  
 如需詳細資訊，請參閱 Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameformatva--cstringtformatv"></a><a name="formatv"></a>CStringT::FormatV  
 格式化的訊息字串，使用變數引數清單。  
  
```  
void FormatV(PCXSTR pszFormat, va_list args);
```  
  
### <a name="parameters"></a>參數  
 `pszFormat`  
 格式控制字串的指標。 它會掃描插入並且據以格式化。 格式字串是類似於執行階段函式`printf`-樣式格式字串，但它可讓您插入任意順序的參數。  
  
 `args`  
 引數清單的指標。  
  
### <a name="remarks"></a>備註  
 將格式化的字串和引數的變數清單`CStringT`在同一個字串的方式來`vsprintf_s`資料格式化成 C 樣式的字元陣列。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&119;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities #&120;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]  
  
##  <a name="a-namegetenvironmentvariablea--cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable  
 設定指定的環境變數的值的字串。  
  
```  
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```  
  
### <a name="parameters"></a>參數  
 `pszVar`  
 以 null 終止的字串，指定環境變數的指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 擷取指定之變數的值從呼叫處理序的環境區塊。 值會以 null 結束的字元字串的形式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&121;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]  
  
##  <a name="a-nameinserta--cstringtinsert"></a><a name="insert"></a>CStringT::Insert  
 字串內的指定索引處插入單一字元或子字串。  
  
```  
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```  
  
### <a name="parameters"></a>參數  
 `iIndex`  
 之前插入會進行字元的索引。  
  
 `psz`  
 要插入的子字串的指標。  
  
 `ch`  
 要插入的字元。  
  
### <a name="return-value"></a>傳回值  
 變更字串的長度。  
  
### <a name="remarks"></a>備註  
 `iIndex`參數會識別將會移至騰出空間給字元或子字串的第一個字元。 如果`nIndex`為零，整個字串之前進行插入。 如果`nIndex`多於字串的長度，此函數會串連存在字串和新的資料提供由`ch`或`psz`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&122;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]  
  
##  <a name="a-namelefta--cstringtleft"></a><a name="left"></a>CStringT::Left  
 從 `nCount` 這個物件中擷取最左邊的 `CStringT` 個字元，並傳回所擷取子字串的複本。  
  
```  
CStringT Left(int nCount) const; 
```  
  
### <a name="parameters"></a>參數  
 `nCount`  
 要從 `CStringT` 這個物件擷取的字元數。  
  
### <a name="return-value"></a>傳回值  
 `CStringT` 物件，該物件中包含所指定字元範圍的複本。 傳回的 `CStringT` 物件可以是空的。  
  
### <a name="remarks"></a>備註  
 如果 `nCount` 超過字串長度，則會擷取整個字串。 `Left` 類似於 Basic `Left` 函式。  
  
 對於多位元組字元集 (MBCS)，`nCount` 會將每個 8 位元序列視為一個字元，因此，`nCount` 會傳回多位元組字元數的兩倍。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&123;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]  
  
##  <a name="a-nameloadstringa--cstringtloadstring"></a><a name="loadstring"></a>CStringT::LoadString  
 讀取所識別的 Windows 字串資源`nID`，到現有`CStringT`物件。  
  
```  
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `hInstance`  
 模組的執行個體控制代碼。  
  
 `nID`  
 Windows 字串資源識別碼。  
  
 `wLanguageID`  
 字串資源的語言。  
  
### <a name="return-value"></a>傳回值  
 如果資源的載入作業成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 載入字串資源 ( `nID`) 從指定的模組 ( `hInstance`) 使用指定的語言 ( `wLanguage`)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&124;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]  
  
##  <a name="a-namemakelowera--cstringtmakelower"></a><a name="makelower"></a>CStringT::MakeLower  
 將轉換`CStringT`小寫的字串物件。  
  
```  
CStringT& MakeLower();
```  
  
### <a name="return-value"></a>傳回值  
 產生小寫的字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&125;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]  
  
##  <a name="a-namemakereversea--cstringtmakereverse"></a><a name="makereverse"></a>CStringT::MakeReverse  
 反轉順序中的字元`CStringT`物件。  
  
```  
CStringT& MakeReverse();
```  
  
### <a name="return-value"></a>傳回值  
 所產生的反轉字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&126;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]  
  
##  <a name="a-namemakeuppera--cstringtmakeupper"></a><a name="makeupper"></a>CStringT::MakeUpper  
 將轉換`CStringT`大寫的字串物件。  
  
```  
CStringT& MakeUpper();
```  
  
### <a name="return-value"></a>傳回值  
 產生大寫的字串。  
  
### <a name="remarks"></a>備註  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&127;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]  
  
##  <a name="a-namemida--cstringtmid"></a><a name="mid"></a>CStringT::Mid  
 擷取子字串的長度`nCount`從這個字元`CStringT`物件，位置開始`iFirst`（以零為起始）。  
  
```  
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const; 
```  
  
### <a name="parameters"></a>參數  
 `iFirst`  
 在此第一個字元以零起始的索引`CStringT`擷取子字串中要包含的物件。  
  
 `nCount`  
 要從 `CStringT` 這個物件擷取的字元數。 如果未提供此參數，會擷取字串的其餘部分。  
  
### <a name="return-value"></a>傳回值  
 `CStringT` 物件，該物件中包含所指定字元範圍的複本。 請注意，傳回`CStringT`可能是空的物件。  
  
### <a name="remarks"></a>備註  
 函數會傳回所擷取子字串的複本。 `Mid`類似於基本 Mid 函式 （之處在於 Basic 中的索引是以&1; 起始）。  
  
 對於多位元組字元集 (MBCS)，`nCount`指的是每個 8 位元字元; 也就是前置和後隨位元組中其中一個多位元組字元會視為兩個字元。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&128;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]  
  
##  <a name="a-nameoemtoansia--cstringtoemtoansi"></a><a name="oemtoansi"></a>CStringT::OemToAnsi  
 將在此的所有字元都轉換`CStringT`ANSI 字元集的 OEM 字元集中的物件。  
  
```  
void OemToAnsi();
```  
  
### <a name="remarks"></a>備註  
 此函式不存在如果`_UNICODE`定義。  
  
### <a name="example"></a>範例  
 請參閱範例[CStringT::AnsiToOem](#ansitooem)。  
  
##  <a name="a-nameoperatoradda--cstringtoperator-"></a><a name="operator_add"></a>CStringT::operator +  
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
 `ch1`  
 要串連的字串為 ANSI 或 Unicode 字元。  
  
 `ch2`  
 要串連的字串為 ANSI 或 Unicode 字元。  
  
 `str1`  
 A`CStringT`来串連的字串或字元。  
  
 `str2`  
 A`CStringT`来串連的字串或字元。  
  
 `psz1`  
 以 null 終止的字串來串連字串或字元，與指標。  
  
 `psz2`  
 要串連的字串或字元字串的指標。  
  
### <a name="remarks"></a>備註  
 有七個多載形式的`CStringT::operator+`函式。 第一個版本會串連兩個現有`CStringT`物件。 後面兩個串連`CStringT`物件和 null 結尾字串。 後面兩個串連`CStringT`物件和一個 ANSI 字元。 這兩個串連`CStringT`物件和 Unicode 字元。  
  
> [!NOTE]
>  雖然您可以建立`CStringT`執行個體包含內嵌 null 字元時，我們建議您不要它。 在呼叫方法和運算子`CStringT`包含內嵌的 null 字元的物件可能會產生非預期的結果。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&140;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]  
  
##  <a name="a-nameoperatoraddeqa--cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT::operator + =  
 串連字串結尾的字元。  
  
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
 str  
 對 `CThisSimpleString` 物件的參考。  
  
 `bMFCDLL`  
 布林值，指定專案是否 MFC DLL。  
  
 `BaseType`  
 字串基底型別。  
  
 `var`  
 若要連接到此字串的 variant 物件。  
  
 `ch`  
 要串連的字串為 ANSI 或 Unicode 字元。  
  
 `pszSrc`  
 串連的原始字串指標。  
  
 `strSrc`  
 A`CStringT`要與這個字串串連。  
  
### <a name="remarks"></a>備註  
 運算子可接受另一個`CStringT`物件、 字元指標或單一字元。 您應該要注意的例外狀況可能是每當您使用這個串連運算子，因為新的儲存體可配置的字元新增至這個記憶體`CStringT`物件。  
  
 如需`CThisSimpleString`，請參閱 < 備註 > 一節[CStringT::CStringT](#cstringt)。  
  
> [!NOTE]
>  雖然您可以建立`CStringT`執行個體包含內嵌 null 字元時，我們建議您不要它。 在呼叫方法和運算子`CStringT`包含內嵌的 null 字元的物件可能會產生非預期的結果。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&141; 毫秒](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]  
  
##  <a name="a-nameoperatoreqeqa--cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT::operator = =  
 判斷兩個字串是否以邏輯方式相等。  
  
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
 `ch1`  
 比較為 ANSI 或 Unicode 字元。  
  
 `ch2`  
 比較為 ANSI 或 Unicode 字元。  
  
 `str1`  
 A`CStringT`進行比較。  
  
 `str2`  
 A`CStringT`進行比較。  
  
 `psz1`  
 以 null 終止的字串比較的指標。  
  
 `psz2`  
 以 null 終止的字串比較的指標。  
  
### <a name="remarks"></a>備註  
 測試是否字串或字元，在左邊的字串或字元在右側，且傳回 TRUE 或 FALSE 據以。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&142;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]  
  
##  <a name="a-nameoperatorneqa--cstringtoperator-"></a><a name="operator_neq"></a>CStringT::operator ！ =  
 判斷兩個字串是否以邏輯方式不相等。  
  
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
 `ch1`  
 要串連的字串為 ANSI 或 Unicode 字元。  
  
 `ch2`  
 要串連的字串為 ANSI 或 Unicode 字元。  
  
 `str1`  
 A`CStringT`進行比較。  
  
 `str2`  
 A`CStringT`進行比較。  
  
 `psz1`  
 以 null 終止的字串比較的指標。  
  
 `psz2`  
 以 null 終止的字串比較的指標。  
  
### <a name="remarks"></a>備註  
 如果字串或字元左邊不相等的字串或字元右邊的測試。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&143;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]  
  
##  <a name="a-nameoperatorlta--cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT::operator&lt;  
 判斷運算子左邊的字串是否小於右邊的字串。  
  
```  
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 A`CStringT`進行比較。  
  
 `str2`  
 A`CStringT`進行比較。  
  
 `psz1`  
 以 null 終止的字串比較的指標。  
  
 `psz2`  
 以 null 終止的字串比較的指標。  
  
### <a name="remarks"></a>備註  
 直到逐字元的字串之間的字彙比較︰  
  
-   發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。  
  
-   找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。  
  
-   找不到任何差異，並發現字串具有相同的字串數，因此字串是相等的。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&144;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]  
  
##  <a name="a-nameoperatorgta--cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT::operator&gt;  
 判斷是否大於右邊的字串運算子左邊的字串。  
  
```  
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 A`CStringT`進行比較。  
  
 `str2`  
 A`CStringT`進行比較。  
  
 `psz1`  
 以 null 終止的字串比較的指標。  
  
 `psz2`  
 以 null 終止的字串比較的指標。  
  
### <a name="remarks"></a>備註  
 直到逐字元的字串之間的字彙比較︰  
  
-   發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。  
  
-   找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。  
  
-   找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&145;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]  
  
##  <a name="a-nameoperatorlteqa--cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT::operator&lt;=  
 判斷運算子左邊的字串是否小於或等於右邊的字串。  
  
```  
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 A`CStringT`進行比較。  
  
 `str2`  
 A`CStringT`進行比較。  
  
 `psz1`  
 以 null 終止的字串比較的指標。  
  
 `psz2`  
 以 null 終止的字串比較的指標。  
  
### <a name="remarks"></a>備註  
 直到逐字元的字串之間的字彙比較︰  
  
-   發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。  
  
-   找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。  
  
-   找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&146;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]  
  
##  <a name="a-nameoperatorgteqa--cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT::operator&gt;=  
 判斷運算子左邊的字串是否大於或等於右邊的字串。  
  
```  
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>參數  
 `str1`  
 A`CStringT`進行比較。  
  
 `str2`  
 A`CStringT`進行比較。  
  
 `psz1`  
 若要比較的字串指標。  
  
 `psz2`  
 若要比較的字串指標。  
  
### <a name="remarks"></a>備註  
 直到逐字元的字串之間的字彙比較︰  
  
-   發現兩個對應的字元不相等，並將其比較的結果做為字串間比較的結果。  
  
-   找不到任何差異，但有一個字串的字元數比另一個字串還多，因而將較短的字串視為小於較長的字串。  
  
-   找到相等的字串，並發現字串具有相同的字串數，因此字串是相等的。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&147; 的形式](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]  
  
##  <a name="a-nameremovea--cstringtremove"></a><a name="remove"></a>CStringT::Remove  
 從字串中移除指定之字元的所有執行個體。  
  
```  
int Remove(XCHAR chRemove);
```  
  
### <a name="parameters"></a>參數  
 `chRemove`  
 要從字串中移除的字元。  
  
### <a name="return-value"></a>傳回值  
 從字串中移除的字元計數。 如果字串不會變更為零。  
  
### <a name="remarks"></a>備註  
 字元的比較會區分大小寫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&129;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]  
  
##  <a name="a-namereplacea--cstringtreplace"></a><a name="replace"></a>CStringT::Replace  
 有兩個版本的`Replace`。第一個版本會使用另一個子字串取代子字串的一或多個複本。 兩個子字串是以 null 結束。 第二個版本會使用另一個字元取代字元的一或多個的複本。 若對字元資料儲存在這兩個版本`CStringT`。  
  
```  
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```  
  
### <a name="parameters"></a>參數  
 `pszOld`  
 以 null 終止的字串來取代指標`pszNew`。  
  
 `pszNew`  
 指向以 null 結束的字串，以取代`pszOld`。  
  
 `chOld`  
 要被取代的字元`chNew`。  
  
 `chNew`  
 字元取代`chOld`。  
  
### <a name="return-value"></a>傳回值  
 傳回已取代的字元或子字串或為零的執行個體數目，如果字串不會變更。  
  
### <a name="remarks"></a>備註  
 `Replace`變更字串長度，因為`pszNew`和`pszOld`不必有相同的長度和舊的子字串的多個複本可以變更到新的專案。 函式會執行區分大小寫的相符項目。  
  
 範例`CStringT`執行個體`CString`， `CStringA`，和`CStringW`。  
  
 如`CStringA`，`Replace`適用於 ANSI 或多位元組 (MBCS) 字元。 如`CStringW`，`Replace`搭配寬字元。  
  
 如`CString`，字元資料型別已選取在編譯時期，根據是否定義下表中的常數。  
  
|定義的常數|字元資料類型|  
|----------------------|-------------------------|  
|`_UNICODE`|寬字元|  
|`_MBCS`|多位元組字元|  
|都不|單一位元組字元|  
|兩種模式|未定義|  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&200;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]  
  
##  <a name="a-namereversefinda--cstringtreversefind"></a><a name="reversefind"></a>CStringT::ReverseFind  
 搜尋這`CStringT`字元的最後一個相符項目的物件。  
  
```  
int ReverseFind(XCHAR ch) const throw();
```  
  
### <a name="parameters"></a>參數  
 `ch`  
 要搜尋的字元。  
  
### <a name="return-value"></a>傳回值  
 在這個最後一個字元的以零起始的索引`CStringT`符合要求的字元，則為 –&1;，如果找不到該字元的物件。  
  
### <a name="remarks"></a>備註  
 函式是執行階段函式類似`strrchr`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&130;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]  
  
##  <a name="a-namerighta--cstringtright"></a><a name="right"></a>CStringT::Right  
 擷取最後一個 (也就是最右邊)`nCount`從這個字元`CStringT`物件，並傳回所擷取子字串的複本。  
  
```  
CStringT Right(int nCount) const; 
```  
  
### <a name="parameters"></a>參數  
 `nCount`  
 要從 `CStringT` 這個物件擷取的字元數。  
  
### <a name="return-value"></a>傳回值  
 `CStringT` 物件，該物件中包含所指定字元範圍的複本。 請注意，傳回`CStringT`物件可以是空白。  
  
### <a name="remarks"></a>備註  
 如果 `nCount` 超過字串長度，則會擷取整個字串。 `Right`類似於基本`Right`函式 （不包括任何 Basic 中的索引以零為起始）。  
  
 對於多位元組字元集 (MBCS)，`nCount`指的是每個 8 位元字元; 也就是前置和後隨位元組中其中一個多位元組字元會視為兩個字元。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&131;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]  
  
##  <a name="a-namesetsysstringa--cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT::SetSysString  
 重新配置`BSTR`指向`pbstr`複製的內容和`CStringT`物件，包括`NULL`字元。  
  
```  
BSTR SetSysString(BSTR* pbstr) const; 
```  
  
### <a name="parameters"></a>參數  
 `pbstr`  
 字元字串指標。  
  
### <a name="return-value"></a>傳回值  
 新字串。  
  
### <a name="remarks"></a>備註  
 視內容而定`CStringT`物件、 值`BSTR`所參考的`pbstr`可以變更。 函式會擲回`CMemoryException`如果存在記憶體不足。  
  
 此函式通常用來變更自動化的傳址方式傳遞的字串值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&132;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]  
  
##  <a name="a-namespanexcludinga--cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT::SpanExcluding  
 從字串中，不在所識別的字元集中的第一個字元開始擷取字元`pszCharSet`。  
  
```  
CStringT SpanExcluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>參數  
 `pszCharSet`  
 字串會解譯為一組字元。  
  
### <a name="return-value"></a>傳回值  
 包含在字串中的字元的子字串`pszCharSet`、 從字串中的第一個字元開始和結束，同時也是在字串中找到的第一個字元`pszCharSet`(也就從第一個字元字串中，設定，但不包括字串中所找到的第一個字元開始`pszCharSet`)。 如果中的字元，它會傳回整個字串`pszCharSet`字串中找到。  
  
### <a name="remarks"></a>備註  
 `SpanExcluding`擷取和傳回前面的字元從第一個出現的所有字元`pszCharSet`(亦即，從字元`pszCharSet`並不會傳回下列字串中的所有字元)。 如果字元; 沒有`pszCharSet`在字串中，然後找到`SpanExcluding`傳回整個字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&133;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]  
  
##  <a name="a-namespanincludinga--cstringtspanincluding"></a><a name="spanincluding"></a>CStringT::SpanIncluding  
 從字串中，所識別的字元集中的第一個字元開始擷取字元`pszCharSet`。  
  
```  
CStringT SpanIncluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>參數  
 `pszCharSet`  
 字串會解譯為一組字元。  
  
### <a name="return-value"></a>傳回值  
 包含在字串中的字元的子字串`pszCharSet`、 從字串中的第一個字元開始和結束時不在字串中找到字元`pszCharSet`。 `SpanIncluding`如果字串中的第一個字元不是指定集合中，則傳回空的子字串。  
  
### <a name="remarks"></a>備註  
 如果字串的第一個字元不在字元集，則`SpanIncluding`會傳回空字串。 否則，它會傳回集合中的連續字元序列。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&134;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]  
  
##  <a name="a-nametokenizea--cstringttokenize"></a><a name="tokenize"></a>CStringT::Tokenize  
 在目標字串中尋找下一個語彙基元  
  
```  
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const; 
```  
  
### <a name="parameters"></a>參數  
 `pszTokens`  
 包含 token 分隔符號的字串。 這些分隔符號的順序並不重要。  
  
 `iStart`  
 要開始搜尋的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A`CStringT`物件，其中包含目前語彙基元的值。  
  
### <a name="remarks"></a>備註  
 `Tokenize`函式在目標字串中尋找下一個語彙基元。 中的字元組`pszTokens`指定可能要找的語彙基元的分隔符號。 每次呼叫`Tokenize`函式開始`iStart`、 略過開頭分隔符號，並傳回`CStringT`物件，其中包含目前語彙基元，直到下一步的分隔符號字元的字元的字串。 值`iStart`更新，而如果已到達字串結尾後結束分隔符號字元，則為-1 的位置。 多個權杖可以由一系列的呼叫中斷超出目標字串的其餘部分`Tokenize`，並使用`iStart`來追蹤要讀取的下一個語彙基元的字串中的位置。 當沒有多個語彙基元函式會傳回空字串和`iStart`會設為-1。  
  
 不同於 CRT 語彙基元化函式，例如[strtok_s、 _strtok_s_l、 wcstok_s、 _wcstok_s_l、 _mbstok_s、 _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)，`Tokenize`不會修改目標字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&135;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]  
  
### <a name="remarks"></a>備註  
 此範例的輸出如下所示︰  
  
 `Resulting Token: First`  
  
 `Resulting Token: Second`  
  
 `Resulting Token: Third`  
  
##  <a name="a-nametrima--cstringttrim"></a><a name="trim"></a>CStringT::Trim  
 修剪開頭和結尾字元字串。  
  
```  
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```  
  
### <a name="parameters"></a>參數  
 `chTarget`  
 要修剪的目標字元。  
  
 `pszTargets`  
 字串，包含要修剪的目標字元指標。 所有前置和後端中出現的字元`pszTarget`中將被去除`CStringT`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回已修剪的字串。  
  
### <a name="remarks"></a>備註  
 移除所有開頭和尾端出現下列其中一項︰  
  
-   指定的字元`chTarget.`  
  
-   在所指定的字串中找到的所有字元`pszTargets.`  
  
-   空白字元。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&136;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]  
  
### <a name="remarks"></a>備註  
 此範例的輸出如下所示︰  
  
 `Before: "******Soccer is best, but liquor is quicker!!!!!"`  
  
 `After : "Soccer is best, but liquor is quicker"`  
  
##  <a name="a-nametrimlefta--cstringttrimleft"></a><a name="trimleft"></a>CStringT::TrimLeft  
 修剪前置字元的字串。  
  
```  
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```  
  
### <a name="parameters"></a>參數  
 `chTarget`  
 要修剪的目標字元。  
  
 `pszTargets`  
 字串，包含要修剪的目標字元指標。 所有開頭指定項目中的字元`pszTarget`中將被去除`CStringT`物件。  
  
### <a name="return-value"></a>傳回值  
 產生已修剪的字串。  
  
### <a name="remarks"></a>備註  
 移除所有開頭和尾端出現下列其中一項︰  
  
-   指定的字元`chTarget.`  
  
-   在所指定的字串中找到的所有字元`pszTargets.`  
  
-   空白字元。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&137;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]  
  
##  <a name="a-nametrimrighta--cstringttrimright"></a><a name="trimright"></a>CStringT::TrimRight  
 會修剪尾端字元字串。  
  
```  
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```  
  
### <a name="parameters"></a>參數  
 `chTarget`  
 要修剪的目標字元。  
  
 `pszTargets`  
 字串，包含要修剪的目標字元指標。 所有後端中出現的字元`pszTarget`中將被去除`CStringT`物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`CStringT`物件，其中包含已修剪的字串。  
  
### <a name="remarks"></a>備註  
 移除尾端的下列其中一項目︰  
  
-   指定的字元`chTarget.`  
  
-   在所指定的字串中找到的所有字元`pszTargets.`  
  
-   空白字元。  
  
 `CStringT& TrimRight(XCHAR chTarget)`版本會接受一個字元的參數和結尾會移除該字元的所有複本`CStringT`字串資料。 它會從字串結尾開始，且前端運作。 當它找到不同的字元或停止`CSTringT`用盡字元資料。  
  
 `CStringT& TrimRight(PCXSTR pszTargets)`版本接受以 null 結束的字串，包含要搜尋所有不同的字元。 它會移除這些字元的所有複本`CStringT`物件。 它會從字串的結尾，然後前端的運作方式。 當它找到的字元; 不在目標字串中，或停止`CStringT`用盡字元資料。 它不會嘗試比對整個目標字串結尾的子字串`CStringT`。  
  
 `CStringT& TrimRight()`版本不需要參數。 它會修剪任何尾端空白字元結尾`CStringT`字串。 插入換行符號、 空格或定位點，可以是空白字元。  
  
-  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATLMFC_Utilities #&138;](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)



