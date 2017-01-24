---
title: "成員 &#39;&lt;成員名稱1&gt;&#39; 隱含宣告 &#39;&lt;隱含成員名稱&gt;&#39;，它與基底類別 &#39;&lt;基底類別名稱&gt;&#39; 中的成員產生衝突 | Microsoft Docs"
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
  - "vbc40022"
  - "bc40022"
helpviewer_keywords: 
  - "BC40022"
ms.assetid: be5bb2ee-2274-42b2-b843-179b14127b34
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 成員 &#39;&lt;成員名稱1&gt;&#39; 隱含宣告 &#39;&lt;隱含成員名稱&gt;&#39;，它與基底類別 &#39;&lt;基底類別名稱&gt;&#39; 中的成員產生衝突
成員 '\<成員名稱1\>' 隱含宣告 '\<隱含成員名稱\>'，它與基底類別 '\<基底類別名稱\>' 中的成員產生衝突，因此，成員不應該宣告為 'Overloads'  
  
 衍生類別中的屬性會使用與基底類別之成員相同的名稱來產生隱含成員，並指定 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 關鍵字。  
  
 多載可用於在同一個類別中定義屬性或程序的多個版本。 除非基底類別成員已指定 `Overloads`，否則您無法定義基底類別成員的其他版本。 因為衝突的基底類別成員未指定 `Overloads`，所以編譯器會假設這個屬性為 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) 隱含基底類別成員。  
  
 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器會建立與所宣告之特定程式設計項目對應的隱含成員。 下表摘要說明這些隱含或*「綜合」*\(synthetic\) 成員。  
  
|宣告項目|隱含建立的成員|  
|----------|-------------|  
|列舉|`value__` 成員|  
|事件|`add_<eventname>` 程序<br /><br /> `remove_<eventname>` 程序<br /><br /> `<eventname>Event` 欄位<br /><br /> `<eventname>EventHandler` 委派|  
|屬性|`get_<propertyname>` 程序<br /><br /> `set_<propertyname>` 程序|  
|`My.Form` 成員、`My.WebService` 成員，或以 <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute> 屬性標記之類別的成員|`m_<variablename>` `Static` 變數<br /><br /> `<variablename>` 屬性<br /><br /> `get_<variablename>` 程序<br /><br /> `set_<variablename>` 程序|  
|`WithEvents` 變數|`_<variablename>` 變數<br /><br /> `<variablename>` 屬性<br /><br /> `get_<variablename>` 程序<br /><br /> `set_<variablename>` 程序|  
  
 因為有名稱衝突的風險，所以您應該避免使用與任何一個隱含成員相同的格式來命名任何宣告的程式設計項目。 例如，您應該避免任何開頭為 `get_` 或 `set_` 的項目名稱。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **錯誤 ID︰**BC40022  
  
### 更正這個錯誤  
  
-   如果您想要隱藏或遮蔽基底類別成員，請在屬性的宣告中以 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) 關鍵字取代 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 關鍵字。  
  
-   如果您不想要遮蔽基底類別成員，請變更屬性的名稱，以避免上表所述的名稱衝突。  
  
## 請參閱  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)