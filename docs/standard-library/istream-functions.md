---
title: "&lt;istream&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: aa35f177bcb986e141d0e46e48dc007a96f94498
ms.lasthandoff: 02/24/2017

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
 操作工具會擷取並捨棄任何符合下列條件的元素 `ch`：[use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open)< **ctype**\< **Elem**> >( [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). **is**( **ctype**\< **Elem**>:: **space**, **ch**) 為 true。  
  
 此函數如果在擷取元素時遇到檔案結尾，就會呼叫 [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)( **eofbit**)。 它會傳回 `_Istr`。  
  
### <a name="example"></a>範例  
  如需使用 `ws` 的範例，請參閱 [operator>>](../standard-library/istream-operators.md#operator_gt__gt_)。  
  
## <a name="see-also"></a>另請參閱  
 [\<istream>](../standard-library/istream.md)


