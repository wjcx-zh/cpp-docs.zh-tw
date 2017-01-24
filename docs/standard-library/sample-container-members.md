---
title: "範例容器成員 | Microsoft Docs"
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
helpviewer_keywords: 
  - "容器類別"
ms.assetid: dc5a1998-a31b-4adf-b888-8abe5b87a4e0
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 範例容器成員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題將 Visual C\+\+ 文件做為用於 Standard C\+\+ 程式庫的容器的非執行的範例。  如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
## 參考  
  
## Typedef  
  
|||  
|-|-|  
|[const\_iterator](../standard-library/container-class-const-iterator.md)|描述可以當做常數 Iterator Base 受控制序列的物件。|  
|[const\_reference](../standard-library/container-class-const-reference.md)|描述可以做為受控制序列的項目之常數參考的物件。|  
|[const\_reverse\_iterator](../standard-library/container-class-const-reverse-iterator.md)|描述可以當做常數反向 Iterator Base 受控制序列的物件。|  
|[difference\_type](../standard-library/container-class-difference-type.md)|描述可代表任何兩個項目之間的差異超過受控制序列的物件。|  
|[Iterator](../standard-library/container-class-iterator.md)|描述可以當做 Iterator Base 受控制序列的物件。|  
|[參照](../standard-library/container-class-reference.md)|描述可以做為受控制序列的項目之參考的物件。|  
|[reverse\_iterator](../standard-library/container-class-reverse-iterator.md)|描述能以反向 Iterator Base 受控制序列的物件。|  
|[size\_type](../standard-library/container-class-size-type.md)|描述可以表示的所有受控制序列的物件。|  
|[value\_type](../standard-library/container-class-value-type.md)|動作樣板參數 **Ty**的同義字。|  
  
## 成員函式  
  
|||  
|-|-|  
|[begin](../standard-library/container-class-begin.md)|傳回的序列中的第一個項目的 Iterator \(或超出空序列的結尾\)。|  
|[clear](../standard-library/container-class-clear.md)|呼叫 [啟動](../standard-library/container-class-begin.md)， [清除](../standard-library/container-class-erase.md)\( [結束](../standard-library/container-class-end.md)\)。|  
|[empty](../standard-library/container-class-empty.md)|傳回一個空的受控制序列的 **true** 。|  
|[end](../standard-library/container-class-end.md)|傳回序列中的結尾點的 Iterator。|  
|[清除](../standard-library/container-class-erase.md)|清除項目。|  
|[max\_size](../standard-library/container-class-max-size.md)|不論受控制序列的長度，傳回物件可以控制最長的長度，以常數時間。|  
|[rbegin](../standard-library/container-class-rbegin.md)|傳回在受控制序列之結尾點的反向 Iterator，會指定反向序列的開頭。|  
|[rend](../standard-library/container-class-rend.md)|成員函式傳回的序列中的第一個項目的反向 Iterator \(或超出空序列的結尾\)，會指定反向序列的結尾。|  
|[size](../standard-library/container-class-size.md)|不論受控制序列的長度，傳回受控制序列的長度，以常數時間。|  
|[交換](../standard-library/container-class-swap.md)|交換 **\*this** 和 `_Right`的控制順序。|