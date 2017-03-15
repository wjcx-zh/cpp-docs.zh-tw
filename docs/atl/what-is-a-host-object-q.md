---
title: "What Is a Host Object? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "host objects"
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# What Is a Host Object?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

主應用程式物件是表示特定視窗的 ATL 提供的 ActiveX 控制項容器的 COM 物件。  主應用程式物件的子類別 \(Subclass\) 容器視窗，以便反映訊息至控制項，它提供控制項將使用的所需的容器，介面，而且會公開 \(Expose\) [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) 和 [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) 介面可讓您設定控制項的環境。  
  
 您可以使用主應用程式物件設定容器的環境屬性。  
  
## 請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)