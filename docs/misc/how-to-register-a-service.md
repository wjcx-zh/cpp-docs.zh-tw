---
title: "如何：註冊服務 | Microsoft Docs"
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
  - "服務, 註冊"
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 如何：註冊服務
Managed Package Framework \(MPF\) 提供屬性以控制受管理服務的註冊。 RegPkg 公用程式使用這些屬性，向 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 註冊服務。  
  
## 範例  
 下列程式碼來自 [VSSDK 範例](../misc/vssdk-samples.md)。  
  
 [!code-vb[VSSDKRegisterService#1](../misc/codesnippet/VisualBasic/how-to-register-a-service_1.vb)]
 [!code-cs[VSSDKRegisterService#1](../misc/codesnippet/CSharp/how-to-register-a-service_1.cs)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 會向 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 註冊 SMyGlobalService 服務。 如需 <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> 和 <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 的詳細資訊，請參閱[註冊和取消註冊 Vspackage](../Topic/Registering%20and%20Unregistering%20VSPackages.md)。  
  
 若要註冊會取代另一個同名服務的服務，請使用 <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>而非 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>。  
  
## 穩固程式設計  
 若要更輕鬆地重新編譯服務提供者，而不需要變更服務用戶端，或反之亦然，您可以在個別組件模組中定義服務和其介面。 下列程式碼來自 Reference.Services \(C\#\) 範例中的 IMyGlobalService.cs 檔案。  
  
 [!code-vb[VSSDKRegisterService#2](../misc/codesnippet/VisualBasic/how-to-register-a-service_2.vb)]
 [!code-cs[VSSDKRegisterService#2](../misc/codesnippet/CSharp/how-to-register-a-service_2.cs)]  
  
 需要有 <xref:System.Runtime.InteropServices.ComVisibleAttribute>才能透過 Unmanaged 程式碼取得介面。  
  
> [!NOTE]
>  雖然您可以針對服務和介面使用相同的類型或 GUID，但是建議您使用不同的類型或 GUID，因為服務可以公開不同的介面。  
  
## 請參閱  
 [Registering VSPackages](http://msdn.microsoft.com/zh-tw/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [服務的基本資訊](../Topic/Service%20Essentials.md)