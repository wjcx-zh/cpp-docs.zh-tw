---
title: "如何：強制載入 VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage, 強制載入"
  - "VSPackage, 載入"
ms.assetid: 05f4dc3f-3c9a-45ea-96da-986553b5c5f2
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# 如何：強制載入 VSPackage
VSPackages 通常會在其所附的功能，才能完成處理程序時，才載入。  不過，在某些情況下，VSPackage 可能必須強制另一個要載入的 VSPackage。  比方說，輕量級 VSPackage 可能會載入較大的 VSPackage 中程式設計的內容，並不是 CMDUIContext。  
  
 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>方法，以強制載入的 VSPackage。  
  
### 若要強制載入 VSPackage  
  
-   插入這個程式碼複製到<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>會強制載入另一個 VSPackage VSPackage 的方法：  
  
     [!code-cs[ForceVSPackageLoad#01](../misc/codesnippet/CSharp/how-to-force-a-vspackage-to-load_1.cs)]  
  
     當初始化 VSPackage 時，它會強制`PackageToBeLoaded`載入。  
  
## 穩固程式設計  
 強制載入不適用於 VSPackage 的通訊。  請改用 [使用並提供服務](../Topic/Using%20and%20Providing%20Services.md)。  
  
## 請參閱  
 [管理 Vspackage](../Topic/Managing%20VSPackages.md)   
 [Vspackage](../Topic/VSPackages.md)