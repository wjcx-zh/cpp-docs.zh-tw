---
title: "成員存取 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "成員存取, 多載運算子"
  - "成員選取運算子"
  - "運算子多載, 成員存取運算子"
  - "指標, 智慧型"
  - "智慧型指標"
  - "智慧型指標, 定義"
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 成員存取
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別成員存取可以透過多載成員存取運算子 \(**–\>**\) 的方式控制。  在這種用法中，這個運算子會視為一元運算子，而多載運算子函式必須是類別成員函式。  因此，這類函式的宣告如下：  
  
## 語法  
  
```  
  
class-type *operator–>()  
```  
  
## 備註  
 其中 *class\-type* 是這個運算子所屬類別的名稱。  成員存取運算子函式必須是非靜態成員函式。  
  
 這個運算子 \(通常會搭配指標取值運算子\) 會用來實作「智慧型指標」，這類指標會在取值或計數用法之前驗證指標。  
  
 **.** 成員存取運算子無法多載。  
  
## 請參閱  
 [運算子多載](../cpp/operator-overloading.md)