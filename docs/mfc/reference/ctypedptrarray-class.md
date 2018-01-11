---
title: "CTypedPtrArray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
dev_langs: C++
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6e08749341bd7865c89e397e36aeff3a6ccc0d71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ctypedptrarray-class"></a>CTypedPtrArray 類別
為 `CPtrArray` 或 `CObArray`類別的物件提供類型安全「包裝函式」。  
  
## <a name="syntax"></a>語法  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>參數  
 `BASE_CLASS`  
 基底類別的具類型的指標陣列類別; 事件類別必須是陣列類別 (`CObArray`或`CPtrArray`)。  
  
 `TYPE`  
 基底類別的陣列中儲存的項目類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTypedPtrArray::Add](#add)|將新的項目加入至陣列的結尾。 如有必要，讓陣列成長|  
|[CTypedPtrArray::Append](#append)|加入另一個陣列的內容。 如有必要，讓陣列成長|  
|[CTypedPtrArray::Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|  
|[CTypedPtrArray::ElementAt](#elementat)|傳回陣列中項目指標的臨時參考。|  
|[CTypedPtrArray::GetAt](#getat)|傳回給定索引的值。|  
|[CTypedPtrArray::InsertAt](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|  
|[CTypedPtrArray::SetAt](#setat)|設定給定索引的值；不容許陣列成長。|  
|[CTypedPtrArray::SetAtGrow](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CTypedPtrArray::operator]](#operator_at)|設定或取得指定索引處的項目。|  
  
## <a name="remarks"></a>備註  
 當您使用`CTypedPtrArray`而`CPtrArray`或`CObArray`，c + + 型別檢查功能可協助消除不相符的指標類型所造成的錯誤。  
  
 此外，`CTypedPtrArray`包裝函式會執行大部分的會是必要，如果您使用轉型`CObArray`或`CPtrArray`。  
  
 因為所有`CTypedPtrArray`函式會以內嵌方式，使用此範本時並不會大幅影響大小或您的程式碼的速度。  
  
 如需有關使用`CTypedPtrArray`，請參閱文章[集合](../../mfc/collections.md)和[樣板架構類別](../../mfc/template-based-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## <a name="requirements"></a>需求  
 **Header:** afxtempl.h  
  
##  <a name="add"></a>CTypedPtrArray::Add  
 此成員函式呼叫`BASE_CLASS` **:: 新增**。  
  
```  
INT_PTR Add(TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定要加入至陣列元素的類型樣板參數。  
  
 `newElement`  
 要加入此陣列的項目。  
  
### <a name="return-value"></a>傳回值  
 加入項目的索引。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CObArray::Add](../../mfc/reference/cobarray-class.md#add)。  
  
##  <a name="append"></a>CTypedPtrArray::Append  
 此成員函式呼叫`BASE_CLASS` **:: Append**。  
  
```  
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>參數  
 `BASE_CLASS`  
 基底類別的具類型的指標陣列類別; 事件類別必須是陣列類別 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。  
  
 *型別*  
 基底類別的陣列中儲存的項目類型。  
  
 *src*  
 要附加至陣列元素的來源。  
  
### <a name="return-value"></a>傳回值  
 第一個附加的項目索引。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CObArray::Append](../../mfc/reference/cobarray-class.md#append)。  
  
##  <a name="copy"></a>CTypedPtrArray::Copy  
 此成員函式呼叫`BASE_CLASS` **:: 複製**。  
  
```  
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>參數  
 `BASE_CLASS`  
 基底類別的具類型的指標陣列類別; 事件類別必須是陣列類別 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。  
  
 *型別*  
 基底類別的陣列中儲存的項目類型。  
  
 *src*  
 要複製到陣列之項目的來源。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)。  
  
##  <a name="elementat"></a>CTypedPtrArray::ElementAt  
 此內嵌函式呼叫`BASE_CLASS` **:: ElementAt**。  
  
```  
TYPE& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存此陣列中的項目類型的樣板參數。  
  
 `nIndex`  
 整數索引大於或等於 0 且小於或等於所傳回的值`BASE_CLASS` **:: GetUpperBound**。  
  
### <a name="return-value"></a>傳回值  
 所指定的位置處的項目的臨時參考`nIndex`。 這個項目是範本參數所指定型別的*類型*。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)。  
  
##  <a name="getat"></a>CTypedPtrArray::GetAt  
 此內嵌函式呼叫`BASE_CLASS` **:: GetAt**。  
  
```  
TYPE GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在陣列中的項目類型的樣板參數。  
  
 `nIndex`  
 整數索引大於或等於 0 且小於或等於所傳回的值`BASE_CLASS` **:: GetUpperBound**。  
  
### <a name="return-value"></a>傳回值  
 所指定的位置處的項目副本`nIndex`。 這個項目是範本參數所指定型別的*類型*。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)  
  
##  <a name="insertat"></a>CTypedPtrArray::InsertAt  
 此成員函式呼叫`BASE_CLASS` **:: InsertAt**。  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    TYPE newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 可能會大於所傳回的值的整數索引[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。  
  
 *型別*  
 基底類別的陣列中儲存的項目類型。  
  
 `newElement`  
 要放在這個陣列中的物件指標。 A`newElement`值的**NULL**允許。  
  
 `nCount`  
 這個項目應該是次數插入 （預設值為 1）。  
  
 `nStartIndex`  
 可能會大於所傳回的值的整數索引`CObArray::GetUpperBound`。  
  
 `BASE_CLASS`  
 基底類別的具類型的指標陣列類別; 事件類別必須是陣列類別 ( [CObArray](../../mfc/reference/cobarray-class.md)或[CPtrArray](../../mfc/reference/cptrarray-class.md))。  
  
 `pNewArray`  
 另一個陣列，包含要加入至這個陣列的項目。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)。  
  
##  <a name="operator_at"></a>CTypedPtrArray::operator]  
 這些內嵌運算子呼叫`BASE_CLASS` **:: 運算子 []**。  
  
```  
TYPE& operator[ ](int_ptr nindex);  
TYPE operator[ ](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>參數  
 *型別*  
 指定儲存在陣列中的項目類型的樣板參數。  
  
 `nIndex`  
 整數索引大於或等於 0 且小於或等於所傳回的值`BASE_CLASS` **:: GetUpperBound**。  
  
### <a name="remarks"></a>備註  
 針對陣列不是呼叫第一個運算子， **const**，可以用於權限 （右值） 或指派陳述式的左邊 （左值）。 第二個，叫用**const**陣列，可以使用僅在右邊。  
  
 偵錯版本的程式庫判斷提示的註標 （請在左邊或右邊指派陳述式） 是否超出範圍。  
  
##  <a name="setat"></a>CTypedPtrArray::SetAt  
 此成員函式呼叫`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(
    INT_PTR nIndex,  
    TYPE ptr);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 整數索引大於或等於 0 且小於或等於所傳回的值[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)。  
  
 *型別*  
 基底類別的陣列中儲存的項目類型。  
  
 *ptr*  
 要插入 nIndex 陣列中的項目指標。 允許 NULL 值。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)。  
  
##  <a name="setatgrow"></a>CTypedPtrArray::SetAtGrow  
 此成員函式呼叫`BASE_CLASS` **:: SetAtGrow**。  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    TYPE newElement);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 大於或等於 0 的整數索引。  
  
 *型別*  
 基底類別的陣列中儲存的項目類型。  
  
 `newElement`  
 要加入此陣列的物件指標。 A **NULL**允許值。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPtrArray 類別](../../mfc/reference/cptrarray-class.md)   
 [CObArray 類別](../../mfc/reference/cobarray-class.md)
