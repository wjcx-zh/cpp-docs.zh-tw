---
title: "IUnknown | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 介面, base interface"
  - "IUnknown interface"
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# IUnknown
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 是所有其他 COM 介面的基底介面。這個介面會定義三個方法：[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)、[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317)。  [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 可讓介面使用者向物件查詢另一個介面的指標。  [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 會實作參考計數介面。  
  
## 請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [IUnknown and Interface Inheritance](http://msdn.microsoft.com/library/windows/desktop/ms692713)