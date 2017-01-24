---
title: "lock::try_acquire | Microsoft Docs"
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
  - "try_acquire"
  - "lock.try_acquire"
  - "msclr.lock.try_acquire"
  - "lock::try_acquire"
  - "msclr::lock::try_acquire"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock::try_acquire"
ms.assetid: ef0649a9-e611-4495-84bd-2784533221d9
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::try_acquire
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得物件的鎖定，等候一個經過指定的時間和傳回 `bool` 報告作業成功而不會擲回例外狀況。  
  
## 語法  
  
```  
bool try_acquire(  
   int _timeout_ms  
);  
bool try_acquire(  
   System::TimeSpan _timeout  
);  
```  
  
#### 參數  
 `_timeout`  
 逾時值 \(以毫秒為單位\) 或 <xref:System.TimeSpan>。  
  
## 傳回值  
 `true` ，如果已取得鎖定，則為 `false` 。  
  
## 備註  
 如果鎖定已取得，這個函式不會執行任何動作。  
  
## 範例  
 這個範例使用類別的單一執行個體跨多個執行緒的。類別會使用自己的鎖定確保對其內部資料的存取權為每個執行緒是一致的。主應用程式執行緒使用類別的同一個執行個體上具有鎖定定期檢查任何背景工作執行緒是否仍存在，而且會結束，直到所有背景工作執行緒完成其工作。  
  
```  
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
 [lock::acquire](../dotnet/lock-acquire.md)