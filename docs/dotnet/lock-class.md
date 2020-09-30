---
title: lock 類別
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::lock::lock
- msclr::lock::is_locked
- msclr::lock.is_locked
- msclr::lock::acquire
- msclr::lock::try_acquire
- msclr::lock::release
- msclr::lock::operator==
- msclr::lock::operator!=
helpviewer_keywords:
- msclr::lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: 7b2f187ec940af95523d0bbfb9265d7d9d6f69e8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508643"
---
# <a name="lock-class"></a>lock 類別

這個類別會自動進行鎖定，以同步處理從數個執行緒對物件的存取。  當建立時，它會取得鎖定，而當終結時，會釋放鎖定。

## <a name="syntax"></a>語法

```cpp
ref class lock;
```

## <a name="remarks"></a>備註

`lock` 僅適用于 CLR 物件，且只能在 CLR 程式碼中使用。

就內部而言，鎖定類別會使用 <xref:System.Threading.Monitor> 來同步存取。 如需詳細資訊，請參閱參考的文章。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|---------|-----------|
|[lock::lock](#lock)|`lock`會建立物件，並選擇性地在指定的一段時間內（或完全不會）等待取得鎖定。|
|[lock：： ~ lock](#tilde-lock)|Destructs `lock` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|---------|-----------|
|[lock::acquire](#acquire)|取得物件的鎖定，選擇性地等候一段指定的時間，或完全不取得鎖定。|
|[lock::is_locked](#is-locked)|指出是否持有鎖定。|
|[lock::release](#release)|釋放鎖定。|
|[lock::try_acquire](#try-acquire)|取得物件的鎖定，等候指定的時間量，並傳回 **`bool`** 來回報取得成功，而不是擲回例外狀況。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|---------|-----------|
|[lock：： operator &nbsp; bool](#operator-bool)|`lock`在條件運算式中使用的運算子。|
|[lock::operator==](#operator-equality)|等號比較運算子。|
|[lock：： operator！ =](#operator-inequality)|不等比較運算子。|

## <a name="requirements"></a>需求

**標頭檔** \<msclr\lock.h>

**命名空間** msclr

## <a name="locklock"></a><a name="lock"></a> lock：： lock

`lock`會建立物件，並選擇性地在指定的一段時間內（或完全不會）等待取得鎖定。

```cpp
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

### <a name="parameters"></a>參數

*_object*<br/>
要鎖定的物件。

*_timeout*<br/>
超時值（以毫秒為單位）或為 <xref:System.TimeSpan> 。

### <a name="exceptions"></a>例外狀況

<xref:System.ApplicationException>如果在超時之前未發生鎖定取得，則擲回。

### <a name="remarks"></a>備註

第三種形式的函式會嘗試在 `_object` 指定的超時時間內取得鎖定 (如果沒有 <xref:System.Threading.Timeout.Infinite> 指定) ，則為。

第四種形式的函式不會取得鎖定 `_object` 。 `lock_later` 這是 [lock_when 列舉](../dotnet/lock-when-enum.md)的成員。 在此情況下，請使用 [lock：：取得](#acquire) 或 [lock：： try_acquire](#try-acquire) 取得鎖定。

呼叫函式時，會自動釋放鎖定。

`_object` 不可為 <xref:System.Threading.ReaderWriterLock> 。  如果是，就會產生編譯器錯誤。

### <a name="example"></a>範例

此範例會在多個執行緒中使用類別的單一實例。 類別會對本身使用鎖定，以確保對每個執行緒而言，其內部資料的存取都是一致的。 主應用程式執行緒會在類別的相同實例上使用鎖定，以定期檢查是否有任何背景工作執行緒仍然存在。 然後，主應用程式會等到所有工作者執行緒都完成其工作之後，才會結束。

```cpp
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

## <a name="locklock"></a><a name="tilde-lock"></a> lock：： ~ lock

Destructs `lock` 物件。

```cpp
~lock();
```

### <a name="remarks"></a>備註

此呼叫函式會呼叫 [lock：： release](#release)。

### <a name="example"></a>範例

此範例會在多個執行緒中使用類別的單一實例。  類別會對本身使用鎖定，以確保對每個執行緒而言，其內部資料的存取都是一致的。  主應用程式執行緒會在類別的相同實例上使用鎖定，以定期檢查是否有任何背景工作執行緒仍然存在。 然後，主應用程式會等到所有工作者執行緒都完成其工作之後，才會結束。

```cpp
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

## <a name="lockacquire"></a><a name="acquire"></a> lock：：取得

取得物件的鎖定，選擇性地等候一段指定的時間，或完全不取得鎖定。

```cpp
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>參數

*_timeout*<br/>
Timeout 值（以毫秒為單位）或 <xref:System.TimeSpan> 。

### <a name="exceptions"></a>例外狀況

<xref:System.ApplicationException>如果在超時之前未發生鎖定取得，則擲回。

### <a name="remarks"></a>備註

如果未提供超時值，預設的超時值為 <xref:System.Threading.Timeout.Infinite> 。

如果已經取得鎖定，此函式不會執行任何動作。

### <a name="example"></a>範例

此範例會在多個執行緒中使用類別的單一實例。  類別會對本身使用鎖定，以確保對每個執行緒而言，其內部資料的存取都是一致的。 主應用程式執行緒會在類別的相同實例上使用鎖定，以定期檢查是否有任何背景工作執行緒仍然存在。 然後，主應用程式會等到所有工作者執行緒都完成其工作之後，才會結束。

```cpp
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

## <a name="lockis_locked"></a><a name="is-locked"></a> lock：： is_locked

指出是否持有鎖定。

```cpp
bool is_locked();
```

### <a name="return-value"></a>傳回值

**`true`** 如果保留鎖定，則為， **`false`** 否則為。

### <a name="example"></a>範例

此範例會在多個執行緒中使用類別的單一實例。  類別會對本身使用鎖定，以確保對每個執行緒而言，其內部資料的存取都是一致的。  主應用程式執行緒會在類別的相同實例上使用鎖定，以定期檢查是否有任何背景工作執行緒仍然存在，並等候結束，直到所有背景工作執行緒都完成其工作為止。

```cpp
// msl_lock_is_locked.cpp
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
      if (l.is_locked()) { // check if we got the lock
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
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockoperator-bool"></a><a name="operator-bool"></a> lock：： operator bool

`lock`在條件運算式中使用的運算子。

```cpp
operator bool();
```

### <a name="return-value"></a>傳回值

**`true`** 如果保留鎖定，則為， **`false`** 否則為。

### <a name="remarks"></a>備註

這個運算子實際上會轉換成 `_detail_class::_safe_bool` 更安全的， **`bool`** 因為它無法轉換成整數類資料類型。

### <a name="example"></a>範例

此範例會在多個執行緒中使用類別的單一實例。  類別會對本身使用鎖定，以確保對每個執行緒而言，其內部資料的存取都是一致的。 主應用程式執行緒會在類別的相同實例上使用鎖定，以定期檢查是否有任何背景工作執行緒仍然存在。 主要應用程式會等到所有工作者執行緒都完成其工作之後，才會結束。

```cpp
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

## <a name="lockrelease"></a><a name="release"></a> lock：： release

釋放鎖定。

```cpp
void release();
```

### <a name="remarks"></a>備註

如果未持有鎖定，就 `release` 不會執行任何動作。

您不需要明確呼叫此函數。 當 `lock` 物件超出範圍時，它的函式會 `release` 呼叫。

### <a name="example"></a>範例

此範例會在多個執行緒中使用類別的單一實例。 類別會對本身使用鎖定，以確保對每個執行緒而言，其內部資料的存取都是一致的。 主應用程式執行緒會在類別的相同實例上使用鎖定，以定期檢查是否有任何背景工作執行緒仍然存在。 然後，主應用程式會等到所有工作者執行緒都完成其工作之後，才會結束。

```cpp
// msl_lock_release.cpp
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

## <a name="locktry_acquire"></a><a name="try-acquire"></a> lock：： try_acquire

取得物件的鎖定，等候指定的時間量，並傳回 **`bool`** 來回報取得成功，而不是擲回例外狀況。

```cpp
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>參數

*_timeout*<br/>
Timeout 值（以毫秒為單位）或 <xref:System.TimeSpan> 。

### <a name="return-value"></a>傳回值

**`true`** 如果已取得鎖定，則 **`false`** 為，否則為。

### <a name="remarks"></a>備註

如果已經取得鎖定，此函式不會執行任何動作。

### <a name="example"></a>範例

此範例會在多個執行緒中使用類別的單一實例。 類別會對本身使用鎖定，以確保對每個執行緒而言，其內部資料的存取都是一致的。 主應用程式執行緒會在類別的相同實例上使用鎖定，以定期檢查是否有任何背景工作執行緒仍然存在。 然後，主應用程式會等到所有工作者執行緒都完成其工作之後，才會結束。

```cpp
// msl_lock_try_acquire.cpp
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

## <a name="lockoperator"></a><a name="operator-equality"></a> lock：： operator = =

等號比較運算子。

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>參數

*t*<br/>
要比較是否相等的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果與 `t` 鎖定的物件相同，則傳回， **`false`** 否則傳回。

### <a name="example"></a>範例

```cpp
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

## <a name="lockoperator"></a><a name="operator-inequality"></a> lock：： operator！ =

不等比較運算子。

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>參數

*t*<br/>
要比較是否不相等的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果 `t` 與鎖定的物件不同，則傳回， **`false`** 否則傳回。

### <a name="example"></a>範例

```cpp
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
