---
title: "成員 &#39;&lt;成員名稱&gt;&#39; 隱含地定義成員 &#39;&lt;隱含成員名稱&gt;&#39;，而後者的名稱與類型參數相同。 | Microsoft Docs"
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
  - "BC32070"
  - "vbc32070"
helpviewer_keywords: 
  - "BC32070"
ms.assetid: cc0b3fcf-c141-47e2-9b33-d2b91c8bf2d6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 成員 &#39;&lt;成員名稱&gt;&#39; 隱含地定義成員 &#39;&lt;隱含成員名稱&gt;&#39;，而後者的名稱與類型參數相同。
泛型類別的成員會產生與類別之類型參數同名的隱含成員。  
  
 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器會建立與所宣告之特定程式設計項目對應的隱含成員。 下表摘要說明這些隱含或*「綜合」*\(synthetic\) 成員。  
  
|宣告項目|隱含建立的成員|  
|----------|-------------|  
|列舉|`value__` 成員|  
|事件|`add_<eventname>` 程序<br /><br /> `remove_<eventname>` 程序<br /><br /> `<eventname>Event` 欄位<br /><br /> `<eventname>EventHandler` 委派|  
|屬性|`get_<propertyname>` 程序<br /><br /> `set_<propertyname>` 程序|  
|`My.` 集合變數|`m_<variablename>` `Static` 變數<br /><br /> `<variablename>` 屬性<br /><br /> `get_<variablename>` 程序<br /><br /> `set_<variablename>` 程序|  
|`WithEvents` 變數|`_<variablename>` 變數<br /><br /> `<variablename>` 屬性<br /><br /> `get_<variablename>` 程序<br /><br /> `set_<variablename>` 程序|  
  
 因為名稱可能會衝突，所以您應該避免使用與任何這些隱含成員相同的格式來命名任何宣告的程式設計項目。 例如，您應該避免任何開頭為 `get_` 或 `set_` 的項目名稱。  
  
 **錯誤 ID︰**BC32070  
  
### 更正這個錯誤  
  
-   如果類型參數的名稱具有彈性，請變更它，以避免與上表所列的名稱衝突。  
  
-   如果類型參數必須保留其名稱，請變更類別成員的名稱，以避免與上表所列的名稱衝突。  
  
## 請參閱  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)