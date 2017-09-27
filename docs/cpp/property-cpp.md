---
title: "屬性 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- property_cpp
- Property
dev_langs:
- C++
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
caps.latest.revision: 7
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d4cb68d02f9ee543c2d3271bc48ad4318352faa2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="property-c"></a>property (C++)
**Microsoft 特定的**  
  
 這個屬性可以套用至類別或結構定義中的非靜態「虛擬資料成員」。 編譯器會將這些「虛擬資料成員」的參考變更為函式呼叫，將它們視為資料成員。  
  
## <a name="syntax"></a>語法  
  
```  
  
      __declspec( property( get=get_func_name ) ) declarator  
__declspec( property( put=put_func_name ) ) declarator  
__declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## <a name="remarks"></a>備註  
 當編譯器查看成員選取運算子右側以此屬性宣告的資料成員 (「**。**「 或 」**->**")，它將作業轉換成**取得**或**放**函式，視這類運算式為左值或右值。 在更複雜的內容，例如"`+=`」，請重寫藉由同時執行**取得**和**放**。  
  
 在類別或結構定義中也可以使用這個屬性宣告空陣列。 例如：  
  
```  
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 上述陳述式表示可以同時使用 `x[]` 和一個或多個陣列索引。 在這種情況下，`i=p->x[a][b]` 會轉換為 `i=p->GetX(a, b)`，而 `p->x[a][b] = i` 則會轉換為 `p->PutX(a, b, i);`  
  
 **END Microsoft 特定的**  
  
## <a name="example"></a>範例  
  
```  
// declspec_property.cpp  
struct S {  
   int i;  
   void putprop(int j) {   
      i = j;  
   }  
  
   int getprop() {  
      return i;  
   }  
  
   __declspec(property(get = getprop, put = putprop)) int the_prop;  
};  
  
int main() {  
   S s;  
   s.the_prop = 5;  
   return s.the_prop;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)
