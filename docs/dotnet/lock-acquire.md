---
title: lock::acquire
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- lock::acquire
- acquire
- msclr.lock.acquire
- msclr::lock::acquire
- lock.acquire
helpviewer_keywords:
- acquire method
ms.assetid: c214274e-7519-4739-82aa-91b04a32d3f9
ms.openlocfilehash: a799f934024def40c2003f8496b2457d12eb69bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533727"
---
# <a name="lockacquire"></a>lock::acquire

取得物件，或者等候一段指定的時間，或者完全不要，取得鎖定的鎖定。

## <a name="syntax"></a>語法

```
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

#### <a name="parameters"></a>參數

*逾時 _t*<br/>
逾時值以毫秒為單位，或為<xref:System.TimeSpan>。

## <a name="exceptions"></a>例外狀況

會擲回<xref:System.ApplicationException>如果取得鎖定逾時之前不會發生。

## <a name="remarks"></a>備註

如果未提供的逾時值的預設逾時是<xref:System.Threading.Timeout.Infinite>。

如果已取得鎖定，此函式沒有任何作用。

## <a name="example"></a>範例

此範例會跨多個執行緒使用單一類別的執行個體。  類別會使用本身的鎖定，以確保一致的每個執行緒存取其內部的資料。  主應用程式執行緒的類別相同的執行個體上使用鎖定，來定期檢查以查看是否仍存在的任何背景工作執行緒，並等候直到所有的背景工作執行緒結束已完成其工作。

```
// msl_lock_acquire.cpp
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

## <a name="see-also"></a>另請參閱

[lock 成員](../dotnet/lock-members.md)<br/>
[lock::try_acquire](../dotnet/lock-try-acquire.md)