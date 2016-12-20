---
title: "容器類別::rend | Microsoft Docs"
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
  - "rend 方法"
ms.assetid: 80f3dd04-dd2c-4b52-b0ed-d567ec5d186c
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 容器類別::rend
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題將 Visual C\+\+ 文件做為用於 Standard C\+\+ 程式庫的容器的非執行的範例。  如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
 成員函式傳回的序列中的第一個項目的反向 Iterator \(或超出空序列的結尾\)，會指定反向序列的結尾。  
  
## 語法  
  
```  
  
      const_reverse_iterator rend( ) const;   
reverse_iterator rend( );  
```  
  
## 請參閱  
 [範例容器類別](../standard-library/sample-container-class.md)