---
title: "數值 (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: <cliext/numeric>
dev_langs: C++
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cdf9ccb65299af688fde2fbff7b3d6cedad6de96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)
定義容器樣板函式執行數值處理提供的演算法。  
  
## <a name="syntax"></a>語法  
  
```  
#include <cliext/numeric>  
```  
  
## <a name="functions"></a>函式  
  
|功能|描述|  
|--------------|-----------------|  
|[accumulate (STL/CLR)](../dotnet/accumulate-stl-clr.md)|藉由計算連續的部分總和來計算指定範圍內所有元素 (包括某個初始值) 的總和，或是計算連續部分結果 (同樣是使用指定的二進位運算而非加總來計算出) 的結果。|  
|[adjacent_difference (STL/CLR)](../dotnet/adjacent-difference-stl-clr.md)|計算在輸入範圍中每個項目及其前置項之間的後續差異並將結果輸出至目的範圍，或計算一般化程序的結果，其中由另一個指定的二進位運算取代差異作業。|  
|[inner_product (STL/CLR)](../dotnet/inner-product-stl-clr.md)|計算兩個範圍的元素乘積總和並將它加到指定的初始值，或計算一般化程序的結果，其中總和及乘積二進位運算會由其他指定的二進位運算取代。|  
|[partial_sum (STL/CLR)](../dotnet/partial-sum-stl-clr.md)|計算一系列中的第一個項目，透過輸入範圍內的總和`i`th 項目，並將每個總和的結果`i`個元素的目的範圍，或計算一般化程序的結果，其中總和運算由另一個指定的二進位運算取代。|  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/數字 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [STL/CLR 程式庫參考](../dotnet/stl-clr-library-reference.md)