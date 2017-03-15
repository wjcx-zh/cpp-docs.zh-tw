---
title: "COM 簡介 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM"
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM 簡介
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM 基本上就是「物件模型\>的 ActiveX 控制項和 OLE 建置。  COM 可讓物件將其功能公開 \(Expose\) 給其他元件和主應用程式。  它定義物件如何公開本身，而這個公開的運作方式跨處理序或在網路上。  COM 也會定義物件的生命週期。  
  
 對 COM 的基礎是這些概念:  
  
-   [介面](../atl/interfaces-atl.md) —物件將其功能的機制。  
  
-   [IUnknown](../atl/iunknown.md) —其他的基本介面。  此實作會查詢機制的參考次數和介面執行透過 COM。  
  
-   [參考計數。](../atl/reference-counting.md) —物件的技術 \(或，必定是介面\)，以便決定不再使用時機和可用的移除本身。  
  
-   [QueryInterface](../atl/queryinterface.md) —使用的方法來查詢特定介面的物件。  
  
-   [封送處理](../atl/marshaling.md) —讓物件跨執行緒、處理序和網路範圍來使用的機制，可讓您與位置無關。  
  
-   [彙總](../atl/aggregation.md) —一種在哪個物件可供其他。  
  
## 請參閱  
 [Introduction to COM and ATL](../atl/introduction-to-com-and-atl.md)   
 [The Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)