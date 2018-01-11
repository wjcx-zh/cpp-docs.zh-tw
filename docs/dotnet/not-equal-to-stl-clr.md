---
title: "not_equal_to (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::not_equal_to
dev_langs: C++
helpviewer_keywords: not_equal_to function [STL/CLR]
ms.assetid: 1b66e0ca-eace-4672-8da9-ed16f8608bca
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ae79c521f7edcc055ec6eee5907a6102ebf26134
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="notequalto-stlclr"></a>not_equal_to (STL/CLR)
此範本類別描述函式，呼叫時，則傳回 true 只有第一個引數不是等於第二個。 您可以使用它指定其引數類型方面的函式物件。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Arg>  
    ref class not_equal_to  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    not_equal_to();  
    not_equal_to(not_equal_to<Arg>% right);  
  
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
|not_equal_to|建構仿函式。|  
  
|運算子|描述|  
|--------------|-----------------|  
|operator()|計算所需的函數。|  
|運算子 delegate_type ^|會轉換成委派仿函式。|  
  
## <a name="remarks"></a>備註  
 此範本類別描述兩個引數函式。 它會定義此成員運算子`operator()`使物件做為函式呼叫時，它只會傳回 true 的第一個引數是否不等於第二個。  
  
 您也可以傳遞物件做為函式引數的型別`delegate_type^`並會適當地加以轉換。  
  
## <a name="example"></a>範例  
  
```  
// cliext_not_equal_to.cpp   
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
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 3  
4 4  
0 1  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<功能 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [equal_to (STL/CLR)](../dotnet/equal-to-stl-clr.md)