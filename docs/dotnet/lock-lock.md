---
title: "lock::lock | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "lock::lock"
  - "lock.lock"
  - "msclr.lock.lock"
  - "msclr::lock::lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock 建構函式"
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::lock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構 `lock` 物件，並選擇性地等候取得鎖定不一定，在指定的時間或。  
  
## 語法  
  
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
  
#### 參數  
 `_object`  
 要鎖定的物件。  
  
 `_timeout`  
 逾時值 \(以毫秒為單位\) 或 <xref:System.TimeSpan>。  
  
## 例外狀況  
 如果鎖定作業不在逾時之前，就會擲回 <xref:System.ApplicationException> 。  
  
## 備註  
 建構函式的前三個表單嘗試取得 `_object` 的鎖定在指定的逾時週期 \(或 <xref:System.Threading.Timeout.Infinite> \)，如果沒有指定\)。  
  
 建構函式的第四個表單不會取得 `_object`的鎖定。  `lock_later` 是 [lock\_when 列舉](../dotnet/lock-when-enum.md)的成員。  使用 [lock::acquire](../dotnet/lock-acquire.md) 或 [lock::try\_acquire](../dotnet/lock-try-acquire.md) 在這種情況下取得鎖定。  
  
 鎖定時，解構函式呼叫，將會自動釋放。  
  
 `_object` 不可以是 <xref:System.Threading.ReaderWriterLock>。如果是，編譯器將會發生錯誤。  
  
## 範例  
 這個範例使用類別的單一執行個體跨多個執行緒的。類別會使用自己的鎖定確保對其內部資料的存取權為每個執行緒是一致的。主應用程式執行緒使用類別的同一個執行個體上具有鎖定定期檢查任何背景工作執行緒是否仍存在，而且會結束，直到所有背景工作執行緒完成其工作。  
  
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
  
  **在執行緒 3，計數器 \= 0**  
**在執行緒 3，計數器 \= 10**  
**在執行緒 5，計數器 \= 0**  
**在執行緒 5，計數器 \= 10**  
**在執行緒 7，計數器 \= 0**  
**在執行緒 7，計數器 \= 10**  
**在執行緒 4，計數器 \= 0**  
**在執行緒 4，計數器 \= 10**  
**在執行緒 6，計數器 \= 0**  
**在執行緒 6，計數器 \= 10**  
**任何執行緒完成。**   
## 需求  
 **標頭檔** \<msclr \\ lock.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [lock 成員](../dotnet/lock-members.md)   
 [lock::~lock](../dotnet/lock-tilde-lock.md)   
 [lock::acquire](../dotnet/lock-acquire.md)   
 [lock::try\_acquire](../dotnet/lock-try-acquire.md)