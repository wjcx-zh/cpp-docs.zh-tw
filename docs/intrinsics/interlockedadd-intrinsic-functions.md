---
title: "_InterlockedAdd 內建函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedAdd64_acq_cpp"
  - "_InterlockedAdd64_acq"
  - "_InterlockedAdd_acq"
  - "_InterlockedAdd_nf"
  - "_InterlockedAdd64_rel"
  - "_InterlockedAdd64"
  - "_InterlockedAdd_cpp"
  - "_InterlockedAdd_rel_cpp"
  - "_InterlockedAdd_rel"
  - "_InterlockedAdd64_rel_cpp"
  - "_InterlockedAdd64_cpp"
  - "_InterlockedAdd_acq_cpp"
  - "_InterlockedAdd64_nf"
  - "_InterlockedAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedAdd 內建函式"
  - "_InterlockedAdd_acq 內建函式"
  - "_InterlockedAdd_nf 內建函式"
  - "_InterlockedAdd_rel 內建函式"
  - "_InterlockedAdd64 內建函式"
  - "_InterlockedAdd64_acq 內建函式"
  - "_InterlockedAdd64_nf 內建函式"
  - "_InterlockedAdd64_rel 內建函式"
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedAdd 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 執行不可部分完成的相加，這可確保多個執行緒可以存取共用變數時，操作可成功完成。  
  
## 語法  
  
```  
long _InterlockedAdd(    long volatile * Addend,    long Value ); long _InterlockedAdd_acq(    long volatile * Addend,    long Value ); long _InterlockedAdd_nf(    long volatile * Addend,    long Value ); long _InterlockedAdd_rel(    long volatile * Addend,    long Value ); __int64 _InterlockedAdd64(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_acq(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_nf (    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedAdd64_rel(    __int64 volatile * Addend,    __int64 Value );  
```  
  
#### 參數  
 \[in, out\] `Addend`  
 指向要加入整數的指標；由相加的結果所取代。  
  
 \[in\] `Value`  
 要加入的值。  
  
## 傳回值  
 兩個函式都傳回相加的結果。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_InterlockedAdd`|ARM|  
|`_InterlockedAdd_acq`|ARM|  
|`_InterlockedAdd_nf`|ARM|  
|`_InterlockedAdd_rel`|ARM|  
|`_InterlockedAdd64`|ARM|  
|`_InterlockedAdd64_acq`|ARM|  
|`_InterlockedAdd64_nf`|ARM|  
|`_InterlockedAdd64_rel`|ARM|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 這些函式的 `_acq` 或 `_rel` 版本後置字元在取得或發行語意之後執行連鎖相加。  取得語意表示在任何後續的記憶體讀取和寫入之前，會使所有執行緒和處理器都看見運算的結果。  在進入關鍵區段時，取得非常有用。  發行語意表示，在使運算的結果本身可見之前，會強制使所有的執行緒和處理器都看見所有的記憶體讀取和寫入。  離開關鍵區段時，發行非常有用。  具有 `_nf` \(「沒有圍牆」\) 後置字元的內建函式不做為記憶體屏障。  
  
 這些常式僅以內建函式的形式供您使用。  
  
## 範例  
  
```  
// interlockedadd.cpp  
// Compile with: /Oi /EHsc  
// processor: ARM  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedAdd)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FF0000;  
        long retval;  
        retval = _InterlockedAdd(&data1, data2);  
        printf("0x%x 0x%x 0x%x", data1, data2, retval);  
}  
```  
  
## 輸出  
  
```  
0xffffff00 0xff0000 0xffffff00  
```  
  
## 範例  
  
```  
// interlockedadd64.cpp  
// compile with: /Oi /EHsc  
// processor: ARM  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_InterlockedAdd64)  
  
int main()  
{  
        __int64 data1 = 0x0000FF0000000000;  
        __int64 data2 = 0x00FF0000FFFFFFFF;  
        __int64 retval;  
        cout << hex << data1 << " + " << data2 << " = " ;  
        retval = _InterlockedAdd64(&data1, data2);  
        cout << data1 << endl;  
        cout << "Return value: " << retval << endl;  
}  
```  
  
## 輸出  
  
```  
ff0000000000 + ff0000ffffffff = ffff00ffffffff  
Return value: ffff00ffffffff  
```  
  
### END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)