---
title: "警告：在同一個相依組件的不同版本之間發現衝突 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResolveAssemblyReference.SuggestedRedirects"
ms.assetid: fd14a789-bbdf-46c7-bcd3-9d3165adf96d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 警告：在同一個相依組件的不同版本之間發現衝突
如果專案的相依性圖形包含同一個組件不同版本的參考，就會顯示這個警告。  
  
 如果您有 app.config 檔，則 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 可讓您在其中加入繫結重新導向。  繫結重新導向會強制所有組件參考重新導向至組件的較高版本號碼。[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 會將重新導向資訊儲存在 app.config 中。  如果您使用繫結重新導向，這個警告就不會再出現。  
  
 如果您決定不加入繫結重新導向，專案仍會參考先前同一個組件版本。  但是，這個警告仍會出現。  
  
### 若要更正這個錯誤  
  
-   按兩下警告，當出現 \[您要在 app.config 檔中加入繫結重新導向記錄以修正這些衝突嗎?\] 提示時，選取 \[是\]。