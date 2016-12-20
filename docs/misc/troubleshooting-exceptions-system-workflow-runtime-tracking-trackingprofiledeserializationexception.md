---
title: "疑難排解例外狀況：System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException | Microsoft Docs"
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
  - "EHWRTTrackingProfileDeserialization"
helpviewer_keywords: 
  - "System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException 例外狀況"
  - "TrackingProfileDeserializationException 例外狀況"
ms.assetid: ce8fe4c1-43e3-4930-947e-74b8d94f32bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException
當 XML 文件無法由 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException> 還原序列化為 <xref:System.Workflow.Runtime.Tracking.TrackingProfile> 時，就會擲回 <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> 例外狀況 \(Exception\)。  
  
## 備註  
 當 <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> 擲回此例外狀況時，會提供訊息來描述例外狀況的原因。 在某些情況下，<xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> 會提供在嘗試還原序列化 <xref:System.Workflow.Runtime.Tracking.TrackingProfile> 時，發生的驗證錯誤和警告清單。 如此有提供這類清單，則 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException.ValidationEventArgs%2A> 屬性會包含這份清單。  
  
## 請參閱  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)