---
title: 佇列 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::queue
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d5b91a2556a93f3cd74a24ea57306d70f2cbdb41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="queue-stlclr"></a>queue (STL/CLR)
此範本類別描述控制不同長度序列的項目具有先進存取的物件。 您可以使用容器配接器`queue`管理為佇列基礎容器。  
  
 在以下描述`GValue`相同`Value`後者是 ref 型別，除非在這種情況下很`Value^`。 同樣地，`GContainer`相同`Container`後者是 ref 型別，除非在這種情況下很`Container^`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
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
|[queue::const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[queue::container_type (STL/CLR)](../dotnet/queue-container-type-stl-clr.md)|基礎容器的類型。|  
|[queue::difference_type (STL/CLR)](../dotnet/queue-difference-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)|容器配接器的泛型介面的型別。|  
|[queue::generic_value (STL/CLR)](../dotnet/queue-generic-value-stl-clr.md)|容器配接器的泛型介面的項目類型。|  
|[queue::reference (STL/CLR)](../dotnet/queue-reference-stl-clr.md)|項目的參考類型。|  
|[queue::size_type (STL/CLR)](../dotnet/queue-size-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)|取代所有項目。|  
|[queue::back (STL/CLR)](../dotnet/queue-back-stl-clr.md)|存取最後一個項目。|  
|[queue::empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)|測試項目是否不存在。|  
|[queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)|存取第一個項目。|  
|[queue::get_container (STL/CLR)](../dotnet/queue-get-container-stl-clr.md)|存取基礎容器。|  
|[queue::pop (STL/CLR)](../dotnet/queue-pop-stl-clr.md)|移除第一個項目。|  
|[queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)|加入新的最後一個項目。|  
|[queue::queue (STL/CLR)](../dotnet/queue-queue-stl-clr.md)|建構容器物件。|  
|[queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md)|計算元素的數目。|  
|[queue::to_array (STL/CLR)](../dotnet/queue-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
  
|屬性|描述|  
|--------------|-----------------|  
|[queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)|存取最後一個項目。|  
|[queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)|存取第一個項目。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)|取代受控制的序列。|  
|[operator!= (queue) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)|決定如果`queue`物件是否不等於另一個`queue`物件。|  
|[operator< (queue) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)|決定如果`queue`物件是否小於另一個`queue`物件。|  
|[operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|決定如果`queue`物件是否小於或等於另一個`queue`物件。|  
|[operator== (queue) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)|決定如果`queue`物件是否等於另一個`queue`物件。|  
|[operator> (queue) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)|決定如果`queue`物件是否大於另一個`queue`物件。|  
|[operator>= (queue) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|決定如果`queue`物件是否大於或等於另一個`queue`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|IQueue\<值、 容器 >|維護泛型容器配接器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放的序列型別的基礎容器中，透過它所控制的儲存體`Container`，其中存放`Value`項目，而且視成長。 物件會限制存取只按第一個項目並取出最後一個項目，實作先進先出佇列 （也稱為 FIFO 佇列中或只是佇列）。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)