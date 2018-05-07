---
title: lock::operator = = |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::operator==
- msclr.lock.operator==
- msclr::lock::operator==
- lock.operator==
dev_langs:
- C++
helpviewer_keywords:
- lock::operator==
ms.assetid: 3dcf1e5a-53fc-495d-9df5-d7849a41c36c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 276ad5b44dd2112abad2c7c2e293fc65b173fffc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="lockoperator"></a>lock::operator==
等號比較運算子。  
  
## <a name="syntax"></a>語法  
  
```  
template<class T> bool operator==(  
   T t  
);  
```  
  
#### <a name="parameters"></a>參數  
 `t`  
 要比較相等的物件。  
  
## <a name="return-value"></a>傳回值  
 傳回`true`如果`t`鎖定的物件，與相同`false`否則。  
  
## <a name="example"></a>範例  
  
```  
// msl_lock_op_eq.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
int main () {  
   Object^ o1 = gcnew Object;  
   lock l1(o1);  
   if (l1 == o1) {  
      Console::WriteLine("Equal!");  
   }  
}  
```  
  
```Output  
Equal!  
```  
  
## <a name="requirements"></a>需求  
 **標頭檔** \<msclr\lock.h >  
  
 **命名空間**msclr  
  
## <a name="see-also"></a>另請參閱  
 [lock 成員](../dotnet/lock-members.md)   
 [lock::operator!=](../dotnet/lock-operator-inequality.md)