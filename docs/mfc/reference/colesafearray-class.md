---
title: "COleSafeArray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleSafeArray
dev_langs:
- C++
helpviewer_keywords:
- COleSafeArray class
- arrays [C++], safe
- safe arrays
- ODBC, safe arrays
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3cb6fa49e3adf7e14c34baf7feb64d12e54f2758
ms.lasthandoff: 02/24/2017

---
# <a name="colesafearray-class"></a>COleSafeArray 類別
類別，用來處理任意類型和維度的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
class COleSafeArray : public tagVARIANT  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleSafeArray::COleSafeArray](#colesafearray)|建構 `COleSafeArray` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleSafeArray::AccessData](#accessdata)|擷取陣列資料的指標。|  
|[COleSafeArray::AllocData](#allocdata)|陣列配置記憶體。|  
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|安全陣列描述項，會配置記憶體。|  
|[COleSafeArray::Attach](#attach)|提供的現有控制**VARIANT**陣列`COleSafeArray`物件。|  
|[COleSafeArray::Clear](#clear)|釋出所有資料在基礎**VARIANT**。|  
|[COleSafeArray::Copy](#copy)|建立一份現有的陣列。|  
|[COleSafeArray::Create](#create)|建立安全的陣列。|  
|[COleSafeArray::CreateOneDim](#createonedim)|建立一維`COleSafeArray`物件。|  
|[COleSafeArray::Destroy](#destroy)|會破壞現有的陣列。|  
|[COleSafeArray::DestroyData](#destroydata)|終結安全陣列中的資料。|  
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|終結安全陣列的描述元。|  
|[COleSafeArray::Detach](#detach)|卸離**VARIANT**陣列`COleSafeArray`物件 （如此將不會釋放資料）。|  
|[COleSafeArray::GetByteArray](#getbytearray)|複製到的安全陣列的內容[CByteArray](../../mfc/reference/cbytearray-class.md)。|  
|[COleSafeArray::GetDim](#getdim)|傳回陣列中的維度數目。|  
|[COleSafeArray::GetElement](#getelement)|擷取安全陣列的單一項目。|  
|[COleSafeArray::GetElemSize](#getelemsize)|傳回大小，以位元組為單位的安全陣列中的一個項目。|  
|[COleSafeArray::GetLBound](#getlbound)|會傳回任何維度的安全陣列的下限。|  
|[COleSafeArray::GetOneDimSize](#getonedimsize)|傳回一維的項目數`COleSafeArray`物件。|  
|[COleSafeArray::GetUBound](#getubound)|會傳回任何維度的安全陣列的上限。|  
|[COleSafeArray::Lock](#lock)|陣列的鎖定計數遞增，並將陣列資料的指標放在陣列描述項。|  
|[COleSafeArray::PtrOfIndex](#ptrofindex)|索引項目傳回的指標。|  
|[COleSafeArray::PutElement](#putelement)|將單一項目指派到陣列。|  
|[COleSafeArray::Redim](#redim)|變更安全陣列的最小顯著性 （最右邊） 的繫結。|  
|[COleSafeArray::ResizeOneDim](#resizeonedim)|變更在一維的項目數`COleSafeArray`物件。|  
|[COleSafeArray::UnaccessData](#unaccessdata)|遞減鎖定計數的陣列，並使指標擷取`AccessData`。|  
|[COleSafeArray::Unlock](#unlock)|減量鎖定計數的陣列，以便釋出或調整其大小。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|存取基礎**VARIANT**結構`COleSafeArray`物件。|  
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|存取基礎**VARIANT**結構`COleSafeArray`物件。|  
|[COleSafeArray::operator =](#operator_eq)|複製值到`COleSafeArray`物件 ( **SAFEARRAY**， **VARIANT**， `COleVariant`，或`COleSafeArray`陣列)。|  
|[COleSafeArray::operator = =](#operator_eq_eq)|比較兩個變數的陣列 ( **SAFEARRAY**，**變異**， `COleVariant`，或`COleSafeArray`陣列)。|  
|[COleSafeArray::operator&lt;&lt;](#operator_lt_lt)|輸出的內容`COleSafeArray`傾印內容的物件。|  
  
## <a name="remarks"></a>備註  
 `COleSafeArray`衍生自 OLE **VARIANT**結構。 OLE **SAFEARRAY**成員函式都是透過`COleSafeArray`，以及一組專為位元組的一維陣列的成員函式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `tagVARIANT`  
  
 `COleSafeArray`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  
  
##  <a name="a-nameaccessdataa--colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafeArray::AccessData  
 擷取陣列資料的指標。  
  
```  
void AccessData(void** ppvData);
```  
  
### <a name="parameters"></a>參數  
 `ppvData`  
 陣列資料指標的指標。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&26;](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]  
  
##  <a name="a-nameallocdataa--colesafearrayallocdata"></a><a name="allocdata"></a>COleSafeArray::AllocData  
 安全陣列配置記憶體。  
  
```  
void AllocData();
```  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="a-nameallocdescriptora--colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafeArray::AllocDescriptor  
 安全陣列的描述元，會配置記憶體。  
  
```  
void AllocDescriptor(DWORD dwDims);
```  
  
### <a name="parameters"></a>參數  
 `dwDims`  
 安全陣列中的維度數目。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="a-nameattacha--colesafearrayattach"></a><a name="attach"></a>COleSafeArray::Attach  
 提供在現有的資料控制**VARIANT**陣列`COleSafeArray`物件。  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>參數  
 *varSrc*  
 A **VARIANT**物件。 *VarSrc*參數都必須有[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)**VT_ARRAY**。  
  
### <a name="remarks"></a>備註  
 來源**VARIANT**的類型設為`VT_EMPTY`。 如果有的話，此函式會清除目前的陣列資料。  
  
### <a name="example"></a>範例  
  請參閱範例[COleSafeArray::AccessData](#accessdata)。  
  
##  <a name="a-namecleara--colesafearrayclear"></a><a name="clear"></a>COleSafeArray::Clear  
 清除安全陣列。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 函式，藉以設定清除安全陣列`VARTYPE`之物件的`VT_EMPTY`。 釋放目前的內容，並釋放陣列。  
  
##  <a name="a-namecolesafearraya--colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafeArray::COleSafeArray  
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
 將現有`COleSafeArray`物件或**SAFEARRAY**要複製到新`COleSafeArray`物件。  
  
 `vtSrc`  
 **VARTYPE**新`COleSafeArray`物件。  
  
 `psaSrc`  
 指標**SAFEARRAY**要複製到新`COleSafeArray`物件。  
  
 *varSrc*  
 將現有**VARIANT**或`COleVariant`物件複製到新`COleSafeArray`物件。  
  
 `pSrc`  
 指標**VARIANT**物件複製到新`COleSafeArray`物件。  
  
### <a name="remarks"></a>備註  
 所有這些建構函式建立新的`COleSafeArray`物件。 如果沒有參數，空`COleSafeArray`物件建立 ( `VT_EMPTY`)。 如果`COleSafeArray`複製從另一個陣列的[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)即隱含地 ( `COleSafeArray`， `COleVariant`，或**VARIANT**)、 **VARTYPE**陣列保留且不需要指定的來源。 如果`COleSafeArray`複製從另一個陣列的**VARTYPE**不知道 ( **SAFEARRAY**)、 **VARTYPE**中必須指定`vtSrc`參數。  
  
 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="a-namecopya--colesafearraycopy"></a><a name="copy"></a>COleSafeArray::Copy  
 建立現有的安全陣列的複本。  
  
```  
void Copy(LPSAFEARRAY* ppsa);
```  
  
### <a name="parameters"></a>參數  
 *ppsa*  
 這是要傳回新的陣列描述元中的位置指標。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="a-namecreatea--colesafearraycreate"></a><a name="create"></a>COleSafeArray::Create  
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
 `vtSrc`  
 陣列的基底型別 (也就是**VARTYPE**陣列的每個項目)。 **VARTYPE**限制為 variant 類型的子集。 既不**VT_ARRAY**和**VT_BYREF**可以設定旗標。 `VT_EMPTY`和**VT_NULL**不是有效的基底型別陣列。 所有其他型別是合法的。  
  
 `dwDims`  
 陣列中的維度數目。 這可以使用在建立陣列之後變更[Redim](#redim)。  
  
 *rgElements*  
 每個維度陣列中的項目數的陣列指標。  
  
 *rgsabounds*  
 向量的範圍 （一個用於每個維度） 的指標陣列的配置。  
  
### <a name="remarks"></a>備註  
 如有必要，此函式將會清除目前的陣列資料。 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&27;](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="a-namecreateonedima--colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafeArray::CreateOneDim  
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
 陣列的基底型別 (也就是**VARTYPE**陣列的每個項目)。  
  
 `dwElements`  
 陣列中的項目數目。 這可以使用在建立陣列之後變更[ResizeOneDim](#resizeonedim)。  
  
 `pvSrcData`  
 將資料複製到陣列的指標。  
  
 *nLBound*  
 陣列的下限。  
  
### <a name="remarks"></a>備註  
 函式會配置並初始化陣列複製指定的資料時，如果資料指標`pvSrcData`不**NULL**。  
  
 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&28;](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]  
  
##  <a name="a-namedestroya--colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray::Destroy  
 會破壞現有的陣列描述項和陣列中的所有資料。  
  
```  
void Destroy();
```  
  
### <a name="remarks"></a>備註  
 如果物件儲存在陣列中，會釋放每個物件。 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="a-namedestroydataa--colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray::DestroyData  
 終結安全陣列中的所有資料。  
  
```  
void DestroyData();
```  
  
### <a name="remarks"></a>備註  
 如果物件儲存在陣列中，會釋放每個物件。 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="a-namedestroydescriptora--colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray::DestroyDescriptor  
 終結安全陣列的描述元。  
  
```  
void DestroyDescriptor();
```  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
##  <a name="a-namedetacha--colesafearraydetach"></a><a name="detach"></a>COleSafeArray::Detach  
 卸離**VARIANT**資料`COleSafeArray`物件。  
  
```  
VARIANT Detach();
```  
  
### <a name="return-value"></a>傳回值  
 基礎**VARIANT**值`COleSafeArray`物件。  
  
### <a name="remarks"></a>備註  
 函式中斷安全陣列中的資料，藉由設定[VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4)之物件的`VT_EMPTY`。 它會釋放陣列呼叫 Windows 函式的呼叫端的責任[Variant](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835)。  
  
 錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
  請參閱範例[COleSafeArray::PutElement](#putelement)。  
  
##  <a name="a-namegetbytearraya--colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafeArray::GetByteArray  
 複製到的安全陣列的內容`CByteArray`。  
  
```  
void GetByteArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>參數  
 `bytes`  
 參考[CByteArray](../../mfc/reference/cbytearray-class.md)物件。  
  
##  <a name="a-namegetdima--colesafearraygetdim"></a><a name="getdim"></a>COleSafeArray::GetDim  
 傳回維度中的數字`COleSafeArray`物件。  
  
```  
DWORD GetDim();
```  
  
### <a name="return-value"></a>傳回值  
 安全陣列中的維度數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&27;](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]  
  
##  <a name="a-namegetelementa--colesafearraygetelement"></a><a name="getelement"></a>COleSafeArray::GetElement  
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
 要放入陣列的元素位置的指標。  
  
### <a name="remarks"></a>備註  
 此函式會自動呼叫 windows 函式`SafeArrayLock`和`SafeArrayUnlock`之前和之後擷取的項目。 如果字串、 物件或變數資料元素，函式會複製項目中的正確方式。 參數`pvData`應該指向大型緩衝區不足，無法包含的項目。  
  
 錯誤時，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&29;](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]  
  
##  <a name="a-namegetelemsizea--colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafeArray::GetElemSize  
 擷取中的項目大小`COleSafeArray`物件。  
  
```  
DWORD GetElemSize();
```  
  
### <a name="return-value"></a>傳回值  
 以位元組為單位的安全陣列的項目大小。  
  
##  <a name="a-namegetlbounda--colesafearraygetlbound"></a><a name="getlbound"></a>COleSafeArray::GetLBound  
 傳回的任何維度下限`COleSafeArray`物件。  
  
```  
void GetLBound(
    DWORD dwDim,  
    long* pLBound);
```  
  
### <a name="parameters"></a>參數  
 `dwDim`  
 要取得最小值的陣列維度。  
  
 *pLBound*  
 要傳回的最小值的位置指標。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&30;](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]  
  
##  <a name="a-namegetonedimsizea--colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafeArray::GetOneDimSize  
 傳回一維的項目數`COleSafeArray`物件。  
  
```  
DWORD GetOneDimSize();
```  
  
### <a name="return-value"></a>傳回值  
 安全的一維陣列中項目的數目。  
  
### <a name="example"></a>範例  
  請參閱範例[COleSafeArray::CreateOneDim](#createonedim)。  
  
##  <a name="a-namegetubounda--colesafearraygetubound"></a><a name="getubound"></a>COleSafeArray::GetUBound  
 會傳回任何維度的安全陣列的上限。  
  
```  
void GetUBound(
    DWORD dwDim,  
    long* pUBound);
```  
  
### <a name="parameters"></a>參數  
 `dwDim`  
 要取得上限的陣列維度。  
  
 *pUBound*  
 要傳回上限的位置指標。  
  
### <a name="remarks"></a>備註  
 錯誤時，此函式會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&31;](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]  
  
##  <a name="a-namelocka--colesafearraylock"></a><a name="lock"></a>COleSafeArray::Lock  
 陣列和位置的指標陣列中的資料陣列描述項的鎖定計數遞增。  
  
```  
void Lock();
```  
  
### <a name="remarks"></a>備註  
 錯誤時，就會擲回[COleException](../../mfc/reference/coleexception-class.md)。  
  
 指標，陣列描述項無效，直到`Unlock`呼叫。 呼叫`Lock`可以巢狀; 相同數量的呼叫`Unlock`所需。  
  
 無法刪除陣列，而遭到鎖定。  
  
##  <a name="a-nameoperatorlpcvarianta--colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafeArray::operator LPCVARIANT  
 呼叫此轉型運算子，來存取基礎**VARIANT**這個結構`COleSafeArray`物件。  
  
```  
operator LPCVARIANT() const;  
```  
  
##  <a name="a-nameoperatorlpvarianta--colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafeArray::operator LPVARIANT  
 呼叫此轉型運算子，來存取基礎**VARIANT**這個結構`COleSafeArray`物件。  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>備註  
 請注意，變更中的值**VARIANT**結構存取此函式所傳回的指標會變更這個值`COleSafeArray`物件。  
  
##  <a name="a-nameoperatoreqa--colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray::operator =  
 這些多載的指派運算子會將來源值複製到這`COleSafeArray`物件。  
  
```  
COleSafeArray& operator=(const COleSafeArray& saSrc);  
COleSafeArray& operator=(const VARIANT& varSrc);  
  COleSafeArray& operator=(LPCVARIANT pSrc);  
COleSafeArray& operator=(const COleVariant& varSrc);
```  
  
### <a name="remarks"></a>備註  
 每個運算子的簡短描述如下︰  
  
- **運算子 = (** *saSrc* **)**複製現有`COleSafeArray`成為此物件的物件。  
  
- **運算子 = (** *varSrc***)**複製現有**VARIANT**或`COleVariant`到此物件陣列。  
  
- **運算子 = (** `pSrc` **)**複製**VARIANT** array 物件來存取`pSrc`到此物件。  
  
##  <a name="a-nameoperatoreqeqa--colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray::operator = =  
 這個運算子比較兩個陣列 ( **SAFEARRAY**， **VARIANT**， `COleVariant`，或`COleSafeArray`陣列)，並傳回非零，如果相等，否則為 0。  
  
```  
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;  
   
BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;  
   
BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;  ```  
  
### Remarks  
 Two arrays are equal if they have an equal number of dimensions, equal size in each dimension, and equal element values.  
  
##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;  
 The `COleSafeArray` insertion (<<) operator supports diagnostic dumping and storing of a `COleSafeArray` object to an archive.  
  
```  
CDumpContext i AFXAPI 運算子<( CDumpContext& dc, cdumpcontext&=""></( CDumpContext& dc,>  
    COleSafeArray i saSrc);
```  
  
##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex  
 Returns a pointer to the element specified by the index values.  
  
```  
void PtrOfIndex (長*rgIndices void** ppvData);
```  
  
### Parameters  
 `rgIndices`  
 An array of index values that identify an element of the array. All indexes for the element must be specified.  
  
 `ppvData`  
 On return, pointer to the element identified by the values in `rgIndices`.  
  
##  <a name="putelement"></a>  COleSafeArray::PutElement  
 Assigns a single element into the array.  
  
```  
void PutElement (長*rgIndices void* pvData);
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

