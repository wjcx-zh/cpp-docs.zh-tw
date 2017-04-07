---
title: "CTypedPtrMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- type-safe collections
- template classes, CTypedPtrMap class
- maps
- CTypedPtrMap class
- pointer maps
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
caps.latest.revision: 23
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
ms.openlocfilehash: 919d751c6ffe4b10ffad047f1b6be832bf49a1af
ms.lasthandoff: 02/24/2017

---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap 類別
為指標對應類別 `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`和 `CMapStringToPtr`的物件提供類型安全「包裝函式」。  
  
## <a name="syntax"></a>語法  
  
```  
template<class BASE_CLASS, class KEY, class VALUE>  
class CTypedPtrMap : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>參數  
 `BASE_CLASS`  
 基底類別的型別的指標對應類別;必須是指標對應類別 ( `CMapPtrToPtr`， `CMapPtrToWord`， `CMapWordToPtr`，或`CMapStringToPtr`)。  
  
 `KEY`  
 做為索引鍵的對應物件的類別。  
  
 `VALUE`  
 儲存在對應中的物件類別。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|取得逐一查看下一個項目。|  
|[CTypedPtrMap::Lookup](#lookup)|傳回`KEY`根據`VALUE`。|  
|[CTypedPtrMap::RemoveKey](#removekey)|移除索引鍵所指定的項目。|  
|[CTypedPtrMap::SetAt](#setat)|將項目插入對應中。如果找到相符的索引鍵，會取代現有的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CTypedPtrMap::operator]](#operator_at)|在對應中插入項目。|  
  
## <a name="remarks"></a>備註  
 當您使用`CTypedPtrMap`，c + + 型別檢查功能，有助於排除不相符的指標類型所造成的錯誤。  
  
 因為所有`CTypedPtrMap`函式會以內嵌方式，使用此範本並不會大幅影響大小或您的程式碼的速度。  
  
 如需有關使用`CTypedPtrMap`，請參閱文章[集合](../../mfc/collections.md)和[樣板架構類別](../../mfc/template-based-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## <a name="requirements"></a>需求  
 **Header:** afxtempl.h  
  
##  <a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc  
 擷取對應的項目在`rNextPosition`，然後更新`rNextPosition`來指向對應中的下一個項目。  
  
```  
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 `rPosition`  
 指定的參考**位置**前一個傳回值`GetNextAssoc`或`BASE_CLASS` **:: GetStartPosition**呼叫。  
  
 *索引鍵*  
 指定對應的索引鍵的類型樣板參數。  
  
 `rKey`  
 指定傳回的索引鍵的擷取的項目。  
  
 *值*  
 指定的對應值的類型樣板參數。  
  
 `rValue`  
 指定擷取的項目傳回的值。  
  
### <a name="remarks"></a>備註  
 此函式是最適合用來逐一查看對應中的所有項目。 請注意，位置順序不一定與索引鍵值順序相同。  
  
 如果擷取的項目是在對應中，最後則新值`rNextPosition`設為**NULL**。  
  
 內嵌函式呼叫`BASE_CLASS` **:: GetNextAssoc**。  
  
##  <a name="lookup"></a>CTypedPtrMap::Lookup  
 `Lookup`若要快速尋找完全符合的索引鍵的對應項目，會使用雜湊演算法。  
  
```  
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 `BASE_CLASS`  
 指定此對應類別的基底類別的樣板參數。  
  
 `key`  
 要查閱之項目的索引鍵。  
  
 *值*  
 指定此對應中所儲存值的類型樣板參數。  
  
 `rValue`  
 指定擷取的項目傳回的值。  
  
### <a name="return-value"></a>傳回值  
 非零，如果找不到項目。否則為 0。  
  
### <a name="remarks"></a>備註  
 內嵌函式呼叫`BASE_CLASS` **:: 查閱**。  
  
##  <a name="operator_at"></a>CTypedPtrMap::operator]  
 這個運算子只用於在指派陳述式 (l-value) 的左側。  
  
```  
VALUE& operator[ ](base_class ::base_arg_key key);
```  
  
### <a name="parameters"></a>參數  
 *值*  
 指定此對應中所儲存值的類型樣板參數。  
  
 `BASE_CLASS`  
 指定此對應類別的基底類別的樣板參數。  
  
 `key`  
 要尋找或建立對應中的項目索引鍵。  
  
### <a name="remarks"></a>備註  
 如果沒有具有指定之索引鍵的對應項目，則會建立新的項目。 任何 「 右側 」 （右值） 相當於這個運算子因為沒有索引鍵在對應中找到的可能性。 使用`Lookup`項目擷取的成員函式。  
  
##  <a name="removekey"></a>CTypedPtrMap::RemoveKey  
 此成員函式呼叫`BASE_CLASS` **:: RemoveKey**。  
  
```  
BOOL RemoveKey(KEY key);
```  
  
### <a name="parameters"></a>參數  
 *索引鍵*  
 指定對應的索引鍵的類型樣板參數。  
  
 `key`  
 要移除的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 非零，如果找到並成功移除，則此項目否則為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)。  
  
##  <a name="setat"></a>CTypedPtrMap::SetAt  
 此成員函式呼叫`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(KEY key, VALUE newValue);
```  
  
### <a name="parameters"></a>參數  
 *索引鍵*  
 指定對應的索引鍵的類型樣板參數。  
  
 `key`  
 指定的索引鍵值的 newValue。  
  
 `newValue`  
 指定的物件指標做為新項目的值。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr 類別](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord 類別](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapWordToPtr 類別](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr 類別](../../mfc/reference/cmapstringtoptr-class.md)

