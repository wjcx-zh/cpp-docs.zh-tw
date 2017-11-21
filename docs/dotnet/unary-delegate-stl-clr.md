---
title: "unary_delegate (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::unary_delegate
dev_langs: C++
helpviewer_keywords: unary_delegate function [STL/CLR]
ms.assetid: b3ee253c-98e8-466e-a272-505e47aed061
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50a59472b2aa2873cf1efe00741f3ddfd98f0e5e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="unarydelegate-stlclr"></a>unary_delegate (STL/CLR)
Genereic 類別描述一個引數的委派。 您可以使用它指定的委派，以其引數和傳回型別。  
  
## <a name="syntax"></a>語法  
  
```  
generic<typename Arg,  
    typename Result>  
    delegate Result unary_delegate(Arg);  
```  
  
#### <a name="parameters"></a>參數  
 引數  
 引數型別。  
  
 結果  
 傳回型別。  
  
## <a name="remarks"></a>備註  
 Genereic 委派說明的單一引數函式。  
  
 請注意，如：  
  
 `unary_delegare<int, int> Fun1;`  
  
 `unary_delegare<int, int> Fun2;`  
  
 型別`Fun1`和`Fun2`是同義字，而為：  
  
 `delegate int Fun1(int);`  
  
 `delegate int Fun2(int);`  
  
 它們不是相同的類型。  
  
## <a name="example"></a>範例  
  
```  
// cliext_unary_delegate.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
int hash_val(wchar_t val)   
    {   
    return ((val * 17 + 31) % 67);   
    }   
  
typedef cliext::unary_delegate<wchar_t, int> Mydelegate;   
int main()   
    {   
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 5  
hash(L'b') = 22  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<功能 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)   
 [binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)   
 [unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)