---
title: "You must implement IExtenderProviderUnk to extend this object. | Microsoft Docs"
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
  - "vs.message.VS_E_EXT_NONDISPATCHEXTENDEE"
ms.assetid: e0d4087f-9fa9-4fa9-92d9-7aed3103b2d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# You must implement IExtenderProviderUnk to extend this object.
Extendee 物件是以 IUnknown 為基礎，而不是以 IDispatch 介面為基礎。  
  
### 若要更正這個錯誤  
  
1.  讓擴充性提供者實作 IExtenderProviderUnk，而非 IExtenderProvider。  
  
## 請參閱  
 <xref:EnvDTE.IExtenderProviderUnk>   
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>