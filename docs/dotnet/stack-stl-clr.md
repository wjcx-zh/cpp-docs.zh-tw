---
title: 堆疊 (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack
dev_langs:
- C++
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 290857b51fea6726ec7e4a836d4afe1b33a8e615
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172440"
---
# <a name="stack-stlclr"></a>stack (STL/CLR)
此範本類別描述控制不同長度序列的項目可存取後進先出的物件。 您可以使用容器配接器`stack`管理向下推送堆疊基礎容器。  
  
 在以下描述`GValue`相同`Value`後者是 ref 型別，除非在這種情況下很`Value^`。 同樣地，`GContainer`相同`Container`後者是 ref 型別，除非在這種情況下很`Container^`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
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
|[stack::const_reference (STL/CLR)](../dotnet/stack-const-reference-stl-clr.md)|項目的常數參考類型。|  
|[stack::container_type (STL/CLR)](../dotnet/stack-container-type-stl-clr.md)|基礎容器的類型。|  
|[stack::difference_type (STL/CLR)](../dotnet/stack-difference-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[stack::generic_container (STL/CLR)](../dotnet/stack-generic-container-stl-clr.md)|容器配接器的泛型介面的型別。|  
|[stack::generic_value (STL/CLR)](../dotnet/stack-generic-value-stl-clr.md)|容器配接器的泛型介面的項目類型。|  
|[stack::reference (STL/CLR)](../dotnet/stack-reference-stl-clr.md)|項目的參考類型。|  
|[stack::size_type (STL/CLR)](../dotnet/stack-size-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[stack::value_type (STL/CLR)](../dotnet/stack-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[stack::assign (STL/CLR)](../dotnet/stack-assign-stl-clr.md)|取代所有項目。|  
|[stack::empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)|測試項目是否不存在。|  
|[stack::get_container (STL/CLR)](../dotnet/stack-get-container-stl-clr.md)|存取基礎容器。|  
|[stack::pop (STL/CLR)](../dotnet/stack-pop-stl-clr.md)|移除最後一個項目。|  
|[stack::push (STL/CLR)](../dotnet/stack-push-stl-clr.md)|加入新的最後一個項目。|  
|[stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)|計算元素的數目。|  
|[stack::stack (STL/CLR)](../dotnet/stack-stack-stl-clr.md)|建構容器物件。|  
|[stack::top (STL/CLR)](../dotnet/stack-top-stl-clr.md)|存取最後一個項目。|  
|[stack::to_array (STL/CLR)](../dotnet/stack-to-array-stl-clr.md)|將受控制的序列複製到新的陣列。|  
  
|屬性|描述|  
|--------------|-----------------|  
|[stack::top_item (STL/CLR)](../dotnet/stack-top-item-stl-clr.md)|存取最後一個項目。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[stack::operator= (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)|取代受控制的序列。|  
|[operator!= (stack) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)|決定如果`stack`物件是否不等於另一個`stack`物件。|  
|[operator< (stack) (STL/CLR)](../dotnet/operator-less-than-stack-stl-clr.md)|決定如果`stack`物件是否小於另一個`stack`物件。|  
|[operator<= (stack) (STL/CLR)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|決定如果`stack`物件是否小於或等於另一個`stack`物件。|  
|[operator== (stack) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)|決定如果`stack`物件是否等於另一個`stack`物件。|  
|[operator> (stack) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)|決定如果`stack`物件是否大於另一個`stack`物件。|  
|[operator>= (stack) (STL/CLR)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|決定如果`stack`物件是否大於或等於另一個`stack`物件。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重複的物件。|  
|IStack\<值、 容器 >|維護泛型容器配接器。|  
  
## <a name="remarks"></a>備註  
 物件可配置及釋放的序列型別的基礎容器中，透過它所控制的儲存體`Container`，其中存放`Value`項目，而且視成長。 物件會限制存取推進和拉出剛才的最後一個元素，實作後進先出佇列 （也稱為 LIFO 佇列或堆疊）。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<堆疊 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)