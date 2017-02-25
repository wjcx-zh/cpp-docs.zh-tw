---
title: "_InterlockedCompareExchange 內建函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedCompareExchange_HLERelease"
  - "_InterlockedCompareExchange8_nf"
  - "_InterlockedCompareExchange16_acq_cpp"
  - "_InterlockedCompareExchange_acq_cpp"
  - "_InterlockedCompareExchange16_rel_cpp"
  - "_InterlockedCompareExchange64_rel_cpp"
  - "_InterlockedCompareExchange_cpp"
  - "_InterlockedCompareExchange16_cpp"
  - "_InterlockedCompareExchange64_acq_cpp"
  - "_InterlockedCompareExchange_acq"
  - "_InterlockedCompareExchange64_rel"
  - "_InterlockedCompareExchange64_nf"
  - "_InterlockedCompareExchange_rel_cpp"
  - "_InterlockedCompareExchange16_nf"
  - "_InterlockedCompareExchange8"
  - "_InterlockedCompareExchange64_np"
  - "_InterlockedCompareExchange16_rel"
  - "_InterlockedCompareExchange64_acq"
  - "_InterlockedCompareExchange8_rel"
  - "_InterlockedCompareExchange_HLEAcquire"
  - "_InterlockedCompareExchange64_HLERelease"
  - "_InterlockedCompareExchange64_cpp"
  - "_InterlockedCompareExchange_np"
  - "_InterlockedCompareExchange8_acq"
  - "_InterlockedCompareExchange16_acq"
  - "_InterlockedCompareExchange_rel"
  - "_InterlockedCompareExchange64_HLEAcquire"
  - "_InterlockedCompareExchange64"
  - "_InterlockedCompareExchange16"
  - "_InterlockedCompareExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建的 _InterlockedCompareExchange"
  - "內建的 _InterlockedCompareExchange_acq"
  - "內建的 _InterlockedCompareExchange_rel"
  - "內建的 _InterlockedCompareExchange16"
  - "內建的 _InterlockedCompareExchange64"
  - "內建的 _InterlockedCompareExchange64_acq"
  - "內建的 _InterlockedCompareExchange64_rel"
  - "內建的 InterlockedCompareExchange"
  - "內建的 InterlockedCompareExchange_acq"
  - "內建的 InterlockedCompareExchange_rel"
  - "內建的 InterlockedCompareExchange16"
  - "內建的 InterlockedCompareExchange64"
  - "內建的 InterlockedCompareExchange64_acq"
  - "內建的 InterlockedCompareExchange64_rel"
ms.assetid: c3ad79c0-a523-4930-a3a4-69a65d7d5c81
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _InterlockedCompareExchange 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 執行連鎖比較和交換。  
  
## 語法  
  
```  
long _InterlockedCompareExchange(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_acq(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_HLEAcquire(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_HLERelease(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_np(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
long _InterlockedCompareExchange_rel(  
   long volatile * Destination,  
   long Exchange,  
   long Comparand  
);  
char _InterlockedCompareExchange8(  
   char volatile * Destination,  
   char Exchange,  
   char Comparand  
);  
char _InterlockedCompareExchange8_acq(  
   char volatile * Destination,  
   char Exchange,  
   char Comparand  
);  
char _InterlockedCompareExchange8_nf(  
   char volatile * Destination,  
   char Exchange,  
   char Comparand  
);  
char _InterlockedCompareExchange8_rel(  
   char volatile * Destination,  
   char Exchange,  
   char Comparand  
);  
short _InterlockedCompareExchange16(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
short _InterlockedCompareExchange16_acq(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
short _InterlockedCompareExchange16_nf(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
short _InterlockedCompareExchange16_np(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
short _InterlockedCompareExchange16_rel(  
   short volatile * Destination,  
   short Exchange,  
   short Comparand  
);  
__int64 _InterlockedCompareExchange64(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_acq(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_HLEAcquire (  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_HLERelease(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_nf(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_np(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
__int64 _InterlockedCompareExchange64_rel(  
   __int64 volatile * Destination,  
   __int64 Exchange,  
   __int64 Comparand  
);  
```  
  
#### 參數  
 \[in、out\] `Destination`  
 目的地值的指標。  會忽略正負號。  
  
 \[in\] `Exchange`  
 交換值。  會忽略正負號。  
  
 \[in\] `Comparand`  
 要與目的地比較的值。  會忽略正負號。  
  
## 傳回值  
 傳回值是 `Destination` 指標的初始值。  
  
## 需求  
  
