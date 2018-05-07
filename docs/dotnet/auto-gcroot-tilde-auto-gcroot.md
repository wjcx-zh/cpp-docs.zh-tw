---
title: 'auto_gcroot:: ~ auto_gcroot |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_gcroot::~auto_gcroot
- ~auto_gcroot
- auto_gcroot.~auto_gcroot
- msclr::auto_gcroot::~auto_gcroot
- msclr.auto_gcroot.~auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot::~auto_gcroot
ms.assetid: 3c970d43-0cb1-4b27-8bee-0394d91b4739
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f0e99c7e99e8c6c68996ceea4d4a8120f6e048ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="autogcrootautogcroot"></a>auto_gcroot::~auto_gcroot
`auto_gcroot`解構函式。  
  
## <a name="syntax"></a>語法  
  
```  
~auto_gcroot();  
```  
  
## <a name="remarks"></a>備註  
 解構函式也 destructs 擁有的物件。  
  
## <a name="example"></a>範例  
  
```  
// msl_auto_gcroot_dtor.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
public:  
   ClassA() { Console::WriteLine( "ClassA constructor" ); }  
   ~ClassA() { Console::WriteLine( "ClassA destructor" ); }  
};  
  
int main()  
{  
   // create a new scope for a:  
   {  
      auto_gcroot<ClassA^> a = gcnew ClassA;  
   }  
   // a goes out of scope here, invoking its destructor  
   // which in turns destructs the ClassA object.  
  
   Console::WriteLine( "done" );  
}  
```  
  
```Output  
ClassA constructor  
ClassA destructor  
done  
```  
  
## <a name="requirements"></a>需求  
 **標頭檔** \<msclr\auto_gcroot.h >  
  
 **命名空間**msclr  
  
## <a name="see-also"></a>另請參閱  
 [auto_gcroot 成員](../dotnet/auto-gcroot-members.md)   
 [auto_gcroot::release](../dotnet/auto-gcroot-release.md)   
 [auto_gcroot::auto_gcroot](../dotnet/auto-gcroot-auto-gcroot.md)