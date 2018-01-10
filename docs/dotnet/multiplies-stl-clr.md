---
title: "乘以 (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multiplies
dev_langs: C++
helpviewer_keywords: multiplies function [STL/CLR]
ms.assetid: 76d23149-789a-48a1-89f8-9103df82a1df
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1012997408f108192425a4a7c127baa873b34795
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multiplies-stlclr"></a>multiplies (STL/CLR)
此範本類別描述函式，呼叫時，會傳回第一個引數，第二個時間。 您可以使用它指定其引數類型方面的函式物件。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Arg>  
    ref class multiplies  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    multiplies();  
    multiplies(multiplies<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>參數  
 引數  
 引數和傳回值的類型。  
  
## <a name="member-functions"></a>成員函式  
  
|類型定義|描述|  
|---------------------|-----------------|  
|delegate_type|泛型委派類型。|  
|first_argument_type|仿函式的第一個引數型別。|  
|result_type|仿函式結果的型別。|  
|second_argument_type|仿函式的第二個引數的型別。|  
  
|成員|描述|  
|------------|-----------------|  
|multiplies|建構仿函式。|  
  
|運算子|描述|  
|--------------|-----------------|  
|operator()|計算所需的函數。|  
|運算子 delegate_type ^|會轉換成委派仿函式。|  
  
## <a name="remarks"></a>備註  
 此範本類別描述兩個引數函式。 它會定義此成員運算子`operator()`使物件做為函式呼叫時，它會傳回第一個引數，第二個時間。  
  
 您也可以傳遞物件做為函式引數的型別`delegate_type^`並會適當地加以轉換。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiplies.cpp   
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
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::multiplies<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
2 1  
8 3  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<功能 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [將分割 (STL/CLR)](../dotnet/divides-stl-clr.md)   
 [modulus (STL/CLR)](../dotnet/modulus-stl-clr.md)