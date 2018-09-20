---
title: '鎖定:: ~ 鎖定 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ~lock
- msclr.lock.~lock
- lock.~lock
- msclr::lock::~lock
- lock::~lock
dev_langs:
- C++
helpviewer_keywords:
- ~lock destructor
ms.assetid: 55fa9f6c-d7a6-48ef-9236-ee03342c1d20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 01dd3a947161cae27174e383a8b080641253e32e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439012"
---
# <a name="locklock"></a>lock::~lock

Destructs`lock`物件。

## <a name="syntax"></a>語法

```
~lock();
```

## <a name="remarks"></a>備註

解構函式呼叫[lock::release](../dotnet/lock-release.md)。

## <a name="example"></a>範例

此範例會跨多個執行緒使用單一類別的執行個體。  類別會使用本身的鎖定，以確保一致的每個執行緒存取其內部的資料。  主應用程式執行緒的類別相同的執行個體上使用鎖定，來定期檢查以查看是否仍存在的任何背景工作執行緒，並等候直到所有的背景工作執行緒結束已完成其工作。

```
// msl_lock_dtor.cpp
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
[lock::lock](../dotnet/lock-lock.md)