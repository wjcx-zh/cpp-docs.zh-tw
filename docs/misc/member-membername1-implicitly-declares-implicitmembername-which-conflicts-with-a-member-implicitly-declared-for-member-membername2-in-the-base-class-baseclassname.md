---
title: "成員 &#39;&lt;成員名稱1&gt;&#39; 隱含宣告 &#39;&lt;隱含成員名稱&gt;&#39;，它與基底類別 &#39;&lt;基底類別名稱&gt;&#39; 中為成員 &#39;&lt;成員名稱2&gt;&#39; 所隱含宣告的成員產生衝突 | Microsoft Docs"
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
  - "vbc40018"
  - "bc40018"
helpviewer_keywords: 
  - "BC40018"
ms.assetid: 43844e55-9ce1-4b88-9aa8-839b37f30e5a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 成員 &#39;&lt;成員名稱1&gt;&#39; 隱含宣告 &#39;&lt;隱含成員名稱&gt;&#39;，它與基底類別 &#39;&lt;基底類別名稱&gt;&#39; 中為成員 &#39;&lt;成員名稱2&gt;&#39; 所隱含宣告的成員產生衝突
成員 '\<成員名稱1\>' 隱含宣告 '\<隱含成員名稱\>'，它與基底類別 '\<基底類別名稱\>' 中為成員 '\<成員名稱2\>' 所隱含宣告的成員產生衝突。 因此該成員應該宣告為 'Shadows'。  
  
 衍生類別的成員會使用與基底類別之隱含成員相同的名稱來產生隱含成員。 因為隱含成員不會指定 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)，所以編譯器會假設這個成員會 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) 隱含基底類別成員。 如果您明確指定這個成員的 `Shadows` 關鍵字，則您的程式碼更容易讀取且不容易發生錯誤。  
  
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
  
 **錯誤 ID︰**BC40018  
  
### 更正這個錯誤  
  
-   如果您想要隱藏或遮蔽隱含的基底類別成員，請在衍生類別成員的宣告中包含 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) 關鍵字。  
  
-   如果您不想要遮蔽隱含的基底類別成員，請變更衍生類別成員的名稱，以避免與上表所列的名稱發生衝突。  
  
## 請參閱  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)