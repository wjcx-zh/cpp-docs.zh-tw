---
title: "logical_or (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::logical_or
dev_langs:
- C++
helpviewer_keywords:
- logical_or function [STL/CLR]
ms.assetid: 3b5eac9b-4aaf-4395-8d76-49100487d85a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7d80fd86c0426d54a803c3111911f284507bcb11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="logicalor-stlclr"></a>logical_or (STL/CLR)
此範本類別描述函式，呼叫時，則傳回 true 的第一個引數或第二個測試，做為 true 時，才。 您可以使用它指定其引數類型方面的函式物件。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Arg>  
    ref class logical_or  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    logical_or();  
    logical_or(logical_or<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>參數  
 引數  
 引數的型別。  
  
## <a name="member-functions"></a>成員函式  
  
|類型定義|描述|  
|---------------------|-----------------|  
|delegate_type|泛型委派類型。|  
|first_argument_type|仿函式的第一個引數型別。|  
|result_type|仿函式結果的型別。|  
|second_argument_type|仿函式的第二個引數的型別。|  
  
|成員|描述|  
|------------|-----------------|  
|logical_or|建構仿函式。|  
  
|運算子|描述|  
|--------------|-----------------|  
|operator()|計算所需的函數。|  
|運算子 delegate_type ^|會轉換成委派仿函式。|  
  
## <a name="remarks"></a>備註  
 此範本類別描述兩個引數函式。 它會定義此成員運算子`operator()`使物件做為函式呼叫時，它只會傳回 true 的第一個引數或做為第二個測試為 true。  
  
 您也可以傳遞物件做為函式引數的型別`delegate_type^`並會適當地加以轉換。  
  
## <a name="example"></a>範例  
  
```  
// cliext_logical_or.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(2);   
    c1.push_back(0);   
    Myvector c2;   
    c2.push_back(0);   
    c2.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 2 0" and " 0 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::logical_or<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
2 0  
0 0  
1 0  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<功能 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [logical_and (STL/CLR)](../dotnet/logical-and-stl-clr.md)