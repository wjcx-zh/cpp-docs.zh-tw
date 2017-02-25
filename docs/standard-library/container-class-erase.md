---
title: "容器類別::erase | Microsoft Docs"
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
helpviewer_keywords: 
  - "erase 方法"
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 容器類別::erase
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題將 Visual C\+\+ 文件做為用於 Standard C\+\+ 程式庫的容器的非執行的範例。  如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
 清除項目。  
  
## 語法  
  
```  
  
      iterator erase(  
   iterator _Where   
);  
iterator erase(  
   iterator _First,  
   iterator _Last   
);  
```  
  
## 備註  
 第 10% 成員函式中受控制序列的項目指向 \_Where**.**第二 \+ 成成員函式中受控制序列的項目介於 \[`_First`， `_Last`\)。  兩個指定保持在所有項目外的第一個項目被移除的傳回 Iterator 或 [結束](../standard-library/container-class-end.md) ，如果沒有此類項目存在則為。  
  
 在複製作業擲回例外狀況，成員函式擲回例外狀況。  
  
## 請參閱  
 [範例容器類別](../standard-library/sample-container-class.md)