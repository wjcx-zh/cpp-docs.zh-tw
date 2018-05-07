---
title: 清單 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list
dev_langs:
- C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4ff009da3ca29697e9b3affceb424bcd84b9b896
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="list-stlclr"></a>list (STL/CLR)
此範本類別描述控制不同長度序列的項目具有雙向存取的物件。 使用容器`list`管理項目序列以雙向連結清單的節點，各儲存一個項目。  
  
 在以下描述`GValue`相同`Value`後者是 ref 型別，除非在這種情況下很`Value^`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>參數  
 值  
 受控制序列中項目的類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](../dotnet/list-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[list::const_reference (STL/CLR)](../dotnet/list-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[list::const_reverse_iterator (STL/CLR)](../dotnet/list-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[list::difference_type (STL/CLR)](../dotnet/list-difference-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[list::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)|容器的泛型介面型別。|  
|[list::generic_iterator (STL/CLR)](../dotnet/list-generic-iterator-stl-clr.md)|泛型介面，該容器的迭代器類型。|  
|[list::generic_reverse_iterator (STL/CLR)](../dotnet/list-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器類型。|  
|[list::generic_value (STL/CLR)](../dotnet/list-generic-value-stl-clr.md)|泛型介面的容器項目的類型。|  
|[list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[list::reference (STL/CLR)](../dotnet/list-reference-stl-clr.md)|項目的參考類型。|  
|[list::reverse_iterator (STL/CLR)](../dotnet/list-reverse-iterator-stl-clr.md)|受控制序列的反向迭代器類型。|  
|[list::size_type (STL/CLR)](../dotnet/list-size-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[list::value_type (STL/CLR)](../dotnet/list-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)|取代所有項目。|  
|[list::back (STL/CLR)](../dotnet/list-back-stl-clr.md)|存取最後一個項目。|  
|[list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[list::clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)|移除所有項目。|  
|[list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)|測試項目是否不存在。|  
|[list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)|指定受控制序列的結尾。|  
|[list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)|移除位於指定位置的項目。|  
|[list::front (STL/CLR)](../dotnet/list-front-stl-clr.md)|存取第一個項目。|  
|[list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)|將項目加入指定的位置。|  
|[list::list (STL/CLR)](../dotnet/list-list-stl-clr.md)|建構容器物件。|  
|[list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)|合併兩個受控制的序列的已排序。|  
|[list::pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)|移除最後一個項目。|  
|[list::pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)|移除第一個項目。|  
|[list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)|加入新的最後一個項目。|  
|[list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)|加入新的第一個項目。|  
|[list::rbegin (STL/CLR)](../dotnet/list-rbegin-stl-clr.md)|指定反向受控制序列的開頭。|  
|[list::remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)|移除具有指定值的項目。|  
|[list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)|移除通過指定的測試的項目。|  
|[list::rend (STL/CLR)](../dotnet/list-rend-stl-clr.md)|指定反向受控制序列的結尾。|  
|[list::resize (STL/CLR)](../dotnet/list-resize-stl-clr.md)|變更項目數目。|  
|[list::reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)|反轉受控制的序列。|  
|[list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)|計算元素的數目。|  
|[list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)|受控制的序列的訂單。|  
|[list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)|重新拼接節點之間的連結。|  
|[list::swap (STL/CLR)](../dotnet/list-swap-stl-clr.md)|交換兩個容器的內容。|  
|[list::to_array (STL/CLR)](../dotnet/list-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
|[list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)|移除通過指定測試的相鄰項目。|  
  
|屬性|描述|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](../dotnet/list-back-item-stl-clr.md)|存取最後一個項目。|  
|[list::front_item (STL/CLR)](../dotnet/list-front-item-stl-clr.md)|存取第一個項目。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)|取代受控制的序列。|  
|[operator!= (list) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)|決定如果`list`物件是否不等於另一個`list`物件。|  
|[operator< (list) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)|決定如果`list`物件是否小於另一個`list`物件。|  
|[operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)|決定如果`list`物件是否小於或等於另一個`list`物件。|  
|[operator== (list) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)|決定如果`list`物件是否等於另一個`list`物件。|  
|[operator> (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)|決定如果`list`物件是否大於另一個`list`物件。|  
|[operator>= (list) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|決定如果`list`物件是否大於或等於另一個`list`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|項目順序。|  
|<xref:System.Collections.ICollection>|維護群組的項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目順序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|IList\<值 >|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放它為雙向連結清單中的個別節點所控制的序列的儲存體。 它會改變節點，而非由複製到另一個節點的內容之間的連結，重新排列項目。 這表示您可以插入和移除項目，自由地不干擾其餘項目。 因此，清單是適合做為基礎的容器樣板類別[佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)或樣板類別[堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 A`list`物件支援雙向迭代器，這表示您可以逐步執行至指定的迭代器，指定受控制序列中的項目相鄰的項目。 特殊的前端節點對應至所傳回的迭代器[list:: end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`。 如果有的話，可以減少此連線到受控制序列中，最後一個元素的迭代器。 您可以遞增到前端節點的清單迭代器，然後它會比較等於`end()`。 您無法取值 （dereference） 所傳回的迭代器，但`end()`。  
  
 請注意，您不能直接提供其數值位置-需要的隨機存取迭代器的清單項目參考。 清單是`not`可用做為基礎容器樣板類別[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 清單的迭代器會儲存其相關的清單 節點，接著會儲存到其相關聯的容器的控制代碼的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 只要其相關的清單節點是與一些清單相關聯的清單迭代器會保持有效。 此外，有效的迭代器是 dereferencable--您可用它來存取或修改項目值，它會指定-，只要不等於`end()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼，並會`not`摧毀其項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)