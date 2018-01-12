---
title: "collection_adapter (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::collection_adapter
dev_langs: C++
helpviewer_keywords: collection_adapter class [STL/CLR]
ms.assetid: 31964058-1f50-48bf-82c2-b0b3cc8a7887
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a1a03dd6ecc52cd3921428e681fe5affa11d275
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="collectionadapter-stlclr"></a>collection_adapter (STL/CLR)
包裝 STL/CLR 容器做為.NET 集合。 A`collection_adapter`是範本類別描述一個簡單的 STL/CLR 容器物件。 它會包裝基底類別程式庫 (BCL) 介面，並傳回您用於管理受控制的序列的迭代器配對。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
#### <a name="parameters"></a>參數  
 Coll  
 已包裝的集合型別。  
  
## <a name="specializations"></a>特製化  
  
|特製化|描述|  
|--------------------|-----------------|  
|IEnumerable|項目序列。|  
|ICollection|會維護一組項目。|  
|IList|會維護排序的群組的項目。|  
|IDictionary|維護一組 {索引鍵值} 的配對。|  
|IEnumerable\<值 >|透過具類型的項目序列。|  
|ICollection\<值 >|會維護一組具類型的項目。|  
|IList\<值 >|會維護排序的群組的具類型的項目。|  
|IDictionary\<值 >|會維護一組型別 {索引鍵的值} 配對。|  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](../dotnet/collection-adapter-difference-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[collection_adapter::iterator (STL/CLR)](../dotnet/collection-adapter-iterator-stl-clr.md)|受控制序列之迭代器的類型。|  
|[collection_adapter::key_type (STL/CLR)](../dotnet/collection-adapter-key-type-stl-clr.md)|字典索引鍵的類型。|  
|[collection_adapter::mapped_type (STL/CLR)](../dotnet/collection-adapter-mapped-type-stl-clr.md)|字典值的型別。|  
|[collection_adapter::reference (STL/CLR)](../dotnet/collection-adapter-reference-stl-clr.md)|項目的參考類型。|  
|[collection_adapter::size_type (STL/CLR)](../dotnet/collection-adapter-size-type-stl-clr.md)|兩個項目之間帶正負號距離的類型。|  
|[collection_adapter::value_type (STL/CLR)](../dotnet/collection-adapter-value-type-stl-clr.md)|元素的類型。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)|將指定的已包裝的 BCL 介面。|  
|[collection_adapter::begin (STL/CLR)](../dotnet/collection-adapter-begin-stl-clr.md)|指定受控制序列的開頭。|  
|[collection_adapter::collection_adapter (STL/CLR)](../dotnet/collection-adapter-collection-adapter-stl-clr.md)|建構的配置器物件。|  
|[collection_adapter::end (STL/CLR)](../dotnet/collection-adapter-end-stl-clr.md)|指定受控制序列的結尾。|  
|[collection_adapter::size (STL/CLR)](../dotnet/collection-adapter-size-stl-clr.md)|計算元素的數目。|  
|[collection_adapter::swap (STL/CLR)](../dotnet/collection-adapter-swap-stl-clr.md)|交換兩個容器的內容。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](../dotnet/collection-adapter-operator-assign-stl-clr.md)|取代預存的 BCL 控制代碼。|  
  
## <a name="remarks"></a>備註  
 您可以使用此範本類別來操作 BCL 容器做為 STL/CLR 容器。 `collection_adapter`儲存 BCL 介面，其接著控制項的項目序列的控制代碼。 A`collection_adapter`物件`X`會傳回輸入迭代器的一組`X.begin()`和`X.end()`您瀏覽項目，依序使用。 部分特製化也可讓您撰寫`X.size()`來決定受控制序列的長度。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<配接器 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)   
 [make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)