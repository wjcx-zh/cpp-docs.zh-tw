---
title: "QueryInterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "介面, 可用性"
  - "介面, 指標"
  - "QueryInterface 方法"
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# QueryInterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

雖然有物件可以表示功能的機制會靜態地提供 \(在將其具現化之前\)，基本 COM 機制是使用 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)**IUnknown** 呼叫的方法。  
  
 每個介面從 **IUnknown**衍生自，因此，每個介面有 `QueryInterface`的實作。  不論實作中，這個方法會查詢物件使用呼叫端需要指標的介面 IID。  如果連接的物件支援， `QueryInterface` 擷取指標，介面，同時也會呼叫 `AddRef`。  否則，會傳回 **E\_NOINTERFACE** 錯誤碼。  
  
 請注意您必須隨時相容 [參考計數。](../atl/reference-counting.md) 規則。  如果您呼叫在介面指標的 **版本** 遞減參考計數為零，就不應該再使用該指標。  您有時會需要取得物件 \(也就是您的弱式參考可能希望以取得指向它的其中一個介面，而不需要加入參考計數\)，不過，藉由呼叫 `QueryInterface` 這樣做不可以跟隨 **版本**。  以這種方式使用衍生的指標無效，而且不應該使用。  這很很明顯地，當 [\_ATL\_DEBUG\_INTERFACES](../Topic/_ATL_DEBUG_INTERFACES.md) 定義，因此，定義這個巨集就會尋找參考一個有用的方式計算 Bug。  
  
## 請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [QueryInterface: Navigating in an Object](http://msdn.microsoft.com/library/windows/desktop/ms687230)