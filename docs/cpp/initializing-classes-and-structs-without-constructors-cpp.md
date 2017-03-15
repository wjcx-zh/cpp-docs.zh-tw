---
title: "在沒有建構函式的情況下初始化類別和結構 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在沒有建構函式的情況下初始化類別和結構 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您不一定需要定義類別的建構函式，尤其是相當簡單的類別。  使用者可以使用統一初始化來初始化類別或結構的物件 \(如下列範例所示\)：  
  
```  
struct TempData  
{  
    int StationId;  
    time_t time;  
    double current;  
    double max;  
    double min;  
};  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    // Member initialization:  
    TempData td { 45978, GetCurrentTime(), 28.9, 37.0, 16.7 };  
  
    // Default initialization = {0,0,0,0,0}  
    TempData td_default {};  
  
    //Error C4700 uninitialized local variable  
    TempData td_noInit;   
    return 0;  
}  
```  
  
## 請參閱  
 [類別和結構](../cpp/classes-and-structs-cpp.md)   
 [建構函式](../cpp/constructors-cpp.md)