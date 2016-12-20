---
title: "VSPackage 和 Managed 封裝架構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Managed 封裝架構"
  - "VSPackage, Managed 封裝架構"
  - "Managed VSPackage, Managed 封裝架構"
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# VSPackage 和 Managed 封裝架構
您可以藉由建立 VSPackage 與受管理的套件架構 \(MPF\) 類別，而不是使用 COM interop 類別來減少開發時間。  
  
 有兩種方式可以建立受管理的 VSPackage：  
  
-   使用[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]封裝專案範本  
  
     如需詳細資訊，請參閱 [逐步解說：使用 Visual Studio 封裝範本建立功能表命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
-   建置您的 VSPackage，而不[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]封裝專案範本  
  
     比方說，您可以複製範例 VSPackage，並變更 Guid 和名稱。  您可以找到範例 VSX\] 部分中[程式碼庫](http://code.msdn.microsoft.com/vsx/)。  
  
## 在本節中  
 [Managed 封裝架構類別](../misc/managed-package-framework-classes.md)  
 告訴您，並列出 MPF 類別的命名空間和 DLL 檔案。  
  
## 相關章節  
 [逐步解說：使用 Visual Studio 封裝範本建立功能表命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)  
 說明如何建立受管理的 VSPackage。  
  
 [Managed VSPackage](../misc/managed-vspackages.md)  
 介紹 VSPackages 適用於 managed 程式碼的層面。