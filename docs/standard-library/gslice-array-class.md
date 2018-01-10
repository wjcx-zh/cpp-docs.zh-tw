---
title: "gslice_array 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: valarray/std::gslice_array
dev_langs: C++
helpviewer_keywords: gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c030885dd0ab6b9c102167e9702dce02589973b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="gslicearray-class"></a>gslice_array 類別
可藉由提供 valarray 之一般切割所定義的子集陣列之間的作業，支援一般切割物件的內部、輔助的範本類別。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Type>  
class gslice_array : public gsplice {  
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
 此類別描述一個物件，該物件會將對 [valarray](../standard-library/valarray-class.md)**\<Type>** 類別之 **va** 物件的參考與 [gslice](../standard-library/gslice-class.md) 類別的 **gs** 物件儲存在一起，後者描述要從 **valarray\<Type>** 物件選取的元素序列。  
  
 您只能藉由撰寫 [va&#91;gs&#93;](../standard-library/valarray-class.md#op_at) 格式的運算式來建構 **gslice_array\<Type>** 物件。 gslice_array 類別的成員函式會接著像針對 **valarray\<Type>** 定義的對應函式簽章一樣運作，不同的是，只有選取的元素序列會受到影響。  
  
 此範本類別是由某些 valarray 運算間接建立的，無法直接在程式中使用。 配量註標運算子會改用內部輔助範本類別：  
  
 `gslice_array`\< **Type**> `valarray`\< **Type**>:: `operator[]` ( **constgslice&**)。  
  
 您只能藉由撰寫 **va[gsl]** 格式的運算式，為 valarray **va** 的配量 **gsl** 建構 **gslice_array\<Type>** 物件。 gslice_array 類別的成員函式會接著像針對 **valarray\<Type>** 定義的對應函式簽章一樣運作，不同的是，只有選取的元素序列會受到影響。 gslice_array 所控制的序列是由配量建構函式的三個參數所定義，亦即第一個配量中第一個元素的索引、每個配量中的元素數目，以及每個配量中元素之間的距離。  
  
 在以下範例中：  
  
```  
const size_t lv[] = {2, 3};  
const size_t dv[] = {7, 2};  
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with  
//   indices 3, 5, 7, 10, 12, 14  
```  
  
 索引必須有效，程序才能有效。  
  
## <a name="example"></a>範例  
 如需如何宣告及使用 slice_array 的範例，請參閱 [gslice::gslice](../standard-library/gslice-class.md#gslice) 的範例。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<valarray>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

