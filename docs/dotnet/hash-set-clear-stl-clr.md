---
title: 'hash_set:: clear (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::clear
dev_langs:
- C++
helpviewer_keywords:
- clear member [STL/CLR]
ms.assetid: 9f38b72a-5db8-485a-b41a-7d47ac57f4a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d1280dd73c5175f670003d8f06d520bcb0657eb9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127366"
---
# <a name="hashsetclear-stlclr"></a>hash_set::clear (STL/CLR)
移除所有項目。  
  
## <a name="syntax"></a>語法  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>備註  
 成員函式可有效地呼叫[hash_set:: erase (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md) `(` [hash_set:: begin (STL/CLR)](../dotnet/hash-set-begin-stl-clr.md) `(),` [hash_set:: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`())`. 您可以使用它來確定受控制的序列是空白。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_set_clear.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::erase (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md)