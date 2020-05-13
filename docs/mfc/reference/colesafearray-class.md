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
ms.openlocfilehash: 10e9975bac776429a38bfc707215a9465ce35c2e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753766"
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
|[COleSafearray:COleSafearray](#colesafearray)|建構 `COleSafeArray` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleSafearray:存取資料](#accessdata)|檢索指向數組數據的指標。|
|[COleSafearray:allocData](#allocdata)|為陣列分配記憶體。|
|[COleSafearray::均等描述符](#allocdescriptor)|為安全陣組描述符分配記憶體。|
|[COleSafearray:附加](#attach)|將現有`VARIANT`數位的控制權授予`COleSafeArray`物件。|
|[COleSafearray:清除](#clear)|釋放基礎`VARIANT`中的所有數據。|
|[COleSafearray:複製](#copy)|創建現有陣列的副本。|
|[COleSafearray:建立](#create)|創建安全陣列。|
|[COleSafearray:建立 Dim](#createonedim)|創建一維`COleSafeArray`物件。|
|[COleSafeArray::D](#destroy)|銷毀現有陣組。|
|[COleSafeArray::D](#destroydata)|銷毀安全數組中的數據。|
|[COleSafeArray::D描述符](#destroydescriptor)|銷毀安全陣列的描述符。|
|[COleSafearray::D埃塔奇](#detach)|從`COleSafeArray`物件分離 VARIANT 陣列(以便不會釋放數據)。|
|[COleSafearray:取得位元組](#getbytearray)|將安全陣組的內容複製到[CByteArray](../../mfc/reference/cbytearray-class.md)中。|
|[COleSafearray:GetDim](#getdim)|傳回陣列中的維度數目。|
|[COleSafearray:取得元素](#getelement)|檢索安全數組的單個元素。|
|[COleSafearray:取得Elemsize](#getelemsize)|返回安全陣列中一個元素的大小(以位元組為單位)。|
|[COleSafearray:GetLBound](#getlbound)|返回安全陣列的任何維度的下限。|
|[COleSafearray:取得 Dimmsize](#getonedimsize)|返回一維`COleSafeArray`物件中的元素數。|
|[COleSafearray:GetUBund](#getubound)|返回安全數組的任何維度的上限。|
|[COleSafearray:鎖](#lock)|增加陣列的鎖計數,並在數位描述符中放置指向數位數據的指標。|
|[COleSafearray::PtrofIndex](#ptrofindex)|返回指向索引元素的指標。|
|[COleSafearray::Put元素](#putelement)|將單一項目指派到陣列。|
|[COleSafearray:雷西姆](#redim)|更改安全陣列的最小顯著(最右)綁定。|
|[COleSafearray:調整 Dim 的大小](#resizeonedim)|更改一維`COleSafeArray`物件中的元素數。|
|[COleSafearray:取消存取資料](#unaccessdata)|刪除陣列的鎖計數,使檢索到`AccessData`的指標無效。|
|[COleSafearray:解鎖](#unlock)|對陣列的鎖計數進行縮減,以便可以釋放或調整大小。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleSafearray::操作員LPCVARIANT](#operator_lpcvariant)|訪問`VARIANT``COleSafeArray`對象的基礎結構。|
|[COleSafearray::操作員LPVARIANT](#operator_lpvariant)|訪問`VARIANT``COleSafeArray`對象的基礎結構。|
|[COleSafeArray::操作員 |](#operator_eq)|`COleSafeArray`將值複製到物件 (、、`COleVariant``COleSafeArray``SAFEARRAY``VARIANT`或陣列)。|
|[COleSafeArray::操作員 |](#operator_eq_eq)|比較兩`SAFEARRAY`個變數組(、、、`VARIANT``COleVariant`或`COleSafeArray`陣列)。|
|[COleSafeArray::操作員&lt;&lt;](#operator_lt_lt)|將`COleSafeArray`物件的內容輸出到轉儲上下文。|

## <a name="remarks"></a>備註

`COleSafeArray`派生自 OLE`VARIANT`結構。 OLE`SAFEARRAY`成員函數可透過`COleSafeArray`以及專為位元組的一維陣組設計的一組成員函數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafearray:存取資料

檢索指向數組數據的指標。

```cpp
void AccessData(void** ppvData);
```

### <a name="parameters"></a>參數

*ppvData*<br/>
指向陣列數據的指標。

### <a name="remarks"></a>備註

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a>COleSafearray:allocData

為安全數組分配記憶體。

```cpp
void AllocData();
```

### <a name="remarks"></a>備註

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafearray::均等描述符

為安全陣列的描述符分配記憶體。

```cpp
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>參數

*德迪姆斯*<br/>
安全陣列中的維度數。

### <a name="remarks"></a>備註

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearrayattach"></a><a name="attach"></a>COleSafearray:附加

將現有`VARIANT`數位中的數據控制權授予`COleSafeArray`物件。

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>參數

*varSrc*<br/>
`VARIANT` 物件。 *varSrc*參數必須具有 VARTYPE [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)。

### <a name="remarks"></a>備註

源`VARIANT`的類型設置為VT_EMPTY。 此函數清除當前陣列數據(如果有)。

### <a name="example"></a>範例

  請參考[COleSafeArray 的範例:存取資料](#accessdata)。

## <a name="colesafearrayclear"></a><a name="clear"></a>COleSafearray:清除

清除安全陣列。

```cpp
void Clear();
```

### <a name="remarks"></a>備註

該函數通過將物件`VARTYPE`設置為VT_EMPTY來清除安全陣列。 釋放當前內容並釋放陣列。

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafearray:COleSafearray

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

*薩斯爾克*<br/>
現有`COleSafeArray`物件`SAFEARRAY`或要複製到`COleSafeArray`新 物件。

*弗茨爾克*<br/>
新`COleSafeArray`物件的 VARTYPE。

*普薩斯克*<br/>
`SAFEARRAY`要複製到新`COleSafeArray`物件的指標。

*varSrc*<br/>
要複製到`VARIANT`新`COleVariant``COleSafeArray`物件的現有或物件。

*pSrc*<br/>
指向要複製到新`VARIANT``COleSafeArray`物件的物件的指標。

### <a name="remarks"></a>備註

所有這些構造函數都創建新`COleSafeArray`的物件。 如果沒有參數,則創建空`COleSafeArray`物件(VT_EMPTY)。 如果從其中一個陣列複製的 VARTYPE 隱式`COleSafeArray``COleVariant`已知`VARIANT`(a , 或 ), 則保留源陣列`COleSafeArray`的 VARTYPE,無需指定。 `COleSafeArray`如果從不知道 VARTYPE 的另一個陣列`SAFEARRAY`(), 必須在*vtSrc*參數中指定 VARTYPE。

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraycopy"></a><a name="copy"></a>COleSafearray:複製

創建現有安全陣列的副本。

```cpp
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>參數

*普薩*<br/>
指向要返回新陣列描述符的位置的指標。

### <a name="remarks"></a>備註

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraycreate"></a><a name="create"></a>COleSafearray:建立

分配和初始化陣列的數據。

```cpp
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

*弗茨爾克*<br/>
陣列的基礎類型(即陣列每個元素的 VARTYPE)。 VARTYPE 僅限於變體類型的子集。 無法設置VT_ARRAY和VT_BYREF標誌。 VT_EMPTY和VT_NULL不是陣列的有效基類型。 所有其他類型都是合法的。

*德迪姆斯*<br/>
陣列中的維度數。 在使用[Redim](#redim)建立陣列後,可以更改此更改。

*rg元素*<br/>
指向陣列中每個維度的元素數的陣列。

*格薩邦*<br/>
指向邊界向量(每個維度一個)的指標,用於為陣列分配。

### <a name="remarks"></a>備註

如有必要,此函數將清除當前陣列數據。 錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafearray:建立 Dim

創建新的一維`COleSafeArray`物件。

```cpp
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>參數

*弗茨爾克*<br/>
陣列的基礎類型(即陣列每個元素的 VARTYPE)。

*dwElements*<br/>
陣列中的元素數。 在使用[ResizeOneDim](#resizeonedim)建立陣列後,可以更改此更改。

*pvSrcData*<br/>
指向要複製到陣列的數據的指標。

*nLBound*<br/>
陣列的下限。

### <a name="remarks"></a>備註

函數分配和初始化陣列的數據,如果指標*pvSrcData*不是 NULL,則複製指定的數據。

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray::D

銷毀現有陣列描述符和陣列中的所有數據。

```cpp
void Destroy();
```

### <a name="remarks"></a>備註

如果物件存儲在陣列中,則釋放每個物件。 錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray::D

銷毀安全陣列中的所有數據。

```cpp
void DestroyData();
```

### <a name="remarks"></a>備註

如果物件存儲在陣列中,則釋放每個物件。 錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray::D描述符

銷毀安全陣列的描述符。

```cpp
void DestroyDescriptor();
```

### <a name="remarks"></a>備註

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearraydetach"></a><a name="detach"></a>COleSafearray::D埃塔奇

從`COleSafeArray`物件`VARIANT`分離 數據。

```
VARIANT Detach();
```

### <a name="return-value"></a>傳回值

物件中`VARIANT``COleSafeArray`的基礎值。

### <a name="remarks"></a>備註

該函數通過將物件的 VARTYPE 設置為VT_EMPTY來分離安全陣列中的數據。 調用方有責任通過調用 Windows 函數[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)來釋放陣列。

錯誤時,函數會拋出一個[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  請參閱[COleSafeArray::PutElement](#putelement)) 的範例。

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafearray:取得位元組

將安全陣列的內容複製到中`CByteArray`。

```cpp
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>參數

*位元組*<br/>
對[CByteArray](../../mfc/reference/cbytearray-class.md)物件的引用。

## <a name="colesafearraygetdim"></a><a name="getdim"></a>COleSafearray:GetDim

返回物件中的`COleSafeArray`維度數。

```
DWORD GetDim();
```

### <a name="return-value"></a>傳回值

安全陣列中的維度數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a>COleSafearray:取得元素

檢索安全數組的單個元素。

```cpp
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>參數

*rg索引*<br/>
陣列的每個維度索引陣列的指標。

*pvData*<br/>
指向位置以放置陣列的元素。

### <a name="remarks"></a>備註

此函數自動調用視窗函數`SafeArrayLock``SafeArrayUnlock`以及 檢索元素之前和之後。 如果數據元素是字串、對象或變體,則函數以正確的方式複製該元素。 參數*pvData*應指向足夠大的緩衝區以包含該元素。

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafearray:取得Elemsize

檢索`COleSafeArray`物件中元素的大小。

```
DWORD GetElemSize();
```

### <a name="return-value"></a>傳回值

安全陣組元素的大小(以位元組為單位)。

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a>COleSafearray:GetLBound

返回`COleSafeArray`物件任何維度的下限。

```cpp
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>參數

*dwDim*<br/>
要為其獲取下限的陣列維度。

*pL 結合*<br/>
指向位置以返回下限。

### <a name="remarks"></a>備註

錯誤時,函數會拋出一個[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafearray:取得 Dimmsize

返回一維`COleSafeArray`物件中的元素數。

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>傳回值

一維安全陣列中的元素數。

### <a name="example"></a>範例

  請參閱[COleSafearray 的範例::建立OneDim](#createonedim)。

## <a name="colesafearraygetubound"></a><a name="getubound"></a>COleSafearray:GetUBund

返回安全數組的任何維度的上限。

```cpp
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>參數

*dwDim*<br/>
要為其獲取上限的陣列維度。

*pUBound*<br/>
指向位置以返回上邊界。

### <a name="remarks"></a>備註

錯誤時,函數會拋出一個[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a>COleSafearray:鎖

增加陣列的鎖計數,並在數位描述符中放置指向數位數據的指標。

```cpp
void Lock();
```

### <a name="remarks"></a>備註

錯誤時,它拋出一個[COleException](../../mfc/reference/coleexception-class.md)。

陣列描述符中的指標在調用之前`Unlock`有效。 可以嵌套`Lock`對的調用;需要同等數量的呼叫`Unlock`。

陣列鎖定時無法刪除。

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafearray::操作員LPCVARIANT

呼叫此強制轉換運算符以造訪此`VARIANT``COleSafeArray`物件的基礎結構。

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafearray::操作員LPVARIANT

呼叫此強制轉換運算符以造訪此`VARIANT``COleSafeArray`物件的基礎結構。

```
operator LPVARIANT();
```

### <a name="remarks"></a>備註

請注意,更改此函數返回的`VARIANT`指標存取的結構中的值將更改此`COleSafeArray`物件的值。

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray::操作員 |

這些重載賦值運算符將源值複製到此`COleSafeArray`物件中。

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>備註

每個運算子的簡要描述如下:

- **運算子 =(** *saSrc* **)** 將現有`COleSafeArray`物件複製到此物件中。

- 運算子 **(varSrc* **operator =(** **)** 將現有`VARIANT`或`COleVariant`數位複製到此物件中。

- 運算子 *=(pSrc* **operator =(** **)** 將`VARIANT` *pSrc*存取的陣列物件複製到此物件中。

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray::操作員 |

此`SAFEARRAY`運算元 比較兩個陣列(、、、`VARIANT``COleVariant``COleSafeArray`或陣列),如果陣列相等,則返回非零陣列;否則 0。

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>備註

如果兩個陣列的維度數相等、每個維度的大小相等且元素值相等,則兩個陣列相等。

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a>COleSafeArray::操作員&lt;&lt;

插入`COleSafeArray`(<<)運算子支援診斷轉印並將`COleSafeArray`物件儲存到存檔。

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a>COleSafearray::PtrofIndex

返回指向索引值指定的元素的指標。

```cpp
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>參數

*rg索引*<br/>
標識數組元素的索引值陣列。 必須指定元素的所有索引。

*ppvData*<br/>
返回時,指標指向*rgIndices*中的值標識的元素。

## <a name="colesafearrayputelement"></a><a name="putelement"></a>COleSafearray::Put元素

將單一項目指派到陣列。

```cpp
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>參數

*rg索引*<br/>
陣列的每個維度索引陣列的指標。

*pvData*<br/>
要指派給陣列的資料指標。 VT_DISPATCH、VT_UNKNOWN和VT_BSTR變體類型是指針,不需要另一級別的間接。

### <a name="remarks"></a>備註

此函數在分配元素之前和之後自動調用 Windows 函數[SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock)和安全[ArrayUnlock。](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) 如果資料項目是字串、物件或變數，函數會正確將它複製，而且如果現有的項目是字串、物件或變數，則會正確清除。

請注意，您可以在陣列中擁有多個鎖定，因此您可以在陣列由其他作業鎖定時將項目放入陣列。

錯誤時,函數會拋出[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleexception](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a>COleSafearray:雷西姆

更改安全陣列的最小顯著(最右)綁定。

```cpp
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>參數

*psabund New*<br/>
指向包含新陣列綁定的新安全陣列綁定結構的指標。 只能更改陣列的最小尺寸。

### <a name="remarks"></a>備註

錯誤時,函數會拋出一個[COleException](../../mfc/reference/coleexception-class.md)。

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a>COleSafearray:調整 Dim 的大小

更改一維`COleSafeArray`物件中的元素數。

```cpp
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>參數

*dwElements*<br/>
一維安全陣列中的元素數。

### <a name="remarks"></a>備註

錯誤時,函數會拋出一個[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  請參閱[COleSafearray 的範例::建立OneDim](#createonedim)。

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a>COleSafearray:取消存取資料

刪除陣列的鎖計數,使檢索到`AccessData`的指標無效。

```cpp
void UnaccessData();
```

### <a name="remarks"></a>備註

錯誤時,函數會拋出一個[COleException](../../mfc/reference/coleexception-class.md)。

### <a name="example"></a>範例

  請參考[COleSafeArray 的範例:存取資料](#accessdata)。

## <a name="colesafearrayunlock"></a><a name="unlock"></a>COleSafearray:解鎖

對陣列的鎖計數進行縮減,以便可以釋放或調整大小。

```cpp
void Unlock();
```

### <a name="remarks"></a>備註

完成對陣列中數據的訪問後,將調用此函數。 錯誤時,它拋出一個[COleException](../../mfc/reference/coleexception-class.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleVariant 類別](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
