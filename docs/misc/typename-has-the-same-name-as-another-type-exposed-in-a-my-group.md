---
title: "&#39;&lt;類型名稱&gt;&#39; 與在 &#39;My&#39; 群組公開的另一個類型有相同的名稱 | Microsoft Docs"
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
  - "vbc36015"
  - "bc36015"
helpviewer_keywords: 
  - "BC36015"
ms.assetid: cd2286da-49be-461f-bec9-58e9c53e250b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類型名稱&gt;&#39; 與在 &#39;My&#39; 群組公開的另一個類型有相同的名稱
'\<類型名稱\>' 與在 'My' 群組公開的另一個類型有相同的名稱。 請重新命名表單或它的封入命名空間。  
  
 類別或結構宣告成與其中一個 `My` 物件中的類別或結構同名。  
  
 無法避免兩個類別之間的名稱衝突，這兩個類別可透過 `My` 物件 \(例如 `My.Forms`\) 存取。  
  
 如果 `My` 物件的類別之間有潛在的名稱衝突，則編譯器會將類型的屬性名稱從 *ClassName* 變更為 *RootNamespace*\_*Namespace*\_*ClassName*。 例如，請考慮使用兩個名為 `Form1` 的表單。 如果其中一個表單是在根命名空間 `WindowsApplication1` 和命名空間 `Namespace1` 中，則可以透過 `My.Forms.WindowsApplication1_Namespace1_Form1` 來存取該表單。  
  
 如果兩個類別同名，而且位在名稱中有底線的巢狀命名空間中，則會發生這個錯誤。 編譯器建構類別的新屬性名稱時，還是會發生名稱衝突。  
  
 **錯誤 ID︰**BC36015  
  
### 更正這個錯誤  
  
1.  重新命名新的表單。  
  
2.  重新命名命名空間。  
  
     避免將任何類別或結構命名成與現有類別或結構同名。  
  
## 請參閱  
 <xref:System.Windows.Forms.Form>   
 <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>   
 [NOTINBUILD：當多個變數擁有相同名稱時解析參考](http://msdn.microsoft.com/zh-tw/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [My.Forms Object](../Topic/My.Forms%20Object.md)