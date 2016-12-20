---
title: "如何：從 DTE 物件取得服務 | Microsoft Docs"
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
  - "服務, 從 DTE 物件"
ms.assetid: c26a51d4-86f0-454b-9625-5443e55eec7d
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 如何：從 DTE 物件取得服務
您可以從具有存取權的任何程式取得服務[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]自動化<xref:EnvDTE.DTEClass>物件。  例如，您可以存取<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服務從透過 DTE 物件精靈。  您可以使用這項服務寫入活動的記錄檔。  如需詳細資訊，請參閱 [如何︰ 使用活動記錄檔](../Topic/How%20to:%20Use%20the%20Activity%20Log.md)。  
  
 DTE 物件實作<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>，您可以用來查詢服務從 managed 程式碼，藉由使用<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>。  
  
### 若要從 DTE 物件中取得服務  
  
1.  下列程式碼會建立<xref:Microsoft.VisualStudio.Shell.ServiceProvider>從 DTE 物件和呼叫<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>的型別<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服務。  服務轉換成介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>，這用來寫入活動的記錄檔中的項目。  如需詳細資訊關於如何寫入活動的記錄檔，請參閱[如何︰ 使用活動記錄檔](../Topic/How%20to:%20Use%20the%20Activity%20Log.md)。  
  
     [!code-cs[GetAServiceFromTheDTEObject#1](../misc/codesnippet/CSharp/how-to-get-a-service-from-the-dte-object_1.cs)]
     [!code-vb[GetAServiceFromTheDTEObject#1](../misc/codesnippet/VisualBasic/how-to-get-a-service-from-the-dte-object_1.vb)]  
  
## 請參閱  
 [使用並提供服務](../Topic/Using%20and%20Providing%20Services.md)   
 [服務的基本資訊](../Topic/Service%20Essentials.md)