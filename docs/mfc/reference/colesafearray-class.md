---
title: COleSafeArray 類別 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e001e3a5d58e962a318d6282efa47d0188edbe3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060139"
---
# <a name="colesafearray-class"></a>COleSafeArray 類別

類別，用來處理任意類型和維度的陣列。

## <a name="syntax"></a>語法

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|建構 `COleSafeArray` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|擷取陣列資料的指標。|
|[COleSafeArray::AllocData](#allocdata)|陣列配置記憶體。|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|安全陣列描述元，會配置記憶體。|
|[COleSafeArray::Attach](#attach)|提供現有的控制項`VARIANT`陣列`COleSafeArray`物件。|
|[COleSafeArray::Clear](#clear)|釋出所有資料在基礎`VARIANT`。|
|[COleSafeArray::Copy](#copy)|建立現有陣列的複本。|
|[COleSafeArray::Create](#create)|建立安全的陣列。|
|[COleSafeArray::CreateOneDim](#createonedim)|建立一維`COleSafeArray`物件。|
|[COleSafeArray::Destroy](#destroy)|終結現有的陣列。|
|[COleSafeArray::DestroyData](#destroydata)|終結安全陣列中的資料。|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|終結安全陣列描述的元。|
|[COleSafeArray::Detach](#detach)|中斷連結的變數陣列`COleSafeArray`物件 （如此將不會釋放資料）。|
|[COleSafeArray::GetByteArray](#getbytearray)|複製到的安全陣列的內容[CByteArray](../../mfc/reference/cbytearray-class.md)。|
|[COleSafeArray::GetDim](#getdim)|傳回陣列中的維度數目。|
|[Colesafearray:: Getelement](#getelement)|擷取安全陣列的單一項目。|
|[COleSafeArray::GetElemSize](#getelemsize)|傳回大小，以位元組為單位的安全陣列中的一個項目。|
|[COleSafeArray::GetLBound](#getlbound)|會傳回任何維度的安全陣列的下限。|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|傳回一維的元素數目`COleSafeArray`物件。|
|[COleSafeArray::GetUBound](#getubound)|傳回安全陣列中任何維度的上限。|
|[COleSafeArray::Lock](#lock)|陣列的鎖定計數遞增，並將陣列資料的指標放在陣列描述元。|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|索引項目中傳回的指標。|
|[COleSafeArray::PutElement](#putelement)|將單一項目指派到陣列。|
|[COleSafeArray::Redim](#redim)|變更最小顯著性 （最右邊） 的繫結，安全陣列。|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|變更中的一維的項目數`COleSafeArray`物件。|
|[COleSafeArray::UnaccessData](#unaccessdata)|減量鎖定計數陣列和失效所擷取的指標`AccessData`。|
|[COleSafeArray::Unlock](#unlock)|減量鎖定計數的陣列，因此可以釋出或調整大小。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|存取基礎`VARIANT`結構`COleSafeArray`物件。|
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|存取基礎`VARIANT`結構`COleSafeArray`物件。|
|[COleSafeArray::operator =](#operator_eq)|將值插入`COleSafeArray`物件 (`SAFEARRAY`， `VARIANT`， `COleVariant`，或`COleSafeArray`陣列)。|
|[COleSafeArray::operator = =](#operator_eq_eq)|比較兩個 variant 的陣列 (`SAFEARRAY`， `VARIANT`， `COleVariant`，或`COleSafeArray`陣列)。|
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|輸出的內容`COleSafeArray`傾印內容的物件。|

## <a name="remarks"></a>備註

`COleSafeArray` 衍生自 OLE`VARIANT`結構。 OLE`SAFEARRAY`成員函式都是透過`COleSafeArray`，以及做為一組專為位元組的一維陣列的成員函式。

## <a name="inheritance-hierarchy"></a>繼承階層

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="accessdata"></a>  COleSafeArray::AccessData

擷取陣列資料的指標。

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>參數

*ppvData*<br/>
指向陣列資料的指標。

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>  COleSafeArray::AllocData

安全陣列配置記憶體。

```
void AllocData();
```

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor

安全陣列描述元，會配置記憶體。

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>參數

*dwDims*<br/>
安全陣列中的維度數目。

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="attach"></a>  COleSafeArray::Attach

中的現有資料的控制權`VARIANT`陣列`COleSafeArray`物件。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
`VARIANT` 物件。 *VarSrc*參數必須要有 VARTYPE [VT_ARRAY](/windows/desktop/api/wtypes/ne-wtypes-varenum)。

### <a name="remarks"></a>備註

來源`VARIANT`的類型設為 VT_EMPTY。 此函式會清除目前的陣列資料，如果有的話。

### <a name="example"></a>範例

  範例，請參閱[COleSafeArray::AccessData](#accessdata)。

##  <a name="clear"></a>  COleSafeArray::Clear

清除 安全陣列。

```
void Clear();
```

### <a name="remarks"></a>備註

藉由設定函式會清除的安全陣列`VARTYPE`設為 VT_EMPTY 的物件。 目前的內容會釋出，並釋放陣列。

##  <a name="colesafearray"></a>  COleSafeArray::COleSafeArray

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
將現有`COleSafeArray`物件或`SAFEARRAY`複製到新`COleSafeArray`物件。

*vtSrc*<br/>
新的 VARTYPE`COleSafeArray`物件。

*psaSrc*<br/>
指標`SAFEARRAY`複製到新`COleSafeArray`物件。

*varSrc*<br/>
將現有`VARIANT`或是`COleVariant`複製到新的物件`COleSafeArray`物件。

*pSrc*<br/>
指標`VARIANT`複製到新的物件`COleSafeArray`物件。

### <a name="remarks"></a>備註

這些建構函式的所有新建`COleSafeArray`物件。 如果沒有參數，空`COleSafeArray`建立物件 (為 VT_EMPTY)。 如果`COleSafeArray`會從其 VARTYPE 稱為隱含的另一個陣列複製 ( `COleSafeArray`， `COleVariant`，或`VARIANT`)，來源陣列的 VARTYPE 會保留，不須指定。 如果`COleSafeArray`會從其 VARTYPE 未知的另一個陣列複製 (`SAFEARRAY`)，必須在指定的 VARTYPE *vtSrc*參數。

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="copy"></a>  COleSafeArray::Copy

建立現有安全陣列的複本。

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>參數

*ppsa*<br/>
這是要傳回新的陣列描述元中的位置指標。

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="create"></a>  COleSafeArray::Create

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
陣列 (也就是陣列的每個項目 VARTYPE) 的基底型別。 VARTYPE 僅限於 variant 的類型子集。 VT_ARRAY 或 VT_BYREF 旗標都不可以設定。 VT_EMPTY 和 VT_NULL 並非有效的陣列的基底型別。 所有其他類型是合法的。

*dwDims*<br/>
陣列中的維度數目。 使用建立陣列之後可以變更這[Redim](#redim)。

*rgElements*<br/>
每個維度中陣列的項目數的陣列指標。

*rgsabounds*<br/>
向量界限 （一個用於每個維度） 的指標陣列配置。

### <a name="remarks"></a>備註

如有必要，這個函式將會清除目前的陣列資料。 發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim

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
陣列 (也就是陣列的每個項目 VARTYPE) 的基底型別。

*dwElements*<br/>
陣列中的項目數目。 使用建立陣列之後可以變更這[ResizeOneDim](#resizeonedim)。

*pvSrcData*<br/>
要複製到陣列的資料指標。

*nLBound*<br/>
陣列的下限。

### <a name="remarks"></a>備註

函式會配置並初始化陣列，複製指定的資料時，如果資料指標*pvSrcData*不是 NULL。

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>  COleSafeArray::Destroy

終結現有的陣列描述元和陣列中的所有資料。

```
void Destroy();
```

### <a name="remarks"></a>備註

如果物件會儲存在陣列中，會釋出每個物件。 發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="destroydata"></a>  COleSafeArray::DestroyData

終結安全陣列中的所有資料。

```
void DestroyData();
```

### <a name="remarks"></a>備註

如果物件會儲存在陣列中，會釋出每個物件。 發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor

終結安全陣列描述的元。

```
void DestroyDescriptor();
```

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="detach"></a>  COleSafeArray::Detach

卸離`VARIANT`來自`COleSafeArray`物件。

```
VARIANT Detach();
```

### <a name="return-value"></a>傳回值

基礎`VARIANT`中的值`COleSafeArray`物件。

### <a name="remarks"></a>備註

函式會藉由設定物件的 VARTYPE 設為 VT_EMPTY，中斷連結的安全陣列中的資料。 它是以釋放陣列呼叫 Windows 函式的呼叫者的責任[VariantClear](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantclear)。

發生錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  範例，請參閱[COleSafeArray::PutElement](#putelement)。

##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray

安全陣列的內容複製`CByteArray`。

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>參數

*位元組*<br/>
參考[CByteArray](../../mfc/reference/cbytearray-class.md)物件。

##  <a name="getdim"></a>  COleSafeArray::GetDim

傳回中的維度數目`COleSafeArray`物件。

```
DWORD GetDim();
```

### <a name="return-value"></a>傳回值

安全陣列中的維度數目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>  Colesafearray:: Getelement

擷取安全陣列的單一項目。

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>參數

*rgIndices*<br/>
陣列的每個維度索引陣列的指標。

*pvData*<br/>
將陣列的項目之位置的指標。

### <a name="remarks"></a>備註

此函式會自動呼叫 windows 函式`SafeArrayLock`和`SafeArrayUnlock`之前和之後擷取的項目。 如果資料項目是字串、 物件或變數，函式會正確地複製項目。 參數*pvData*應該指向大型足夠的緩衝區包含的項目。

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize

擷取中的項目大小`COleSafeArray`物件。

```
DWORD GetElemSize();
```

### <a name="return-value"></a>傳回值

大小 （位元組），安全陣列的項目。

##  <a name="getlbound"></a>  COleSafeArray::GetLBound

會傳回任何維度的下限`COleSafeArray`物件。

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>參數

*dwDim*<br/>
用來取得下限的陣列維度。

*pLBound*<br/>
要傳回下限的位置指標。

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize

傳回一維的元素數目`COleSafeArray`物件。

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>傳回值

一維的安全陣列中的項目數目。

### <a name="example"></a>範例

  範例，請參閱[COleSafeArray::CreateOneDim](#createonedim)。

##  <a name="getubound"></a>  COleSafeArray::GetUBound

傳回安全陣列中任何維度的上限。

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>參數

*dwDim*<br/>
陣列維度，用來取得上限。

*pUBound*<br/>
要傳回上限的位置指標。

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>  COleSafeArray::Lock

陣列和位置的指標陣列描述元中的陣列資料的鎖定計數會遞增。

```
void Lock();
```

### <a name="remarks"></a>備註

發生錯誤時，就會擲回[COleException](../../mfc/reference/coleexception-class.md)。

將指標陣列描述元中的是有效期限`Unlock`呼叫。 若要呼叫`Lock`可以巢狀; 呼叫數目相等`Unlock`所需。

鎖定時，無法刪除陣列。

##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT

呼叫此轉型運算子，來存取基礎`VARIANT`這個結構`COleSafeArray`物件。

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT

呼叫此轉型運算子，來存取基礎`VARIANT`這個結構`COleSafeArray`物件。

```
operator LPVARIANT();
```

### <a name="remarks"></a>備註

請注意，變更中的值`VARIANT`存取此函式所傳回的指標，結構會變更這個值`COleSafeArray`物件。

##  <a name="operator_eq"></a>  COleSafeArray::operator =

這些多載的指派運算子會將來源值複製到這個`COleSafeArray`物件。

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
  COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>備註

每個運算子的簡短描述如下：

- **運算子 = (** *saSrc* **)** 複製現有`COleSafeArray`成為這個物件的物件。

- **運算子 = (** *varSrc* **)** 複製現有`VARIANT`或`COleVariant`到這個物件的陣列。

- **運算子 = (** *pSrc* **)** 複本`VARIANT`陣列物件存取*pSrc*到這個物件。

##  <a name="operator_eq_eq"></a>  COleSafeArray::operator = =

此運算子比較兩個陣列 (`SAFEARRAY`， `VARIANT`， `COleVariant`，或`COleSafeArray`陣列)，並傳回非零值，如果不相等，否則為 0。

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>備註

這兩個陣列相等如果它們有相同數目的維度，在每個維度和相等的項目值的大小相同。

##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;

`COleSafeArray`插入 (<<) 運算子支援診斷傾印和儲存`COleSafeArray`封存的物件。

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex

讓指標回到指定的索引值的項目。

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>參數

*rgIndices*<br/>
識別陣列中的元素的索引值的陣列。 必須指定所有索引的項目。

*ppvData*<br/>
中的值所識別的項目傳回，指標*rgIndices*。

##  <a name="putelement"></a>  COleSafeArray::PutElement

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
要指派給陣列的資料指標。 VT_DISPATCH、 VT_UNKNOWN 和 VT_BSTR variant 類型都是指標，而且不需要另一個間接取值層級。

### <a name="remarks"></a>備註

此函式會自動呼叫 Windows 函式[SafeArrayLock](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraylock)並[SafeArrayUnlock](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearrayunlock)之前和之後指派項目。 如果資料項目是字串、物件或變數，函數會正確將它複製，而且如果現有的項目是字串、物件或變數，則會正確清除。

請注意，您可以在陣列中擁有多個鎖定，因此您可以在陣列由其他作業鎖定時將項目放入陣列。

發生錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>  COleSafeArray::Redim

變更最小顯著性 （最右邊） 的繫結，安全陣列。

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>參數

*psaboundNew*<br/>
指標，指向新的安全陣列繫結結構，其中包含新繫結的陣列。 陣列的最小顯著性維度可能會變更。

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim

變更中的一維的項目數`COleSafeArray`物件。

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>參數

*dwElements*<br/>
一維的安全陣列中的項目數目。

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  範例，請參閱[COleSafeArray::CreateOneDim](#createonedim)。

##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData

減量鎖定計數陣列和失效所擷取的指標`AccessData`。

```
void UnaccessData();
```

### <a name="remarks"></a>備註

發生錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  範例，請參閱[COleSafeArray::AccessData](#accessdata)。

##  <a name="unlock"></a>  COleSafeArray::Unlock

減量鎖定計數的陣列，因此可以釋出或調整大小。

```
void Unlock();
```

### <a name="remarks"></a>備註

存取陣列中的資料完成之後，會呼叫此函數。 發生錯誤時，就會擲回[COleException](../../mfc/reference/coleexception-class.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 類別](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
