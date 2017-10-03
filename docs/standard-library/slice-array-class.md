---
title: "slice_array 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- valarray/std::slice_array
dev_langs:
- C++
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
caps.latest.revision: 20
author: corob-msft
ms.author: corob
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 12c40729fa9a848a87f37283277e88392fb04614
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="slicearray-class"></a>slice_array 類別
可藉由提供 valarray 之切割所定義的子集陣列之間的作業，支援切割物件的內部、輔助的範本類別。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Type>  
class slice_array : public slice {  
public:  
    typedef Type value_type;  
    void operator=(const valarray<Type>& x) const;

 
    void operator=(const Type& x) const;

 
    void operator*=(const valarray<Type>& x) const;

 
    void operator/=(const valarray<Type>& x) const;

 
    void operator%=(const valarray<Type>& x) const;

 
    void operator+=(const valarray<Type>& x) const;

 
    void operator-=(const valarray<Type>& x) const;

 
    void operator^=(const valarray<Type>& x) const;

 
    void operator&=(const valarray<Type>& x) const;

 
    void operator|=(const valarray<Type>& x) const;

 
    void operator<<=(const valarray<Type>& x) const;

 
    void operator>>=(const valarray<Type>& x) const;

 
// The rest is private or implementation defined  
}  
```  
  
## <a name="remarks"></a>備註  
 此類別描述一個物件，該物件會將對 [valarray](../standard-library/valarray-class.md)**\<Type>** 類別之物件的參考與 [slice](../standard-library/slice-class.md) 類別的物件儲存在一起，後者描述要從 **valarray\<Type>** 物件選取的項目序列。  
  
 此樣板類別是由某些 valarray 運算間接建立的，無法直接在程式中使用。 配量註標運算子會使用內部輔助樣板類別：  
  
 `slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`)。  
  
 您只能藉由撰寫 [va&#91;sl&#93;](../standard-library/valarray-class.md#op_at) 格式的運算式，為 valarray **va** 的配量 **sl** 建構 **slice_array\<Type>** 物件。 slice_array 類別的成員函式接著會像針對 **valarray\<Type>** 定義的對應函式簽章一樣運作，不同的是，只有選取的項目序列會受到影響。 slice_array 所控制的序列是由配量建構函式的三個參數所定義，亦即配量中第一個項目的索引、項目數，以及項目之間的距離。 從由 **va**[ `slice`(2, 5, 3)] 所宣告之 valarray **va** 所剪下的 slice_array，會選取含有 **va** 之索引 2、5、8、11 及 14 的項目。 索引必須有效，程序才能有效。  
  
## <a name="example"></a>範例  
 如需如何宣告及使用 slice_array 的範例，請參閱 [slice::slice](../standard-library/slice-class.md#slice) 的範例。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<valarray>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


