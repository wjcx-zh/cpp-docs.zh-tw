---
title: "Can I Host More Than One Control in a Single Window? | Microsoft Docs"
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
  - "控制項 [ATL], hosting multiple"
  - "windows [C++], hosting multiple controls"
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Can I Host More Than One Control in a Single Window?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

裝載多個唯一 ATL 主視窗的一個控制項都是不可能的。  每個主視窗是設計來一次正確地放置一個控制項 \(這可讓您處理訊息反映和每個控制項的環境屬性 \(Ambient Property\) 的簡單機制\)。  不過，如果您需要使用者，請在單一視窗的多個控制項，是一個簡單事宜建立多個主應用程式視窗為該視窗的子系。  
  
## 請參閱  
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)