---
title: "配對 (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::pair
dev_langs: C++
helpviewer_keywords: pair class [STL/CLR]
ms.assetid: 3326b4d9-a52a-49e5-8103-9aa5e8b352de
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a8c4ae8ee9fbcfddd6009d4e91134d59a9a02cc9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pair-stlclr"></a>pair (STL/CLR)
此範本類別描述包裝一組值的物件。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    ref class pair;  
```  
  
#### <a name="parameters"></a>參數  
 Value1  
 第一個包裝值類型。  
  
 Value2  
 第二個換行的值類型。  
  
## <a name="members"></a>成員  
  
|類型定義|描述|  
|---------------------|-----------------|  
|[pair::first_type (STL/CLR)](../dotnet/pair-first-type-stl-clr.md)|第一個包裝的值類型。|  
|[pair::second_type (STL/CLR)](../dotnet/pair-second-type-stl-clr.md)|第二個包裝值類型。|  
  
|成員物件|描述|  
|-------------------|-----------------|  
|[pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)|第一個預存的值。|  
|[pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)|第二個儲存的值。|  
  
|成員函式|描述|  
|---------------------|-----------------|  
|[pair::pair (STL/CLR)](../dotnet/pair-pair-stl-clr.md)|建構組物件。|  
|[pair::swap (STL/CLR)](../dotnet/pair-swap-stl-clr.md)|交換兩對的內容。|  
  
|運算子|描述|  
|--------------|-----------------|  
|[pair::operator= (STL/CLR)](../dotnet/pair-operator-assign-stl-clr.md)|取代預存的值的配對。|  
  
## <a name="remarks"></a>備註  
 此物件會儲存一組值。 您可以使用此範本類別，將兩個值結合成單一物件。 請注意， `cliext::pair` （此處所述） 存放區僅限受管理類型; 若要儲存對 unmanaged 的類型使用`std::pair`中宣告`<utility>`。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/公用程式 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [make_pair (STL/CLR)](../dotnet/make-pair-stl-clr.md)