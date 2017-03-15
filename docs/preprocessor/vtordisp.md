---
title: "vtordisp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.vtordisp"
  - "vtordisp_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Pragma, vtordisp"
  - "vtordisp pragma"
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# vtordisp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 加入隱藏 vtordisp 建構函式\/解構函式替代成員的控制項。  
  
## 語法  
  
```cpp  
#pragma vtordisp([push,] n)  
#pragma vtordisp(pop)  
#pragma vtordisp()  
#pragma vtordisp([push,] {on | off})  
```  
  
#### 參數  
 `push`  
 在內部編譯器堆疊上推入目前的 vtordisp 設定，並將新的 vtordisp 設定設為 `n`。如果未指定 `n`，則不會變更目前的 vtordisp 設定。  
  
 `pop`  
 從內部編譯器堆疊中移除最上方的記錄，並將 vtordisp 設定還原為已移除的值。  
  
 `n`  
 為 vtordisp 設定指定新的值。  可能的值為 0、1 或 2，對應到 \/vd0、\/vd1 和 \/vd2 編譯器選項。  如需詳細資訊，請參閱[\/vd \(停用建構替代\)](../build/reference/vd-disable-construction-displacements.md)。  
  
 `on`  
 相當於 `#pragma vtordisp(1)`。  
  
 `off`  
 相當於 `#pragma vtordisp(0)`。  
  
## 備註  
 `vtordisp` pragma 只適用於使用虛擬基底的程式碼。  如果衍生類別會覆寫它從虛擬基底類別繼承的虛擬函式，而且如果衍生類別的建構函式或解構函式會使用虛擬基底類別的指標呼叫函式，編譯器可能會在內含虛擬基底的類別中採用額外的隱藏 `vtordisp` 欄位。  
  
 `vtordisp` pragma 會影響其後類別的配置。  \/vd0、\/vd1 和 \/vd2 選項指定了與完整模組相同的行為。  指定 `0` 或 `off` 會抑制隱藏的 `vtordisp` 成員。  只有在類別的建構函式和解構函式無法呼叫由 `this` 指標所指向物件的虛擬函式時，才關閉 `vtordisp`。  
  
 指定 `1` 或 `on` 時，預設會在所需的位置啟用隱藏的 `vtordisp` 成員。  
  
 指定 `2` 可為所有具有虛擬函式的虛擬基底啟用隱藏的 `vtordisp` 成員。`vtordisp(2)` 可在部分建構的物件上確保 `dynamic_cast` 的正確效能。  如需詳細資訊，請參閱[編譯器警告 \(層級 1\) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)。  
  
 `#pragma vtordisp()` \(不含引數\)，將 vtordisp 設定還原為其初始設定值。  
  
```  
#pragma vtordisp(push, 2)  
class GetReal : virtual public VBase { ... };  
#pragma vtordisp(pop)  
```  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)