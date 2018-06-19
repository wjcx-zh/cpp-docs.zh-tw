---
title: make_pair (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::make_pair
dev_langs:
- C++
helpviewer_keywords:
- make_pair function [STL/CLR]
ms.assetid: 74733f2c-97b0-4d69-b431-5ab8f0de9e3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 99e2cc7bc7255940b28f2f85dae1a7cbebd6df46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33134984"
---
# <a name="makepair-stlclr"></a>make_pair (STL/CLR)
請`pair`從一組值。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### <a name="parameters"></a>參數  
 `Value1`  
 第一個包裝的值類型。  
  
 `Value2`  
 第二個包裝值類型。  
  
 `first`  
 要包裝的第一個值。  
  
 `second`  
 第二個換行的值。  
  
## <a name="remarks"></a>備註  
 此範本函式會傳回 `pair<Value1, Value2>(first, second)`。 使用它來建構`pair<Value1, Value2>`從一組值的物件。  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[y, 4]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/公用程式 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)