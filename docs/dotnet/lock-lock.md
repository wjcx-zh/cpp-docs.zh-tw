---
title: "lock::lock |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- lock::lock
- lock.lock
- msclr.lock.lock
- msclr::lock::lock
dev_langs: C++
helpviewer_keywords: lock constructor
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5148da4421b24a64dca97288975af42b9688e4ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="locklock"></a>lock::lock
建構`lock`物件，並選擇性地等候一段指定的時間，或完全不用，取得鎖定。  
  
## <a name="syntax"></a>語法  
  
```  
template<class T> lock(  
   T ^ _object  
);  
template<class T> lock(  
   T ^ _object,  
   int _timeout  
);  
template<class T> lock(  
   T ^ _object,  
   System::TimeSpan _timeout  
);  
template<class T> lock(  
   T ^ _object,  
   lock_later  
);  
```  
  
#### <a name="parameters"></a>參數  
 `_object`  
 要鎖定的物件。  
  
 `_timeout`  
 逾時值以毫秒為單位，或做為<xref:System.TimeSpan>。  
  
## <a name="exceptions"></a>例外狀況  
 擲回<xref:System.ApplicationException>如果取得鎖定逾時前不會發生。  
  
## <a name="remarks"></a>備註  
 前三個表單的建構函式嘗試取得的鎖定上`_object`在指定的逾時期限內 (或<xref:System.Threading.Timeout.Infinite>如果未指定)。  
  
 第四個表單的建構函式不會在取得鎖定`_object`。 `lock_later`成員的[lock_when 列舉](../dotnet/lock-when-enum.md)。 使用[lock::acquire](../dotnet/lock-acquire.md)或[lock::try_acquire](../dotnet/lock-try-acquire.md)在此情況下取得的鎖定。  
  
 解構函式呼叫時，會自動釋放鎖定。  
  
 `_object` 不可以是 <xref:System.Threading.ReaderWriterLock>。  如果是，編譯器會產生錯誤。  
  
## <a name="example"></a>範例  
 這個範例會跨多個執行緒使用單一類別的執行個體。  類別本身會使用鎖定，以確保其內部資料存取都是一致的每個執行緒。  主應用程式執行緒會定期檢查以查看是否仍然存在任何背景工作執行緒，並等候結束，直到所有的工作者執行緒完成其工作使用相同類別的執行個體上的鎖定。  
  
```  
// msl_lock_lock.cpp  
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
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't  
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
 [lock:: ~ 鎖定](../dotnet/lock-tilde-lock.md)   
 [lock::acquire](../dotnet/lock-acquire.md)   
 [lock::try_acquire](../dotnet/lock-try-acquire.md)