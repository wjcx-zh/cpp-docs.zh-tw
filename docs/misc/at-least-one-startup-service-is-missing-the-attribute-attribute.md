---
title: "At least one startup service is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_ss_attrib"
ms.assetid: 987c42dc-4394-4b07-b7fa-a8e7afc6fdfb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one startup service is missing the &#39;attribute&#39; attribute
啟始服務需要 ID 屬性 \(Attribute\)，但在 `<Service>` 項目中找不到。  例如：  
  
```  
<Service ID="{0000-0000-0000-00000000-000000000000}"/>  
```  
  
 這表示專案檔已損毀。  
  
 最可能導致這個錯誤的原因是以手動方式編輯專案檔。  
  
 **若要更正這個錯誤**  
  
-   儲存專案檔案。  
  
     有瑕疵的區段將不會被寫出，且下一次開啟專案時不會發生這個錯誤。  
  
## 請參閱  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)