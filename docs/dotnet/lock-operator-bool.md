---
title: "lock::operator bool |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- operator bool
- msclr.lock.operator bool
- lock.operator bool
- msclr::lock::operator bool
- lock::operator bool
dev_langs: C++
helpviewer_keywords: lock::operator bool
ms.assetid: 007f0372-f812-4f1e-ba43-2584bd96eb11
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1156576abd9a8fe98270ee6a8edb864793d127fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="lockoperator-bool"></a>lock::operator bool
使用運算子`lock`條件運算式中。  
  
## <a name="syntax"></a>語法  
  
```  
operator bool();  
```  
  
## <a name="return-value"></a>傳回值  
 `true`如果鎖定，`false`否則。  
  
## <a name="remarks"></a>備註  
 這個運算子實際將轉換成`_detail_class::_safe_bool`即比安全`bool`因為它無法轉換成整數類資料類型。  
  
## <a name="example"></a>範例  
 這個範例會跨多個執行緒使用單一類別的執行個體。  類別本身會使用鎖定，以確保其內部資料存取都是一致的每個執行緒。  主應用程式執行緒會定期檢查以查看是否仍然存在任何背景工作執行緒，並等候結束，直到所有的工作者執行緒完成其工作使用相同類別的執行個體上的鎖定。  
  
```  
// msl_lock_op_bool.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
ref class CounterClass {  
private:  
   int Counter;     
  
public:  
   property int ThreadCount;  
  
   // function called by multiple threads, use lock to keep Counter consistent  
   // for each thread  
   void UseCounter() {  
      try {  
         lock l(this); // wait infinitely  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         for (int i = 0; i < 10; i++) {  
            Counter++;  
            Thread::Sleep(10);  
         }  
  
         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,   
            Counter);  
  
         Counter = 0;  
         // lock is automatically released when it goes out of scope and its destructor is called  
      }  
      catch (...) {  
         Console::WriteLine("Couldn't acquire lock!");  
      }  
  
      ThreadCount--;  
   }  
};  
  
int main() {  
   // create a few threads to contend for access to the shared data  
   CounterClass^ cc = gcnew CounterClass;  
   array<Thread^>^ tarr = gcnew array<Thread^>(5);  
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);  
   for (int i = 0; i < tarr->Length; i++) {  
      tarr[i] = gcnew Thread(startDelegate);  
      cc->ThreadCount++;  
      tarr[i]->Start();  
   }  
  
   // keep our main thread alive until all worker threads have completed  
   lock l(cc, lock_later); // don't lock now, just create the object  
   while (true) {  
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't  
      if (l) { // use bool operator to check for lock  
         if (0 == cc->ThreadCount) {  
            Console::WriteLine("All threads completed.");  
            break; // all threads are gone, exit while  
         }  
         else {  
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);  
            l.release(); // some threads exist, let them do their work  
         }  
      }  
   }  
}  
```  
  
```Output  
In thread 3, Counter = 0  
In thread 3, Counter = 10  
In thread 5, Counter = 0  
In thread 5, Counter = 10  
In thread 7, Counter = 0  
In thread 7, Counter = 10  
In thread 4, Counter = 0  
In thread 4, Counter = 10  
In thread 6, Counter = 0  
In thread 6, Counter = 10  
All threads completed.  
```  
  
## <a name="requirements"></a>需求  
 **標頭檔** \<msclr\lock.h >  
  
 **命名空間**msclr  
  
## <a name="see-also"></a>請參閱  
 [lock 成員](../dotnet/lock-members.md)   
 [lock::is_locked](../dotnet/lock-is-locked.md)