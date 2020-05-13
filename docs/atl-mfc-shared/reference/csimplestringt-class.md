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
ms.openlocfilehash: 76d418c4f063d5787209ea72e7c681013eb37801
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747028"
---
# <a name="csimplestringt-class"></a>CSimpleStringT 類別

此表示物件`CSimpleStringT`。

## <a name="syntax"></a>語法

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>參數

*BaseType*<br/>
字串類的字元類型。 可以是下列其中一項：

- **字元**(用於 ANSI 字串)。

- **wchar_t(** 對於 Unicode 字串)。

- TCHAR(適用於 ANSI 和 Unicode 字串)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|指向常量字串的指標。|
|[簡單StringT::PXSTR](#pxstr)|指向字串的指標。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[簡單StringT::簡單StringT](#ctor)|以各種方式構造`CSimpleStringT`物件。|
|[簡單StringT:_CSimpleStringT](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleStringT::附加](#append)|將`CSimpleStringT`物件追加到現有`CSimpleStringT`物件。|
|[CSimpleStringT::附錄查爾](#appendchar)|將字元追加到現有`CSimpleStringT`物件。|
|[CSimpleStringT::複製字元](#copychars)|將字元或字元複製到另一個字串。|
|[CSimpleStringT::複製字元重疊](#copycharsoverlapped)|將字元或字元複製到緩衝區重疊的另一個字串。|
|[簡單StringT:空](#empty)|強制字串的長度為零。|
|[CSimpleStringT::免費額外](#freeextra)|釋放以前由字串元件分配的任何額外記憶體。|
|[簡單StringT:獲取 Alloc 長度](#getalloclength)|檢索`CSimpleStringT`物件的分配長度。|
|[簡單Stringt:getat](#getat)|返回給定位置的字元。|
|[簡單StringT:取得緩衝區](#getbuffer)|返回指向 中的字元`CSimpleStringT`的指標。|
|[CSimpleStringT:取得緩衝區集長度](#getbuffersetlength)|返回指向`CSimpleStringT`的指標,該指標將截斷到指定長度。|
|[簡單StringT:取得長度](#getlength)|傳`CSimpleStringT`回 物件中的字元數。|
|[CSimpleStringT:取得管理員](#getmanager)|檢索`CSimpleStringT`物件的記憶體管理器。|
|[簡單StringT:取得String](#getstring)|取索字串|
|[簡單StringT::是空的](#isempty)|測試`CSimpleStringT`物件是否不包含字元。|
|[簡單StringT:鎖緩衝區](#lockbuffer)|關閉引言計數並保護緩衝區中的字串。|
|[CSimpleStringT::P重新分配](#preallocate)|為字元緩衝區分配特定數量的記憶體。|
|[CSimpleStringT::釋放緩衝區](#releasebuffer)|釋放對返回的`GetBuffer`緩衝區的控制。|
|[CSimpleStringT::釋放緩衝區集長度](#releasebuffersetlength)|釋放對返回的`GetBuffer`緩衝區的控制。|
|[簡單Stringt::Setat](#setat)|在給定位置設置字元。|
|[簡單StringT:setManager](#setmanager)|設置`CSimpleStringT`物件的記憶體管理員。|
|[簡單StringT::設置String](#setstring)|設定`CSimpleStringT`物件的字串。|
|[簡單StringT:字串長度](#stringlength)|傳回指定字串中的字元數。|
|[CSimpleStringT::截流](#truncate)|將字串截排到指定長度。|
|[CSimpleStringT::解鎖緩衝區](#unlockbuffer)|啟用引用計數並釋放緩衝區中的字串。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[簡單StringT::操作員 PCXSTR](#operator_pcxstr)|直接存取為 C`CSimpleStringT`樣式 字串儲存在物件中的字元。|
|[CSimpleStringT::operator\[\]](#operator_at)|傳回給定位置的字元 = 運算`GetAt`子取代 。|
|[CSimpleStringT::運算符 |](#operator_add_eq)|將新字串串聯到現有字串的末尾。|
|[CSimpleStringT::運算符 |](#operator_eq)|為`CSimpleStringT`物件分配新值。|

### <a name="remarks"></a>備註

`CSimpleStringT`是 Visual C++ 支援的各種字串類的基類。 它為字串物件的記憶體管理和基本緩衝區操作提供了最少的支援。 有關更進階的字串物件,請參閱[CStringt 類別](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="requirements"></a>需求

**標題:** atlsimpstr.h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT::附加

將`CSimpleStringT`物件追加到現有`CSimpleStringT`物件。

### <a name="syntax"></a>語法

```cpp
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>參數

*斯特斯爾克*<br/>
要`CSimpleStringT`追加的物件。

*皮茨斯爾克*<br/>
指向包含要追加的字元的字串的指標。

*N 長度*<br/>
要附加的字元數。

### <a name="remarks"></a>備註

調用此方法將現有`CSimpleStringT`物件追加到另一`CSimpleStringT`個 物件。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::Append` 的用法。

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::附錄查爾

將字元追加到現有`CSimpleStringT`物件。

### <a name="syntax"></a>語法

```cpp
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>參數

*ch*<br/>
要附加的字元

### <a name="remarks"></a>備註

呼叫此函數以將指定的字元追加到現有`CSimpleStringT`物件的末尾。

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::複製字元

將字元或字元複製到`CSimpleStringT`物件。

### <a name="syntax"></a>語法

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>參數

*pchDest*<br/>
指向字串的指標。

*普施斯克*<br/>
指向包含要複製的字元的字串的指標。

*n查理斯*<br/>
要複製的*pchSrc*字元數。

### <a name="remarks"></a>備註

呼叫此方法以將字元從*pchSrc*複製到*pchDest*字串。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::CopyChars` 的用法。

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::複製字元重疊

將字元或字元複製到`CSimpleStringT`物件。

### <a name="syntax"></a>語法

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>參數

*pchDest*<br/>
指向字串的指標。

*普施斯克*<br/>
指向包含要複製的字元的字串的指標。

*n查理斯*<br/>
要複製的*pchSrc*字元數。

### <a name="remarks"></a>備註

呼叫此方法以將字元從*pchSrc*複製到*pchDest*字串。 與`CopyChars``CopyCharsOverlapped`不同,提供了一種安全的方法,用於從可能重疊的字元緩衝區複製。

### <a name="example"></a>範例

請參閱[CSimpleStringT::複製字元](#copychars)的範例,`CSimpleStringT::SetString`或 ( 位於 atlsimpstr.h) 的原始碼。

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a>簡單StringT::簡單StringT

建構 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>參數

*斯特斯爾克*<br/>
要複製到`CSimpleStringT``CSimpleStringT`此物件的現有物件。

*普施斯克*<br/>
指向長度*nLength*的字元陣列的指標,而不是 null 終止。

*皮茨斯爾克*<br/>
要複製到此`CSimpleStringT`物件的 null 中止字串。

*N 長度*<br/>
中字元數的計數`pch`。

*普斯特林姆格*<br/>
指向物件的記憶體管理器的`CSimpleStringT`指標。 有關 的詳細`IAtlStringMgr`資訊 和記憶體`CSimpleStringT`管理 ,請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。

### <a name="remarks"></a>備註

構造新`CSimpleStringT`物件。 由於建構函數將輸入數據複製到新的分配存儲中,因此可能會導致記憶體異常。

### <a name="example"></a>範例

下面的範例展示使用 ATL`CSimpleStringT::CSimpleStringT`**類型def**`CSimpleString`的 。 `CSimpleString`是類範本`CSimpleStringT`的常用專門化。

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

## <a name="csimplestringtempty"></a><a name="empty"></a>簡單StringT:空

使此`CSimpleStringT`對象成為空字串,並根據需要釋放記憶體。

### <a name="syntax"></a>語法

```cpp
void Empty() throw();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[字串:CString 的狀況 。](../cstring-exception-cleanup.md)

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::Empty` 的用法。

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::免費額外

釋放以前由字串分配但不再需要的任何額外記憶體。

### <a name="syntax"></a>語法

```cpp
void FreeExtra();
```

### <a name="remarks"></a>備註

這將減少字串物件消耗的記憶體開銷。 該方法將緩衝區重新分配到[GetLength](#getlength)返回的確切長度。

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

此範例的輸出如下所示:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a>簡單StringT:獲取 Alloc 長度

檢索`CSimpleStringT`物件的分配長度。

### <a name="syntax"></a>語法

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>傳回值

為此物件分配的字元數。

### <a name="remarks"></a>備註

呼叫此方法以確定為此`CSimpleStringT`物件分配的字元數。 有關調用此函數的示例,請參閱[FreeExtra。](#freeextra)

## <a name="csimplestringtgetat"></a><a name="getat"></a>簡單Stringt:getat

從物件傳回一個字`CSimpleStringT`元 。

### <a name="syntax"></a>語法

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>參數

*i查爾*<br/>
`CSimpleStringT`對象中字元的零基索引。 *iChar*參數必須大於或等於 0,小於[GetLength](#getlength)返回的值。 否則,`GetAt`將產生異常。

### <a name="return-value"></a>傳回值

包含`XCHAR`字串中指定位置的字元 。

### <a name="remarks"></a>備註

呼叫此方法傳回*iChar*指定的一個字元。 重載子標 (*****) 運算`GetAt`子是 的 方便別名。 空終止符是可定址的,無需使用`GetAt`生成異常。 但是,它不按`GetLength`計數,返回的值為 0。

### <a name="example"></a>範例

下面的範例展示如何使用`CSimpleStringT::GetAt`。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>簡單StringT:取得緩衝區

返回指向物件的內部字元緩衝區的`CSimpleStringT`指標。

### <a name="syntax"></a>語法

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>參數

*n 最小緩衝區長度*<br/>
字元緩衝區可以容納的最小字元數。 此值不包括空終止符的空間。

如果*nMinBufferLength 大於*當前緩衝區的長`GetBuffer`度,則銷毀當前緩衝區,將其替換為請求大小的緩衝區,並將物件引用計數重置為零。 如果以前在此緩衝區上調用[LockBuffer,](#lockbuffer)則丟失緩衝區鎖。

### <a name="return-value"></a>傳回值

指向`PXSTR`物件的(空終止)字元緩衝區的指標。

### <a name="remarks"></a>備註

調用此方法以返回`CSimpleStringT`物件的緩衝區內容。 返回`PXSTR`的不是常量,因此允許直接修改`CSimpleStringT`內容。

如果使用返回`GetBuffer`的指標更改字串內容,則必須在使用任何其他`CSimpleStringT`成員方法之前調用[ReleaseBuffer。](#releasebuffer)

傳`GetBuffer`回的位址在呼叫後可能無效`ReleaseBuffer`,`CSimpleStringT`因為其他`CSimpleStringT`操作可能導致緩衝區被重新分配。 如果不更改 的長`CSimpleStringT`度 ,則不會重新分配緩衝區。

銷毀物件時,`CSimpleStringT`將自動釋放緩衝區內存。

如果自己跟蹤字串長度,則不應追加終止空字元。 但是,在釋放使用`ReleaseBuffer`的緩衝區時,必須指定最終字串長度。 如果確實追加了終止空字元,則應為長度傳遞 -1(預設值)。 `ReleaseBuffer`然後確定緩衝區長度。

如果記憶體不足以滿足`GetBuffer`請求,此方法將引發 CMemoryException*。

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

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT:取得緩衝區集長度

返回指向物件內部字元緩衝區的`CSimpleStringT`指標,如果需要,將截斷或增加其長度以完全匹配*nLength*中指定的長度。

### <a name="syntax"></a>語法

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>參數

*N 長度*<br/>
字元緩衝區的確切`CSimpleStringT`大小(以字元表示)。

### <a name="return-value"></a>傳回值

指向`PXSTR`物件的(空終止)字元緩衝區的指標。

### <a name="remarks"></a>備註

調用此方法以檢索`CSimpleStringT`物件內部緩衝區的指定長度。 返回`PXSTR`的指標不**協調**,因此允許直接`CSimpleStringT`修改 內容。

如果使用[GetBufferSetLength 傳回](#getbuffersetlength)的指標更改字串內容,請呼`ReleaseBuffer`叫 以在使用`CsimpleStringT``CSimpleStringT`任何其他方法之前更新的內部狀態。

傳`GetBufferSetLength`回的位址在呼叫後可能無效`ReleaseBuffer`,`CSimpleStringT`因為其他`CSimpleStringT`操作可能導致緩衝區被重新分配。 如果不更改 的長`CSimpleStringT`度 ,則不重新分配緩衝區。

銷毀物件時,`CSimpleStringT`將自動釋放緩衝區內存。

如果自己跟蹤字串長度,請不要追加終止空字元。 使用 釋放緩衝區時,必須指定最終字串長度`ReleaseBuffer`。 如果在調用`ReleaseBuffer`時追加了終止空字元 ,則將長度`ReleaseBuffer`傳遞給 -1(預設值`ReleaseBuffer`),並將 對緩衝`strlen`區執行 以確定 其長度。

有關引用計數的詳細資訊,請參閱以下文章:

- 使用 Windows SDK 的[引譯計數管理物件存留期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)。

- 在 Windows SDK[中 提供引言值 。](/windows/win32/com/implementing-reference-counting)

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

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>簡單StringT:取得長度

傳回物件`CSimpleStringT`中的字元數。

### <a name="syntax"></a>語法

```
int GetLength() const throw();
```

### <a name="return-value"></a>傳回值

字串中字元的計數。

### <a name="remarks"></a>備註

呼叫此方法以返回物件中的字元數。 計數不包括空終止符。

對於多位元組位元集 (MBCS),`GetLength`計算每個 8 位元字元;也就是說,一個多位元組位元中的引線和跟蹤位元組計為兩個字節。 有關調用此函數的示例,請參閱[FreeExtra。](#freeextra)

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT:取得管理員

檢索`CSimpleStringT`物件的記憶體管理器。

### <a name="syntax"></a>語法

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>傳回值

指向物件的記憶體管理器的`CSimpleStringT`指標。

### <a name="remarks"></a>備註

調用此方法以檢索`CSimpleStringT`物件使用的記憶體管理員。 有關記憶體管理員和字串物件的詳細資訊,請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>簡單StringT:取得String

檢索字串。

### <a name="syntax"></a>語法

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>傳回值

指向 null 終止字串的指標。

### <a name="remarks"></a>備註

呼叫此方法以檢索與`CSimpleStringT`物件關聯的字串。

> [!NOTE]
> 返回`PCXSTR`的指標**是 const,** 不允許`CSimpleStringT`直接修改 內容。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::GetString` 的用法。

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>簡單StringT::是空的

測試`CSimpleStringT`空條件的物件。

### <a name="syntax"></a>語法

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果物件長度為`CSimpleStringT`0,則返回 TRUE;如果物件長度為 0,則返回 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

呼叫此方法以確定物件是否包含空字串。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::IsEmpty` 的用法。

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a>簡單StringT:鎖緩衝區

關閉引言計數並保護緩衝區中的字串。

### <a name="syntax"></a>語法

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>傳回值

指向`CSimpleStringT`物件的指標或 null 終止的字串。

### <a name="remarks"></a>備註

調用此方法以鎖定`CSimpleStringT`對象的緩衝區。 以呼叫`LockBuffer`,可以建立字串的副本,該副本為 -1 表示引用計數。 當引用計數值為 -1 時,緩衝區中的字串被視為處於"鎖定"狀態。 處於鎖定狀態時,字串通過兩種方式受到保護:

- 任何其他字串都無法獲取對鎖定字串中數據的引用,即使該字串已分配給鎖定的字串也是如此。

- 鎖定的字串永遠不會引用另一個字串,即使該其他字串複製到鎖定的字串。

通過在緩衝區中鎖定字串,可確保字串對緩衝區的獨佔保留將保持不變。

完成`LockBuffer`後,調用[UnlockBuffer](#unlockbuffer)將引用計數重置為 1。

> [!NOTE]
> 如果在鎖定的緩衝區上調用[GetBuffer,](#getbuffer)`GetBuffer``nMinBufferLength`並將參數 設置為大於當前緩衝區的長度,則將丟失緩衝區鎖。 這種調用會破壞`GetBuffer`當前緩衝區,將其替換為請求大小的緩衝區,並將引用計數重置為零。

有關引用計數的詳細資訊,請參閱以下文章:

- 透過 Windows SDK 中的[引譯計數管理物件存留期](/windows/win32/com/managing-object-lifetimes-through-reference-counting)

- 在 Windows SDK[中 提供引言計數](/windows/win32/com/implementing-reference-counting)

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

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT::運算子\[\]

呼叫此函數以造訪字元陣列的單個字元。

### <a name="syntax"></a>語法

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>參數

*i查爾*<br/>
字串中字元的零基索引。

### <a name="remarks"></a>備註

重載子標 (*****) 運算符傳回*iChar*中的零基索引指定的單個字元。 此運算符是[GetAt](#getat)成員函數的便捷替代。

> [!NOTE]
> 可以使用下標 (*****) 運算元獲取 中的`CSimpleStringT`字元的值 ,但不能`CSimpleStringT`使用它來更改 中字元的值。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::operator []` 的用法。

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT::運算子\[\]

呼叫此函數以造訪字元陣列的單個字元。

### <a name="syntax"></a>語法

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>參數

*i查爾*<br/>
字串中字元的零基索引。

### <a name="remarks"></a>備註

重載子標 (*****) 運算符傳回*iChar*中的零基索引指定的單個字元。 此運算符是[GetAt](#getat)成員函數的便捷替代。

> [!NOTE]
> 可以使用下標 (*****) 運算元獲取 中的`CSimpleStringT`字元的值 ,但不能`CSimpleStringT`使用它來更改 中字元的值。

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT::運算符 |

將新字串或字元聯接到現有字串的末尾。

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

*皮茨斯爾克*<br/>
指向 null 終止字串的指標。

*斯特斯爾克*<br/>
指向現有`CSimpleStringT`物件的指標。

*ch*<br/>
要附加的字元。

### <a name="remarks"></a>備註

運算元接受另一`CSimpleStringT`個物件或字元。 請注意,每當使用此串聯運算元時,都可能發生記憶體異常,因為可能會為添加到此`CSimpleStringT`物件的字元分配新存儲。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::operator +=` 的用法。

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT::運算符 |

為`CSimpleStringT`物件分配新值。

### <a name="syntax"></a>語法

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>參數

*皮茨斯爾克*<br/>
指向 null 終止字串的指標。

*斯特斯爾克*<br/>
指向現有`CSimpleStringT`物件的指標。

### <a name="remarks"></a>備註

如果目標字串(左側)已足夠大以存儲新數據,則不執行新的記憶體分配。 請注意,每當使用賦值運算符時,都可能發生記憶體異常,因為通常分配新存儲來保存生成的`CSimpleStringT`物件。

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

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>簡單StringT::操作員 PCXSTR

直接存取為 C`CSimpleStringT`樣式 字串儲存在物件中的字元。

### <a name="syntax"></a>語法

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>傳回值

指向字串資料的字元指標。

### <a name="remarks"></a>備註

不複製任何字元;僅返回指標。 小心此運算符。 如果在獲取字元指標`CString`後更改物件,則可能導致重新分配記憶體,使指標無效。

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

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT::PCXSTR

指向常量字串的指標。

### <a name="syntax"></a>語法

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT::P重新分配

為`CSimpleStringT`物件分配特定數量的位元組。

### <a name="syntax"></a>語法

```cpp
void Preallocate( int nLength);
```

#### <a name="parameters"></a>參數

*N 長度*<br/>
字元緩衝區的確切`CSimpleStringT`大小(以字元表示)。

### <a name="remarks"></a>備註

調用此方法為`CSimpleStringT`物件分配特定的緩衝區大小。

`CSimpleStringT`如果無法為字元緩衝區分配空間,則生成STATUS_NO_MEMORY異常。 默認情況下,記憶體分配由 WIN32 API`HeapAlloc`函`HeapReAlloc`數 或執行。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::Preallocate` 的用法。

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>簡單StringT::PXSTR

指向字串的指標。

### <a name="syntax"></a>語法

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::釋放緩衝區

釋放[GetBuffer](#getbuffer)分配的緩衝區的控制權。

### <a name="syntax"></a>語法

```cpp
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>參數

*n 新長度*<br/>
字串的新長度以字元表示,不包括空終止字元。 如果字串為 null 終止,則 -1`CSimpleStringT`預設值 將大小設定為字串的當前長度。

### <a name="remarks"></a>備註

呼叫此方法以重新分配或釋放字串物件的緩衝區。 如果您知道緩衝區的字串為 null 終止,則可以省略*nNewLength 參數*。 如果字串未為 null 終止,請使用*nNewLength*指定其長度。 [GetBuffer](#getbuffer)返回的位址`ReleaseBuffer`在調用後或任何`CSimpleStringT`其他 操作無效。

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

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT::釋放緩衝區集長度

釋放[GetBuffer](#getbuffer)分配的緩衝區的控制權。

### <a name="syntax"></a>語法

```cpp
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>參數

*n 新長度*<br/>
要釋放的字串的長度

### <a name="remarks"></a>備註

此函數在功能上與[ReleaseBuffer](#releasebuffer)類似,只不過必須傳遞字串物件的有效長度。

## <a name="csimplestringtsetat"></a><a name="setat"></a>簡單Stringt::Setat

從`CSimpleStringT`物件設置單個字元。

### <a name="syntax"></a>語法

```cpp
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>參數

*i查爾*<br/>
`CSimpleStringT`對象中字元的零基索引。 *iChar*參數必須大於或等於 0,小於[GetLength](#getlength)返回的值。

*ch*<br/>
新字元。

### <a name="remarks"></a>備註

呼叫此方法來覆蓋位於*iChar*的字元。 如果*iChar*超過現有字串的邊界,此方法將不會放大字串。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::SetAt` 的用法。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>簡單StringT:setManager

指定`CSimpleStringT`物件的記憶體管理員。

### <a name="syntax"></a>語法

```cpp
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>參數

*普斯特林姆格*<br/>
指向新記憶體管理器的指標。

### <a name="remarks"></a>備註

呼叫此方法以指定`CSimpleStringT`物件使用的新記憶體管理員。 有關記憶體管理員和字串物件的詳細資訊,請參閱[記憶體管理和 CStringT](../memory-management-with-cstringt.md)。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::SetManager` 的用法。

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>簡單StringT::設置String

設定`CSimpleStringT`物件的字串。

### <a name="syntax"></a>語法

```cpp
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>參數

*皮茨斯爾克*<br/>
指向 null 終止字串的指標。

*N 長度*<br/>
*pszSrc*中字元數的計數。

### <a name="remarks"></a>備註

將字串複製到物件中`CSimpleStringT`。 `SetString`覆蓋緩衝區中較舊的字串資料。

兩個版本`SetString`的檢查*pszSrc*是否為空指標,如果是,則引發E_INVALIDARG錯誤。

*szSrc*的`SetString`單 參數版本將指向 null 終止字串。

的`SetString`兩參數版本也期望*pszSrc*是一個 null 終止的字串。 它使用*nLength*作為字串長度,除非它首先遇到空終止符。

的`SetString`兩參數版本還檢查*pszSrc*`CSimpleStringT`是否指向 中 當前緩衝區中的位置。 在此特殊情況中,`SetString`使用記憶體複製函數在將字串資料複製回其緩衝區時不覆蓋字串資料。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::SetString` 的用法。

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a>簡單StringT:字串長度

傳回指定字串中的字元數。

### <a name="syntax"></a>語法

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>參數

*psz*<br/>
指向 null 終止字串的指標。

### <a name="return-value"></a>傳回值

*psz*中的字元數 ;不包括空終止符。

### <a name="remarks"></a>備註

呼叫此方法以檢索*psz*指向的字串中的字元。

### <a name="example"></a>範例

下列範例示範 `CSimpleStringT::StringLength` 的用法。

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT::截流

將字串截排到新長度。

### <a name="syntax"></a>語法

```cpp
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>參數

*n 新長度*<br/>
字串的新長度。

### <a name="remarks"></a>備註

呼叫此方法以將字串的內容截接到新長度。

> [!NOTE]
> 這不會影響緩衝區的分配長度。 要減小或增加當前緩衝區,請參閱[FreeExtra](#freeextra)和[預分配](#preallocate)。

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

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT::解鎖緩衝區

解鎖`CSimpleStringT`對象的緩衝區。

### <a name="syntax"></a>語法

```cpp
void UnlockBuffer() throw();
```

### <a name="remarks"></a>備註

呼叫此方法將字串的引用計數重置為 1。

析`CSimpleStringT`構函數會自動調`UnlockBuffer`用 以確保在調用析構函數時緩衝區未鎖定。 有關此方法的範例,請參閱[LockBuffer](#lockbuffer)。

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>簡單StringT:_CSimpleStringT

終結 `CSimpleStringT` 物件。

### <a name="syntax"></a>語法

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>備註

呼叫此方法以銷毀物件`CSimpleStringT`。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
