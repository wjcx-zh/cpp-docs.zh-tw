---
title: "容器類別::swap | Microsoft Docs"
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
  - "swap 方法"
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 容器類別::swap
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題將 Visual C\+\+ 文件做為用於 Standard C\+\+ 程式庫的容器的非執行的範例。  如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
 交換 **\*this** 和 `_Right`的控制順序。  
  
## 語法  
  
```  
  
      void swap(  
   Container& _Right  
);  
```  
  
## 備註  
 如果 **get\_allocator \=\=** `_Right`**.get\_allocator**，它在常數時間如此做。  否則，它會執行許多工作項目，而且建構函式呼叫比例與項目數目兩個受控制序列的。  
  
## 請參閱  
 [範例容器類別](../standard-library/sample-container-class.md)