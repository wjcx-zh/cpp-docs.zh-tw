---
title: "priority_queue (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue
dev_langs: C++
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7d1459da07f7e392a2da1fbf5d6e9d72c8f4653
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
此範本類別描述控制不同長度排序項目序列的有限存取的物件。 您可以使用容器配接器`priority_queue`來管理其優先順序佇列為基礎容器。  
  
 在以下描述`GValue`相同`Value`後者是 ref 型別，除非在這種情況下很`Value^`。 同樣地，`GContainer`相同`Container`後者是 ref 型別，除非在這種情況下很`Container^`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### <a name="parameters"></a>參數  
 值  
 受控制序列中項目的類型。  
  
 容器  
 基礎容器的類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[priority_queue::const_reference (STL/CLR)](../dotnet/priority-queue-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[priority_queue::container_type (STL/CLR)](../dotnet/priority-queue-container-type-stl-clr.md)|基礎容器的類型。|  
|[priority_queue::difference_type (STL/CLR)](../dotnet/priority-queue-difference-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)|容器配接器的泛型介面的型別。|  
|[priority_queue::generic_value (STL/CLR)](../dotnet/priority-queue-generic-value-stl-clr.md)|容器配接器的泛型介面的項目類型。|  
|[priority_queue::reference (STL/CLR)](../dotnet/priority-queue-reference-stl-clr.md)|項目的參考類型。|  
|[priority_queue::size_type (STL/CLR)](../dotnet/priority-queue-size-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)|兩個項目順序的委派。|  
|[priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[priority_queue::assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)|取代所有項目。|  
|[priority_queue::empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)|測試項目是否不存在。|  
|[priority_queue::get_container (STL/CLR)](../dotnet/priority-queue-get-container-stl-clr.md)|存取基礎容器。|  
|[priority_queue::pop (STL/CLR)](../dotnet/priority-queue-pop-stl-clr.md)|移除 hghest 優先權項目。|  
|[priority_queue::priority_queue (STL/CLR)](../dotnet/priority-queue-priority-queue-stl-clr.md)|建構容器物件。|  
|[priority_queue::push (STL/CLR)](../dotnet/priority-queue-push-stl-clr.md)|加入新項目。|  
|[priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)|計算元素的數目。|  
|[priority_queue::top (STL/CLR)](../dotnet/priority-queue-top-stl-clr.md)|存取最高優先權項目。|  
|[priority_queue::to_array (STL/CLR)](../dotnet/priority-queue-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
|[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)|將複製兩個項目順序的委派。|  
  
|屬性|描述|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](../dotnet/priority-queue-top-item-stl-clr.md)|存取最高優先權項目。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)|取代受控制的序列。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|IPriorityQueue\<值、 容器 >|維護泛型容器配接器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放的序列型別的基礎容器中，透過它所控制的儲存體`Container`，其中存放`Value`項目，而且視成長。 它會保留為堆積，與最高優先權項目 （最上層元素） 準備好可存取，並卸除式排序順序。 物件會限制存取推入新的項目並取出只的最高優先權項目，實作優先權佇列。  
  
 物件，排序它藉由呼叫預存的委派類型的物件所控制的序列[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)。 當您建構 priority_queue; 時，您可以指定預存的委派物件如果您指定沒有委派的物件時，預設值是比較`operator<(value_type, value_type)`。 您藉由呼叫成員函式中存取這個預存的物件[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`。  
  
 這類委派的物件必須強制執行嚴格弱式排序類型的值[priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)。 這表示任何兩個索引鍵`X`和`Y`:  
  
 `value_comp()(X, Y)`傳回的相同的布林值結果，在每次呼叫。  
  
 如果`value_comp()(X, Y)`是 true，則`value_comp()(Y, X)`必須為 false。  
  
 如果`value_comp()(X, Y)`是 true，則`X`稱為排序之前`Y`。  
  
 如果`!value_comp()(X, Y) && !value_comp()(Y, X)`是 true，則`X`和`Y`被視為具有對等順序。  
  
 對於任何項目`X`前面`Y`受控制序列中`key_comp()(Y, X)`為 false。 （預設委派物件索引鍵永遠不會減少值中。）  
  
 最高優先順序項目，因此是其中一個元素的任何其他項目之前未經過排序。  
  
 因為基礎容器會保留為堆積排序的項目：  
  
 容器必須支援隨機存取迭代器。  
  
 可能會以不同的順序彈出具有對等順序的項目，比它們推入。 （順序不穩定。）  
  
 因此，基礎容器的候選項目包含[deque (STL/CLR)](../dotnet/deque-stl-clr.md)和[向量 (STL/CLR)](../dotnet/vector-stl-clr.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)