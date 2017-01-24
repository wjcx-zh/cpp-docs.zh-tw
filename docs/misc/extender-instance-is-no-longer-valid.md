---
title: "Extender instance is no longer valid. | Microsoft Docs"
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
  - "vs.message.VS_E_EXT_EXTINVALID"
ms.assetid: 6361ba35-f2c5-4024-9362-46d7d9daf651
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender instance is no longer valid.
擴充性執行個體無法成功建立，或者已經被終結。  
  
### 若要更正這個錯誤  
  
1.  再次從 Extendee 物件取得擴充性執行個體  
  
     \-或\-  
  
     呼叫 DTE.ObjectExtenders.GetExtender\(\)，重新取得擴充性執行個體。  
  
## 請參閱  
 <xref:EnvDTE.ObjectExtenders>   
 <xref:EnvDTE.ObjectExtenders.GetExtender%2A>