---
title: "必須是識別項，前面加上句號 | Microsoft Docs"
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
  - "bc36576"
  - "vbc36576"
helpviewer_keywords: 
  - "BC36576"
ms.assetid: 02217cc4-8972-4a6d-97a6-4ecbb7399af2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是識別項，前面加上句號
在未指派給屬性名稱的情況下，無法推斷屬性名稱的值已包括在匿名類型宣告的初始設定式清單中。  
  
```  
' Not valid. ' Dim anon1 = New With {.grade = 100, 95}  
```  
  
 **錯誤 ID︰**BC36576  
  
### 更正這個錯誤  
  
-   提供初始設定式清單中每個值的屬性名稱 \(如下列程式碼所示\)：  
  
    ```  
    Dim anon2 = New With {.grade1 = 100, .grade2 = 95}  
    ```  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [如何：宣告匿名類型的執行個體 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)