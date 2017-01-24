---
title: "Cannot find custom tool &#39;custom tool&#39; on this system | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_instantiate_generator1"
ms.assetid: 51fe9bec-b8bc-4a4c-94aa-15a1f7cc8b6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot find custom tool &#39;custom tool&#39; on this system
專案系統無法建立自訂工具。  所要求的自訂工具不會執行，因為專案系統無法產生該項工具。  請確定自訂工具已正確地安裝和註冊。  
  
 為特定檔案的 `CustomTool` 屬性 \(Property\) 指定無效的自訂工具名稱，可能是導致這種錯誤的原因。  也有可能是因為編輯了專案檔 \(.vbproj\/.csproj\)，而造成 `CustomTool` 屬性 \(Property\) 值無效。  或是您使用了在另一台具有自訂工具之電腦上所開發的專案，但在您的電腦上並未安裝這個自訂工具。  如需 `CustomTool` 屬性的詳細資訊，請參閱 [File Properties](http://msdn.microsoft.com/zh-tw/013c4aed-08d6-4dce-a124-ca807ca08959)。  
  
 如果 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) 不能用於自訂工具，也會發生這個錯誤。  例如，它可能沒有註冊或必要的 DLL 可能遺失。  
  
## 請參閱  
 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)