---
title: "名稱 &#39;&lt;名稱&gt;&#39; 未宣告或不在目前範圍 | Microsoft Docs"
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
  - "vbc36610"
  - "bc36610"
helpviewer_keywords: 
  - "BC36610"
ms.assetid: e66a4b8a-9252-42ae-a30d-341fad4f74be
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 名稱 &#39;&lt;名稱&gt;&#39; 未宣告或不在目前範圍
LINQ 查詢參考了程式設計項目，但編譯器找不到具有相同名稱的項目。  
  
 **錯誤 ID︰**BC36610  
  
### 更正這個錯誤  
  
1.  請檢查參考陳述式中的名稱拼寫。[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 不區分大小寫，但拼字的任何其他變化會視為不同的名稱。 請注意，底線 \(`_`\) 是名稱的一部分，因此也是拼字的一部分。  
  
2.  請確認程式設計項目在範圍中。 如果參考陳述式是在宣告程式設計項目的區域之外，您可能必須限定項目名稱。 如需詳細資訊，請參閱[Scope in Visual Basic](../Topic/Scope%20in%20Visual%20Basic.md)。  
  
3.  請確定您在物件和其成員之間有成員存取運算子 \(`.`\)。 例如，如果您有 <xref:System.Windows.Forms.TextBox> 控制項，名為 `TextBox1`，那麼要存取它的 <xref:System.Windows.Forms.TextBoxBase.Text%2A> 屬性，您應該輸入 `TextBox1.Text`。 如果您改為輸入 `TextBox1Text`，便會建立不同的名稱。  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [Visual Basic Naming Conventions](../Topic/Visual%20Basic%20Naming%20Conventions.md)   
 [References to Declared Elements](../Topic/References%20to%20Declared%20Elements%20\(Visual%20Basic\).md)