---
title: "Concurrency::graphics::direct3d 命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_graphics/Concurrency::graphics::direct3d"
  - "amp_short_vectors/Concurrency::graphics::direct3d"
dev_langs: 
  - "C++"
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::graphics::direct3d 命名空間
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供 [get\_texture](../Topic/get_texture%20Function.md) 和 [make\_texture](../Topic/make_texture%20Function.md) 方法。  
  
## 語法  
  
```  
namespace direct3d;  
```  
  
## Members  
  
### 功能  
  
|名稱|描述|  
|--------|--------|  
|[get\_sampler 函式](../Topic/get_sampler%20Function.md)|在表示指定之取樣器物件的特定加速器檢視上，取得 Direct3D 取樣器狀態介面。|  
|[get\_texture 函式](../Topic/get_texture%20Function.md)|取得做為指定之[材質](../../../parallel/amp/reference/texture-class.md)物件基礎的 Direct3D 材質介面。|  
|[make\_sampler 函式](../Topic/make_sampler%20Function.md)|從 Direct3D 取樣器狀態介面指標建立取樣器。|  
|[make\_texture 函式](../Topic/make_texture%20Function.md)|使用指定的參數建立 [texture](../../../parallel/amp/reference/texture-class.md) 物件。|  
|[msad4 函式](../Topic/msad4%20Function.md)|比較 4 位元組參考值和 8 位元組來源值，並累積 4 個總和的向量。|  
  
## 需求  
 **標頭：**amp\_graphics.h  
  
 **命名空間：**Concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)