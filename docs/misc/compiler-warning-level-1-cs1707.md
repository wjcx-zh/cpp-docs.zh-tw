---
title: "編譯器警告 (層級 1) CS1707 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1707"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1707"
ms.assetid: 47b6096e-4e4b-4057-b9d7-4a096139267a
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1707
由於新的語言規則，委派 'DelegateName' 是繫結至 'MethodName1' 而非 'MethodName2'  
  
 C\# 2.0 實作將委派繫結至方法的新規則。 會考慮過去未查看過的其他資訊。 這個警告表示委派現在繫結之方法的多載與之前繫結之方法的多載不同。 您可能會想要確認委派應實際繫結至 'MethodName1' 而非 'MethodName2'。  
  
 如需編譯器如何判斷繫結委派之方法的說明，請參閱[在委派中使用變異數](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)。