|內建|架構|標頭|  
|--------|--------|--------|  
|`_InterlockedCompareExchange`, `_InterlockedCompareExchange8`, `_InterlockedCompareExchange16`, `_InterlockedCompareExchange64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedCompareExchange_acq`, `_InterlockedCompareExchange_rel`, `_InterlockedCompareExchange8_acq`, `_InterlockedCompareExchange8_nf`, `_InterlockedCompareExchange8_rel`,`_InterlockedCompareExchange16_acq`, `_InterlockedCompareExchange16_nf`, `_InterlockedCompareExchange16_rel`, `_InterlockedCompareExchange64_acq`, `_InterlockedCompareExchange64_nf`, `_InterlockedCompareExchange64_rel`,|ARM|\<intrin.h\>|  
|`_InterlockedCompareExchange_np`, `_InterlockedCompareExchange16_np`, `_InterlockedCompareExchange64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedCompareExchange_HLEAcquire`, `_InterlockedCompareExchange_HLERelease`, `_InterlockedCompareExchange64_HLEAcquire`, `_InterlockedCompareExchange64_HLERelease`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 備註  
 `_InterlockedCompareExchange` 會執行不可部分完成的 `Destination` 值與 `Comparand` 值的比較。  如果 `Destination` 值等於 `Comparand` 值，則 `Exchange` 值會儲存在 `Destination` 所指定的位址。  否則，不會執行任何作業。  
  
 `_InterlockedCompareExchange` 提供 Win32 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [InterlockedCompareExchange](http://msdn.microsoft.com/library/ms683560.aspx) 函式的編譯器內建支援。  
  
 在 `_InterlockedCompareExchange` 上有數個變化，會因所涉及的資料類型，以及是否使用處理器專用的取得或釋放語意，而有所不同。  
  
 `_InterlockedCompareExchange` 函式在長整數值上運算；`_InterlockedCompareExchange8` 在 8 位元整數值上運算；`_InterlockedCompareExchange16` 在短整數值上運算；`_InterlockedCompareExchange64` 在 64 位元整數值上運算。  
  
 在 ARM 平台上，搭配取得和釋放語意的 `_acq` 和 `_rel` 字尾使用內建函式，例如在重要區段的開頭和結尾處。  搭配 `_nf` \(「無範圍」\) 字尾的 ARM 內建函式不會當做記憶體屏障。  
  
 搭配 `_np` \(「不預先擷取」\) 字尾使用內建函式，可避免編譯器插入可能的預先提取作業。  
  
 在支援 Hardware Lock Elision \(HLE\) 指令的 Intel 平台上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 \(lock write\) 的階段以加速效能。  如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。  
  
 這些常式只可做為內建函式。  
  
## 範例  
 在下列範例中，`_InterlockedCompareExchange` 會用於簡單的低層級執行緒同步處理。  此方法針對多執行緒程式設計有其基礎限制；它會以示範連鎖內建函式的一般用法的方式呈現。  為求最佳結果，請使用 Windows API。  如需多執行緒程式設計的進一步資訊，請參閱[撰寫多執行緒 Win32 程式](../parallel/writing-a-multithreaded-win32-program.md)。  
  
```  
// intrinExample.cpp  
// compile with: /EHsc /O2  
// Simple example of using _Interlocked* intrinsics to  
// do manual synchronization  
//  
// Add [-DSKIP_LOCKING] to the command line to disable  
// the locking. This will cause the threads to execute out  
// of sequence.  
  
#define _CRT_RAND_S  
  
#include "windows.h"  
  
#include <iostream>  
#include <queue>  
#include <intrin.h>  
  
using namespace std;  
  
// --------------------------------------------------------------------  
  
// if defined, will not do any locking on shared data  
//#define SKIP_LOCKING  
  
// A common way of locking using _InterlockedCompareExchange.  
// Please refer to other sources for a discussion of the many issues  
// involved. For example, this particular locking scheme performs well   
// when lock contention is low, as the while loop overhead is small and  
// locks are acquired very quickly, but degrades as many callers want  
// the lock and most threads are doing a lot of interlocked spinning.  
// There are also no guarantees that a caller will ever acquire the  
// lock.  
namespace MyInterlockedIntrinsicLock  
{  
    typedef unsigned LOCK, *PLOCK;  
  
#pragma intrinsic(_InterlockedCompareExchange, _InterlockedExchange)  
  
    enum {LOCK_IS_FREE = 0, LOCK_IS_TAKEN = 1};  
  
    void Lock(PLOCK pl)   
    {  
#if !defined(SKIP_LOCKING)  
        // If *pl == LOCK_IS_FREE, it is set to LOCK_IS_TAKEN  
        // atomically, so only 1 caller gets the lock.  
        // If *pl == LOCK_IS_TAKEN,  
        // the result is LOCK_IS_TAKEN, and the while loop keeps spinning.  
        while (_InterlockedCompareExchange((long *)pl,  
                                           LOCK_IS_TAKEN, // exchange  
                                           LOCK_IS_FREE)  // comparand  
               == LOCK_IS_TAKEN)  
        {  
            // spin!  
        }  
        // This will also work.  
        //while (_InterlockedExchange(pl, LOCK_IS_TAKEN) ==   
        //                             LOCK_IS_TAKEN)  
        //{  
        //    // spin!  
        //}  
  
        // At this point, the lock is acquired.  
#endif  
    }  
  
    void Unlock(PLOCK pl) {  
#if !defined(SKIP_LOCKING)  
        _InterlockedExchange((long *)pl, LOCK_IS_FREE);  
#endif  
    }  
}  
  
// ------------------------------------------------------------------  
  
// Data shared by threads  
  
queue<int> SharedQueue;  
MyInterlockedIntrinsicLock::LOCK SharedLock;  
int TicketNumber;  
  
// ------------------------------------------------------------------  
  
DWORD WINAPI  
ProducerThread(  
    LPVOID unused  
    )  
{  
    unsigned int randValue;  
    while (1) {  
        // Acquire shared data. Enter critical section.  
        MyInterlockedIntrinsicLock::Lock(&SharedLock);  
  
        //cout << ">" << TicketNumber << endl;  
        SharedQueue.push(TicketNumber++);  
  
        // Release shared data. Leave critical section.  
        MyInterlockedIntrinsicLock::Unlock(&SharedLock);  
  
        rand_s(&randValue);  
        Sleep(randValue % 20);  
    }  
  
    return 0;  
}  
  
DWORD WINAPI  
ConsumerThread(  
    LPVOID unused  
    )  
{  
    while (1) {  
        // Acquire shared data. Enter critical section  
        MyInterlockedIntrinsicLock::Lock(&SharedLock);  
  
        if (!SharedQueue.empty()) {  
            int x = SharedQueue.front();  
            cout << "<" << x << endl;  
            SharedQueue.pop();  
        }  
  
        // Release shared data. Leave critical section  
        MyInterlockedIntrinsicLock::Unlock(&SharedLock);  
  
        unsigned int randValue;  
        rand_s(&randValue);  
        Sleep(randValue % 20);  
    }  
    return 0;  
}  
  
int main(  
    void  
    )  
{  
    const int timeoutTime = 500;  
    int unused1, unused2;  
    HANDLE threads[4];  
  
    // The program creates 4 threads:  
    // two producer threads adding to the queue  
    // and two consumers taking data out and printing it.  
    threads[0] = CreateThread(NULL,  
                              0,  
                              ProducerThread,  
                              &unused1,  
                              0,  
                              (LPDWORD)&unused2);  
  
    threads[1] = CreateThread(NULL,  
                              0,  
                              ConsumerThread,  
                              &unused1,  
                              0,  
                              (LPDWORD)&unused2);  
  
    threads[2] = CreateThread(NULL,  
                              0,  
                              ProducerThread,  
                              &unused1,  
                              0,  
                              (LPDWORD)&unused2);  
  
    threads[3] = CreateThread(NULL,  
                              0,  
                              ConsumerThread,  
                              &unused1,  
                              0,  
                              (LPDWORD)&unused2);  
  
    WaitForMultipleObjects(4, threads, TRUE, timeoutTime);  
  
    return 0;  
}  
```  
  
  **\<0**  
**\<1**  
**\<2**  
**\<3**  
**\<4**  
**\<5**  
**\<6**  
**\<7**  
**\<8**  
**\<9**  
**\<10**  
**\<11**  
**\<12**  
**\<13**  
**\<14**  
**\<15**  
**\<16**  
**\<17**  
**\<18**  
**\<19**  
**\<20**  
**\<21**  
**\<22**  
**\<23**  
**\<24**  
**\<25**  
**\<26**  
**\<27**  
**\<28**  
**\<29**   
## END Microsoft 特定的  
  
## 請參閱  
 [\_InterlockedCompareExchange128](../intrinsics/interlockedcompareexchange128.md)   
 [\_InterlockedCompareExchangePointer 內建函式](../intrinsics/interlockedcompareexchangepointer-intrinsic-functions.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)