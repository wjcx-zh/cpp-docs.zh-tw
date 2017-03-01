---
title: "CComBSTR 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComBSTR
- CComBSTR
- ATL.CComBSTR
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
caps.latest.revision: 21
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
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: e7b61a5826836e7d26a0d470631d7230f7b7be56
ms.lasthandoff: 02/24/2017

---
# <a name="ccombstr-class"></a>CComBSTR 類別
這個類別是包裝函式`BSTR`s。  
  
## <a name="syntax"></a>語法  
  
```
class CComBSTR
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComBSTR::CComBSTR](#ccombstr)|建構函式。|  
|[CComBSTR:: ~ CComBSTR](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComBSTR::Append](#append)|字串附加至`m_str`。|  
|[CComBSTR::AppendBSTR](#appendbstr)|將附加`BSTR`到`m_str`。|  
|[CComBSTR::AppendBytes](#appendbytes)|將指定的位元組數附加`m_str`。|  
|[CComBSTR::ArrayToBSTR](#arraytobstr)|建立`BSTR`safearray 中每個項目的第一個字元，並將它附加`CComBSTR`物件。|  
|[CComBSTR::AssignBSTR](#assignbstr)|指派`BSTR`到`m_str`。|  
|[CComBSTR::Attach](#attach)|附加`BSTR`到`CComBSTR`物件。|  
|[CComBSTR::BSTRToArray](#bstrtoarray)|建立以零為起始的一維 safearray，其中的陣列的每個項目是從字元`CComBSTR`物件。|  
|[CComBSTR::ByteLength](#bytelength)|傳回的長度`m_str`以位元組為單位。|  
|[CComBSTR::Copy](#copy)|傳回一份`m_str`。|  
|[CComBSTR::CopyTo](#copyto)|傳回一份`m_str`透過**[out]**參數|  
|[CComBSTR::Detach](#detach)|卸離`m_str`從`CComBSTR`物件。|  
|[CComBSTR::Empty](#empty)|釋出`m_str`。|  
|[CComBSTR::Length](#length)|傳回的長度`m_str`。|  
|[CComBSTR::LoadString](#loadstring)|載入字串資源。|  
|[CComBSTR::ReadFromStream](#readfromstream)|載入`BSTR`從資料流的物件。|  
|[CComBSTR::ToLower](#tolower)|將字串轉換成小寫。|  
|[CComBSTR::ToUpper](#toupper)|將字串轉換成大寫。|  
|[CComBSTR::WriteToStream](#writetostream)|儲存`m_str`資料流。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CComBSTR::operator BSTR](#operator_bstr)|轉換 （cast)`CComBSTR`物件傳遞給`BSTR`。|  
|[CComBSTR::operator ！](#operator_not)|傳回`true`或`false`，取決於是否`m_str`是`NULL`。|  
|[CComBSTR::operator ！ =](#operator_neq)|比較`CComBSTR`字串。|  
|[CComBSTR::operator i](#operator_amp)|傳回的位址`m_str`。|  
|[CComBSTR::operator + =](#operator_add_eq)|將附加`CComBSTR`物件。|  
|[CComBSTR::operator](#operator_lt)|比較`CComBSTR`字串。|  
|[CComBSTR::operator =](#operator_eq)|將值指派至`m_str`。|  
|[CComBSTR::operator = =](#operator_eq_eq)|比較`CComBSTR`字串。|  
|[CComBSTR::operator >](#operator_gt)|比較`CComBSTR`字串。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComBSTR::m_str](#m_str)|包含`BSTR`聯`CComBSTR`物件。|  
  
## <a name="remarks"></a>備註  
 `CComBSTR`類別是包裝函式`BSTR`都是固定長度的字串。 長度會儲存在字串中前置資料的記憶體位置的整數。  
  
 A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) null 結束之後，最後一個計算字元，但也可能包含內嵌字串內的 null 字元。 字串長度取決於字元計數，而不是第一個 null 字元。  
  
> [!NOTE]
>  `CComBSTR`類別會提供一些取出 ANSI 或 Unicode 字串，做為引數的成員 （建構函式、 指派運算子和比較運算子）。 因為暫時的 Unicode 字串通常會在內部建立，這些函式的 ANSI 版本會比 Unicode 對應項目沒有效率。 為了提高效率，請盡可能使用 Unicode 版本。  
  
> [!NOTE]
>  由於 Visual Studio.NET 中實作的改良的查閱行為，程式碼如`bstr = L"String2" + bstr;`，這在舊版中，已編譯應該改為實作為`bstr = CStringW(L"String2") + bstr`。  
  
 如需使用時的注意事項清單`CComBSTR`，請參閱[使用 ccombstr 進行程式設計](../../atl/programming-with-ccombstr-atl.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-nameappenda--ccombstrappend"></a><a name="append"></a>CComBSTR::Append  
 附加 `lpsz`或`BSTR`成員`bstrSrc`至[m_str](#m_str)。  
  
```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>參數  
 `bstrSrc`  
 [in]A`CComBSTR`来附加的物件。  
  
 *ch*  
 [in]要附加的字元。  
  
 `lpsz`  
 [in]要附加的零結尾的字元字串。 您可以傳遞 Unicode 字串，透過**LPCOLESTR**多載或透過 ANSI 字串`LPCSTR`版本。  
  
 `nLen`  
 [in]從字元數`lpsz`附加。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`在成功時或任何標準`HRESULT`錯誤值。  
  
### <a name="remarks"></a>備註  
 ANSI 字串將會轉換成 Unicode，再附加。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&32;](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]  
  
##  <a name="a-nameappendbstra--ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR::AppendBSTR  
 指定附加`BSTR`至[m_str](#m_str)。  
  
```
HRESULT AppendBSTR(BSTR p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]A`BSTR`附加。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`在成功時或任何標準`HRESULT`錯誤值。  
  
### <a name="remarks"></a>備註  
 請勿將一般的寬字元字串傳遞至這個方法。 編譯器無法捕捉錯誤，執行的階段便會發生錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&33;](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]  
  
##  <a name="a-nameappendbytesa--ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR::AppendBytes  
 將指定的位元組數附加[m_str](#m_str)而無需轉換。  
  
```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpsz`  
 [in]要附加的位元組陣列的指標。  
  
 `p`  
 [in]要附加的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`在成功時或任何標準`HRESULT`錯誤值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&34;](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]  
  
