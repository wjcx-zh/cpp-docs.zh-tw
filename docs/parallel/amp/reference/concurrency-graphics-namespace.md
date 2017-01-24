---
title: "Concurrency::graphics 命名空間 | Microsoft Docs"
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
  - "amp_graphics/Concurrency::graphics"
  - "amp_short_vectors/Concurrency::graphics"
dev_langs: 
  - "C++"
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::graphics 命名空間
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

圖形命名空間提供專為圖形程式設計所設計的類型和函式。  
  
## 語法  
  
```  
namespace graphics;  
```  
  
## Members  
  
### 命名空間  
  
|名稱|描述|  
|--------|--------|  
|[Concurrency::graphics::direct3d 命名空間](../../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md)|提供 Direct3D Interop 的函式。|  
  
### Typedef  
  
|名稱|描述|  
|--------|--------|  
|`uint`|[uint\_2 類別](../../../parallel/amp/reference/uint-2-class.md)、[uint\_3 類別](../../../parallel/amp/reference/uint-3-class.md) 和 [uint\_4 類別](../../../parallel/amp/reference/uint-4-class.md) 的項目類型。  定義為 `typedef unsigned int uint;`。|  
  
### 列舉  
  
|名稱|描述|  
|--------|--------|  
|[address\_mode 列舉](../Topic/address_mode%20Enumeration.md)|指定材質取樣支援的位址模式。|  
|[filter\_mode 列舉](../Topic/filter_mode%20Enumeration.md)|指定材質取樣支援的篩選模式。|  
  
### 類別  
  
|名稱|描述|  
|--------|--------|  
|[texture 類別](../../../parallel/amp/reference/texture-class.md)|材質是在範圍內 accelerator\_view 上的資料彙總。  它是變數集合，對應範圍網域中的每個項目。  每個變數都會保留對應到 C\+\+ 基本類型 \(unsigned int、int、float、double\)、純量類型範數或 unorm \(定義於 concurrency::graphics\) 或合適短向量類型 \(定義於 concurrency::graphics\) 的值。|  
|[writeonly\_texture\_view 類別](../../../parallel/amp/reference/writeonly-texture-view-class.md)|writeonly\_texture\_view 提供材質的唯寫存取。|  
|[double\_2 類別](../../../parallel/amp/reference/double-2-class.md)|代表 2 個 `double` 值的短向量。|  
|[double\_3 類別](../../../parallel/amp/reference/double-3-class.md)|代表 3 個 `double` 值的短向量。|  
|[double\_4 類別](../../../parallel/amp/reference/double-4-class.md)|代表 4 個 `double` 值的短向量。|  
|[float\_2 類別](../../../parallel/amp/reference/float-2-class.md)|代表 2 個 `float` 值的短向量。|  
|[float\_3 類別](../../../parallel/amp/reference/float-3-class.md)|代表 3 個 `float` 值的短向量。|  
|[float\_4 類別](../../../parallel/amp/reference/float-4-class.md)|代表 4 個 `float` 值的短向量。|  
|[int\_2 類別](../../../parallel/amp/reference/int-2-class.md)|代表 2 個 `int` 值的短向量。|  
|[int\_3 類別](../../../parallel/amp/reference/int-3-class.md)|代表 3 個 `int` 值的短向量。|  
|[int\_4 類別](../../../parallel/amp/reference/int-4-class.md)|代表 4 個 `int` 值的短向量。|  
|[norm\_2 類別](../../../parallel/amp/reference/norm-2-class.md)|代表 2 個 `norm` 值的短向量。|  
|[norm\_3 類別](../../../parallel/amp/reference/norm-3-class.md)|代表 3 個 `norm` 值的短向量。|  
|[norm\_4 類別](../../../parallel/amp/reference/norm-4-class.md)|代表 4 個 `norm` 值的短向量。|  
|[uint\_2 類別](../../../parallel/amp/reference/uint-2-class.md)|代表 2 個 `uint` 值的短向量。|  
|[uint\_3 類別](../../../parallel/amp/reference/uint-3-class.md)|代表 3 個 `uint` 值的短向量。|  
|[uint\_4 類別](../../../parallel/amp/reference/uint-4-class.md)|代表 4 個 `uint` 值的短向量。|  
|[unorm\_2 類別](../../../parallel/amp/reference/unorm-2-class.md)|代表 2 個 `unorm` 值的短向量。|  
|[unorm\_3 類別](../../../parallel/amp/reference/unorm-3-class.md)|代表 3 個 `unorm` 值的短向量。|  
|[unorm\_4 類別](../../../parallel/amp/reference/unorm-4-class.md)|代表 4 個 `unorm` 值的短向量。|  
|[sampler 類別](../../../parallel/amp/reference/sampler-class.md)|表示用於材質取樣的取樣器組態。|  
|[short\_vector 結構](../../../parallel/amp/reference/short-vector-structure.md)|提供一個短向量值的基本實作。|  
|[short\_vector\_traits 結構](../../../parallel/amp/reference/short-vector-traits-structure.md)|提供擷取短向量的長度和類型。|  
|[texture\_view 類別](../../../parallel/amp/reference/texture-view-class.md)|提供材質的讀取存取和寫入存取。|  
  
### 功能  
  
|名稱|描述|  
|--------|--------|  
|[copy 函式](../Topic/copy%20Function.md)|多載。  將來源材質的內容複製到目的端主機緩衝區。|  
|[copy\_async 函式](../Topic/copy_async%20Function.md)|多載。  以非同步方式將來源材質的內容複製到目的端主機緩衝區中。|  
  
## 需求  
 **標頭：**amp\_graphics.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)