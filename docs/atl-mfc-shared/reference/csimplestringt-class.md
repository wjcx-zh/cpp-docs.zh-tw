---
title: "CSimpleStringT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
dev_langs: C++
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: acbf4753bb29b8f28cac9fe4fb6ceff72ceda8a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="csimplestringt-class"></a>CSimpleStringT 類別
此類別代表`CSimpleStringT`物件。  
  
## <a name="syntax"></a>語法  
  
```
template <typename BaseType>
class CSimpleStringT
```  
  
### <a name="parameters"></a>參數  
 `BaseType`  
 字串類別的字元類型。 可以是下列其中一項：  
  
- `char`（適用於 ANSI 字元字串）。  
  
- `wchar_t`（適用於 Unicode 字元字串）。  
  
- **TCHAR** （適用於 ANSI 和 Unicode 字元字串）。  

## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleStringT::PCXSTR](#pcxstr)|常數字串指標。|  
|[CSimpleStringT::PXSTR](#pxstr)|字串的指標。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleStringT::CSimpleStringT](#ctor)|建構`CSimpleStringT`物件以各種方式。|  
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|解構函式。|  

  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleStringT::Append](#append)|將附加`CSimpleStringT`物件到現有`CSimpleStringT`物件。|  
|[CSimpleStringT::AppendChar](#appendchar)|將字元附加至現有`CSimpleStringT`物件。|  
|[CSimpleStringT::CopyChars](#copychars)|將字元複製到另一個字串中。|  
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|將字元複製到另一個緩衝區重疊的字串中。|  
|[CSimpleStringT::Empty](#empty)|會強制將長度為零的字串。|  
|[CSimpleStringT::FreeExtra](#freeextra)|釋放先前由字串物件配置任何額外的記憶體。|  
|[CSimpleStringT::GetAllocLength](#getalloclength)|擷取的配置的長度`CSimpleStringT`物件。|  
|[CSimpleStringT::GetAt](#getat)|傳回指定位置處的字元。|  
|[CSimpleStringT::GetBuffer](#getbuffer)|讓指標回到中的字元`CSimpleStringT`。|  
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|讓指標回到中的字元`CSimpleStringT`、 刪減為指定的長度。|  
|[CSimpleStringT::GetLength](#getlength)|傳回的字元數`CSimpleStringT`物件。|  
|[CSimpleStringT::GetManager](#getmanager)|擷取的記憶體管理員`CSimpleStringT`物件。|  
|[CSimpleStringT::GetString](#getstring)|擷取的字元字串|  
|[CSimpleStringT::IsEmpty](#isempty)|測試是否`CSimpleStringT`物件未包含任何字元。|  
|[CSimpleStringT::LockBuffer](#lockbuffer)|停用參考計數，並保護緩衝區中的字串。|  
|[CSimpleStringT::Preallocate](#preallocate)|一段特定記憶體配置的字元緩衝區。|  
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|釋放控制項所傳回的緩衝區`GetBuffer`。|  
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|釋放控制項所傳回的緩衝區`GetBuffer`。|  
|[CSimpleStringT::SetAt](#setat)|設定字元的指定位置。|  
|[CSimpleStringT::SetManager](#setmanager)|設定的記憶體管理員`CSimpleStringT`物件。|  
|[CSimpleStringT::SetString](#setstring)|設定的字串`CSimpleStringT`物件。|  
|[CSimpleStringT::StringLength](#stringlength)|指定的字串中傳回字元的數。|  
|[CSimpleStringT::Truncate](#truncate)|會截斷至指定之長度的字串。|  
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|可讓參考計數，並釋放緩衝區中的字串。|  

### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|直接存取儲存在字元`CSimpleStringT`物件做為 C 樣式字串。|  
|[CSimpleStringT::operator\[\]](#operator_at)|傳回指定位置處的字元-運算子替代`GetAt`。|  
|[CSimpleStringT::operator + =](#operator_add_eq)|串連至現有的字串結尾的新字串。|  
|[CSimpleStringT::operator =](#operator_eq)|指派新值`CSimpleStringT`物件。|  
  
### <a name="remarks"></a>備註  
 `CSimpleStringT`為 Visual c + + 所支援的各種字串類別的基底類別。 它提供最小支援的字串物件和基本緩衝區操作的記憶體管理。 對於更進階的字串物件，請參閱[CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="requirements"></a>需求  
 **標頭：** atlsimpstr.h  


## <a name="append"></a>CSimpleStringT::Append
將附加`CSimpleStringT`物件到現有`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
void Append(const CSimpleStringT& strSrc); 
void Append(PCXSTR pszSrc, int nLength); 
void Append(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>參數  
 `strSrc`  
 `CSimpleStringT`来附加的物件。  
  
 `pszSrc`  
 包含要附加的字元字串的指標。  
  
 `nLength`  
 要附加的字元數。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以附加現有`CSimpleStringT`物件與其他`CSimpleStringT`物件。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::Append` 的用法。  
  
```cpp  
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```
  
##  <a name="appendchar"></a>CSimpleStringT::AppendChar
將字元附加至現有`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
void AppendChar(XCHAR ch);
```  
#### <a name="parameters"></a>參數  
 *ch*  
 要附加的字元  
  
### <a name="remarks"></a>備註  
 呼叫此函式可將指定的字元附加至現有的結尾`CSimpleStringT`物件。  
  
##  <a name="copychars"></a>CSimpleStringT::CopyChars  
 將複製的字元或字元`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
static void CopyChars(
  XCHAR* pchDest,
  const XCHAR* pchSrc, 
  int nChars) throw();
```  
#### <a name="parameters"></a>參數  
 `pchDest`  
 字元字串指標。  
  
 `pchSrc`  
 包含要複製的字元字串的指標。  
  
 `nChars`  
 數目`pchSrc`来複製的字元。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以複製的字元`pchSrc`至`pchDest`字串。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::CopyChars` 的用法。  
  
```cpp  
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```
  
##  <a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped
將複製的字元或字元`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
static void CopyCharsOverlapped(
  XCHAR* pchDest,
  const XCHAR* pchSrc,
  int nChars) throw(); 
```  
#### <a name="parameters"></a>參數  
 `pchDest`  
 字元字串指標。  
  
 `pchSrc`  
 包含要複製的字元字串的指標。  
  
 `nChars`  
 數目`pchSrc`来複製的字元。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以複製的字元`pchSrc`至`pchDest`字串。 不同於`CopyChars`，`CopyCharsOverlapped`提供安全的方法，將從可能重疊的字元緩衝區複製。  
  
### <a name="example"></a>範例  
 請參閱範例的[CSimpleStringT::CopyChars](#copychars)，或如原始程式碼`CSimpleStringT::SetString`（位於 atlsimpstr.h）。  
  
##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT  
 建構 `CSimpleStringT` 物件。  
  
### <a name="syntax"></a>語法  
  
```  
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr); 
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr); 
CSimpleStringT(const CSimpleStringT& strSrc); 
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw(); 
```  
#### <a name="parameters"></a>參數  
 `strSrc`  
 現有`CSimpleStringT`物件複製到這個`CSimpleStringT`物件。  
  
 `pchSrc`  
 長度的字元陣列的指標`nLength`、 null 結尾。  
  
 `pszSrc`  
 以 null 結束的字串複製到這`CSimpleStringT`物件。  
  
 `nLength`  
 中的字元數的計數`pch`。  
  
 `pStringMgr`  
 指向的記憶體管理員的`CSimpleStringT`物件。 如需有關`IAtlStringMgr`和記憶體管理`CSimpleStringT`，請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。  
  
### <a name="remarks"></a>備註  
 建構新`CSimpleStringT`物件。 建構函式會將輸入的資料複製到新配置的儲存體，因為可能會造成記憶體例外狀況。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`CSimpleStringT::CSimpleStringT`使用 ATL `typedef` `CSimpleString`。 `CSimpleString`常用的類別樣板特製化`CSimpleStringT`。  
  
```cpp  
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"   
```

  
##  <a name="empty"></a>CSimpleStringT::Empty
使這個成為`CSimpleStringT`物件為空字串，並釋出適當的記憶體。  
  
### <a name="syntax"></a>語法  
  
```  
void Empty() throw();  
```  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[字串： CString 例外狀況清除](../cstring-exception-cleanup.md)。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::Empty` 的用法。  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());  
```  
  
##  <a name="freeextra"></a>CSimpleStringT::FreeExtra
釋放先前配置的字串，但不再需要任何額外的記憶體。  
  
### <a name="syntax"></a>語法  
  
```  
void FreeExtra(); 
```  
### <a name="remarks"></a>備註  
 這應該降低字串物件所耗用的記憶體額外負荷。 這個方法重新配置所傳回的實際長度的緩衝區[GetLength](#getlength)。  
  
### <a name="example"></a>範例  
```cpp  
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its 
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra 
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```
  
### <a name="remarks"></a>備註  
 此範例的輸出如下所示：  
  
 `Alloc length is 1031, String length is 1024`  
  
 `Alloc length is 1031, String length is 15`  
  
 `Alloc length is 15, String length is 15`  
  
##  <a name="getalloclength"></a>CSimpleStringT::GetAllocLength  
擷取的配置的長度`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
int GetAllocLength() const throw();  
```  
### <a name="return-value"></a>傳回值  
 此物件所配置的字元數。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來判斷這個配置的字元數`CSimpleStringT`物件。 請參閱[FreeExtra](#freeextra)呼叫此函式的範例。  
  
##  <a name="getat"></a>CSimpleStringT::GetAt  
傳回從一個字元`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
XCHAR GetAt(int iChar) const;
```  
#### <a name="parameters"></a>參數  
 `iChar`  
 以零為起始的索引中之字元`CSimpleStringT`物件。 `iChar`參數必須大於或等於 0，且所傳回的值大於或等於[GetLength](#getlength)。 否則，`GetAt`會產生例外狀況。  
  
### <a name="return-value"></a>傳回值  
 `XCHAR` ，其中包含在字串中指定位置處的字元。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以傳回所指定的一個字元`iChar`。 多載註標 (`[]`) 運算子是方便別名`GetAt`。 不會產生例外狀況，使用 null 結束字元是可定址`GetAt`。 不過，它就不會計算由`GetLength`，而傳回的值為 0。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`CSimpleStringT::GetAt`。  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```
  
##  <a name="getbuffer"></a>CSimpleStringT::GetBuffer  
傳回的內部字元緩衝區的指標`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
PXSTR GetBuffer(int nMinBufferLength); 
PXSTR GetBuffer();
```  
#### <a name="parameters"></a>參數  
 `nMinBufferLength`  
 字元緩衝區可以保存的字元數目下限。 此値不包含 null 結束字元的空間。  
  
 如果`nMinBufferLength`大於目前的緩衝區長度`GetBuffer`終結目前緩衝區、 取代要求的大小的緩衝區和物件參考計數重設為 0。 如果您先前已經呼叫[LockBuffer](#lockbuffer)在這個緩衝區中，您會喪失緩衝區鎖定。  
  
### <a name="return-value"></a>傳回值  
 `PXSTR`的物件 （以 null 終止） 字元緩衝區的指標。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以傳回的緩衝區內容`CSimpleStringT`物件。 傳回`PXSTR`不是一個常數，因此便可直接修改`CSimpleStringT`內容。  
  
 如果您使用傳回的指標`GetBuffer`變更字串的內容，您必須呼叫[ReleaseBuffer](#releasebuffer)您使用任何其他之前`CSimpleStringT`成員方法。  
  
 所傳回的位址`GetBuffer`可能不是有效的呼叫後方`ReleaseBuffer`因為其他`CSimpleStringT`作業可能會造成`CSimpleStringT`都重新配置的緩衝區。 如果您未變更的長度不重新配置緩衝區`CSimpleStringT`。  
  
 緩衝區記憶體會自動釋放時`CSimpleStringT`物件被終結。  
  
 如果您追蹤的字串長度自行，您應該不附加結束的 null 字元。 不過，您必須指定最終字串長度時釋放緩衝區與`ReleaseBuffer`。 如果您不要附加結束的 null 字元，您應該傳遞的長度-1 （預設值）。 `ReleaseBuffer`然後會判斷緩衝區長度。  
  
 如果沒有記憶體不足，無法滿足`GetBuffer`要求時，這個方法會擲回 CMemoryException *。  
  
### <a name="example"></a>範例  
```cpp  
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();   
```
  
##  <a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength  
傳回的內部字元緩衝區的指標`CSimpleStringT`物件、 截斷或成長它的長度，如有必要完全符合指定的長度`nLength`。  
  
### <a name="syntax"></a>語法  
  
```  
PXSTR GetBufferSetLength(int nLength);
```  
#### <a name="parameters"></a>參數  
 `nLength`  
 確切大小`CSimpleStringT`以字元為單位的字元緩衝區。  
  
### <a name="return-value"></a>傳回值  
 A`PXSTR`的物件 （以 null 終止） 字元緩衝區的指標。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取指定的內部緩衝區的長度`CSimpleStringT`物件。 傳回`PXSTR`指標不是`const`因此允許直接修改`CSimpleStringT`內容。  
  
 如果您使用傳回的指標[GetBufferSetLength](#getbuffersetlength)若要變更的字串內容，請呼叫`ReleaseBuffer`更新的內部狀態`CsimpleStringT`您使用任何其他之前`CSimpleStringT`方法。  
  
 所傳回的位址`GetBufferSetLength`可能不是有效的呼叫後方`ReleaseBuffer`因為其他`CSimpleStringT`作業可能會造成`CSimpleStringT`都重新配置的緩衝區。 如果您未變更的長度，不會指派緩衝區`CSimpleStringT`。  
  
 緩衝區記憶體會自動釋放時`CSimpleStringT`物件被終結。  
  
 如果您追蹤的字串長度自行，請勿不附加結束的 null 字元。 當您放開緩衝區使用時，您必須指定最終字串長度`ReleaseBuffer`。 如果您不要附加結束的 null 字元，當您呼叫`ReleaseBuffer`，傳遞 – 1 （預設值） 的長度為`ReleaseBuffer`，和`ReleaseBuffer`將會執行`strlen`來判斷其長度的緩衝區上。  
  
 如需有關參考計數的詳細資訊，請參閱下列文章：  
  
- [管理透過參考計數的物件存留期](http://msdn.microsoft.com/library/windows/desktop/ms687260)Windows SDK 中。 
  
- [實作參考計數](http://msdn.microsoft.com/library/windows/desktop/ms693431)Windows SDK 中。
  
- [規則管理參考計數](http://msdn.microsoft.com/library/windows/desktop/ms692481)Windows SDK 中。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::GetBufferSetLength` 的用法。  
  
```cpp  
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer() 
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```
  
##  <a name="getlength"></a>CSimpleStringT::GetLength  
傳回的字元數`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
int GetLength() const throw();  
```  
### <a name="return-value"></a>傳回值  
 字串中字元的計數。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以傳回物件中的字元數。 計數不包含 null 結束字元。  
  
 多位元組字元集 (MBCS)，如`GetLength`一個多位元組字元中的每個 8 位元字元; 也就是前置和後隨位元組都會計入為兩個位元組的計數。 請參閱[FreeExtra](#freeextra)呼叫此函式的範例。  
  
##  <a name="getmanager"></a>CSimpleStringT::GetManager  
擷取的記憶體管理員`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
IAtlStringMgr* GetManager() const throw();  
```  
### <a name="return-value"></a>傳回值  
 指標，memory manager`CSimpleStringT`物件。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取記憶體管理員所使用`CSimpleStringT`物件。 如需有關記憶體管理員和字串物件的詳細資訊，請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。  
  
##  <a name="getstring"></a>CSimpleStringT::GetString
擷取的字元字串。  
  
### <a name="syntax"></a>語法  
  
```  
PCXSTR GetString() const throw();
```  
### <a name="return-value"></a>傳回值  
 以 null 結束的字元字串指標。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取相關聯的字元字串`CSimpleStringT`物件。  
  
> [!NOTE]
>  傳回`PCXSTR`指標`const`，且不允許直接修改`CSimpleStringT`內容。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::GetString` 的用法。  
  
```cpp  
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```
  
##  <a name="isempty"></a>CSimpleStringT::IsEmpty  
測試`CSimpleStringT`空白條件的物件。  
  
### <a name="syntax"></a>語法  
  
```  
bool IsEmpty() const throw();  
```  
### <a name="return-value"></a>傳回值  
 傳回**true**如果`CSimpleStringT`物件具有 0 的長度，否則為**false**。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來判斷物件是否包含空字串。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::IsEmpty` 的用法。  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```
  
##  <a name="lockbuffer"></a>CSimpleStringT::LockBuffer  
停用參考計數，並保護緩衝區中的字串。  
  
### <a name="syntax"></a>語法  
  
```  
PXSTR LockBuffer();
```  
### <a name="return-value"></a>傳回值  
 指標`CSimpleStringT`物件或以 null 結束的字串。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來鎖定緩衝的`CSimpleStringT`物件。 藉由呼叫`LockBuffer`，您建立一份字串中，參考計數為-1。 當參考計數值為-1 時，緩衝區中的字串會被視為 「 鎖定 」 的狀態。 處於鎖定狀態時，字串是在兩種方式受到保護：  
  
-   任何其他字串可以鎖定字串中不取得資料的參考，即使該字串指派給鎖定字串。  
  
-   鎖定的字串將會永遠不會參考另一個字串，即使其他該字串會複製到鎖定的字串。  
  
 鎖定字串緩衝區中，您可以確保字串獨佔保留在緩衝區上的將維持不變。  
  
 您已完成之後`LockBuffer`，呼叫[UnlockBuffer](#unlockbuffer)重設為 1 的參考計數。  
  
> [!NOTE]
>  如果您呼叫[GetBuffer](#getbuffer)鎖定的緩衝區，而且您在設定`GetBuffer`參數`nMinBufferLength`大於目前的緩衝區的長度，您將會遺失緩衝區鎖定。 這類呼叫`GetBuffer`終結目前緩衝區、 取代緩衝區的要求的大小，並將參考計數重設為零。  
  
 如需有關參考計數的詳細資訊，請參閱下列文章：  
  
- [管理透過參考計數的物件存留期](http://msdn.microsoft.com/library/windows/desktop/ms687260)windows SDK  
  
- [實作參考計數](http://msdn.microsoft.com/library/windows/desktop/ms693431)windows SDK  
  
- [規則管理參考計數](http://msdn.microsoft.com/library/windows/desktop/ms692481)windows SDK  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::LockBuffer` 的用法。  
  
```cpp  
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```
  
##  <a name="operator_at"></a>CSimpleStringT::operator\[\]  
呼叫此函式可存取單一字元的字元陣列。  
  
### <a name="syntax"></a>語法  
  
```  
XCHAR operator[](int iChar) const;
```  
#### <a name="parameters"></a>參數  
 `iChar`  
 在字串中字元的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 多載註標 (`[]`) 運算子會傳回以零為起始的索引中所指定的單一字元`iChar`。 這位操作員便能方便替代[GetAt](#getat)成員函式。  
  
> [!NOTE]
>  您可以使用註標 (`[]`) 來取得中的字元值的運算子`CSimpleStringT`，但您無法使用它來變更中的字元值`CSimpleStringT`。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用**CSimpleStringT::operator []**。  
  
```cpp  
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```
  
## <a name="operator_at"></a>CSimpleStringT::operator\[\]
呼叫此函式可存取單一字元的字元陣列。  
  
### <a name="syntax"></a>語法  
  
```   
XCHAR operator[](int iChar) const;
```  
  
### <a name="parameters"></a>參數  
 `iChar`  
 在字串中字元的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 多載註標 (`[]`) 運算子會傳回以零為起始的索引中所指定的單一字元`iChar`。 這位操作員便能方便替代[GetAt](#getat)成員函式。  
  
> [!NOTE]
>  您可以使用註標 (`[]`) 來取得中的字元值的運算子`CSimpleStringT`，但您無法使用它來變更中的字元值`CSimpleStringT`。  
  
  
##  <a name="operator_add_eq"></a>CSimpleStringT::operator + =  
加入現有的字串結尾的新字串或字元。  
  
### <a name="syntax"></a>語法  
  
```  
CSimpleStringT& operator +=(PCXSTR pszSrc); 
CSimpleStringT& operator +=(const CSimpleStringT& strSrc); 
template<int t_nSize>  
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc); 
CSimpleStringT& operator +=(char ch); 
CSimpleStringT& operator +=(unsigned char ch); 
CSimpleStringT& operator +=(wchar_t ch);
```  
#### <a name="parameters"></a>參數  
 `pszSrc`  
 以 null 終止的字串指標。  
  
 `strSrc`  
 指向現有的`CSimpleStringT`物件。  
  
 *ch*  
 要附加的字元。  
  
### <a name="remarks"></a>備註  
 運算子會接受另一個`CSimpleStringT`物件或字元。 請注意該記憶體可能會發生例外狀況，每當您使用此串連運算子，因為可能會配置新的存放裝置新增至這個字元`CSimpleStringT`物件。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用**CSimpleStringT::operator + =**。  
  
```cpp  
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```
  
##  <a name="operator_eq"></a>CSimpleStringT::operator =  
指派新值`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
CSimpleStringT& operator =(PCXSTR pszSrc); 
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```  
#### <a name="parameters"></a>參數  
 `pszSrc`  
 以 null 終止的字串指標。  
  
 `strSrc`  
 指向現有的`CSimpleStringT`物件。  
  
### <a name="remarks"></a>備註  
 如果目的字串 （左側） 已經夠大，無法儲存新的資料，會不執行任何新的記憶體配置。 請注意該記憶體可能會發生例外狀況，每當您使用指派運算子，因為新的存放裝置通常會配置來保存所產生的`CSimpleStringT`物件。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用**CSimpleStringT::operator =**。  
  
```cpp  
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;      
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```
  
##  <a name="operator_pcxstr"></a>CSimpleStringT::operator PCXSTR  

 直接存取儲存在字元`CSimpleStringT`物件做為 C 樣式字串。  
  
### <a name="syntax"></a>語法  
  
```  
operator PCXSTR() const throw();
```  
### <a name="return-value"></a>傳回值  
 字串資料的字元指標。  
  
### <a name="remarks"></a>備註  
 沒有字元會複製;只有指標會傳回。 請謹慎使用這個運算子。 如果您變更`CString`物件取得字元指標之後，您可能會導致重新配置的記憶體，讓指標失效。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用**CSimpleStringT::operator PCXSTR**。  
  
```cpp  
// If the prototype of a function is known to the compiler, 
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype, 
// you must invoke the cast operator explicitly. For example, 
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and 
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will 
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;   
``` 
  
##  <a name="pcxstr"></a>CSimpleStringT::PCXSTR
常數字串指標。  
  
### <a name="syntax"></a>語法  
  
```  
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;    
```  
##  <a name="preallocate"></a>CSimpleStringT::Preallocate  
配置的位元組數的特定數量`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
void Preallocate( int nLength);
```  
#### <a name="parameters"></a>參數  
 `nLength`  
 確切大小`CSimpleStringT`以字元為單位的字元緩衝區。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來配置的特定緩衝區大小`CSimpleStringT`物件。  
  
 `CSimpleStringT`會產生`STATUS_NO_MEMORY`例外狀況，如果無法配置空間給字元緩衝區。 根據預設，記憶體配置由 WIN32 API 函式執行`HeapAlloc`或`HeapReAlloc`。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::Preallocate` 的用法。  
  
```cpp  
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```
  
##  <a name="pxstr"></a>CSimpleStringT::PXSTR  
字串的指標。  
  
### <a name="syntax"></a>語法  
  
```  
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;  
```  
##  <a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer  
釋放控制項所配置的緩衝區[GetBuffer](#getbuffer)。  
  
### <a name="syntax"></a>語法  
  
```  
void ReleaseBuffer(int nNewLength = -1);
```  
#### <a name="parameters"></a>參數  
 `nNewLength`  
 中不包括 null 結束字元的字元字串的新長度。 如果字串為 null 終止，-1 預設值會設定`CSimpleStringT`大小目前字串的長度。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來重新配置或釋放字串物件的緩衝區。 如果您知道在緩衝區中的字串為 null 終止，您可以省略`nNewLength`引數。 如果您的字串不是 null 終止，使用`nNewLength`來指定它的長度。 所傳回的位址[GetBuffer](#getbuffer)無效的呼叫後方`ReleaseBuffer`或任何其他`CSimpleStringT`作業。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::ReleaseBuffer` 的用法。  
  
```cpp  
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

  // use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```
  
##  <a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

釋放控制項所配置的緩衝區[GetBuffer](#getbuffer)。  
  
### <a name="syntax"></a>語法  
  
```  
void ReleaseBufferSetLength(int nNewLength);
```  
#### <a name="parameters"></a>參數  
 `nNewLength`  
 將被釋放，字串的長度  
  
### <a name="remarks"></a>備註  
 此函式是在功能上類似於[ReleaseBuffer](#releasebuffer)不同之處在於必須傳遞的字串物件的有效長度。  
  
##  <a name="setat"></a>CSimpleStringT::SetAt  
設定從單一字元`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
void SetAt(int iChar, XCHAR ch);
```  
#### <a name="parameters"></a>參數  
 `iChar`  
 以零為起始的索引中之字元`CSimpleStringT`物件。 `iChar`參數必須大於或等於 0，且所傳回的值大於或等於[GetLength](#getlength)。  
  
 *ch*  
 新的字元。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來覆寫上的字元`iChar`。 這個方法不會放大字串，如果`iChar`超過現有字串的界限。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::SetAt` 的用法。  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
``` 
  
##  <a name="setmanager"></a>CSimpleStringT::SetManager  
指定的記憶體管理員`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
void SetManager(IAtlStringMgr* pStringMgr);
```  
#### <a name="parameters"></a>參數  
 `pStringMgr`  
 新的記憶體管理員指標。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以指定新的記憶體管理員所使用`CSimpleStringT`物件。 如需有關記憶體管理員和字串物件的詳細資訊，請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::SetManager` 的用法。  
  
```cpp  
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```
  
##  <a name="setstring"></a>CSimpleStringT::SetString  
設定的字串`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
void SetString(PCXSTR pszSrc, int nLength); 
void SetString(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>參數  
 `pszSrc`  
 以 null 終止的字串指標。  
  
 `nLength`  
 中的字元數的計數`pszSrc`。  
  
### <a name="remarks"></a>備註  
 複製字串`CSimpleStringT`物件。 `SetString`覆寫較舊字串資料緩衝區中。  
  
 這兩個版本`SetString`檢查是否`pszSrc`為 null 指標，而且如果是，會擲回**E_INVALIDARG**錯誤。  
  
 其中一個參數新版`SetString`預期`pszSrc`指向以 null 結束的字串。  
  
 兩個參數的版本`SetString`也必須要有`pszSrc`是以 null 結束的字串。 它會使用`nLength`為字串的長度除非先遇到 null 結束字元。  
  
 兩個參數的版本`SetString`也會檢查是否`pszSrc`指向某個位置目前緩衝區中`CSimpleStringT`。 在這個特殊的情況下，`SetString`使用記憶體複製函式，因為它會將字串資料複製回到其緩衝區，不會覆寫的字串資料。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::SetString` 的用法。  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```
  
##  <a name="stringlength"></a>CSimpleStringT::StringLength  
指定的字串中傳回字元的數。  
  
### <a name="syntax"></a>語法  
  
```  
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```  
#### <a name="parameters"></a>參數  
 `psz`  
 以 null 終止的字串指標。  
  
### <a name="return-value"></a>傳回值  
 中的字元數`psz`; 不計算 null 結束字元。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取所指向之字串中字元數`psz`。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::StringLength` 的用法。  
  
```cpp  
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
``` 
  
##  <a name="truncate"></a>CSimpleStringT::Truncate
會截斷為新長度的字串。  
  
### <a name="syntax"></a>語法  
  
```  
void Truncate(int nNewLength);
```  
#### <a name="parameters"></a>參數  
 `nNewLength`  
 新字串的長度。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以截斷至新的長度字串的內容。  
  
> [!NOTE]
>  這不會影響配置緩衝區的長度。 若要減少或增加目前緩衝區，請參閱[FreeExtra](#freeextra)和[Preallocate](#preallocate)。  
  
### <a name="example"></a>範例  
 下列範例示範 `CSimpleStringT::Truncate` 的用法。  
  
```cpp  
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
``` 
  
##  <a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer
 解除鎖定的緩衝區`CSimpleStringT`物件。  
  
### <a name="syntax"></a>語法  
  
```  
void UnlockBuffer() throw();
```  
### <a name="remarks"></a>備註  
 呼叫此方法以字串的參考計數重設為 1。  
  
 `CSimpleStringT`解構函式自動呼叫`UnlockBuffer`以確保該緩衝區未鎖定時呼叫解構函式。 如需這個方法的範例，請參閱[LockBuffer](#lockbuffer)。  
  
##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT
終結 `CSimpleStringT` 物件。  
  
### <a name="syntax"></a>語法  
  
```  
~CSimpleStringT() throw();
```  
### <a name="remarks"></a>備註  
 呼叫此方法以終結`CSimpleStringT`物件。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)