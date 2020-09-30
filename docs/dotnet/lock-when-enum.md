---
title: lock_when 列舉
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::lock_when
- msclr.lock_when
- lock_when
helpviewer_keywords:
- lock_when enum
ms.assetid: 6b87bbe9-63cd-450d-a02e-bb91ffd0dcea
ms.openlocfilehash: 991cce4cfa6810f35c2ccb3ec1ed45adf2d849ac
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508690"
---
# <a name="lock_when-enum"></a>lock_when 列舉

指定延遲的鎖定。

## <a name="syntax"></a>語法

```
enum lock_when {
   lock_later
};
```

## <a name="remarks"></a>備註

傳遞至 [lock：： lock](./lock-class.md#lock)時， `lock_later` 指定目前不會執行鎖定。

## <a name="example"></a>範例

此範例會在多個執行緒中使用類別的單一實例。  類別會對本身使用鎖定，以確保其內部資料的存取對每個執行緒都是一致的。  主應用程式執行緒會在類別的相同實例上使用鎖定，以定期檢查是否有任何背景工作執行緒仍然存在，並等候結束，直到所有背景工作執行緒都完成其工作為止。

```cpp
// msl_lock_lock_when.cpp
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

**標頭檔** \<msclr\lock.h>

**命名空間** msclr

## <a name="see-also"></a>另請參閱

[鎖](../dotnet/lock.md)
