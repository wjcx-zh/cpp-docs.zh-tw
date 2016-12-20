---
title: "如何：使用 GetGlobalService | Microsoft Docs"
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
  - "服務, GetGlobalService"
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# 如何：使用 GetGlobalService
有時候您可能需要從 \[工具\] 視窗中取得服務，或控制未設置，否則就不知道您所要之的服務的服務提供者已決定位置的容器。  例如，您可以寫入活動記錄檔從控制項中。  如需有關這些及其他案例的詳細資訊，請參閱[How to: 服務進行疑難排解](../Topic/How%20to:%20Troubleshoot%20Services.md)。  
  
 您可以充分[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]服務，藉由呼叫靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法。  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>初始化任何 VSPackage 衍生自第一次快取的服務提供者會依賴<xref:Microsoft.VisualStudio.Shell.Package>已決定位置。  您必須保證此條件符合時，否則為空的服務準備。  
  
 幸運的是， <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>大多數情況下正常運作。  
  
-   如果 VSPackage 提供服務，只有知道另一台 VSPackage，VSPackage 要求的服務已決定位置之前載入服務所提供的 VSPackage。  
  
-   工具視窗由 VSPackage，如果 \[工具\] 視窗建立之前，已決定位置 VSPackage。  
  
-   如果建立 VSPackage 的工具視窗裝載控制項的容器，在建立控制項容器之前，已決定位置 VSPackage。  
  
### 若要取得的工具視窗或控制項的容器內的服務  
  
-   在這段程式碼中插入的建構函式、 工具視窗或控制項容器：  
  
     [!code-vb[UseGetGlobalService#1](../misc/codesnippet/VisualBasic/how-to-use-getglobalservice_1.vb)]
     [!code-cs[UseGetGlobalService#1](../misc/codesnippet/CSharp/how-to-use-getglobalservice_1.cs)]  
  
     這段程式碼會取得 SVsActivityLog 服務並將其以轉換<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面，可以用來寫入活動的記錄檔。  如需範例，請參閱 [如何︰ 使用活動記錄檔](../Topic/How%20to:%20Use%20the%20Activity%20Log.md)。  
  
## 請參閱  
 [How to: 服務進行疑難排解](../Topic/How%20to:%20Troubleshoot%20Services.md)   
 [使用並提供服務](../Topic/Using%20and%20Providing%20Services.md)   
 [服務的基本資訊](../Topic/Service%20Essentials.md)