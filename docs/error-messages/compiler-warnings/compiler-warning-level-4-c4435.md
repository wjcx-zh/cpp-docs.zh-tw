---
title: "編譯器警告 (層級 4) C4435 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# 編譯器警告 (層級 4) C4435
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class1' : \/vd2 底下的物件配置將因虛擬基底 'class2' 而變更  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 在預設編譯的 \/vd1 選項，衍生類別沒有指示虛擬基底的 `vtordisp` 欄位。如果 \/vd2 或 `#pragma vtordisp(2)` 生效， `vtordisp` 欄位會出現，變更物件配置。如果互動的編譯的模組不同的 `vtordisp` 設定，這會導致二進位碼相容性問題。  
  
## 範例  
 下列範例會產生 C4435。  
  
```cpp  
// C4435.cpp  
// compile with: /c /W4  
#pragma warning(default : 4435)  
class A  
{  
public:  
    virtual ~A() {}  
};  
  
class B : public virtual A  // C4435  
{};  
```  
  
## 請參閱  
 [vtordisp](../../preprocessor/vtordisp.md)   
 [\/vd \(停用建構替代\)](../../build/reference/vd-disable-construction-displacements.md)