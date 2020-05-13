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
ms.openlocfilehash: 71d7b6f7d53e9613b1ac26013d73c1dbd1ef0aab
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746935"
---
# <a name="cstrbuft-class"></a>CStrBufT 類別

此類為現有`GetBuffer``CStringT`物件提供自動資源`ReleaseBuffer`清理和調用。

## <a name="syntax"></a>語法

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>參數

*TCharType*<br/>
類的`CStrBufT`字元類型。 可以是下列其中一項：

- **字元**(用於 ANSI 字串)

- **wchar_t(** 用於 Unicode 字串 )

- TCHAR(適用於 ANSI 與 Unicode 字串)

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|PCXSTR|指向常量字串的指標。|
|PXSTR|指向字串的指標。|
|`StringType`|其緩衝區將由此類範本的專門化操作的字串類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CStrBufT:CStrBufT](#cstrbuft)|字串緩衝區物件的構造函數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStrBufT::設定長度](#setlength)|設置關聯字串物件的字元緩衝區長度。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CStrBufT::操作員PCXSTR](#operator_pcxstr)|檢索指向關聯字串物件的字元緩衝區的**const**指標。|
|[CStrBufT::操作員PXSTR](#operator_pxstr)|檢索指向關聯字串物件的字元緩衝區的指標。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[CStrBufT:AUTO_LENGTH](#auto_length)|在發佈時自動確定字串的新長度。|
|[CStrBufT:SET_LENGTH](#set_length)|在 GetBuffer 時間設定字串物件的長度|

## <a name="remarks"></a>備註

此類用作包裝類,用於替換對[GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[釋放緩衝區](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)的呼叫,或[GetBufferSet](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)`ReleaseBuffer`長度和 。

主要設計為協助器類別,`CStrBufT`為開發者提供一種使用字串物件的字元緩衝區的便捷方法,而不必擔心如何或何時呼叫`ReleaseBuffer`。 這是可能的,因為包裝對象在異常或多個退出代碼路徑的情況下自然超出範圍;導致其析構函數釋放字串資源。

## <a name="requirements"></a>需求

**標題:** atlsimpstr.h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT:AUTO_LENGTH

在發佈時自動確定字串的新長度。

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>備註

在發佈時自動確定字串的新長度。 字串必須為 null 終止。

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT:CStrBufT

構造緩衝區物件。

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>參數

*Str*<br/>
與緩衝區關聯的字串物件。 通常`CStrBuf`,開發人員將使用預定義的類型def(TCHAR變`CStrBufA`體)、(**字元**變`CStrBufW`體)和 **(wchar_t**變體)。

*n 最小長度*<br/>
字元緩衝區的最小長度。

*dwFlags*<br/>
確定是否自動確定字串長度。 可以是下列其中一項：

- AUTO_LENGTH在調用[CSimpleStringT::釋放](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)時自動確定字串長度。 字串必須為 null 終止。 預設值。

- SET_LENGTH字串長度設置時[,CSimpleStringT::getBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)調用。

### <a name="remarks"></a>備註

為關聯的字串物件創建字串緩衝區。 在構造過程中[,CSimpleStringT:獲取緩衝區](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)或[CSimpleStringT::獲取緩衝區集長度](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)調用。

請注意,複製構造函數是**私有**的。

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT::操作員PCXSTR

直接存取為 C 樣式字串儲存在關聯字串物件中的字元。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>傳回值

指向字串資料的字元指標。

### <a name="remarks"></a>備註

呼叫此函數以返回指向字串物件字元緩衝區的指標。 無法使用此指標更改字串物件的內容。

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT::操作員PXSTR

直接存取為 C 樣式字串儲存在關聯字串物件中的字元。

```
operator PXSTR() throw();
```

### <a name="return-value"></a>傳回值

指向字串資料的字元指標。

### <a name="remarks"></a>備註

呼叫此函數以返回指向字串物件字元緩衝區的指標。 開發人員可能會使用此指標更改字串物件的內容。

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT::PCXSTR

指向常量字串的指標。

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT::PXSTR

指向字串的指標。

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT:SET_LENGTH

`GetBuffer`設置字串對象的時間長度。

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>備註

在 GetBuffer 時間設置字串物件的長度。

確定在建構字串緩衝區物件時是否呼叫[CSimpleStringT:getBufferT](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT:getBufferSet 長度](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)。

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT::設定長度

設置字元緩衝區的長度。

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>參數

*N 長度*<br/>
字串物件的字元緩衝區的新長度。

> [!NOTE]
> 必須小於或等於`CStrBufT`中的構造函數中指定的最小緩衝區長度。

### <a name="remarks"></a>備註

呼叫此函數以設置緩衝區物件表示的字串的長度。

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT:弦類型

其緩衝區將由此類範本的專門化操作的字串類型。

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>備註

`TCharType`是用於專門化類範本的字元類型。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
