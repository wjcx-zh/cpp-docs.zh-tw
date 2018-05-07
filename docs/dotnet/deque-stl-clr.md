---
title: deque (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque
dev_langs:
- C++
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 11436466dadf4b06e604af6e2b5150a22c4ed241
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="deque-stlclr"></a>deque (STL/CLR)
此範本類別描述控制不同長度序列的項目具有隨機存取的物件。 使用容器`deque`管理序列的項目看起來像連續區塊存放裝置，但它可以擴張或縮小任一端而不需要複製任何剩餘的項目。 因此它可以有效實作`double-ended queue`。 (因此名稱。)  
  
 在以下描述`GValue`相同`Value`後者是 ref 型別，除非在這種情況下很`Value^`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    ref class deque  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IDeque<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>參數  
 GValue  
 受控制序列中項目的一般類型。  
  
 值  
 受控制序列中項目的類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[deque::const_iterator (STL/CLR)](../dotnet/deque-const-iterator-stl-clr.md)|用於受控制序列的常數迭代器類型。|  
|[deque::const_reference (STL/CLR)](../dotnet/deque-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[deque::const_reverse_iterator (STL/CLR)](../dotnet/deque-const-reverse-iterator-stl-clr.md)|用於受控制序列的常數反向迭代器類型。|  
|[deque::difference_type (STL/CLR)](../dotnet/deque-difference-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)|容器的泛型介面型別。|  
|[deque::generic_iterator (STL/CLR)](../dotnet/deque-generic-iterator-stl-clr.md)|泛型介面，該容器的迭代器類型。|  
|[deque::generic_reverse_iterator (STL/CLR)](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|容器的泛型介面的反向迭代器類型。|  
|[deque::generic_value (STL/CLR)](../dotnet/deque-generic-value-stl-clr.md)|泛型介面的容器項目的類型。|  
|[deque::iterator (STL/CLR)](../dotnet/deque-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[deque::reference (STL/CLR)](../dotnet/deque-reference-stl-clr.md)|項目的參考類型。|  
|[deque::reverse_iterator (STL/CLR)](../dotnet/deque-reverse-iterator-stl-clr.md)|受控制序列的反向迭代器類型。|  
|[deque::size_type (STL/CLR)](../dotnet/deque-size-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[deque::value_type (STL/CLR)](../dotnet/deque-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)|取代所有項目。|  
|[deque::at (STL/CLR)](../dotnet/deque-at-stl-clr.md)|存取指定位置的項目。|  
|[deque::back (STL/CLR)](../dotnet/deque-back-stl-clr.md)|存取最後一個項目。|  
|[deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[deque::clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)|移除所有項目。|  
|[deque::deque (STL/CLR)](../dotnet/deque-deque-stl-clr.md)|建構容器物件。|  
|[deque::empty (STL/CLR)](../dotnet/deque-empty-stl-clr.md)|測試項目是否不存在。|  
|[deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md)|指定受控制序列的結尾。|  
|[deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)|移除位於指定位置的項目。|  
|[deque::front (STL/CLR)](../dotnet/deque-front-stl-clr.md)|存取第一個項目。|  
|[deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)|將項目加入指定的位置。|  
|[deque::pop_back (STL/CLR)](../dotnet/deque-pop-back-stl-clr.md)|移除最後一個項目。|  
|[deque::pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)|移除第一個項目。|  
|[deque::push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)|加入新的最後一個項目。|  
|[deque::push_front (STL/CLR)](../dotnet/deque-push-front-stl-clr.md)|加入新的第一個項目。|  
|[deque::rbegin (STL/CLR)](../dotnet/deque-rbegin-stl-clr.md)|指定反向受控制序列的開頭。|  
|[deque::rend (STL/CLR)](../dotnet/deque-rend-stl-clr.md)|指定反向受控制序列的結尾。|  
|[deque::resize (STL/CLR)](../dotnet/deque-resize-stl-clr.md)|變更項目數目。|  
|[deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md)|計算元素的數目。|  
|[deque::swap (STL/CLR)](../dotnet/deque-swap-stl-clr.md)|交換兩個容器的內容。|  
|[deque::to_array (STL/CLR)](../dotnet/deque-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
  
|屬性|描述|  
|--------------|-----------------|  
|[deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)|存取最後一個項目。|  
|[deque::front_item (STL/CLR)](../dotnet/deque-front-item-stl-clr.md)|存取第一個項目。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[deque::operator!= (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)|判斷兩個`deque`物件不相等。|  
|[deque::operator (STL/CLR)](../dotnet/deque-operator-stl-clr.md)|存取指定位置的項目。|  
|[operator< (deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)|決定如果`deque`物件是否小於另一個`deque`物件。|  
|[operator<= (deque) (STL/CLR)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|決定如果`deque`物件是否小於或等於另一個`deque`物件。|  
|[operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)|取代受控制的序列。|  
|[operator== (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)|決定如果`deque`物件是否等於另一個`deque`物件。|  
|[operator> (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)|決定如果`deque`物件是否大於另一個`deque`物件。|  
|[operator>= (deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|決定如果`deque`物件是否大於或等於另一個`deque`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|<xref:System.Collections.IEnumerable>|項目順序。|  
|<xref:System.Collections.ICollection>|維護群組的項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|透過具類型的項目順序。|  
|<xref:System.Collections.Generic.ICollection%601>|維護群組的具類型的項目。|  
|<xref:System.Collections.Generic.IList%601>|維護已排序的群組的具類型的項目。|  
|IDeque < 值\>|維護泛型容器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放控制代碼指定的區塊之預存陣列透過它所控制的序列的儲存體`Value`項目。 視會逐漸增加的陣列。 成長，就會發生得前面加上或附加新項目成本是固定的時間，而且會干擾沒有剩餘的項目。 您也可以移除任一端的項目以常數時間，而不干擾其餘項目。 因此，deque 是適合做為基礎的容器樣板類別[佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)或樣板類別[堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 A`deque`物件支援隨機存取迭代器，這表示您可以參考項目直接指定其數值位置，從零的第一個 （前端） 項目計數來[deque:: size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() - 1`（回復） 的最後一個項目。 這也表示 deque 是適合做為基礎的容器樣板類別[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 Deque 的迭代器會儲存其相關聯的 deque 物件，以及它所指定的項目偏差的控制代碼。 您可以使用迭代器，只能使用其相關聯的容器物件。 Deque 的項目偏差是`not`一定是相同的位置。 第一個項目插入具有偏差零、 下一個附加的項目偏差 1，但下一個預留的項目有偏差-1。  
  
 插入或清除任一端的項目會`not`更改的項目儲存在任何有效的偏差值。 插入或刪除一個內部項目，不過，`can`變更儲存在指定的偏差，所以由迭代器指定的值也可以變更的項目值。 （若要複製項目向上或向下建立一個洞之前插入或用來填入暴露在清除之後可能有容器）。不過，deque 的迭代器會保持有效，只要其偏差指定有效的項目。 此外，有效的迭代器會維持 dereferencable-您可用它來存取或修改項目值，它會指定-，只要其偏差值不等於所傳回的迭代器的偏差`end()`。  
  
 清除，或移除項目會呼叫解構函式的儲存值。 終結容器清除所有項目。 因此，其項目類型是 ref 類別的容器可確保，任何項目存留期比長容器。 不過請注意，容器的控制代碼，並會`not`摧毀其項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/deque >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)