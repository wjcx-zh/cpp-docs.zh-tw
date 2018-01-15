---
title: "初構和終 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 700b467065d17a61dcfabf9dcaa6577a7ecffc11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="prolog-and-epilog"></a>初構和終解
配置堆疊空間每個函式，呼叫其他函式，將儲存靜態暫存器，或使用例外狀況處理必須有個別的函式表格項目相關聯的回溯資料中所述的位址限制的初構 (請參閱[例外狀況處理 (x64)](../build/exception-handling-x64.md))。 初構儲存暫存器，在他們的住家地址中如有需要，將推入靜態暫存器堆疊上的引數、 區域變數和暫存檔，配置堆疊的固定的部分，並選擇性地建立框架指標。 關聯的回溯資料必須描述初構中的動作，因此必須提供要復原的初構程式碼的效果所需的資訊。  
  
 多個頁面是否包含在堆疊中的固定的配置 (也就是大於 4096 個位元組)，則堆疊配置可能會一個以上的虛擬記憶體分頁，因此，在配置必須檢查之前實際配置。 針對此目的所提供的特殊常式呼叫的初構且其不會終結任何引數暫存器。  
  
 儲存靜態暫存器的慣用的方法是將它們移至前固定的堆疊配置堆疊。 如果固定的堆疊配置之前便已執行已儲存靜態暫存器，則可能是 32 位元位移會是需要位址，暫存器 （stage，推入暫存器只一樣快速移動，而且應該維持不變的區域可預見未來即便推播通知之間的隱含相依性）。 可以依任何順序儲存靜態暫存器。 不過，第一次使用的初構中的靜態暫存器必須將它儲存。  
  
 可能是一般的初構程式碼：  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
sub      RSP, fixed-allocation-size  
lea      R13, 128[RSP]  
...  
```  
  
 本初構會儲存其主要位置引數暫存器 RCX、 儲存靜態暫存器 R13 R15、 配置的固定的部分的堆疊框架，和建立指向 128 位元組的固定的配置區域的框架指標。 使用位移，可讓多個固定的配置區域來處理單位元組位移。  
  
 如果固定的配置的大小大於或等於一頁的記憶體，則必須在修改 RSP 之前呼叫 helper 函式。 這個 helper，__chkstk，負責探查要配置堆疊範圍，以確保會正確地擴充堆疊。 在此情況下，會改為上一個初構範例：  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
mov      RAX,  fixed-allocation-size  
call   __chkstk  
sub      RSP, RAX  
lea      R13, 128[RSP]  
...  
```  
  
 __Chkstk 協助程式不會修改任何暫存器 R10、 R11、 和條件碼以外。 特別是，它將會傳回 RAX 保持不變，並保留所有靜態暫存器和引數傳遞未經修改的暫存器。  
  
 終解程式碼存在於每個函式結束。 沒有通常只有一個初構，可以有許多終。 終解程式碼 （如有必要），會修剪固定的配置的大小堆疊、 取消配置的固定的堆疊配置、 還原靜態暫存器取出從堆疊，其儲存的值和傳回。  
  
 終解程式碼必須遵循嚴格的回溯程式碼的規則集合，才能可靠地回溯例外狀況和插斷。 如此能縮短的回溯資料所需，因為不需要任何額外的資料來描述每個終解。 相反地，回溯程式碼可以判斷終解正在執行的掃描來識別終解程式碼資料流。  
  
 如果沒有框架指標用在函式，則終解必須先解除配置堆疊的固定的部分、 取出靜態暫存器，並將控制權傳回給呼叫的函式。 例如，套用至物件的  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 如果函式中使用框架指標，堆疊必須修剪成固定終執行前的配置。 這是技術不屬於終解的一部分。 例如，下列的終解無法用於復原先前用過的初構：  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 在實務上，使用框架指標時，沒有任何好的理由，在兩個步驟中，調整 RSP，如此就會使用下列的終解：  
  
```  
lea      RSP, fixed-allocation-size - 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 這些是唯一合法的終解形式。 它必須包含的其中一個`add RSP,constant`或`lea RSP,constant[FPReg]`，後面接著一系列的零或多個 8 位元暫存器快顯並傳回或 jmp。 （只有一群 jmp 陳述式是允許終解中。 這些是 jmps 的獨佔 ModRM 記憶體參考類別的其中 ModRM mod 欄位值 00。 禁止您 jmps ModRM mod 欄位值 01 或 10 終解中使用。 請參閱資料表 A-15 AMD x86-64 架構程式設計人員手動磁碟區 3： 一般用途和系統的指示，如需詳細資訊，可允許 ModRM 參照上。)。 沒有其他程式碼可能會出現。 特別是，執行任何動作可以排程在終解中，包括傳回值的載入。  
  
 請注意，不使用框架指標時，必須使用終解`add RSP,constant`取消配置堆疊的固定的一部分。 它不能使用`lea RSP,constant[RSP]`改為。 這項限制存在，所以回溯程式碼有較少辨識終搜尋時的模式。  
  
 遵循這些規則可讓以判斷終解目前正在執行，並模擬的終解中，以重新建立的內容呼叫的函式的其餘部分執行的回溯程式碼。  
  
## <a name="see-also"></a>請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)