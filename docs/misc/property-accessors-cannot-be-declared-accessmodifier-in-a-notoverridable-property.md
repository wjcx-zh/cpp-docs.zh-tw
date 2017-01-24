---
title: "屬性存取子在 &#39;NotOverridable&#39; 屬性中不可以宣告為 &#39;&lt;存取修飾詞&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31106"
  - "bc31106"
helpviewer_keywords: 
  - "BC31106"
ms.assetid: 84bcb157-9c33-4e4f-89a9-c5e6cb73028b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性存取子在 &#39;NotOverridable&#39; 屬性中不可以宣告為 &#39;&lt;存取修飾詞&gt;&#39;
`NotOverridable` 屬性中的 [Get Statement](../Topic/Get%20Statement.md)或 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md) 包含 `Private` 關鍵字。  
  
 下列幾行推論說明無法在 [Property Statement](../Topic/Property%20Statement.md)中搭配使用 `NotOverridable` 和 `Private` 的原因：  
  
1.  未覆寫基底類別屬性或程序的屬性或程序具有預設值 [NotOverridable](../Topic/NotOverridable%20\(Visual%20Basic\).md)。  
  
2.  但是，覆寫基底類別屬性或程序之衍生類別中的屬性或程序具有預設值 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)。 若要終止覆寫的階層架構，您可以將它宣告為 `NotOverridable`。 這是您可以使用 `NotOverridable` 的唯一內容。 也就是說，您只能搭配 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md) 使用 `NotOverridable`。  
  
3.  如果基底類別屬性或程序宣告為[Private](../Topic/Private%20\(Visual%20Basic\).md)，衍生的類別就不能覆寫該屬性或程序，因為無法存取它。 因此，您無法搭配 `Overridable` 使用 `Private`。  
  
4.  若要覆寫屬性或程序，覆寫屬性或程序不僅必須具有完全相同的簽章，也必須具有相同的存取層級。 這表示覆寫屬性或程序無法指定 `Private`，因為可覆寫的屬性或程序無法指定 `Private`。  
  
5.  由於您只能在覆寫屬性或程序上指定 `NotOverridable`，因此無法搭配 `Private` 使用。  
  
 同理可證，覆寫屬性的個別屬性程序 \(`Get` 和 `Set`\) 不可為 `Private`。  
  
 **錯誤 ID︰**BC31106  
  
### 更正這個錯誤  
  
-   從 `Get` 或 `Set` 陳述式中移除 `Private` 關鍵字，或從 `Property` 陳述式中移除 `Overrides` 和 `NotOverridable` 關鍵字。  
  
## 請參閱  
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [Differences Between Shadowing and Overriding](../Topic/Differences%20Between%20Shadowing%20and%20Overriding%20\(Visual%20Basic\).md)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)