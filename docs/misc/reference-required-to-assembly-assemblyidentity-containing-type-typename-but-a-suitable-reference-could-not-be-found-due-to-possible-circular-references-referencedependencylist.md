---
title: "需要組件 &#39;&lt;組件識別&gt;&#39; (包含類型 &#39;&lt;類型名稱&gt;&#39;) 的參考，但找不到適合的參考，因為可能有循環參考: &lt;參考相依性清單&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30962"
  - "vbc30962"
helpviewer_keywords: 
  - "BC30962"
ms.assetid: 6f338158-bfb4-4cc0-bbf7-1111c708613c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 需要組件 &#39;&lt;組件識別&gt;&#39; (包含類型 &#39;&lt;類型名稱&gt;&#39;) 的參考，但找不到適合的參考，因為可能有循環參考: &lt;參考相依性清單&gt;
運算式使用專案外部定義的類型 \(例如類別、結構、介面、列舉或委派\)。 不過，您專案對該組件的參考是一組循環參考的一部分。  
  
 數個專案彼此參考時，參考可能是*「循環」*\(circular\)。 例如，兩個專案可以彼此參考。 一般來說，從某個專案到下一個專案的一連串參考最後會傳回給起始專案。 在這類情況下，沒有用來解析參考之鏈結結尾的最後專案。  
  
 若要存取另一個組件中所定義的類型，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID︰**BC30962  
  
### 更正這個錯誤  
  
-   在專案屬性中，加入產生組件之專案的直接參考，而這個組件定義所使用的類型。  
  
## 請參閱  
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB：參考命名空間和元件](http://msdn.microsoft.com/zh-tw/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [中斷參考的疑難排解](../Topic/Troubleshooting%20Broken%20References.md)