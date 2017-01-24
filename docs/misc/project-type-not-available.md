---
title: "專案類型無法使用 | Microsoft Docs"
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
  - "vs.projecttypenotavailable"
helpviewer_keywords: 
  - "專案類型無法使用錯誤"
ms.assetid: a579fe75-efa2-4dd0-b5d7-ae106d3aedbd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 專案類型無法使用
這個對話方塊顯示有下列錯誤「無法開啟 \<project\>，因為這個版本的應用程式不支援其專案類型 \<project type\>」。  
  
## 解決方法  
  
-   這個對話方塊之所以出現，是因為找不到開啟指定檔案所需的產品或產品版本。  當您嘗試開啟無法以安裝之 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本所開啟的專案檔時，經常會發生這個錯誤。  例如，嘗試使用 [!INCLUDE[vbprvbxprlong](../misc/includes/vbprvbxprlong_md.md)]開啟 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 專案檔時，將會開啟這個對話方塊。  
  
#### 若要解決這個錯誤  
  
-   請安裝正確版本的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
## 請參閱  
 [移植、移轉和升級 Visual Studio 專案](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md)   
 [專案屬性參考](../Topic/Project%20Properties%20Reference.md)