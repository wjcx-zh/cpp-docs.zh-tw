---
title: "The custom tool &#39;custom tool&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.generator_fail_errorinfo"
ms.assetid: e846b946-a123-49fe-b4bc-a7bbda501417
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The custom tool &#39;custom tool&#39; failed. &lt;reason&gt;
自訂工具未成功執行。  
  
 如果在更新包含 N\-Tier 資料集的專案時遇到 MSDataSetGenerator 錯誤，您必須在更新所有專案後重新執行自訂工具。  
  
 自訂工具 'MSDataSetGenerator' 失敗。  \<資料集名稱\> 中 DataSetProject 屬性所指定專案的目標 .NET Framework 版本必須等於或大於目前專案。  
  
### 若要修正 N\-Tier 資料集中的 MSDataSetGenerator 錯誤  
  
-   以滑鼠右鍵按一下 \[方案總管\] 中的 .xsd 檔，然後按一下 \[**執行自訂工具**\]。