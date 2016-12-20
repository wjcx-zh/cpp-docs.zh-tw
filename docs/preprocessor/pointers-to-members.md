---
title: "pointers_to_members | Microsoft Docs"
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
  - "pointers_to_members_CPP"
  - "vc-pragma.pointers_to_members"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "類別成員, 其指標"
  - "成員, 其指標"
  - "pointers_to_members pragma"
  - "Pragma, pointers_to_members"
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pointers_to_members
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 指定類別成員的指標是否可以在其相關類別定義之前宣告，並用來控制解譯指標所需的指標大小和程式碼。  
  
## 語法  
  
```  
  
#pragma pointers_to_members( pointer-declaration, [most-general-representation] )  
```  
  
## 備註  
 您可以將 **pointers\_to\_members** pragma 放置在原始程式檔中，而無需使用 [\/vmx](../build/reference/vmb-vmg-representation-method.md) 編譯器選項或[繼承關鍵字](../cpp/inheritance-keywords.md)。  
  
 *pointer\-declaration* 引數指定您是在關聯的函式定義之前或之後宣告成員的指標。  *pointer\-declaration* 引數為下列兩個符號之一：  
  
|引數|註解|  
|--------|--------|  
|**full\_generality**|產生安全但有時並非是最佳化的程式碼。  如果是在關聯的類別定義之前宣告成員指標，則可以使用 **full\_generality**。  這個引數一定會使用由 *most\-general\-representation* 引數所指定的指標表示。  等於 \/vmg。|  
|**best\_case**|使用所有成員指標的 best\-case 表示，產生安全且最佳化的程式碼。  需要在宣告類別成員的指標之前先定義類別。  預設為 **best\_case**。|  
  
 *most\-general\-representation* 引數指定編譯器可以安全地使用轉譯單位中任何類別成員指標參考的最小指標表示。  這些引數可以是下列其中一項：  
  
|引數|註解|  
|--------|--------|  
|**single\_inheritance**|最常見的表示是單一繼承的成員函式指標。  如果宣告其成員指標類別定義的繼承模型為多重或虛擬，則會產生錯誤。|  
|**multiple\_inheritance**|最常見的表示是多重繼承的成員函式指標。  如果宣告其成員指標類別定義的繼承模型為虛擬，則會產生錯誤。|  
|**virtual\_inheritance**|最常見的表示是虛擬繼承的成員函式指標。  永遠不會產生錯誤。  使用 **\#pragma pointers\_to\_members\(full\_generality\)** 時，這是預設的引數。|  
  
> [!CAUTION]
>  建議您只將 `pointers_to_members` pragma 放置在您要影響的原始程式碼檔案中，而且只放置在任何 `#include` 指示詞之後。  這種作法可使 pragma 影響到其他檔案的風險降低，否則，您會意外地為相同的變數、函式或類別名稱指定多個定義。  
  
## 範例  
  
```  
//   Specify single-inheritance only  
#pragma pointers_to_members( full_generality, single_inheritance )  
```  
  
## END C\+\+ 特定的  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)