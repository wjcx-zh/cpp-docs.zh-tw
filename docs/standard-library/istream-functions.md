---
title: "&lt;istream&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 3fe398e0424ff6fc24eff9b084759aa10c46e98a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt; 函式
|||  
|-|-|  
|[swap](#istream_swap)|[ws](#ws)|  
  
##  <a name="istream_swap"></a>  swap  
 交換兩個資料流物件的元素。  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_istream<Elem, Tr>& left,  
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>  
void swap(
    basic_iostream<Elem, Tr>& left,  
    basic_iostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 資料流。  
  
 `right`  
 資料流。  
  
##  <a name="ws"></a>  ws  
 略過資料流中的空白字元。  
  
```  
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```  
  
### <a name="parameters"></a>參數  
 `_Istr`  
 資料流。  
  
### <a name="return-value"></a>傳回值  
 資料流。  
  
### <a name="remarks"></a>備註  
 操作工具會擷取並捨棄任何符合下列條件的元素 `ch`：[use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **Elem**> >( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **ctype**\< **Elem**>:: **space**, **ch**) 為 true。  
  
 此函數如果在擷取元素時遇到檔案結尾，就會呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**)。 它會傳回 `_Istr`。  
  
### <a name="example"></a>範例  
  如需使用 `ws` 的範例，請參閱 [operator>>](../standard-library/istream-operators.md#op_gt_gt)。  
  
## <a name="see-also"></a>另請參閱  
 [\<istream>](../standard-library/istream.md)


