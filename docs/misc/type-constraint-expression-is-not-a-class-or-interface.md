---
title: "類型條件約束 &#39;&lt;運算式&gt;&#39; 不是類別或介面 | Microsoft Docs"
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
  - "bc32048"
  - "vbc32048"
helpviewer_keywords: 
  - "BC32048"
ms.assetid: 68811886-44ac-43e1-9315-b39857310033
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型條件約束 &#39;&lt;運算式&gt;&#39; 不是類別或介面
條件約束清單包含運算式，此運算式不表示類型參數上有效的條件約束。  
  
 條件約束清單會對傳遞至類型參數的類型引數強制一些必要需求。 您可以利用任意組合指定下列需求：  
  
-   類型引數必須實作一或多個介面  
  
-   類型引數最多只能繼承自一個類別  
  
-   類型引數必須公開建立程式碼可以存取的無參數建構函式  
  
-   類型引數必須是參考類型，或必須是實值類型  
  
 **錯誤 ID：**BC32048  
  
### 更正這個錯誤  
  
-   驗證是否有正確拼寫運算式與它的項目。  
  
-   如果運算式不符合上述的需求清單，請將它從條件約束清單中移除。  
  
-   如果運算式參考介面或類別，請驗證編譯器是否有權存取該介面或類別。 您可能需要限定其名稱，而且也可能需要將參考加入專案中。 如需詳細資訊，請參閱 [NOTINBUILD：當多個變數擁有相同名稱時解析參考](http://msdn.microsoft.com/zh-tw/9601e39f-1911-44e1-ace5-3f6e090408b9)中＜專案參考＞的內容。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [NOTINBUILD 如何：限定宣告的項目名稱](http://msdn.microsoft.com/zh-tw/6bd112f5-df6f-42b8-9427-a9225bfcbaab)   
 [How to: Add and Remove Project References](http://msdn.microsoft.com/zh-tw/f51b784d-0bc8-4c19-a898-e560d5ed696b)