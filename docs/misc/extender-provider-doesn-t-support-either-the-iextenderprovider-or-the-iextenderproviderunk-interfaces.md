---
title: "Extender Provider doesn&#39;t support either the IExtenderProvider or the IExtenderProviderUnk interfaces. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_EXT_EXTPROVINVALID"
ms.assetid: 77d596cd-28db-4ad5-bd4d-e451276e869c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender Provider doesn&#39;t support either the IExtenderProvider or the IExtenderProviderUnk interfaces.
使用的擴充性提供者不支援您實作的介面。  
  
### 若要更正這個錯誤  
  
1.  如果 Extendee 物件支援 IDispatch Automation 介面，請實作 IExtenderProvider。  
  
     \-或\-  
  
     如果 Extendee 物件是以 IUnknown 為基礎，請實作 IExtenderProviderUnk。  
  
## 請參閱  
 <xref:EnvDTE.IExtenderProviderUnk>   
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>