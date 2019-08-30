---
title: COleSafeArray 類別
ms.date: 08/29/2019
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: a0ce0fc03923806c9e044a7edae3178fd3429b76
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177391"
---
# <a name="colesafearray-class"></a>COleSafeArray 類別

類別，用來處理任意類型和維度的陣列。

## <a name="syntax"></a>語法

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|建構 `COleSafeArray` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|抓取陣列資料的指標。|
|[COleSafeArray::AllocData](#allocdata)|配置陣列的記憶體。|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|配置安全陣列描述元的記憶體。|
|[COleSafeArray::Attach](#attach)|將現有`VARIANT`陣列的控制權提供`COleSafeArray`給物件。|
|[COleSafeArray::Clear](#clear)|釋放基礎`VARIANT`中的所有資料。|
|[COleSafeArray::Copy](#copy)|建立現有陣列的複本。|
|[COleSafeArray::Create](#create)|建立安全陣列。|
|[COleSafeArray::CreateOneDim](#createonedim)|建立一維`COleSafeArray`物件。|
|[COleSafeArray::Destroy](#destroy)|終結現有的陣列。|
|[COleSafeArray::DestroyData](#destroydata)|損毀安全陣列中的資料。|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|終結安全陣列的描述元。|
|[COleSafeArray::Detach](#detach)|從`COleSafeArray`物件卸離 VARIANT 陣列 (如此一來, 就不會釋放資料)。|
|[COleSafeArray::GetByteArray](#getbytearray)|將安全陣列的內容複寫到[CByteArray](../../mfc/reference/cbytearray-class.md)中。|
|[COleSafeArray::GetDim](#getdim)|傳回陣列中的維度數目。|
|[COleSafeArray::GetElement](#getelement)|抓取 safe 陣列的單一元素。|
|[COleSafeArray::GetElemSize](#getelemsize)|傳回安全陣列中某個元素的大小 (以位元組為單位)。|
|[COleSafeArray::GetLBound](#getlbound)|傳回安全陣列之任何維度的下限。|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|傳回一維`COleSafeArray`物件中的元素數目。|
|[COleSafeArray::GetUBound](#getubound)|傳回安全陣列之任何維度的上限。|
|[COleSafeArray::Lock](#lock)|遞增陣列的鎖定計數, 並在陣列描述項中放置陣列資料的指標。|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|傳回索引元素的指標。|
|[COleSafeArray::PutElement](#putelement)|將單一項目指派到陣列。|
|[COleSafeArray::Redim](#redim)|變更安全陣列最不重要 (最右邊) 系結。|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|變更一維`COleSafeArray`物件中的元素數目。|
|[COleSafeArray::UnaccessData](#unaccessdata)|遞減陣列的鎖定計數, 並使所取出`AccessData`的指標失效。|
|[COleSafeArray::Unlock](#unlock)|遞減陣列的鎖定計數, 以便釋放或調整大小。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleSafeArray:: operator LPCVARIANT](#operator_lpcvariant)|存取`COleSafeArray`物件的`VARIANT`基礎結構。|
|[COleSafeArray:: operator LPVARIANT](#operator_lpvariant)|存取`COleSafeArray`物件的`VARIANT`基礎結構。|
|[COleSafeArray::operator =](#operator_eq)|將值複製到`COleSafeArray`物件中`SAFEARRAY`( `VARIANT`、 `COleVariant`、或`COleSafeArray`陣列)。|
|[COleSafeArray:: operator = =](#operator_eq_eq)|比較兩個 variant 陣列`SAFEARRAY`( `VARIANT`、 `COleVariant`、或`COleSafeArray`陣列)。|
|[COleSafeArray:: operator&lt;&lt;](#operator_lt_lt)|將`COleSafeArray`物件的內容輸出到傾印內容。|

## <a name="remarks"></a>備註

`COleSafeArray`衍生自 OLE `VARIANT`結構。 OLE `SAFEARRAY`成員函式可透過`COleSafeArray`取得, 以及一組專為一維位元組陣列而設計的成員函式。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="accessdata"></a>COleSafeArray:: AccessData

抓取陣列資料的指標。

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>參數

*ppvData*<br/>
陣列資料指標的指標。

### <a name="remarks"></a>備註

發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>COleSafeArray:: AllocData

配置安全陣列的記憶體。

```
void AllocData();
```

### <a name="remarks"></a>備註

發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="allocdescriptor"></a>COleSafeArray:: AllocDescriptor

為安全陣列的描述元配置記憶體。

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>參數

*dwDims*<br/>
安全陣列中的維度數目。

### <a name="remarks"></a>備註

發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="attach"></a>COleSafeArray:: Attach

將現有`VARIANT`陣列中的資料控制提供`COleSafeArray`給物件。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
`VARIANT` 物件。 *VarSrc*參數必須具有 VARTYPE [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)。

### <a name="remarks"></a>備註

來源`VARIANT`的類型設定為 VT_EMPTY。 此函式會清除目前的陣列資料 (如果有的話)。

### <a name="example"></a>範例

  請參閱[COleSafeArray:: AccessData](#accessdata)的範例。

##  <a name="clear"></a>COleSafeArray:: Clear

清除安全陣列。

```
void Clear();
```

### <a name="remarks"></a>備註

函式會將物件的設`VARTYPE`為 VT_EMPTY, 藉以清除安全陣列。 會釋出目前的內容, 並釋放陣列。

##  <a name="colesafearray"></a>COleSafeArray:: COleSafeArray

建構 `COleSafeArray` 物件。

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>參數

*saSrc*<br/>
現有`COleSafeArray`的物件, `SAFEARRAY`或要複製到新`COleSafeArray`的物件中。

*vtSrc*<br/>
新`COleSafeArray`物件的 VARTYPE。

*psaSrc*<br/>
要複製到新`SAFEARRAY` `COleSafeArray`物件中之的指標。

*varSrc*<br/>
要複製`VARIANT`到`COleVariant` 新`COleSafeArray`物件中的現有或物件。

*pSrc*<br/>
要複製到新`VARIANT` `COleSafeArray`物件中之物件的指標。

### <a name="remarks"></a>備註

所有這些函式都會建立`COleSafeArray`新的物件。 如果沒有參數, 則會建立空`COleSafeArray`的物件 (VT_EMPTY)。 如果是從另一個陣列 (也就是以`COleSafeArray`隱含方式知道的`COleVariant`是, `VARIANT`或) 來複製, 則會保留來源陣列的 vartype, 而且不需要指定。 `COleSafeArray` 如果是從另一個不知道 vartype (`SAFEARRAY`) 的陣列複製, 則必須在*vtSrc*參數中指定 VARTYPE。 `COleSafeArray`

發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="copy"></a>COleSafeArray:: Copy

建立現有安全陣列的複本。

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>參數

*ppsa*<br/>
要在其中傳回新陣列描述元之位置的指標。

### <a name="remarks"></a>備註

發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="create"></a>COleSafeArray:: Create

配置並初始化陣列的資料。

```
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>參數

*vtSrc*<br/>
陣列的基底類型 (也就是陣列的每個元素的 VARTYPE)。 VARTYPE 僅限於 variant 類型的子集。 不能同時設定 VT_ARRAY 和 VT_BYREF 旗標。 VT_EMPTY 和 VT_Null 不是陣列的有效基底類型。 所有其他類型都是合法的。

*dwDims*<br/>
陣列中的維度數目。 這可以在使用[Redim](#redim)建立陣列之後變更。

*rgElements*<br/>
陣列中每個維度之元素數目陣列的指標。

*rgsabounds*<br/>
要為數組配置的界限向量指標 (每個維度各一個)。

### <a name="remarks"></a>備註

此函式會在必要時清除目前的陣列資料。 發生錯誤時, 函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>COleSafeArray:: CreateOneDim

建立新的一維`COleSafeArray`物件。

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>參數

*vtSrc*<br/>
陣列的基底類型 (也就是陣列的每個元素的 VARTYPE)。

*dwElements*<br/>
陣列中的元素數目。 這可以在使用[ResizeOneDim](#resizeonedim)建立陣列之後變更。

*pvSrcData*<br/>
要複製到陣列中之資料的指標。

*nLBound*<br/>
陣列的下限。

### <a name="remarks"></a>備註

如果指標*pvSrcData*不是 Null, 則函式會配置並初始化陣列的資料, 並複製指定的資料。

發生錯誤時, 函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>COleSafeArray::D estroy

終結現有的陣列描述項和陣列中的所有資料。

```
void Destroy();
```

### <a name="remarks"></a>備註

如果物件儲存在陣列中, 則會釋放每個物件。 發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="destroydata"></a>COleSafeArray::D estroyData

損毀安全陣列中的所有資料。

```
void DestroyData();
```

### <a name="remarks"></a>備註

如果物件儲存在陣列中, 則會釋放每個物件。 發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="destroydescriptor"></a>COleSafeArray::D estroyDescriptor

終結安全陣列的描述元。

```
void DestroyDescriptor();
```

### <a name="remarks"></a>備註

發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="detach"></a>COleSafeArray::D etach

卸離`COleSafeArray`物件的資料。`VARIANT`

```
VARIANT Detach();
```

### <a name="return-value"></a>傳回值

物件中的基礎`VARIANT`值。 `COleSafeArray`

### <a name="remarks"></a>備註

函式會藉由將物件的 VARTYPE 設定為 VT_EMPTY, 來卸離安全陣列中的資料。 呼叫 Windows 函式[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)會負責釋放陣列。

發生錯誤時, 函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  請參閱[COleSafeArray::P utelement](#putelement)的範例。

##  <a name="getbytearray"></a>COleSafeArray:: GetByteArray

將安全陣列的內容複寫到中`CByteArray`。

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>參數

*#a0*<br/>
[CByteArray](../../mfc/reference/cbytearray-class.md)物件的參考。

##  <a name="getdim"></a>COleSafeArray:: GetDim

傳回`COleSafeArray`物件中的維度數目。

```
DWORD GetDim();
```

### <a name="return-value"></a>傳回值

安全陣列中的維度數目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>COleSafeArray:: GetElement

抓取 safe 陣列的單一元素。

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>參數

*rgIndices*<br/>
陣列的每個維度索引陣列的指標。

*pvData*<br/>
要放置陣列元素之位置的指標。

### <a name="remarks"></a>備註

此函式會自動呼叫 windows `SafeArrayLock`函`SafeArrayUnlock`式, 以及在抓取元素之前和之後。 如果資料元素是字串、物件或 variant, 函式會以正確的方式複製元素。 參數*pvData*應該指向夠大的緩衝區以包含元素。

發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>COleSafeArray:: GetElemSize

抓取`COleSafeArray`物件中元素的大小。

```
DWORD GetElemSize();
```

### <a name="return-value"></a>傳回值

安全陣列的元素大小 (以位元組為單位)。

##  <a name="getlbound"></a>COleSafeArray:: GetLBound

傳回`COleSafeArray`物件之任何維度的下限。

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>參數

*dwDim*<br/>
要取得下限的陣列維度。

*pLBound*<br/>
要傳回下限之位置的指標。

### <a name="remarks"></a>備註

發生錯誤時, 函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>COleSafeArray:: GetOneDimSize

傳回一維`COleSafeArray`物件中的元素數目。

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>傳回值

一維安全陣列中的元素數目。

### <a name="example"></a>範例

  請參閱[COleSafeArray:: CreateOneDim](#createonedim)的範例。

##  <a name="getubound"></a>COleSafeArray:: GetUBound

傳回安全陣列之任何維度的上限。

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>參數

*dwDim*<br/>
要取得上限的陣列維度。

*pUBound*<br/>
要傳回上限之位置的指標。

### <a name="remarks"></a>備註

發生錯誤時, 函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>COleSafeArray:: Lock

遞增陣列的鎖定計數, 並將指標放在陣列描述元中的陣列資料。

```
void Lock();
```

### <a name="remarks"></a>備註

發生錯誤時, 它會擲回[COleException](../../mfc/reference/coleexception-class.md)。

在呼叫之前`Unlock` , 陣列描述元中的指標是有效的。 呼叫可以進行嵌套; 需要的`Unlock`呼叫次數相等。 `Lock`

陣列在鎖定時無法刪除。

##  <a name="operator_lpcvariant"></a>COleSafeArray:: operator LPCVARIANT

呼叫這個轉型運算子來存取這個`VARIANT` `COleSafeArray`物件的基礎結構。

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>COleSafeArray:: operator LPVARIANT

呼叫這個轉型運算子來存取這個`VARIANT` `COleSafeArray`物件的基礎結構。

```
operator LPVARIANT();
```

### <a name="remarks"></a>備註

請注意, 變更此函式`VARIANT`所傳回之指標所存取的結構中的值, 將會變更`COleSafeArray`這個物件的值。

##  <a name="operator_eq"></a>COleSafeArray:: operator =

這些多載指派運算子會將來源值複製`COleSafeArray`到這個物件。

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>備註

每個運算子的簡短說明如下:

- **operator = (** *saSrc* **)** 將現有`COleSafeArray`的物件複製到這個物件。

- **operator = (** *varSrc* **)** 將現有`VARIANT`的或`COleVariant`陣列複製到這個物件。

- **operator = (** *.psrc* **)** 將 .psrc `VARIANT`存取的陣列物件複製到這個物件。

##  <a name="operator_eq_eq"></a>COleSafeArray:: operator = =

這個運算子會比較兩個`SAFEARRAY`陣列`VARIANT`( `COleVariant`、、 `COleSafeArray`或陣列), 如果相等, 則會傳回非零, 否則會傳回0。

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>備註

如果兩個數組的維度數目相等、每個維度中的大小相等, 以及相等的元素值, 則兩者相等。

##  <a name="operator_lt_lt"></a>COleSafeArray:: operator&lt;&lt;

插入 (< <) 運算子支援將`COleSafeArray`物件的診斷傾印和儲存至封存。 `COleSafeArray`

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>COleSafeArray::P trOfIndex

傳回索引值所指定之元素的指標。

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>參數

*rgIndices*<br/>
識別陣列元素的索引值陣列。 必須指定元素的所有索引。

*ppvData*<br/>
傳回時, 是由*rgIndices*中的值所識別之元素的指標。

##  <a name="putelement"></a>COleSafeArray::P utElement

將單一項目指派到陣列。

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>參數

*rgIndices*<br/>
陣列的每個維度索引陣列的指標。

*pvData*<br/>
要指派給陣列的資料指標。 VT_DISPATCH、VT_UNKNOWN 和 VT_BSTR variant 型別都是指標, 而且不需要另一層間接取值。

### <a name="remarks"></a>備註

此函式會在指派專案之前和之後, 自動呼叫 Windows 函式[SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock)和[SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) 。 如果資料項目是字串、物件或變數，函數會正確將它複製，而且如果現有的項目是字串、物件或變數，則會正確清除。

請注意，您可以在陣列中擁有多個鎖定，因此您可以在陣列由其他作業鎖定時將項目放入陣列。

發生錯誤時, 函數會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>COleSafeArray:: Redim

變更安全陣列最不重要 (最右邊) 系結。

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>參數

*psaboundNew*<br/>
新安全陣列系結結構的指標, 其中包含新的陣列系結。 只有最重要的陣列維度可以變更。

### <a name="remarks"></a>備註

發生錯誤時, 函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="resizeonedim"></a>COleSafeArray:: ResizeOneDim

變更一維`COleSafeArray`物件中的元素數目。

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>參數

*dwElements*<br/>
一維安全陣列中的元素數目。

### <a name="remarks"></a>備註

發生錯誤時, 函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  請參閱[COleSafeArray:: CreateOneDim](#createonedim)的範例。

##  <a name="unaccessdata"></a>COleSafeArray:: UnaccessData

遞減陣列的鎖定計數, 並使所取出`AccessData`的指標失效。

```
void UnaccessData();
```

### <a name="remarks"></a>備註

發生錯誤時, 函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  請參閱[COleSafeArray:: AccessData](#accessdata)的範例。

##  <a name="unlock"></a>COleSafeArray:: Unlock

遞減陣列的鎖定計數, 以便釋放或調整大小。

```
void Unlock();
```

### <a name="remarks"></a>備註

在陣列中的資料存取完成後, 會呼叫此函數。 發生錯誤時, 它會擲回[COleException](../../mfc/reference/coleexception-class.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 類別](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
