---
title: "CTypedPtrMap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9056fc73e2718b2a21936c39e630f4d4fddf1eed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 基底類別的具類型的指標對應類別; 事件類別必須是指標對應類別 ( `CMapPtrToPtr`， `CMapPtrToWord`， `CMapWordToPtr`，或`CMapStringToPtr`)。  
  
 `KEY`  
 做為索引鍵對應的物件類別。  
  
 `VALUE`  
 儲存在 map 中的物件類別。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|取得逐一查看下一個項目。|  
|[CTypedPtrMap::Lookup](#lookup)|傳回`KEY`根據`VALUE`。|  
|[CTypedPtrMap::RemoveKey](#removekey)|移除索引鍵所指定的項目。|  
|[CTypedPtrMap::SetAt](#setat)|將項目插入對應中。如果找到相符的索引鍵，會取代現有的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CTypedPtrMap::operator]](#operator_at)|項目插入對應中。|  
  
## <a name="remarks"></a>備註  
 當您使用`CTypedPtrMap`，c + + 型別檢查功能可協助消除不相符的指標類型所造成的錯誤。  
  
 因為所有`CTypedPtrMap`函式會以內嵌方式，使用此範本時並不會大幅影響大小或您的程式碼的速度。  
  
 如需有關使用`CTypedPtrMap`，請參閱文章[集合](../../mfc/collections.md)和[樣板架構類別](../../mfc/template-based-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `BASE_CLASS`  
  
 `CTypedPtrMap`  
  
## <a name="requirements"></a>需求  
 **Header:** afxtempl.h  
  
##  <a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc  
 擷取位於的地圖元素`rNextPosition`，然後更新`rNextPosition`指向對應中的下一個項目。  
  
```  
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 `rPosition`  
 指定的參考**位置**傳回先前值`GetNextAssoc`或`BASE_CLASS` **:: GetStartPosition**呼叫。  
  
 *KEY*  
 指定對應的索引鍵的類型樣板參數。  
  
 `rKey`  
 指定傳回的索引鍵的擷取的項目。  
  
 *值*  
 指定的對應值的類型樣板參數。  
  
 `rValue`  
 指定的擷取的項目傳回的值。  
  
### <a name="remarks"></a>備註  
 此函式是最適合用來逐一查看對應中的所有項目。 請注意，位置順序不一定與索引鍵值順序相同。  
  
 如果擷取的項目是在對應中，最後則新值`rNextPosition`設**NULL**。  
  
 此內嵌函式呼叫`BASE_CLASS` **:: GetNextAssoc**。  
  
##  <a name="lookup"></a>CTypedPtrMap::Lookup  
 `Lookup`快速尋找地圖元素具有完全符合索引鍵使用雜湊演算法。  
  
```  
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>參數  
 `BASE_CLASS`  
 指定此對應之類別的基底類別的樣板參數。  
  
 `key`  
 要查閱之項目的索引鍵。  
  
 *值*  
 指定此地圖中所儲存值的類型樣板參數。  
  
 `rValue`  
 指定的擷取的項目傳回的值。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果找不到項目。否則便是 0。  
  
### <a name="remarks"></a>備註  
 此內嵌函式呼叫`BASE_CLASS` **:: 查閱**。  
  
##  <a name="operator_at"></a>CTypedPtrMap::operator]  
 此運算子只用於指派陳述式 （左值） 的左半部。  
  
```  
VALUE& operator[ ](base_class ::base_arg_key key);
```  
  
### <a name="parameters"></a>參數  
 *值*  
 指定此地圖中所儲存值的類型樣板參數。  
  
 `BASE_CLASS`  
 指定此對應之類別的基底類別的樣板參數。  
  
 `key`  
 要進行查閱或建立對應中的項目索引鍵。  
  
### <a name="remarks"></a>備註  
 如果沒有具有指定之索引鍵的對應項目，則會建立新的項目。 沒有任何 「 右邊 」 （右值） 相當於這個運算子因為索引鍵找到對應中可能發生。 使用`Lookup`項目擷取的成員函式。  
  
##  <a name="removekey"></a>CTypedPtrMap::RemoveKey  
 此成員函式呼叫`BASE_CLASS` **:: RemoveKey**。  
  
```  
BOOL RemoveKey(KEY key);
```  
  
### <a name="parameters"></a>參數  
 *KEY*  
 指定對應的索引鍵的類型樣板參數。  
  
 `key`  
 要移除的項目索引鍵。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果找到，已成功移除項目否則便是 0。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)。  
  
##  <a name="setat"></a>CTypedPtrMap::SetAt  
 此成員函式呼叫`BASE_CLASS` **:: SetAt**。  
  
```  
void SetAt(KEY key, VALUE newValue);
```  
  
### <a name="parameters"></a>參數  
 *KEY*  
 指定對應的索引鍵的類型樣板參數。  
  
 `key`  
 指定的索引鍵值的 newValue。  
  
 `newValue`  
 指定的物件指標做為新項目的值。  
  
### <a name="remarks"></a>備註  
 如需詳細註解，請參閱[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例收集](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr 類別](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord 類別](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapWordToPtr 類別](../../mfc/reference/cmapwordtoptr-class.md)   
 [CMapStringToPtr 類別](../../mfc/reference/cmapstringtoptr-class.md)
