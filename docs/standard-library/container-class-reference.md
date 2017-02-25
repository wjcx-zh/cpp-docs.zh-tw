---
title: "容器類別::reference | Microsoft Docs"
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
  - "reference 方法"
ms.assetid: ab85a9fb-c628-4761-9a5f-a0231fad7690
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 容器類別::reference
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題將 Visual C\+\+ 文件做為用於 Standard C\+\+ 程式庫的容器的非執行的範例。  如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
 描述可以做為受控制序列的項目之參考的物件。  
  
## 語法  
  
```  
  
typedef T2 reference;  
  
```  
  
## 備註  
 它會說明此為未指定型別的 **T2** \(通常 **Alloc::reference**\) 同義字。  型別 **reference** 物件可以轉換成型別的 [const\_reference](../standard-library/container-class-const-reference.md)物件。  
  
## 請參閱  
 [範例容器類別](../standard-library/sample-container-class.md)