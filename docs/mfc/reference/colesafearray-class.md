---
title: "COleSafeArray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 39c7a471b5c397c430f419514b9ebf1d4da62f62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|安全陣列描述元配置記憶體。|  
|[COleSafeArray::Attach](#attach)|提供的現有控制項，讓**VARIANT**陣列`COleSafeArray`物件。|  
|[COleSafeArray::Clear](#clear)|釋出所有資料在基礎**VARIANT**。|  
|[COleSafeArray::Copy](#copy)|建立現有陣列的複本。|  
|[COleSafeArray::Create](#create)|建立安全的陣列。|  
|[COleSafeArray::CreateOneDim](#createonedim)|建立一維`COleSafeArray`物件。|  
|[COleSafeArray::Destroy](#destroy)|終結現有的陣列。|  
|[COleSafeArray::DestroyData](#destroydata)|終結安全陣列中的資料。|  
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|終結安全陣列的描述的元。|  
|[COleSafeArray::Detach](#detach)|卸離**VARIANT**陣列`COleSafeArray`物件 （如此將不會釋放資料）。|  
|[COleSafeArray::GetByteArray](#getbytearray)|複製到安全的陣列內容[CByteArray](../../mfc/reference/cbytearray-class.md)。|  
|[COleSafeArray::GetDim](#getdim)|傳回陣列中的維度數目。|  
|[Colesafearray:: Getelement](#getelement)|擷取安全陣列的單一項目。|  
|[COleSafeArray::GetElemSize](#getelemsize)|傳回的大小，以位元組為單位的安全陣列有一個項目。|  
|[COleSafeArray::GetLBound](#getlbound)|傳回任何維度的安全陣列的下限。|  
|[COleSafeArray::GetOneDimSize](#getonedimsize)|傳回一維的元素數目`COleSafeArray`物件。|  
|[COleSafeArray::GetUBound](#getubound)|傳回任何維度的安全陣列的上限。|  
|[COleSafeArray::Lock](#lock)|陣列的鎖定計數遞增，並將陣列資料的指標放在陣列描述項。|  
|[COleSafeArray::PtrOfIndex](#ptrofindex)|讓指標回到索引的項目。|  
|[COleSafeArray::PutElement](#putelement)|將單一項目指派到陣列。|  
|[COleSafeArray::Redim](#redim)|變更最小顯著性 （最右邊） 的繫結，安全陣列。|  
|[COleSafeArray::ResizeOneDim](#resizeonedim)|在一維的元素數目變更`COleSafeArray`物件。|  
|[COleSafeArray::UnaccessData](#unaccessdata)|遞減鎖定計數的陣列，並使指標擷取`AccessData`。|  
|[COleSafeArray::Unlock](#unlock)|減量鎖定計數的陣列，因此可以釋出或調整大小。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|存取基礎**VARIANT**結構`COleSafeArray`物件。|  
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|存取基礎**VARIANT**結構`COleSafeArray`物件。|  
|[COleSafeArray::operator =](#operator_eq)|複製值到`COleSafeArray`物件 ( **SAFEARRAY**， **VARIANT**， `COleVariant`，或`COleSafeArray`陣列)。|  
|[COleSafeArray::operator = =](#operator_eq_eq)|比較兩個變數的陣列 ( **SAFEARRAY**， **VARIANT**， `COleVariant`，或`COleSafeArray`陣列)。|  
|[COleSafeArray::operator&lt;&lt;](#operator_lt_lt)|輸出的內容`COleSafeArray`傾印內容的物件。|  
  
## <a name="remarks"></a>備註  
 `COleSafeArray`衍生自 OLE **VARIANT**結構。 OLE **SAFEARRAY**成員函式都是透過`COleSafeArray`，以及做為一組專為一維的位元組陣列的成員函式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="accessdata"></a>COleSafeArray::AccessData  
 擷取陣列資料的指標。  
  
```  
void AccessData(void** ppvData);
```  
  
### <a name="parameters"></a>參數  
 `ppvData`  
 指向陣列資料的指標。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]  
  
##  <a name="allocdata"></a>COleSafeArray::AllocData  
 安全陣列配置記憶體。  
  
```  
void AllocData();
```  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="allocdescriptor"></a>COleSafeArray::AllocDescriptor  
 描述元的安全陣列配置記憶體。  
  
```  
void AllocDescriptor(DWORD dwDims);
```  
  
### <a name="parameters"></a>參數  
 `dwDims`  
 安全陣列中的維度數目。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="attach"></a>COleSafeArray::Attach  
 中的現有資料的控制權**VARIANT**陣列`COleSafeArray`物件。  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>參數  
 *varSrc*  
 A **VARIANT**物件。 *VarSrc*參數必須要有[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)**VT_ARRAY**。  
  
### <a name="remarks"></a>備註  
 來源**VARIANT**的類型設定為`VT_EMPTY`。 如果有的話，此函式會清除陣列，目前的資料。  
  
### <a name="example"></a>範例  
  請參閱範例的[COleSafeArray::AccessData](#accessdata)。  
  
##  <a name="clear"></a>COleSafeArray::Clear  
 清除 安全陣列。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 函式會藉由設定清除安全陣列`VARTYPE`之物件的`VT_EMPTY`。 目前的內容並釋出和釋放陣列。  
  
##  <a name="colesafearray"></a>COleSafeArray::COleSafeArray  
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
 `saSrc`  
 現有`COleSafeArray`物件或**SAFEARRAY**要複製到新`COleSafeArray`物件。  
  
 `vtSrc`  
 **VARTYPE**新`COleSafeArray`物件。  
  
 `psaSrc`  
 指標**SAFEARRAY**要複製到新`COleSafeArray`物件。  
  
 *varSrc*  
 現有**VARIANT**或`COleVariant`物件複製到新`COleSafeArray`物件。  
  
 `pSrc`  
 指標**VARIANT**物件複製到新`COleSafeArray`物件。  
  
### <a name="remarks"></a>備註  
 所有這些建構函式建立新`COleSafeArray`物件。 如果沒有參數，空`COleSafeArray`建立物件 ( `VT_EMPTY`)。 如果`COleSafeArray`複製從另一個陣列的[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)隱含已知 ( `COleSafeArray`， `COleVariant`，或**VARIANT**)、 **VARTYPE**的來源陣列會保留，而不需要指定。 如果`COleSafeArray`複製從另一個陣列的**VARTYPE**不知道 ( **SAFEARRAY**)、 **VARTYPE**中必須指定`vtSrc`參數。  
  
 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="copy"></a>COleSafeArray::Copy  
 建立現有安全陣列的複本。  
  
```  
void Copy(LPSAFEARRAY* ppsa);
```  
  
### <a name="parameters"></a>參數  
 *ppsa*  
 這是要傳回新的陣列描述元中的位置指標。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="create"></a>COleSafeArray::Create  
 配置，並初始化陣列的資料。  
  
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
 `vtSrc`  
 陣列的基底類型 (也就是**VARTYPE**的陣列的每個項目)。 **VARTYPE**限制為 variant 的類型子集。 既不**VT_ARRAY**和**VT_BYREF**可以設定旗標。 `VT_EMPTY`和**VT_NULL**不是有效的基底型別陣列。 所有其他類型是合法的。  
  
 `dwDims`  
 陣列中的維度數目。 這可以與建立陣列之後變更[Redim](#redim)。  
  
 *rgElements*  
 針對陣列中每個維度的項目數的陣列指標。  
  
 *rgsabounds*  
 向量界限 （一個用於每個維度） 的指標至配置的陣列。  
  
### <a name="remarks"></a>備註  
 如有必要，此函式將會清除目前陣列的資料。 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="createonedim"></a>COleSafeArray::CreateOneDim  
 建立新的一維`COleSafeArray`物件。  
  
```  
void CreateOneDim(
    VARTYPE vtSrc,  
    DWORD dwElements,  
    const void* pvSrcData = NULL,  
    long nLBound = 0);
```  
  
### <a name="parameters"></a>參數  
 `vtSrc`  
 陣列的基底類型 (也就是**VARTYPE**的陣列的每個項目)。  
  
 `dwElements`  
 陣列中的項目數目。 這可以與建立陣列之後變更[ResizeOneDim](#resizeonedim)。  
  
 `pvSrcData`  
 將複製到陣列的資料指標。  
  
 *nLBound*  
 陣列的下限。  
  
### <a name="remarks"></a>備註  
 此函式配置，並初始化陣列，複製指定的資料時，如果資料指標`pvSrcData`不**NULL**。  
  
 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]  
  
##  <a name="destroy"></a>COleSafeArray::Destroy  
 終結現有的陣列描述項和陣列中的所有資料。  
  
```  
void Destroy();
```  
  
### <a name="remarks"></a>備註  
 如果物件會儲存在陣列中，會釋放每個物件。 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="destroydata"></a>COleSafeArray::DestroyData  
 終結安全陣列中的所有資料。  
  
```  
void DestroyData();
```  
  
### <a name="remarks"></a>備註  
 如果物件會儲存在陣列中，會釋放每個物件。 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="destroydescriptor"></a>COleSafeArray::DestroyDescriptor  
 終結安全陣列的描述的元。  
  
```  
void DestroyDescriptor();
```  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="detach"></a>COleSafeArray::Detach  
 卸離**VARIANT**資料`COleSafeArray`物件。  
  
```  
VARIANT Detach();
```  
  
### <a name="return-value"></a>傳回值  
 基礎**VARIANT**值`COleSafeArray`物件。  
  
### <a name="remarks"></a>備註  
 藉由設定函式中斷連結的安全陣列中的資料[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)之物件的`VT_EMPTY`。 它會釋放陣列呼叫 Windows 函式的呼叫端的責任[Vvalue](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835)。  
  
 錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
  請參閱範例的[COleSafeArray::PutElement](#putelement)。  
  
##  <a name="getbytearray"></a>COleSafeArray::GetByteArray  
 複製到安全的陣列內容`CByteArray`。  
  
```  
void GetByteArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>參數  
 `bytes`  
 若要參考[CByteArray](../../mfc/reference/cbytearray-class.md)物件。  
  
##  <a name="getdim"></a>COleSafeArray::GetDim  
 傳回中的維度數目`COleSafeArray`物件。  
  
```  
DWORD GetDim();
```  
  
### <a name="return-value"></a>傳回值  
 安全陣列中的維度數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="getelement"></a>Colesafearray:: Getelement  
 擷取安全陣列的單一項目。  
  
```  
void GetElement(
    long* rgIndices,  
    void* pvData);
```  
  
### <a name="parameters"></a>參數  
 `rgIndices`  
 陣列的每個維度索引陣列的指標。  
  
 `pvData`  
 要放入陣列的元素的位置指標。  
  
### <a name="remarks"></a>備註  
 此函式自動呼叫 windows 函式`SafeArrayLock`和`SafeArrayUnlock`之前與之後擷取的項目。 如果資料項目是字串、 物件或變數，函式會複製項目中的正確方式。 參數`pvData`應該指向大型緩衝區不足，無法包含的項目。  
  
 錯誤時，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]  
  
##  <a name="getelemsize"></a>COleSafeArray::GetElemSize  
 擷取中的項目大小`COleSafeArray`物件。  
  
```  
DWORD GetElemSize();
```  
  
### <a name="return-value"></a>傳回值  
 大小，以位元組為單位的安全陣列的項目。  
  
##  <a name="getlbound"></a>COleSafeArray::GetLBound  
 會傳回任何維度的下限`COleSafeArray`物件。  
  
```  
void GetLBound(
    DWORD dwDim,  
    long* pLBound);
```  
  
### <a name="parameters"></a>參數  
 `dwDim`  
 用來取得下限陣列維度。  
  
 *pLBound*  
 要傳回下限的位置指標。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]  
  
##  <a name="getonedimsize"></a>COleSafeArray::GetOneDimSize  
 傳回一維的元素數目`COleSafeArray`物件。  
  
```  
DWORD GetOneDimSize();
```  
  
### <a name="return-value"></a>傳回值  
 安全的一維陣列中項目的數目。  
  
### <a name="example"></a>範例  
  請參閱範例的[COleSafeArray::CreateOneDim](#createonedim)。  
  
##  <a name="getubound"></a>COleSafeArray::GetUBound  
 傳回任何維度的安全陣列的上限。  
  
```  
void GetUBound(
    DWORD dwDim,  
    long* pUBound);
```  
  
### <a name="parameters"></a>參數  
 `dwDim`  
 用來取得上限陣列維度。  
  
 *pUBound*  
 要傳回上限的位置指標。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]  
  
##  <a name="lock"></a>COleSafeArray::Lock  
 鎖定計數遞增陣列並放置在陣列中的資料陣列描述項的指標。  
  
```  
void Lock();
```  
  
### <a name="remarks"></a>備註  
 錯誤時，就會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
 陣列描述元中的指標無效，直到`Unlock`呼叫。 呼叫`Lock`可以巢狀; 有相同數目的呼叫`Unlock`所需。  
  
 鎖定時，無法刪除陣列。  
  
##  <a name="operator_lpcvariant"></a>COleSafeArray::operator LPCVARIANT  
 呼叫此轉型運算子，來存取基礎**VARIANT**這個結構`COleSafeArray`物件。  
  
```  
operator LPCVARIANT() const;  
```  
  
##  <a name="operator_lpvariant"></a>COleSafeArray::operator LPVARIANT  
 呼叫此轉型運算子，來存取基礎**VARIANT**這個結構`COleSafeArray`物件。  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>備註  
 請注意，變更中的值**VARIANT**結構存取此函式傳回的指標會變更這個值`COleSafeArray`物件。  
  
##  <a name="operator_eq"></a>COleSafeArray::operator =  
 這些多載的指派運算子會將來源值複製到這個`COleSafeArray`物件。  
  
```  
COleSafeArray& operator=(const COleSafeArray& saSrc);  
COleSafeArray& operator=(const VARIANT& varSrc);  
  COleSafeArray& operator=(LPCVARIANT pSrc);  
COleSafeArray& operator=(const COleVariant& varSrc);
```  
  
### <a name="remarks"></a>備註  
 每個運算子的簡短描述如下：  
  
- **運算子 = (** *saSrc* **)**複製現有`COleSafeArray`成為這個物件的物件。  
  
- **運算子 = (** *varSrc***)**複製現有**VARIANT**或`COleVariant`到此物件的陣列。  
  
- **運算子 = (** `pSrc` **)**複本**VARIANT**陣列物件來存取`pSrc`到這個物件。  
  
##  <a name="operator_eq_eq"></a>COleSafeArray::operator = =  
 此運算子比較兩個陣列 ( **SAFEARRAY**， **VARIANT**， `COleVariant`，或`COleSafeArray`陣列)，並傳回非零，如果它們相等，否則為 0。  
  
```  
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;  
   
BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;  
   
BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;  ```  
  
### Remarks  
 Two arrays are equal if they have an equal number of dimensions, equal size in each dimension, and equal element values.  
  
##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;  
 The `COleSafeArray` insertion (<<) operator supports diagnostic dumping and storing of a `COleSafeArray` object to an archive.  
  
```  
CDumpContext & AFXAPI 運算子 << (CDumpContext & dc，  
    COleSafeArray & saSrc);
```  
  
##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex  
 Returns a pointer to the element specified by the index values.  
  
```  
void PtrOfIndex (長時間 * rgIndices，  
    void * * ppvData);
```  
  
### Parameters  
 `rgIndices`  
 An array of index values that identify an element of the array. All indexes for the element must be specified.  
  
 `ppvData`  
 On return, pointer to the element identified by the values in `rgIndices`.  
  
##  <a name="putelement"></a>  COleSafeArray::PutElement  
 Assigns a single element into the array.  
  
```  
void PutElement (長時間 * rgIndices，  
    void * pvData);
```  
  
### Parameters  
 `rgIndices`  
 Pointer to an array of indexes for each dimension of the array.  
  
 `pvData`  
 Pointer to the data to assign to the array. **VT_DISPATCH**, **VT_UNKNOWN**, and `VT_BSTR` variant types are pointers and do not require another level of indirection.  
  
### Remarks  
 This function automatically calls the Windows functions [SafeArrayLock](https://msdn.microsoft.com/library/windows/desktop/ms221492.aspx) and [SafeArrayUnlock](https://msdn.microsoft.com/library/windows/desktop/ms221246.aspx) before and after assigning the element. If the data element is a string, object, or variant, the function copies it correctly, and if the existing element is a string, object, or variant, it is cleared correctly.  
  
 Note that you can have multiple locks on an array, so you can put elements into an array while the array is locked by other operations.  
  
 On error, the function throws a [CMemoryException](../../mfc/reference/cmemoryexception-class.md) or [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
 [!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]  
  
##  <a name="redim"></a>  COleSafeArray::Redim  
 Changes the least significant (rightmost) bound of a safe array.  
  
```  
void Redim (SAFEARRAYBOUND * psaboundNew);
```  
  
### Parameters  
 *psaboundNew*  
 Pointer to a new safe array bound structure containing the new array bound. Only the least significant dimension of an array may be changed.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim  
 Changes the number of elements in a one-dimensional `COleSafeArray` object.  
  
```  
void ResizeOneDim (DWORD dwElements);
```  
  
### Parameters  
 `dwElements`  
 Number of elements in the one-dimensional safe array.  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::CreateOneDim](#createonedim).  
  
##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData  
 Decrements the lock count of an array and invalidates the pointer retrieved by `AccessData`.  
  
```  
void UnaccessData();
```  
  
### Remarks  
 On error, the function throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
### Example  
  See the example for [COleSafeArray::AccessData](#accessdata).  
  
##  <a name="unlock"></a>  COleSafeArray::Unlock  
 Decrements the lock count of an array so it can be freed or resized.  
  
```  
void Unlock();
```  
  
### Remarks  
 This function is called after access to the data in an array is finished. On error, it throws a [COleException](../../mfc/reference/coleexception-class.md).  
  
## See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)