##  <a name="a-namearraytobstra--ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR::ArrayToBSTR  
 釋放保留任何現有字串`CComBSTR`物件，然後建立`BSTR`safearray 中每個項目的第一個字元，並將它附加`CComBSTR`物件。  
  
```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```  
  
### <a name="parameters"></a>參數  
 `pSrc`  
 [in]Safearray，包含用來建立字串的項目。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`在成功時或任何標準`HRESULT`錯誤值。  
  
##  <a name="a-nameassignbstra--ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR::AssignBSTR  
 指派`BSTR`至[m_str](#m_str)。  
  
```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```  
  
### <a name="parameters"></a>參數  
 `bstrSrc`  
 [in]A`BSTR`要指派給目前`CComBSTR`物件。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`在成功時或任何標準`HRESULT`錯誤值。  
  
##  <a name="a-nameattacha--ccombstrattach"></a><a name="attach"></a>CComBSTR::Attach  
 附加`BSTR`至`CComBSTR`藉由設定物件[m_str](#m_str)成員*src*。  
  
```
void Attach(BSTR src) throw();
```  
  
### <a name="parameters"></a>參數  
 *src*  
 [in]`BSTR`將附加到物件。  
  
### <a name="remarks"></a>備註  
 請勿將一般的寬字元字串傳遞至這個方法。 編譯器無法捕捉錯誤，執行的階段便會發生錯誤。  
  
> [!NOTE]
>  這個方法會判斷提示，如果`m_str`是非**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&35;](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="a-namebstrtoarraya--ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR::BSTRToArray  
 建立以零為起始的一維 safearray，其中的陣列的每個項目是從字元`CComBSTR`物件。  
  
```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```  
  
### <a name="parameters"></a>參數  
 `ppArray`  
 [out]用來保存結果的函式的 safearray 指標。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`在成功時或任何標準`HRESULT`錯誤值。  
  
##  <a name="a-namebytelengtha--ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR::ByteLength  
 傳回的位元組數目`m_str`，但不包含結束的 null 字元。  
  
```
unsigned int ByteLength() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 長度[m_str](#m_str)以位元組為單位的成員。  
  
### <a name="remarks"></a>備註  
 會傳回 0，如果`m_str`是**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&36;](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]  
  
##  <a name="a-nameccombstra--ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR::CComBSTR  
 建構函式。 預設建構函式集[m_str](#m_str)成員**NULL**。  
  
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
 `nSize`  
 [in] 要從 `sz` 複製的字元數，或以 `CComBSTR` 的字元數表示的初始大小。  
  
 `sz`  
 [in] 要複製的字串。 指定的 Unicode 版本**LPCOLESTR**，ANSI 版本指定`LPCSTR`。  
  
 `pSrc`  
 [in] 要複製的字串。 指定的 Unicode 版本**LPCOLESTR**，ANSI 版本指定`LPCSTR`。  
  
 *src*  
 [in] `CComBSTR` 物件。  
  
 `guid`  
 [in]參考**GUID**結構。  
  
### <a name="remarks"></a>備註  
 複製建構函式集`m_str`副本`BSTR`成員*src*。 **REFGUID**建構函式會將轉換**GUID**字串使用**StringFromGUID2**並將結果儲存起來。  
  
 其他建構函式會將 `m_str` 設為所指定字串的複本。 如果您將值傳給 `nSize`，則只會複製 `nSize` 字元，後面接著結束的 null 字元。  
  
 `CComBSTR` 支援移動語意。 您可以使用移動建構函式 (接受右值參考的建構函式 ( `&&`) 來建立新的物件，會使用相同的基礎資料，如您所傳遞引數，而無需額外複製物件的舊物件。  
  
 解構函式會釋放 `m_str` 所指向的字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&37;](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]  
  
##  <a name="a-namedtora--ccombstrccombstr"></a><a name="dtor"></a>CComBSTR:: ~ CComBSTR  
 解構函式。  
  
```
~CComBSTR();
```  
  
### <a name="remarks"></a>備註  
 解構函式會釋放 `m_str` 所指向的字串。  
  
##  <a name="a-namecopya--ccombstrcopy"></a><a name="copy"></a>CComBSTR::Copy  
 配置並傳回一份`m_str`。  
  
```
BSTR Copy() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 一份[m_str](#m_str)成員。 If `m_str` is **NULL**, returns **NULL**.  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&38;](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]  
  
##  <a name="a-namecopytoa--ccombstrcopyto"></a><a name="copyto"></a>CComBSTR::CopyTo  
 配置並傳回一份[m_str](#m_str)透過參數。  
  
```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```  
  
### <a name="parameters"></a>參數  
 *pbstr*  
 [out]位址`BSTR`，以傳回這個方法所配置的字串。  
  
 `pvarDest`  
 [out]位址**VARIANT** ，以傳回這個方法所配置的字串。  
  
### <a name="return-value"></a>傳回值  
 標準`HRESULT`值，指出成功或失敗的複本。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法之後, **VARIANT**指向`pvarDest`的型別`VT_BSTR`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&39;](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]  
  
##  <a name="a-namedetacha--ccombstrdetach"></a><a name="detach"></a>CComBSTR::Detach  
 卸離[m_str](#m_str)從`CComBSTR`物件，然後設定`m_str`至**NULL**。  
  
```
BSTR Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 `BSTR`聯`CComBSTR`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&40;](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]  
  
##  <a name="a-nameemptya--ccombstrempty"></a><a name="empty"></a>CComBSTR::Empty  
 釋出[m_str](#m_str)成員。  
  
```
void Empty() throw();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&41;](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]  
  
##  <a name="a-namelengtha--ccombstrlength"></a><a name="length"></a>CComBSTR::Length  
 傳回的字元數`m_str`，但不包含結束的 null 字元。  
  
```
unsigned int Length() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 長度[m_str](#m_str)成員。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&42;](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]  
  
##  <a name="a-nameloadstringa--ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR::LoadString  
 載入指定的字串資源`nID`並將它儲存在此物件。  
  
```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```  
  
### <a name="parameters"></a>參數  
 請參閱[LoadString](http://msdn.microsoft.com/library/windows/desktop/ms647486)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**該字串是否已成功載入; 否則傳回**false**。  
  
### <a name="remarks"></a>備註  
 第一個函式會從您透過所指出的模組載入資源`hInst`參數。 第二個函式會從相關聯的資源模組載入資源[CComModule](../../atl/reference/ccommodule-class.md)-衍生本專案中使用的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&43;](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]  
  
##  <a name="a-namemstra--ccombstrmstr"></a><a name="m_str"></a>CComBSTR::m_str  
 包含`BSTR`聯`CComBSTR`物件。  
  
```
BSTR m_str;
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&49;](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]  
  
##  <a name="a-nameoperatorbstra--ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR::operator BSTR  
 轉換 （cast)`CComBSTR`物件傳遞給`BSTR`。  
  
```  
operator BSTR() const throw();
```  
  
### <a name="remarks"></a>備註  
 可讓您傳遞`CComBSTR`具有函式物件**[in] BSTR**參數。  
  
### <a name="example"></a>範例  
 請參閱範例[CComBSTR::m_str](#m_str)。  
  
##  <a name="a-nameoperatornota--ccombstroperator-"></a><a name="operator_not"></a>CComBSTR::operator ！  
 檢查是否`BSTR`字串是 NULL。  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**如果[m_str](#m_str)成員是**NULL**，否則**false**。  
  
### <a name="remarks"></a>備註  
 這個運算子只會檢查 NULL 值，不是空字串。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&35;](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="a-nameoperatorneqa--ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR::operator ！ =  
 傳回的相反邏輯[運算子 = =](#operator_eq_eq)。  
  
```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```  
  
### <a name="parameters"></a>參數  
 `bstrSrc`  
 [in] `CComBSTR` 物件。  
  
 `pszSrc`  
 [in]以零結尾的字串。  
  
 `nNull`  
 [in]必須是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**要比較的項目是否不等於`CComBSTR`物件; 否則會傳回**false**。  
  
### <a name="remarks"></a>備註  
 `CComBSTR`s 會加&1; 比較使用者的預設地區設定的內容中。 最後一個比較運算子只會比較所包含的字串和**NULL**。  
  
##  <a name="a-nameoperatorampa--ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR::operator&amp;  
 傳回的位址`BSTR`儲存在[m_str](#m_str)成員。  
  
```
BSTR* operator&() throw();
```  
  
### <a name="remarks"></a>備註  
 `CComBstr operator &`有特殊的判斷提示相關聯，有助於識別記憶體流失。 程式會判斷提示時`m_str`成員初始化。 這個判斷提示來識別其中程式設計人員使用的情況建立`& operator`來指派新值給`m_str`成員卻未釋放的第一個配置`m_str`。 如果`m_str`等於 NULL，程式會假設該 m_str 未尚未配置。 在此情況下，程式將不會判斷提示。  
  
 預設不啟用這個判斷提示。 定義`ATL_CCOMBSTR_ADDRESS_OF_ASSERT`若要啟用這個判斷提示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&46;](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities #&47;](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]  
  
##  <a name="a-nameoperatoraddeqa--ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR::operator + =  
 字串附加至`CComBSTR`物件。  
  
```
CComBSTR& operator+= (const CComBSTR& bstrSrc);  
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```  
  
### <a name="parameters"></a>參數  
 `bstrSrc`  
 [in]A`CComBSTR`来附加的物件。  
  
 `pszSrc`  
 [in]要附加零結尾的字串。  
  
### <a name="remarks"></a>備註  
 `CComBSTR`s 會加&1; 比較使用者的預設地區設定的內容中。 **LPCOLESTR**進行比較使用`memcmp`中每個字串的未經處理資料。 `LPCSTR`比較執行相同的方式一旦暫存 Unicode 副本`pszSrc`已建立。 最後一個比較運算子只會比較所包含的字串和**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&48;](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]  
  
##  <a name="a-nameoperatorlta--ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR::operator&lt;  
 比較`CComBSTR`字串。  
  
```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**要比較的項目是否小於`CComBSTR`物件; 否則會傳回**false**。  
  
### <a name="remarks"></a>備註  
 使用使用者的預設地區設定來進行比較。  
  
##  <a name="a-nameoperatoreqa--ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR::operator =  
 設定[m_str](#m_str)成員的複本`pSrc`或一份`BSTR`成員*src*。 移動指派運算子將`src`不複製它。   
  
```
CComBSTR& operator= (const CComBSTR& src);  
CComBSTR& operator= (LPCOLESTR pSrc);  
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="remarks"></a>備註  
 `pSrc`參數會指定**LPCOLESTR** Unicode 版本或`LPCSTR`ANSI 版本。  
  
### <a name="example"></a>範例  
 請參閱範例[CComBSTR::Copy](#copy)。  
  
##  <a name="a-nameoperatoreqeqa--ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR::operator = =  
 比較`CComBSTR`字串。 `CComBSTR`s 會加&1; 比較使用者的預設地區設定的內容中。  
  
```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```  
  
### <a name="parameters"></a>參數  
 `bstrSrc`  
 [in] `CComBSTR` 物件。  
  
 `pszSrc`  
 [in]以零結尾的字串。  
  
 `nNull`  
 [in]必須是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 傳回**true**要比較的項目是否等於`CComBSTR`物件; 否則會傳回**false**。  
  
### <a name="remarks"></a>備註  
 最後一個比較運算子只會比較所包含的字串和**NULL**。  
  
##  <a name="a-nameoperatorgta--ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR::operator&gt;  
 比較`CComBSTR`字串。  
  
```
bool operator>(const CComBSTR& bstrSrc) const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**true**要比較的項目是否大於`CComBSTR`物件; 否則會傳回**false**。  
  
### <a name="remarks"></a>備註  
 使用使用者的預設地區設定來進行比較。  
  
##  <a name="a-namereadfromstreama--ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR::ReadFromStream  
 設定[m_str](#m_str)成員`BSTR`包含在指定的資料流。  
  
```
HRESULT ReadFromStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 [in]指標[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)包含資料的資料流上的介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 **ReadToStream**需要的資料流目前位置的呼叫所寫出的資料格式與內容[WriteToStream](#writetostream)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&44;](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]  
  
##  <a name="a-nametolowera--ccombstrtolower"></a><a name="tolower"></a>CComBSTR::ToLower  
 將所包含的字串轉換成小寫。  
  
```
HRESULT ToLower() throw();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 請參閱**CharLowerBuff**如需有關如何執行轉換。  
  
##  <a name="a-nametouppera--ccombstrtoupper"></a><a name="toupper"></a>CComBSTR::ToUpper  
 將所包含的字串轉換成大寫。  
  
```
HRESULT ToUpper() throw();
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 請參閱**CharUpperBuff**如需有關如何執行轉換。  
  
##  <a name="a-namewritetostreama--ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR::WriteToStream  
 儲存[m_str](#m_str)成員的資料流。  
  
```
HRESULT WriteToStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 [in]指標[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)資料流上的介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 您可以重新建立資料流使用的內容從 BSTR [ReadFromStream](#readfromstream)函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&45;](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [ATL 和 MFC 字串轉換巨集](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)

