---
title: "建構會間接參考含有 &lt;類型名稱&gt; 的專案 &#39;&lt;專案名稱&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31533"
  - "bc31533"
helpviewer_keywords: 
  - "BC31533"
ms.assetid: e3f55f9f-92be-4ecb-bc8f-9e57049a0805
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 建構會間接參考含有 &lt;類型名稱&gt; 的專案 &#39;&lt;專案名稱&gt;&#39;
建構會間接參考含有 \<類型名稱\> 的專案 '\<專案名稱\>'。 請在您的專案加入 '\<專案名稱\>' 的專案參考。  
  
 運算式或陳述式會存取另一個專案中所定義的類型，但是您的專案未直接參考定義中專案。  
  
 類型可以是類別、結構、介面、模組或列舉。  
  
 定義所指出類型的專案會產生包含該類型的組件。 如果您的專案未直接參考定義中專案，則編譯器無法保證包含類型的組件是在方案中並且可供存取。  
  
 **錯誤 ID︰**BC31533  
  
### 更正這個錯誤  
  
-   判斷哪個專案定義所指出的類型，並加入其專案參考。  
  
## 請參閱  
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB：管理參考](http://msdn.microsoft.com/zh-tw/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)