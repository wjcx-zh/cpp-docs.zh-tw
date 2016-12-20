---
title: "MSBuild 錯誤 MSB3254 | Microsoft Docs"
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
  - "MSB3254"
ms.assetid: cb9636b2-d9b3-466d-959c-14c7c8017a78
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3254
**MSB3254：將忽略檔案 \<name\>，因為無法讀取。  這個檔案可能是傳入到 InstalledAssemblySubsetTables，或是在 TargetFrameworkDirectories 中搜尋 \<name\> 資料夾找到的。**  
  
 當無法讀取 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] XML 檔案 client.xml 時，就會發生這個錯誤。  這個檔案無法讀取，可能是損毀、鎖定或其他問題所造成。  
  
 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 是完整 [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] 3.5 執行階段程式庫的子集。  如需 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 的詳細資訊，請參閱[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
 程序  
  
### 若要更正這個錯誤  
  
-   確定您擁有檔案的完整使用權限和完整存取權限，或重新安裝 [!INCLUDE[net_client_v35_long](../Token/net_client_v35_long_md.md)] 可轉散發執行階段程式庫來取代損毀的檔案。  
  
## 請參閱  
 [Project Element \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)