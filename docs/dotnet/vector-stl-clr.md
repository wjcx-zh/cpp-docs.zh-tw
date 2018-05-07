---
title: 向量 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: de5d09d569933dc06666ed2008081703d59c1564
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
此範本類別描述控制不同長度序列的項目具有隨機存取的物件。 使用容器`vector`管理的項目序列，做為連續的區塊存放裝置。 區塊會實作為隨成長的陣列。  
  
 在以下描述`GValue`相同`Value`後者是 ref 型別，除非在這種情況下很`Value^`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>參數  
 值  
 受控制序列中項目的類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[vector::const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[vector::const_reference (STL/CLR)](../dotnet/vector-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[vector::const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[vector::difference_type (STL/CLR)](../dotnet/vector-difference-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)|容器的泛型介面型別。|  
|[vector::generic_iterator (STL/CLR)](../dotnet/vector-generic-iterator-stl-clr.md)|泛型介面，該容器的迭代器類型。|  
|[vector::generic_reverse_iterator (STL/CLR)](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器類型。|  
|[vector::generic_value (STL/CLR)](../dotnet/vector-generic-value-stl-clr.md)|泛型介面的容器項目的類型。|  
|[vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[vector::reference (STL/CLR)](../dotnet/vector-reference-stl-clr.md)|項目的參考類型。|  
|[vector::reverse_iterator (STL/CLR)](../dotnet/vector-reverse-iterator-stl-clr.md)|受控制序列的反向迭代器類型。|  
|[vector::size_type (STL/CLR)](../dotnet/vector-size-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[vector::value_type (STL/CLR)](../dotnet/vector-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)|取代所有項目。|  
|[vector::at (STL/CLR)](../dotnet/vector-at-stl-clr.md)|存取指定位置的項目。|  
|[vector::back (STL/CLR)](../dotnet/vector-back-stl-clr.md)|存取最後一個項目。|  
|[vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[vector::capacity (STL/CLR)](../dotnet/vector-capacity-stl-clr.md)|報表配置的儲存體容器的大小。|  
|[vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)|移除所有項目。|  
|[vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)|測試項目是否不存在。|  
|[vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)|指定受控制序列的結尾。|  
|[vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)|移除位於指定位置的項目。|  
|[vector::front (STL/CLR)](../dotnet/vector-front-stl-clr.md)|存取第一個項目。|  
|[vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)|將項目加入指定的位置。|  
|[vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)|移除最後一個項目。|  
|[vector::push_back (STL/CLR)](../dotnet/vector-push-back-stl-clr.md)|加入新的最後一個項目。|  
|[vector::rbegin (STL/CLR)](../dotnet/vector-rbegin-stl-clr.md)|指定反向受控制序列的開頭。|  
|[vector::rend (STL/CLR)](../dotnet/vector-rend-stl-clr.md)|指定反向受控制序列的結尾。|  
|[vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)|可確保容器的最小的成長容量。|  
|[vector::resize (STL/CLR)](../dotnet/vector-resize-stl-clr.md)|變更項目數目。|  
|[vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)|計算元素的數目。|  
|[vector::swap (STL/CLR)](../dotnet/vector-swap-stl-clr.md)|交換兩個容器的內容。|  
|[vector::to_array (STL/CLR)](../dotnet/vector-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
|[vector::vector (STL/CLR)](../dotnet/vector-vector-stl-clr.md)|建構容器物件。|  
  
|屬性|描述|  
|--------------|-----------------|  
|[vector::back_item (STL/CLR)](../dotnet/vector-back-item-stl-clr.md)|存取最後一個項目。|  
|[vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)|存取第一個項目。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)|取代受控制的序列。|  
|[vector::operator (STL/CLR)](../dotnet/vector-operator-stl-clr.md)|存取指定位置的項目。|  
|[operator!= (vector) (STL/CLR)](../dotnet/operator-inequality-vector-stl-clr.md)|決定如果`vector`物件是否不等於另一個`vector`物件。|  
|[operator< (vector) (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)|決定如果`vector`物件是否小於另一個`vector`物件。|  
|[operator<= (vector) (STL/CLR)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|決定如果`vector`物件是否小於或等於另一個`vector`物件。|  
|[operator== (vector) (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)|決定如果`vector`物件是否等於另一個`vector`物件。|  
|[operator> (vector) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)|決定如果`vector`物件是否大於另一個`vector`物件。|  
|[operator>= (vector) (STL/CLR)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|決定如果`vector`物件是否大於或等於另一個`vector`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|項目順序。|  
|<xref:System.Collections.ICollection>|維護群組的項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目順序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|<xref:System.Collections.Generic.IList%601>|維護已排序的群組的具類型的項目。|  
|IVector < 值\>|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放的序列的預存陣列透過它所控制的儲存體`Value`項目，則視成長。 附加新元素的成本是平攤常數時間的方式，就會發生成長。 換句話說，將項目結尾的成本不會增加，平均而言為受控制的序列愈大的長度。 因此，向量為基礎容器樣板類別的候選[堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 A`vector`支援隨機存取迭代器，這表示您可以參考項目直接指定其數值位置，從第一個 （前端） 項目的零計數來`size() - 1`的最後一個 （回到） 項目。 這也表示向量為基礎容器樣板類別的候選[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 向量的迭代器會儲存其相關聯的向量物件，以及它所指定的項目偏差的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 向量項目偏差等同於其位置。  
  
 插入或刪除項目可以變更項目值的指定位置，儲存，因此也可以變更由迭代器指定的值。 （若要複製項目向上或向下建立一個洞之前插入或用來填入暴露在清除之後可能有容器）。不過，向量迭代器就持續有效，只要其偏差是在範圍中`[0, size()]`。 此外，有效的迭代器會維持 dereferencable-您可用它來存取或修改項目值，它會指定-，只要其偏差值不等於`size()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼不會終結其項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)  
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)