---
title: "初構和終解 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 初構和終解
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個會配置堆疊空間、呼叫其他函式、儲存靜態 \(Nonvolatile\) 暫存器或使用例外狀況處理 \(Exception Handling\) 的函式都必須具備一個初構 \(Prolog\)，這個初構的位址限制在與個別函式表 \(Function Table\) 項目 \(請參閱[例外狀況處理 \(x64\)](../build/exception-handling-x64.md)\) 關聯的回溯 \(Unwind\) 資料中有詳細的描述。  必要時，初構會將引數暫存器儲存在主要位址 \(Home Address\)、將靜態暫存器推入堆疊、將堆疊的固定部分配置給區域變數和暫存檔，並選擇性地建立框架指標。  關聯的回溯資料必須描述初構的動作，並提供用於復原初構程式碼 \(Prolog Code\) 之影響所需的資訊。  
  
 如果堆疊中的固定配置大於一頁 \(亦即大於 4096 個位元組\)，堆疊配置可能會超過一個虛擬記憶體頁面，因此，請務必在實際配置之前先檢查配置。  若要檢查配置，可以從初構中呼叫特殊的常式，這個常式不會終結任何引數暫存器。  
  
 若要儲存靜態暫存器，建議在固定堆疊配置之前，先將靜態暫存器移到堆疊中。  如果固定堆疊配置在儲存靜態暫存器之前便已執行，可能就需要 32 位元的替代 \(Displacement\) 來滿足已儲存之暫存器區域 \(報告指出，推入暫存器的速度與移動暫存器一樣，儘管推入動作之間可能具有相依性，但在可見的未來，這個速度將可望維持不變\)。  靜態暫存器可以依任何順序儲存。  然而，在初構中使用靜態暫存器時，第一個動作應該是儲存。  
  
 典型初構的程式碼應該如下：  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
sub      RSP, fixed-allocation-size  
lea      R13, 128[RSP]  
...  
```  
  
 這個初構會將引數暫存器 RCX 儲存到其主要位置 \(Home Location\)、儲存 R13 至 R15 的靜態暫存器、配置堆疊框架的固定部分，然後建立框架指標，將 128 位元組指向固定配置區域。  如果使用位移 \(Offset\)，一位元組位移 \(One\-Byte Offset\) 即可為更多固定配置區域定址。  
  
 如果固定配置的大小大於或等於一個記憶體分頁，則必須在修改 RSP 之前呼叫 Helper 函式。  這個 Helper \(\_\_chkstk\) 負責探查 \(Probe\) 所要配置的堆疊範圍，以確定堆疊已適當地擴充。  在這個情況下，先前的初構範例會改為：  
  
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
  
 \_\_chkstk Helper 不會修改 R10、R11 及條件碼以外的暫存器。  特別是，它會原封不動地傳回 RAX，並且將所有靜態暫存器和傳遞引數的暫存器都維持不變。  
  
 終解程式碼 \(Epilog Code\) 存在於每個函式的結束之處。  通常初構只有一個，但終解可以有很多個。  終解程式碼會將堆疊修剪成固定的配置大小 \(必要時\)、解除配置固定的堆疊配置、從堆疊中移除已儲存的值以還原靜態暫存器，然後再傳回。  
  
 終解程式碼必須遵守嚴格的規則集合，回溯程式碼才能可靠地回溯例外狀況和中斷。  這樣可以減少所需的回溯資料數量，因為不需要額外的資料來描述每一個終解。  相反地，回溯程式碼可以利用掃描程式資料流以識別終解的方式，判斷終解是否正在執行。  
  
 如果函式中未使用框架指標，則終解必須先解除配置堆疊的固定部分，再移除靜態暫存器，然後控制權就會回到呼叫函式。  例如：  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 如果函式使用框架指標，就必須在執行終解之前，先將堆疊修剪成固定的配置。  這在技術方面並不屬於終解的一部分。  例如，您可以使用下列終解來復原先前使用的初構：  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 實際上，使用框架指標時，並不建議執行兩個步驟來調整 RSP，所以會改用下列終解：  
  
```  
lea      RSP, fixed-allocation-size – 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 這是唯一合法的終解形式。  它必須含有 `add RSP,constant` 或 `lea RSP,constant[FPReg]`，後面接著一串零或更多的 8 位元組暫存器移除 \(Pop\)，以及傳回值 \(Return\) 或 jmp  \(終解中只允許一個 jmp 陳述式的子集。  這些陳述式的類別全都是 jmp 加上 ModRM 記憶體參考，其中 ModRM mod 欄位的值為 00。  在具有 ModRM mod 欄位值 01 或 10 的終解中，禁止使用 jmp。  如需允許之 ModRM 參考的詳細資訊，請參閱《AMD x86\-64 Architecture Programmer's Manual Volume 3: General Purpose and System Instructions》中的表格 A\-15\)。  其他程式碼都不能出現。  請特別注意，終解內不能有任何排程，包括載入傳回值。  
  
 注意，未使用框架指標時，終解必須使用 `add RSP,constant` 來解除配置堆疊的固定部分，  不能改用 `lea RSP,constant[RSP]`。  這個限制能讓回溯程式碼在搜尋終解時，需要辨識的模式變少。  
  
 遵循這些規則讓回溯程式碼可以判斷終解目前正在執行，並且能夠模擬執行終解的其餘部分，以重新建立呼叫函式的內容。  
  
## 請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)