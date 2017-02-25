---
title: "Managed 資源屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManagedResourceCompilerTool.ResourceFileName"
  - "VC.Project.VCManagedResourceCompilerTool.OutputFileName"
  - "VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Managed 資源屬性頁"
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Managed 資源屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

啟用資源編譯器的設定。  
  
 \[**Managed 資源**\] 屬性頁包含下列屬性:  
  
 **資源邏輯名稱**  
 指定所產生中繼 .resources 檔案的「*邏輯名稱*」\(Logical Name\)。  邏輯名稱是用來載入資源的名稱。  如果未指定任何邏輯名稱，則會使用資源 \(.resx\) 檔案名稱做為邏輯名稱。  
  
 **輸出檔名稱**  
 指定資源 \(.resx\) 檔促成的最終輸出檔案名稱。  
  
 **預設的當地語系化資源**  
 指定給定的.resx 檔是否促成預設資源或附屬 .dll。  
  
 如需如何存取 \[**Managed 資源**\] 屬性頁的詳細資訊，請參閱 [如何：使用屬性頁指定專案屬性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
## 請參閱  
 [Using RC \(The RC Command Line\)](http://msdn.microsoft.com/library/windows/desktop/aa381055)   
 [屬性頁](../ide/property-pages-visual-cpp.md)   
 [\/ASSEMBLYRESOURCE \(內嵌 Managed 資源\)](../build/reference/assemblyresource-embed-a-managed-resource.md)