---
title: CSimpleStringT 類別
ms.date: 10/18/2018
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
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: bbbab04ff311d874fc209d2c46fadda57e79a222
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219088"
---
# <a name="csimplestringt-class"></a>CSimpleStringT 類別

此類別代表 `CSimpleStringT` 物件。

## <a name="syntax"></a>語法

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>參數

*BaseType*<br/>
字串類別的字元類型。 可以是下列其中一項：

- **`char`**（適用于 ANSI 字元字串）。

- **`wchar_t`**（適用于 Unicode 字元字串）。

- TCHAR （適用于 ANSI 和 Unicode 字元字串）。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|[CSimpleStringT：:P CXSTR](#pcxstr)|常數位串的指標。|
|[CSimpleStringT：:P XSTR](#pxstr)|字串的指標。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|`CSimpleStringT`以各種方式來構造物件。|
|[CSimpleStringT：： ~ CSimpleStringT](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CSimpleStringT：： Append](#append)|將 `CSimpleStringT` 物件附加至現有的 `CSimpleStringT` 物件。|
|[CSimpleStringT::AppendChar](#appendchar)|將字元附加至現有的 `CSimpleStringT` 物件。|
|[CSimpleStringT::CopyChars](#copychars)|將一個或多個字元複製到另一個字串。|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|將一個或多個字元複製到緩衝區重迭的另一個字串。|
|[CSimpleStringT：： Empty](#empty)|強制字串長度為零。|
|[CSimpleStringT::FreeExtra](#freeextra)|釋放字串物件先前配置的任何額外記憶體。|
|[CSimpleStringT::GetAllocLength](#getalloclength)|抓取物件的配置長度 `CSimpleStringT` 。|
|[CSimpleStringT：： GetAt](#getat)|傳回指定位置的字元。|
|[CSimpleStringT：： GetBuffer](#getbuffer)|傳回中之字元的指標 `CSimpleStringT` 。|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|傳回中字元的指標 `CSimpleStringT` ，截斷為指定的長度。|
|[CSimpleStringT：： GetLength](#getlength)|傳回物件中的字元數 `CSimpleStringT` 。|
|[CSimpleStringT::GetManager](#getmanager)|抓取物件的記憶體管理員 `CSimpleStringT` 。|
|[CSimpleStringT：： GetString](#getstring)|抓取字元字串|
|[CSimpleStringT：： IsEmpty](#isempty)|測試物件是否 `CSimpleStringT` 不包含任何字元。|
|[CSimpleStringT::LockBuffer](#lockbuffer)|停用參考計數，並保護緩衝區中的字串。|
|[CSimpleStringT：:P 重新配置](#preallocate)|配置字元緩衝區的特定記憶體數量。|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|釋放所傳回之緩衝區的控制權 `GetBuffer` 。|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|釋放所傳回之緩衝區的控制權 `GetBuffer` 。|
|[CSimpleStringT：： SetAt](#setat)|設定指定位置的字元。|
|[CSimpleStringT::SetManager](#setmanager)|設定物件的記憶體管理員 `CSimpleStringT` 。|
|[CSimpleStringT：： SetString](#setstring)|設定物件的字串 `CSimpleStringT` 。|
|[CSimpleStringT：： StringLength](#stringlength)|傳回指定之字串中的字元數。|
|[CSimpleStringT：：截斷](#truncate)|將字串截斷為指定的長度。|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|啟用參考計數，並釋放緩衝區中的字串。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CSimpleStringT：： operator PCXSTR](#operator_pcxstr)|直接存取以 C 樣式字串儲存在物件中的字元 `CSimpleStringT` 。|
|[CSimpleStringT::operator\[\]](#operator_at)|傳回指定位置的字元-的運算子替代 `GetAt` 。|
|[CSimpleStringT：： operator + =](#operator_add_eq)|將新字串串連至現有字串的結尾。|
|[CSimpleStringT：： operator =](#operator_eq)|將新值指派給 `CSimpleStringT` 物件。|

### <a name="remarks"></a>備註

`CSimpleStringT`是 Visual C++ 支援的各種字串類別的基類。 它針對字串物件和基本緩衝區操作的記憶體管理提供最低的支援。 如需更先進的字串物件，請參閱[CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="requirements"></a>需求

**標頭：** atlsimpstr。h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT：： Append

將 `CSimpleStringT` 物件附加至現有的 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```cpp
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>參數

*strSrc*<br/>
`CSimpleStringT`要附加的物件。

*pszSrc*<br/>
包含要附加之字元的字串指標。

*nLength*<br/>
要附加的字元數。

### <a name="remarks"></a>備註

呼叫這個方法，將現有的 `CSimpleStringT` 物件附加至另一個 `CSimpleStringT` 物件。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::Append` 的用法。

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::AppendChar

將字元附加至現有的 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```cpp
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>參數

*頻道*<br/>
要附加的字元

### <a name="remarks"></a>備註

呼叫此函式可將指定的字元附加至現有物件的結尾 `CSimpleStringT` 。

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::CopyChars

將一個或多個字元複製到 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>參數

*pchDest*<br/>
字元字串的指標。

*pchSrc*<br/>
包含要複製之字元的字串指標。

*nChars*<br/>
要複製的*pchSrc*字元數。

### <a name="remarks"></a>備註

呼叫這個方法，將字元從*pchSrc*複製到*pchDest*字串。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::CopyChars` 的用法。

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

將一個或多個字元複製到 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>參數

*pchDest*<br/>
字元字串的指標。

*pchSrc*<br/>
包含要複製之字元的字串指標。

*nChars*<br/>
要複製的*pchSrc*字元數。

### <a name="remarks"></a>備註

呼叫這個方法，將字元從*pchSrc*複製到*pchDest*字串。 不同于 `CopyChars` ， `CopyCharsOverlapped` 會提供從可能會重迭的字元緩衝區複製的安全方法。

### <a name="example"></a>範例

請參閱[CSimpleStringT：： CopyChars](#copychars)的範例，或的原始程式碼 `CSimpleStringT::SetString` （位於 atlsimpstr 中）。

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a>CSimpleStringT::CSimpleStringT

建構 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>參數

*strSrc*<br/>
`CSimpleStringT`要複製到這個物件中的現有物件 `CSimpleStringT` 。

*pchSrc*<br/>
*NLength*長度的字元陣列指標，而不是以 null 結束。

*pszSrc*<br/>
要複製到這個物件中以 null 結束的字串 `CSimpleStringT` 。

*nLength*<br/>
中的字元數計數 `pch` 。

*pStringMgr*<br/>
物件之記憶體管理員的指標 `CSimpleStringT` 。 如需有關 `IAtlStringMgr` 和的記憶體管理的詳細資訊 `CSimpleStringT` ，請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。

### <a name="remarks"></a>備註

建立新的 `CSimpleStringT` 物件。 因為這些函式會將輸入資料複製到新配置的儲存體，所以可能會產生記憶體例外狀況。

### <a name="example"></a>範例

下列範例示範如何使用 `CSimpleStringT::CSimpleStringT` ATL 來使用 **`typedef`** `CSimpleString` 。 `CSimpleString`是類別樣板常用的特製化 `CSimpleStringT` 。

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

## <a name="csimplestringtempty"></a><a name="empty"></a>CSimpleStringT：： Empty

使此 `CSimpleStringT` 物件成為空字串，並視需要釋放記憶體。

### <a name="syntax"></a>語法

```cpp
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

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::FreeExtra

釋放先前由字串配置但不再需要的任何額外記憶體。

### <a name="syntax"></a>語法

```cpp
void FreeExtra();
```

### <a name="remarks"></a>備註

這應該會降低 string 物件所耗用的記憶體額外負荷。 方法會將緩衝區重新配置為[GetLength](#getlength)所傳回的確切長度。

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

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a>CSimpleStringT::GetAllocLength

抓取物件的配置長度 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>傳回值

配置給這個物件的字元數。

### <a name="remarks"></a>備註

呼叫這個方法，以判斷配置給此物件的字元數 `CSimpleStringT` 。 如需呼叫此函式的範例，請參閱[FreeExtra](#freeextra) 。

## <a name="csimplestringtgetat"></a><a name="getat"></a>CSimpleStringT：： GetAt

從物件傳回一個字元 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>參數

*iChar*<br/>
物件中字元以零為基底的索引 `CSimpleStringT` 。 *IChar*參數必須大於或等於0，且小於[GetLength](#getlength)所傳回的值。 否則， `GetAt` 將會產生例外狀況。

### <a name="return-value"></a>傳回值

`XCHAR`，包含字串中位於指定位置的字元。

### <a name="remarks"></a>備註

呼叫這個方法，以傳回*iChar*所指定的一個字元。 多載的注標（**[]**）運算子是的方便別名 `GetAt` 。 Null 結束字元可以定址，而不需要使用產生例外狀況 `GetAt` 。 不過，它不是由計算 `GetLength` ，而且傳回的值是0。

### <a name="example"></a>範例

下列範例示範如何使用 `CSimpleStringT::GetAt` 。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>CSimpleStringT：： GetBuffer

傳回物件之內部字元緩衝區的指標 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>參數

*nMinBufferLength*<br/>
字元緩衝區可以保存的字元數下限。 這個值不包含 null 結束字元的空間。

如果*nMinBufferLength*大於目前緩衝區的長度，則會終結 `GetBuffer` 目前的緩衝區，以所要求大小的緩衝區取代它，並將物件參考計數重設為零。 如果您先前已在此緩衝區上呼叫[LockBuffer](#lockbuffer) ，就會遺失緩衝區鎖定。

### <a name="return-value"></a>傳回值

`PXSTR`物件的（以 null 終止）字元緩衝區的指標。

### <a name="remarks"></a>備註

呼叫這個方法，以傳回物件的緩衝區內容 `CSimpleStringT` 。 傳回的 `PXSTR` 不是常數，因此允許直接修改 `CSimpleStringT` 內容。

如果您使用所傳回的指標 `GetBuffer` 來變更字串內容，則必須先呼叫[ReleaseBuffer](#releasebuffer) ，然後再使用其他任何 `CSimpleStringT` 成員方法。

在呼叫之後，所傳回的位址 `GetBuffer` 可能不是有效的， `ReleaseBuffer` 因為其他 `CSimpleStringT` 作業可能會導致重新配置 `CSimpleStringT` 緩衝區。 如果您未變更的長度，則不會重新配置緩衝區 `CSimpleStringT` 。

當物件終結時，就會自動釋放緩衝區記憶體 `CSimpleStringT` 。

如果您自行追蹤字串長度，則不應附加終止的 null 字元。 不過，當您釋放緩衝區時，必須指定最後的字串長度 `ReleaseBuffer` 。 如果您確實附加結束的 null 字元，則應該傳遞長度為-1 （預設值）。 `ReleaseBuffer`然後決定緩衝區長度。

如果記憶體不足，無法滿足 `GetBuffer` 要求，這個方法會擲回 CMemoryException *。

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

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

傳回物件之內部字元緩衝區的指標 `CSimpleStringT` ，如果需要完全符合*nLength*中指定的長度，則會截斷或成長其長度。

### <a name="syntax"></a>語法

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>參數

*nLength*<br/>
字元緩衝區的確切大小（ `CSimpleStringT` 以字元為單位）。

### <a name="return-value"></a>傳回值

`PXSTR`物件的（以 null 終止）字元緩衝區的指標。

### <a name="remarks"></a>備註

呼叫這個方法，以抓取物件內部緩衝區的指定長度 `CSimpleStringT` 。 傳回的 `PXSTR` 指標不是 **`const`** ，因此允許直接修改 `CSimpleStringT` 內容。

如果您使用[GetBufferSetLength](#getbuffersetlength)所傳回的指標來變更字串內容，請在 `ReleaseBuffer` `CsimpleStringT` 使用任何其他方法之前，呼叫來更新的內部狀態 `CSimpleStringT` 。

在呼叫之後，所傳回的位址 `GetBufferSetLength` 可能不是有效的， `ReleaseBuffer` 因為其他 `CSimpleStringT` 作業可能會導致重新配置 `CSimpleStringT` 緩衝區。 如果您未變更的長度，則不會重新指派緩衝區 `CSimpleStringT` 。

當物件終結時，就會自動釋放緩衝區記憶體 `CSimpleStringT` 。

如果您自行追蹤字串長度，請勿附加終止的 null 字元。 當您使用釋放緩衝區時，必須指定最後的字串長度 `ReleaseBuffer` 。 如果您在呼叫時附加了終止的 null 字元 `ReleaseBuffer` ，請將長度的傳遞給-1 （預設值） `ReleaseBuffer` ，然後 `ReleaseBuffer` `strlen` 在緩衝區上執行，以判斷其長度。

如需參考計數的詳細資訊，請參閱下列文章：

- 透過 Windows SDK 中的[參考計數來管理物件存留期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)。

- 在 Windows SDK 中[執行參考計數](/windows/win32/com/implementing-reference-counting)。

- 在 Windows SDK 中[管理參考計數的規則](/windows/win32/com/rules-for-managing-reference-counts)。

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

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>CSimpleStringT：： GetLength

傳回物件中的字元數 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```
int GetLength() const throw();
```

### <a name="return-value"></a>傳回值

字串中的字元計數。

### <a name="remarks"></a>備註

呼叫這個方法，以傳回物件中的字元數。 此計數不包括 null 結束字元。

針對多位元組字元集（MBCS），會 `GetLength` 計算每8位字元; 也就是說，一個多位元組字元中的潛在客戶和後隨位元組會視為兩個位元組。 如需呼叫此函式的範例，請參閱[FreeExtra](#freeextra) 。

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT::GetManager

抓取物件的記憶體管理員 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>傳回值

物件之記憶體管理員的指標 `CSimpleStringT` 。

### <a name="remarks"></a>備註

呼叫這個方法，以取出物件所使用的記憶體管理員 `CSimpleStringT` 。 如需記憶體管理員和字串物件的詳細資訊，請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>CSimpleStringT：： GetString

抓取字元字串。

### <a name="syntax"></a>語法

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>傳回值

以 null 結束之字元字串的指標。

### <a name="remarks"></a>備註

呼叫這個方法，以取出與物件相關聯的字元字串 `CSimpleStringT` 。

> [!NOTE]
> 傳回的 `PCXSTR` 指標是 **`const`** ，不允許直接修改 `CSimpleStringT` 內容。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::GetString` 的用法。

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>CSimpleStringT：： IsEmpty

測試 `CSimpleStringT` 空白條件的物件。

### <a name="syntax"></a>語法

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果 `CSimpleStringT` 物件具有0長度，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

呼叫這個方法，以判斷物件是否包含空字串。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::IsEmpty` 的用法。

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a>CSimpleStringT::LockBuffer

停用參考計數，並保護緩衝區中的字串。

### <a name="syntax"></a>語法

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>傳回值

`CSimpleStringT`物件或以 null 終止之字串的指標。

### <a name="remarks"></a>備註

呼叫這個方法來鎖定物件的緩衝區 `CSimpleStringT` 。 藉由呼叫 `LockBuffer` ，您可以建立字串的複本，並以-1 表示參考計數。 當參考計數值為-1 時，緩衝區中的字串會被視為處於「已鎖定」狀態。 處於鎖定狀態時，字串會以兩種方式受到保護：

- 即使該字串已指派給鎖定的字串，其他字串也無法取得鎖定字串中資料的參考。

- 鎖定的字串絕不會參考另一個字串，即使該其他字串已複製到鎖定的字串也一樣。

藉由鎖定緩衝區中的字串，您可以確保字串在緩衝區上的獨佔保存會保持不變。

完成之後 `LockBuffer` ，請呼叫[UnlockBuffer](#unlockbuffer) ，將參考計數重設為1。

> [!NOTE]
> 如果您在鎖定的緩衝區上呼叫[GetBuffer](#getbuffer) ，並將 `GetBuffer` 參數設定 `nMinBufferLength` 為大於目前緩衝區的長度，則會遺失緩衝區鎖定。 這類呼叫 `GetBuffer` 會終結目前的緩衝區，以所要求大小的緩衝區取代它，並將參考計數重設為零。

如需參考計數的詳細資訊，請參閱下列文章：

- 透過 Windows SDK 中的[參考計數來管理物件存留期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)

- 在 Windows SDK 中[執行參考計數](/windows/win32/com/implementing-reference-counting)

- 在 Windows SDK 中[管理參考計數的規則](/windows/win32/com/rules-for-managing-reference-counts)

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

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT：： operator\[\]

呼叫此函式可存取字元陣列的單一字元。

### <a name="syntax"></a>語法

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>參數

*iChar*<br/>
字串中字元以零為基底的索引。

### <a name="remarks"></a>備註

多載的注標（**[]**）運算子會傳回*iChar*中以零為基底的索引所指定的單一字元。 這個運算子是[GetAt](#getat)成員函式的方便替代。

> [!NOTE]
> 您可以使用注標（**[]**）運算子取得中的字元值 `CSimpleStringT` ，但無法使用它來變更中的字元值 `CSimpleStringT` 。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::operator []` 的用法。

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT：： operator\[\]

呼叫此函式可存取字元陣列的單一字元。

### <a name="syntax"></a>語法

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>參數

*iChar*<br/>
字串中字元以零為基底的索引。

### <a name="remarks"></a>備註

多載的注標（**[]**）運算子會傳回*iChar*中以零為基底的索引所指定的單一字元。 這個運算子是[GetAt](#getat)成員函式的方便替代。

> [!NOTE]
> 您可以使用注標（**[]**）運算子取得中的字元值 `CSimpleStringT` ，但無法使用它來變更中的字元值 `CSimpleStringT` 。

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT：： operator + =

將新的字串或字元加入至現有字串的結尾。

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

*pszSrc*<br/>
以 null 結束之字串的指標。

*strSrc*<br/>
現有物件的指標 `CSimpleStringT` 。

*頻道*<br/>
要附加的字元。

### <a name="remarks"></a>備註

運算子會接受另一個 `CSimpleStringT` 物件或字元。 請注意，每當您使用這個串連運算子時，可能會發生記憶體例外狀況，因為新的儲存空間可能會針對加入此物件的字元而配置 `CSimpleStringT` 。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::operator +=` 的用法。

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT：： operator =

將新值指派給 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>參數

*pszSrc*<br/>
以 null 結束之字串的指標。

*strSrc*<br/>
現有物件的指標 `CSimpleStringT` 。

### <a name="remarks"></a>備註

如果目的字串（左側）已經夠大，可以儲存新的資料，則不會執行任何新的記憶體配置。 請注意，當您使用指派運算子時，可能會發生記憶體例外狀況，因為新的儲存體通常會配置來保存產生的 `CSimpleStringT` 物件。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::operator =` 的用法。

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

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>CSimpleStringT：： operator PCXSTR

直接存取以 C 樣式字串儲存在物件中的字元 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>傳回值

字串資料的字元指標。

### <a name="remarks"></a>備註

不會複製任何字元;只會傳回指標。 請小心使用此運算子。 如果您在 `CString` 取得字元指標之後變更物件，則可能會重新配置使指標失效的記憶體。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::operator PCXSTR` 的用法。

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

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT：:P CXSTR

常數位串的指標。

### <a name="syntax"></a>語法

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT：:P 重新配置

設定物件的特定位元組數量 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```cpp
void Preallocate( int nLength);
```

#### <a name="parameters"></a>參數

*nLength*<br/>
字元緩衝區的確切大小（ `CSimpleStringT` 以字元為單位）。

### <a name="remarks"></a>備註

呼叫這個方法來設定物件的特定緩衝區大小 `CSimpleStringT` 。

`CSimpleStringT`如果無法為字元緩衝區配置空間，就會產生 STATUS_NO_MEMORY 的例外狀況。 根據預設，記憶體配置是由 WIN32 API 函數 `HeapAlloc` 或執行 `HeapReAlloc` 。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::Preallocate` 的用法。

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>CSimpleStringT：:P XSTR

字串的指標。

### <a name="syntax"></a>語法

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

釋放[GetBuffer](#getbuffer)所配置之緩衝區的控制權。

### <a name="syntax"></a>語法

```cpp
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>參數

*nNewLength*<br/>
字串的新長度（以字元為單位），不會計算 null 結束字元。 如果字串為 null 終止，-1 預設值會將大小設 `CSimpleStringT` 為字串的目前長度。

### <a name="remarks"></a>備註

呼叫這個方法來重新配置或釋放字串物件的緩衝區。 如果您知道緩衝區中的字串是以 null 終止，您可以省略*nNewLength*引數。 如果您的字串不是以 null 結束，請使用*nNewLength*來指定其長度。 呼叫或任何其他作業之後， [GetBuffer](#getbuffer)傳回的位址無效 `ReleaseBuffer` `CSimpleStringT` 。

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

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

釋放[GetBuffer](#getbuffer)所配置之緩衝區的控制權。

### <a name="syntax"></a>語法

```cpp
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>參數

*nNewLength*<br/>
要釋放的字串長度

### <a name="remarks"></a>備註

此函式的功能類似[ReleaseBuffer](#releasebuffer) ，不同之處在于必須傳遞字串物件的有效長度。

## <a name="csimplestringtsetat"></a><a name="setat"></a>CSimpleStringT：： SetAt

從物件設定單一字元 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```cpp
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>參數

*iChar*<br/>
物件中字元以零為基底的索引 `CSimpleStringT` 。 *IChar*參數必須大於或等於0，且小於[GetLength](#getlength)所傳回的值。

*頻道*<br/>
新的字元。

### <a name="remarks"></a>備註

呼叫這個方法來覆寫位於*iChar*的字元。 如果*iChar*超過現有字串的範圍，這個方法將不會放大字串。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::SetAt` 的用法。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>CSimpleStringT::SetManager

指定物件的記憶體管理員 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```cpp
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>參數

*pStringMgr*<br/>
新記憶體管理員的指標。

### <a name="remarks"></a>備註

呼叫這個方法，以指定物件所使用的新記憶體管理員 `CSimpleStringT` 。 如需記憶體管理員和字串物件的詳細資訊，請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::SetManager` 的用法。

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>CSimpleStringT：： SetString

設定物件的字串 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```cpp
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>參數

*pszSrc*<br/>
以 null 結束之字串的指標。

*nLength*<br/>
*PszSrc*中的字元數計數。

### <a name="remarks"></a>備註

將字串複製到 `CSimpleStringT` 物件中。 `SetString`覆寫緩衝區中較舊的字串資料。

這兩個版本的 `SetString` 會檢查*pszSrc*是否為 null 指標，如果是，則會擲回 E_INVALIDARG 錯誤。

的單一參數版本 `SetString` 預期*pszSrc*會指向以 null 結束的字串。

的雙參數版本 `SetString` 也需要*pszSrc*為以 null 結束的字串。 除非先遇到 null 結束字元，否則會使用*nLength*做為字串長度。

的雙參數版本也會 `SetString` 檢查*pszSrc*是否指向中目前緩衝區的位置 `CSimpleStringT` 。 在此特殊情況下， `SetString` 會使用不會覆寫字串資料的記憶體複製函數，因為它會將字串資料複製回其緩衝區。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::SetString` 的用法。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a>CSimpleStringT：： StringLength

傳回指定之字串中的字元數。

### <a name="syntax"></a>語法

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>參數

*psz*<br/>
以 null 結束之字串的指標。

### <a name="return-value"></a>傳回值

*Psz*中的字元數;不計算 null 結束字元。

### <a name="remarks"></a>備註

呼叫這個方法，以取得*psz*所指向之字串中的字元數。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::StringLength` 的用法。

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT：：截斷

將字串截斷為新的長度。

### <a name="syntax"></a>語法

```cpp
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>參數

*nNewLength*<br/>
字串的新長度。

### <a name="remarks"></a>備註

呼叫這個方法，將字串的內容截斷為新的長度。

> [!NOTE]
> 這不會影響緩衝區的配置長度。 若要減少或增加目前的緩衝區，請參閱[FreeExtra](#freeextra) [和預先](#preallocate)配置。

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

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer

解除鎖定物件的緩衝區 `CSimpleStringT` 。

### <a name="syntax"></a>語法

```cpp
void UnlockBuffer() throw();
```

### <a name="remarks"></a>備註

呼叫這個方法，將字串的參考計數重設為1。

`CSimpleStringT`函式會自動呼叫 `UnlockBuffer` 以確保呼叫析構函式時，不會鎖定緩衝區。 如需這個方法的範例，請參閱[LockBuffer](#lockbuffer)。

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>CSimpleStringT：： ~ CSimpleStringT

終結 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>備註

呼叫這個方法來摧毀 `CSimpleStringT` 物件。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
