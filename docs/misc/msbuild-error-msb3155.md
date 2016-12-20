---
title: "MSBuild 錯誤 MSB3155 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.ProductNotFound"
helpviewer_keywords: 
  - "MSB3155"
ms.assetid: 59bf2293-ef13-4bb1-8f29-5d6966bbe313
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3155
**MSBuild 錯誤 MSB3155: 在 '\<path\>' 中找不到項目 '\<package\>'。**  
  
 在啟動載入器 \(Bootstrapper\) 快取中找不到具有指定之 <xref:Microsoft.Build.Tasks.Deployment.Bootstrapper.Product.ProductCode%2A> 的套件時，就會發生這個警告訊息。  
  
> [!NOTE]
>  Microsoft Data Access Components \(MDAC\) 不再是啟動載入器 \(Bootstrapper\) 套件的一部分。  您可以從 [Microsoft Windows Update](http://go.microsoft.com/fwlink/?LinkId=86676) 網站下載這些 MDAC。  
  
### 若要更正這個錯誤  
  
-   將要安裝的套件清單中的套件移除，或是新增套件至快取。  此外，請確認資訊清單使用有效的 XML 標記且格式正確。  
  
## 請參閱  
 [產品和封裝結構描述參考](../Topic/Product%20and%20Package%20Schema%20Reference.md)   
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)   
 [必要條件對話方塊](../Topic/Prerequisites%20Dialog%20Box.md)   
 [建立啟動載入器套件](../Topic/Creating%20Bootstrapper%20Packages.md)