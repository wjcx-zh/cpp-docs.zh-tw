---
title: 'list:: sort (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::sort
dev_langs:
- C++
helpviewer_keywords:
- sort member [STL/CLR]
ms.assetid: f811d5f4-a19e-4194-8765-1e68097c52f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 670b18e5901ef264474256a1a1e57cde7a28ef01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138340"
---
# <a name="listsort-stlclr"></a>list::sort (STL/CLR)
受控制的序列的訂單。  
  
## <a name="syntax"></a>語法  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>參數  
 pred  
 項目配對的比較子。  
  
## <a name="remarks"></a>備註  
 第一個成員函式重新排列受控制序列中的項目，以便依排序`operator<`-項目不要降低在值隨著您循序完成進度。 您可以使用此成員函式來排序的順序，以遞增的順序。  
  
 第二個成員函式的行為與第一個相同之處在於會依據排序順序`pred`  --  `pred(X, Y)`為 false 的任何項目`X`的項目後面`Y`結果的順序。 您可以使用它來排序的順序，您指定的述詞函式或委派中的順序。  
  
 同時函式會執行穩定的排序--在原始的受控制序列中的項目沒有任何一對已反轉結果的受控制序列中。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
c b a  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)   
 [list:: reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)   
 [list:: splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)   
 [list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)