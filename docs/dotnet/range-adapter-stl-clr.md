---
title: range_adapter (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- range_adapter class [STL/CLR]
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a5b8a02856d7739867e3cf9f76f866a1e84efca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="rangeadapter-stlclr"></a>range_adapter (STL/CLR)
樣板類別，包裝一組迭代器，可用來實作數個基底類別程式庫 (BCL) 介面。 您可以使用 range_adapter 來操作 STL/CLR 範圍，就好像 BCL 集合。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>參數  
 iter  
 對已包裝的迭代器相關聯的類型。  
  
## <a name="members"></a>成員  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](../dotnet/range-adapter-range-adapter-stl-clr.md)|建構的配置器物件。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](../dotnet/range-adapter-operator-assign-stl-clr.md)|取代預存迭代器組。|  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|逐一查看集合中的項目。|  
|<xref:System.Collections.ICollection>|會維護一組項目。|  
|<xref:System.Collections.Generic.IEnumerable%601>|逐一查看集合中具類型的項目...|  
|<xref:System.Collections.Generic.ICollection%601>|會維護一組具類型的項目。|  
  
## <a name="remarks"></a>備註  
 Range_adapter 儲存一組的迭代器，依序分隔的項目序列。 物件會實作四個 BCL 介面，可讓您逐一查看項目，依序。 您可以使用此範本類別來操作非常類似 BCL 容器 STL/CLR 範圍。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<配接器 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)