---
title: "operator== (&lt;sample container&gt;) | Microsoft Docs"
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
  - "std.=="
  - "std::=="
  - "operator=="
  - "std.operator=="
  - "std::operator=="
  - "=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "== 運算子, 使用特定 Standard C++ 物件"
  - "運算子 ==, 容器"
  - "operator==, 容器"
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator== (&lt;sample container&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題將 Visual C\+\+ 文件做為用於 Standard C\+\+ 程式庫的容器的非執行的範例。  如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
 多載比較範本兩個物件的 `operator==` 將 [容器](../standard-library/sample-container-class.md)。  
  
## 語法  
  
```  
  
   template<class Ty>  
bool operator==(  
   const Container <Ty>& _Left,  
   const Container <Ty>& _Right  
);  
```  
  
## 傳回值  
 傳回 `_Left`**.**[大小](../standard-library/container-class-size.md) **\=\=** `_Right`**.size && equal**\(\_Left**.**[啟動](../standard-library/container-class-begin.md)，則為 `_Left`。  [結束](../standard-library/container-class-end.md)*， \_Right***.begin**\)。  
  
## 請參閱  
 [\<sample container\>](../standard-library/sample-container.md)