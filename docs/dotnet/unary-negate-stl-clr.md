---
title: unary_negate (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::unary_negate
dev_langs:
- C++
helpviewer_keywords:
- unary_negate function [STL/CLR]
ms.assetid: 83bbdd86-199c-4451-9f70-72f9ade2264a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 70ce2872e3e941df11402ccde0cb7a94b132b51c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169445"
---
# <a name="unarynegate-stlclr"></a>unary_negate (STL/CLR)
此範本類別描述函式，呼叫時，會傳回邏輯不屬於其預存的單一引數函式。 您可以使用它指定根據其預存函式的函式物件。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>參數  
 Fun  
 預存仿函式的類型。  
  
## <a name="member-functions"></a>成員函式  
  
|類型定義|描述|  
|---------------------|-----------------|  
|argument_type|仿函式引數的型別。|  
|delegate_type|泛型委派類型。|  
|result_type|仿函式結果的型別。|  
  
|成員|描述|  
|------------|-----------------|  
|unary_negate|建構仿函式。|  
  
|運算子|描述|  
|--------------|-----------------|  
|operator()|計算所需的函數。|  
|delegate_type ^|會轉換成委派仿函式。|  
  
## <a name="remarks"></a>備註  
 此範本類別描述一個引數函式儲存其他單一引數函式。 它會定義此成員運算子`operator()`使物件做為函式呼叫時，它會傳回邏輯的預存仿函式不使用引數呼叫。  
  
 您也可以傳遞物件做為函式引數的型別`delegate_type^`並會適當地加以轉換。  
  
## <a name="example"></a>範例  
  
```  
// cliext_unary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
1 0  
1 0  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<功能 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [not1 (STL/CLR)](../dotnet/not1-stl-clr.md)