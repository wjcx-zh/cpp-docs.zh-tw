---
title: "less_equal (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::less_equal
dev_langs: C++
helpviewer_keywords: less_equal function [STL/CLR]
ms.assetid: 87d5bebc-6e5a-4d70-b15c-7260d06d50f0
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f0ecc202e1a83f0f32b0febef488bb1979cccb86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="lessequal-stlclr"></a>less_equal (STL/CLR)
此範本類別描述函式，呼叫時，只會傳回 true 的第一個參數是否小於或等於第二個。 您可以使用它指定其引數類型方面的函式物件。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Arg>  
    ref class less_equal  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    less_equal();  
    less_equal(less_equal<Arg>% right);  
  
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
|less_equal|建構仿函式。|  
  
|運算子|描述|  
|--------------|-----------------|  
|operator()|計算所需的函數。|  
|運算子 delegate_type ^|會轉換成委派仿函式。|  
  
## <a name="remarks"></a>備註  
 此範本類別描述兩個引數函式。 它會定義此成員運算子`operator()`使物件做為函式呼叫時，它只會傳回 true 的第一個參數是否小於或等於第二個。  
  
 您也可以傳遞物件做為函式引數的型別`delegate_type^`並會適當地加以轉換。  
  
## <a name="example"></a>範例  
  
```  
// cliext_less_equal.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(3);   
    c2.push_back(3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 3 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::less_equal<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
3 3  
0 1  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<功能 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [greater (STL/CLR)](../dotnet/greater-stl-clr.md)