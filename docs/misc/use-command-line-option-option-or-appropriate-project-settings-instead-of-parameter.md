---
title: "請用命令列選項 &#39;&lt;選項&gt;&#39; 或適當的專案設定取代 &#39;&lt;參數&gt;&#39; | Microsoft Docs"
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
  - "bc41008"
  - "vbc41008"
helpviewer_keywords: 
  - "BC41008"
ms.assetid: 1c5d6d7a-b767-4dae-aa61-d7fa81d5aad1
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 請用命令列選項 &#39;&lt;選項&gt;&#39; 或適當的專案設定取代 &#39;&lt;參數&gt;&#39;
若要指定一個檔案，以包含組件的公開金鑰、組件的公開金鑰容器或部分簽署的組件，最好是使用 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器選項。 不建議在您的程式碼中使用 <xref:System.Reflection.AssemblyKeyFileAttribute>、<xref:System.Reflection.AssemblyKeyNameAttribute> 或 <xref:System.Reflection.AssemblyDelaySignAttribute> 屬性。  
  
 **錯誤 ID︰**BC41008  
  
### 更正這個錯誤  
  
1.  在您的程式碼中使用 [\/keyfile](../Topic/-keyfile.md)、[\/keycontainer](../Topic/-keycontainer.md) 或 [\/delaysign](../Topic/-delaysign.md)[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 編譯器選項，而不是 <xref:System.Reflection.AssemblyKeyFileAttribute>、<xref:System.Reflection.AssemblyKeyNameAttribute> 或 <xref:System.Reflection.AssemblyDelaySignAttribute> 屬性。  
  
## 請參閱  
 [如何：建立簽署的 Friend 組件](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](../Topic/Visual%20Basic%20Command-Line%20Compiler.md)   
 [\/keyfile](../Topic/-keyfile.md)   
 [\/keycontainer](../Topic/-keycontainer.md)   
 [\/delaysign](../Topic/-delaysign.md)