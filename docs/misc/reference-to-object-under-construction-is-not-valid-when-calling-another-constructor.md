---
title: "呼叫其他建構函式時，參考建構中的物件是無效的 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31095"
  - "vbc31095"
helpviewer_keywords: 
  - "BC31095"
ms.assetid: 68be49f1-e662-45c7-9998-e0006324535d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 呼叫其他建構函式時，參考建構中的物件是無效的
在物件的建構函式建立好物件之前，已建立對該物件成員的參考。  
  
 **錯誤 ID：**BC31095  
  
### 更正這個錯誤  
  
-   從另一個建構函式呼叫建構函式時，請勿使用 `MyBase`、`MyClass` 或 `Me`。  
  
## 請參閱  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)