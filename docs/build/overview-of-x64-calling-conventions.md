---
title: "x64 呼叫慣例概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# x64 呼叫慣例概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 x86 到 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 有兩項重要修改，就是 64 位元定址功能，以及供一般用途使用的 16 個 64 位元暫存器的一般設定。  對於指定的展開暫存器集合，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 只會使用 [\_\_fastcall](../cpp/fastcall.md) 呼叫慣例 \(Calling Convention\) 和 RISC 架構的例外狀況處理模型。  `__fastcall` 模型會將暫存器用於前面四個引數和堆疊框架 \(Stack Frame\)，以傳遞其他參數。  
  
 下列編譯器選項可協助您針對 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 最佳化應用程式：  
  
-   [\/favor \(專為架構最佳化\)](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## 呼叫慣例  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 應用程式二進位介面 \(Application Binary Interface，ABI\) 是 4 個暫存器快速呼叫的呼叫慣例，具有那些暫存器的堆疊支援。  函式中的引數以及那些引數的暫存器之間具有嚴格的一對一對應。  任何不符合 8 個位元組或不是 1、2、4 或 8 個位元組的引數，都必須透過傳址 \(By Reference\) 方式傳遞。  建議您不要試圖將單一引數散佈到多個暫存器。  x87 暫存器堆疊未使用，  但是它可以使用，不過必須在函式呼叫 \(Function Call\) 之間視為 Volatile。  所有的浮點運算都是使用 16 XMM 暫存器完成。  引數會在 RCX、RDX、R8 和 R9 暫存器中傳遞。  如果引數為 float\/double，則會在 XMM0L、XMM1L、XMM2L 和 XMM3L 中傳遞。  16 個位元組的引數會以傳址方式傳遞。  參數傳遞在[參數傳遞](../build/parameter-passing.md)中有詳細說明。  除了這些暫存器之外，RAX、R10、R11、XMM4 和 XMM5 都是 Volatile。  所有其他暫存器都為非 Volatile。  暫存器使用方式在[暫存器使用方式](../build/register-usage.md)和[呼叫端\/被呼叫端儲存的暫存器](../build/caller-callee-saved-registers.md)中有詳細說明。  
  
 呼叫端負責配置參數空間給被呼叫端，即使被呼叫端沒有那麼多參數，呼叫端也必須為 4 個暫存器參數配置足夠的空間。  這有助於支援 C 沒有原型的函式和 vararg C\/C\+\+ 函式的簡化。  對於 vararg 或沒有原型的函式，必須在對應的一般用途暫存器中複製任何浮點值。  前四個參數之後的所有參數都必須儲存在堆疊上，儲存於前四個參數的支援存放區之上、呼叫之前。  Vararg 函式的詳細資訊可以在 [Varargs](../build/varargs.md) 中找到。  沒有原型的函式資訊在[沒有原型的函式](../build/unprototyped-functions.md)中有詳細說明。  
  
## 對齊方式  
 大部分的結構都會自然對齊。  主要的例外是，堆疊指標及 malloc 或 alloca 記憶體，它們會對齊 16 位元組，以增強效能。  16 位元組以上的對齊必須以手動方式完成，但是由於 16 位元組是 XMM 運算的常見對齊大小，因此，這對大部分的程式碼來說應該足夠。  如需結構配置和對齊的詳細資訊，請參閱[類型和儲存區](../build/types-and-storage.md)。  如需堆疊配置的詳細資訊，請參閱[堆疊使用方式](../build/stack-usage.md)。  
  
## 不可回溯性  
 所有的分葉函式 \(既不呼叫函式，也不自行配置任何堆疊空間的函式\) 都必須以資料 \(稱為 xdata 或 ehdata，從 pdata 指向\) 加註，該資料說明作業系統如何適當地將其回溯，以復原非 Volatile 暫存器。  初構 \(Prolog\) 和終解 \(Epilog\) 的限制相當嚴格，如此，它們才能在 xdata 中適當地描述。  在任何不屬於終解或初構部分的程式碼區域中，堆疊指標必須對齊 16 位元組，但分葉函式除外。  如需函式初構和終解之適當結構的詳細資訊，請參閱[初構和終解](../build/prolog-and-epilog.md)。  如需例外狀況處理 \(Exception Handling\) 和例外狀況處理\/回溯 pdata 和 xdata 的詳細資訊，請參閱[例外狀況處理 \(x64\)](../build/exception-handling-x64.md)。  
  
## 請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)