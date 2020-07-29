---
title: CStrBufT 類別
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 4d9d0b403e572d6fdea65355702467c89587cc3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219075"
---
# <a name="cstrbuft-class"></a>CStrBufT 類別

這個類別會針對 `GetBuffer` 現有的物件，提供和呼叫的自動資源清除 `ReleaseBuffer` `CStringT` 。

## <a name="syntax"></a>語法

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>參數

*TCharType*<br/>
類別的字元類型 `CStrBufT` 。 可以是下列其中一項：

- **`char`**（適用于 ANSI 字元字串）

- **`wchar_t`**（適用于 Unicode 字元字串）

- TCHAR （適用于 ANSI 和 Unicode 字元字串）

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|PCXSTR|常數位串的指標。|
|PXSTR|字串的指標。|
|`StringType`|要由這個類別樣板的特製化操作其緩衝區的字串類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|字串緩衝區物件的構造函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CStrBufT：： SetLength](#setlength)|設定相關聯字串物件的字元緩衝區長度。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CStrBufT：： operator PCXSTR](#operator_pcxstr)|抓取 **`const`** 相關聯字串物件之字元緩衝區的指標。|
|[CStrBufT：： operator PXSTR](#operator_pxstr)|抓取相關聯字串物件之字元緩衝區的指標。|

### <a name="public-constants"></a>公用常數

|名稱|說明|
|----------|-----------------|
|[CStrBufT：： AUTO_LENGTH](#auto_length)|在發行時自動判斷字串的新長度。|
|[CStrBufT：： SET_LENGTH](#set_length)|在 GetBuffer 階段設定字串物件的長度|

## <a name="remarks"></a>備註

這個類別是用來取代[GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)的呼叫，或[GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)和的包裝函式類別 `ReleaseBuffer` 。

主要設計為協助程式類別， `CStrBufT` 可讓開發人員使用字串物件的字元緩衝區，而不必擔心如何或何時呼叫 `ReleaseBuffer` 。 這是可能的，因為在例外狀況或多個結束程式碼路徑的情況下，包裝函式物件會自然地超出範圍;導致其析構函式釋放字串資源。

## <a name="requirements"></a>需求

**標頭：** atlsimpstr。h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT：： AUTO_LENGTH

在發行時自動判斷字串的新長度。

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>備註

在發行時自動判斷字串的新長度。 字串必須以 null 結束。

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT

構造緩衝區物件。

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>參數

*字串*<br/>
與緩衝區相關聯的字串物件。 一般而言，開發人員會使用預先定義的 typedef `CStrBuf` （TCHAR variant）、 `CStrBufA` （ **`char`** variant）和 `CStrBufW` （ **`wchar_t`** variant）。

*nMinLength*<br/>
字元緩衝區的最小長度。

*dwFlags*<br/>
決定是否自動決定字串長度。 可以是下列其中一項：

- 呼叫[CSimpleStringT：： Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)時，會自動判斷 AUTO_LENGTH 字串長度。 字串必須以 null 結束。 預設值。

- 呼叫[CSimpleStringT：： GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)時，會設定 SET_LENGTH 字串長度。

### <a name="remarks"></a>備註

建立相關聯字串物件的字串緩衝區。 在結構中，會呼叫[CSimpleStringT：： GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)或[CSimpleStringT：： GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) 。

請注意，複製的函數是 **`private`** 。

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT：： operator PCXSTR

直接存取儲存在相關聯字串物件中的字元做為 C 樣式字串。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>傳回值

字串資料的字元指標。

### <a name="remarks"></a>備註

呼叫此函式可傳回字串物件之字元緩衝區的指標。 無法使用這個指標來變更字串物件的內容。

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT：： operator PXSTR

直接存取儲存在相關聯字串物件中的字元做為 C 樣式字串。

```
operator PXSTR() throw();
```

### <a name="return-value"></a>傳回值

字串資料的字元指標。

### <a name="remarks"></a>備註

呼叫此函式可傳回字串物件之字元緩衝區的指標。 開發人員可以使用這個指標來變更 string 物件的內容。

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT：:P CXSTR

常數位串的指標。

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT：:P XSTR

字串的指標。

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT：： SET_LENGTH

設定字串物件的 `GetBuffer` 時間長度。

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>備註

在 GetBuffer 階段設定字串物件的長度。

決定在結構化字串緩衝區物件時，是否呼叫[CSimpleStringT：： GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT：： GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) 。

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT：： SetLength

設定字元緩衝區的長度。

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>參數

*nLength*<br/>
字串物件之字元緩衝區的新長度。

> [!NOTE]
> 必須小於或等於的函式中所指定的最小緩衝區長度 `CStrBufT` 。

### <a name="remarks"></a>備註

呼叫此函式可設定緩衝區物件所表示的字串長度。

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT::StringType

要由這個類別樣板的特製化操作其緩衝區的字串類型。

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>備註

`TCharType`這是用來特殊化類別樣板的字元類型。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
