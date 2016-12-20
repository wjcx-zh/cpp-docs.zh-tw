---
title: "不能以非陣列類型 &#39;&lt;項目名稱&gt;&#39; 初始化變數 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36536"
  - "bc36536"
helpviewer_keywords: 
  - "BC36536"
ms.assetid: 959415de-164e-4971-aab0-faad315753e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能以非陣列類型 &#39;&lt;項目名稱&gt;&#39; 初始化變數
必須使用陣列值來初始化宣告為陣列的變數。  
  
```  
' Not valid. ' The following line causes this error when executed with Option Strict off. ' Dim arrayVar1() = 10  
```  
  
 **錯誤 ID︰**BC36536  
  
### 更正這個錯誤  
  
-   請使用陣列值來初始化陣列變數：  
  
    ```  
    ' With Option Strict off. Dim arrayVar2() = {1, 2, 3} ' With Option Strict on. Dim arrayVar3() As Integer = {1, 2, 3}  
    ```  
  
## 請參閱  
 [NOTINBUILD 陣列變數](http://msdn.microsoft.com/zh-tw/c2da78bd-6928-46ba-805f-44f819dfaf93)