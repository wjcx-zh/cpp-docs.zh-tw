---
title: lock::operator ！ = |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock.operator!=
- msclr.lock.operator!=
- msclr::lock::operator!=
- lock::operator!=
dev_langs:
- C++
helpviewer_keywords:
- lock::operator!=
ms.assetid: ed1d674e-9ee9-4257-8a7e-2e3567d50222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6b34eb410e05bd102f7a10205e57b3731b8f476d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="lockoperator"></a>lock::operator!=
不等比較運算子。  
  
## <a name="syntax"></a>語法  
  
```  
template<class T> bool operator!=(  
   T t  
);  
```  
  
#### <a name="parameters"></a>參數  
 `t`  
 要比較不相等的物件。  
  
## <a name="return-value"></a>傳回值  
 傳回`true`如果`t`鎖定的物件不同`false`否則。  
  
## <a name="example"></a>範例  
  
```  
// msl_lock_op_ineq.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
int main () {  
   Object^ o1 = gcnew Object;  
   Object^ o2 = gcnew Object;  
   lock l1(o1);  
   if (l1 != o2) {  
      Console::WriteLine("Inequal!");  
   }  
}  
```  
  
```Output  
Inequal!  
```  
  
## <a name="requirements"></a>需求  
 **標頭檔** \<msclr\lock.h >  
  
 **命名空間**msclr  
  
## <a name="see-also"></a>另請參閱  
 [lock 成員](../dotnet/lock-members.md)   
 [lock::operator==](../dotnet/lock-operator-equality.md)