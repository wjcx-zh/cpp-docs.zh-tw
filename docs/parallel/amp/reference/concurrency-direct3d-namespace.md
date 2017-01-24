---
title: "Concurrency::direct3d 命名空間 | Microsoft Docs"
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
  - "amp/Concurrency::direct3d"
  - "amprt/Concurrency::direct3d"
  - "amp_short_vectors/Concurrency::direct3d"
  - "amp_graphics/Concurrency::direct3d"
  - "amp_math/Concurrency::direct3d"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "direct3d 命名空間"
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::direct3d 命名空間
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`direct3d` 命名空間提供支援 D3D 互通性的函式。  可充分運用 D3D 資源在 AMP 程式碼中運算，也可以使用在 AMP 中使用 D3D 程式碼建立的資源，而不需要建立中繼複本。  您可以使用 C\+\+ AMP，以累加方式加速 DirectX 應用程式的大量運算的區段，並將 D3D 應用程式開發介面用於 AMP 計算所產生的資料。  
  
## 語法  
  
```  
namespace direct3d;  
```  
  
## Members  
  
### 類別  
  
|名稱|描述|  
|--------|--------|  
|[scoped\_d3d\_access\_lock 類別](../../../parallel/amp/reference/scoped-d3d-access-lock-class.md)|`accelerator_view` 物件的 D3D 存取鎖定的 RAII 包裝函式。|  
  
### 結構  
  
|名稱|描述|  
|--------|--------|  
|[adopt\_d3d\_access\_lock\_t 結構](../../../parallel/amp/reference/adopt-d3d-access-lock-t-structure.md)|表示應該採用 \(而不是取得\) D3D 存取鎖定的標記類型。|  
  
### 功能  
  
|名稱|描述|  
|--------|--------|  
|[abs 函式](../Topic/abs%20Function.md)|傳回引數的絕對值|  
|[clamp 函式](../Topic/clamp%20Function.md)|多載。  將 \_X 限制在指定的 \_Min 和 \_Max 範圍內|  
|[countbits 函式](../Topic/countbits%20Function.md)|計算 \_X 中的設定位元數|  
|[create\_accelerator\_view 函式](../Topic/create_accelerator_view%20Function.md)|建立從指標到 Direct3D 裝置介面的 [accelerator\_view 類別](../../../parallel/amp/reference/accelerator-view-class.md)|  
|[d3d\_access\_lock 函式](../Topic/d3d_access_lock%20Function.md)|取得 accelerator\_view 的鎖定，以便安全地對與 accelerator\_view 共用的資源執行 D3D 作業|  
|[d3d\_access\_try\_lock 函式](../Topic/d3d_access_try_lock%20Function.md)|嘗試取得對 accelerator\_view 的 D3D 存取鎖定，而不需封鎖。|  
|[d3d\_access\_unlock 函式](../Topic/d3d_access_unlock%20Function.md)|釋放特定 accelerator\_view 的 D3D 存取鎖定。|  
|[firstbithigh 函式](../Topic/firstbithigh%20Function.md)|從最高序位位元向下取得 \_X 中第一個設定位元的位置。|  
|[firstbitlow 函式](../Topic/firstbitlow%20Function.md)|從最低序位位元開始向上取得 \_X 中第一個設定位元的位置。|  
|[get\_buffer 函式](../Topic/get_buffer%20Function.md)|取得構成陣列基礎的 D3D 緩衝區介面。|  
|[imax 函式](../Topic/imax%20Function.md)|比較兩個的值，傳回其中較大的值。|  
|[imin 函式](../Topic/imin%20Function.md)|比較兩個值，傳回其中較小的值。|  
|[is\_timeout\_disabled 函式](../Topic/is_timeout_disabled%20Function.md)|傳回布林旗標，表示指定的 accelerator\_view 是否停用逾時。|  
|[mad 函式](../Topic/mad%20Function.md)|多載。  對三個引數執行算術乘法\/加法運算: \_X \* \_Y \+ \_Z|  
|[make\_array 函式](../Topic/make_array%20Function.md)|從 D3D 緩衝區介面指標建立陣列。|  
|[noise 函式](../Topic/noise%20Function.md)|使用 Perlin 雜訊演算法產生隨機值|  
|[radians 函式](../Topic/radians%20Function.md)|將 \_X 從角度轉換成弧度|  
|[rcp 函式](../Topic/rcp%20Function.md)|計算引數的快速近似倒數|  
|[reversebits 函式](../Topic/reversebits%20Function.md)|反轉 \_X 的位元組順序|  
|[saturate 函式](../Topic/saturate%20Function.md)|將 \_X 限制在 0 到 1 之間的範圍|  
|[sign 函式](../Topic/sign%20Function.md)|多載。  傳回引數的正負號|  
|[smoothstep 函式](../Topic/smoothstep%20Function.md)|傳回介於 0 和 1 之間的平滑 Hermite 插補，如果 \_X 介於 \[\_Min， \_Max\]。|  
|[step 函式](../Topic/step%20Function.md)|比較兩個值，並根據哪一個值較大回傳 0 或 1|  
|[umax 函式](../Topic/umax%20Function.md)|比較兩個不帶正負號的值，傳回其中較大的值。|  
|[umin 函式](../Topic/umin%20Function.md)|比較兩個不帶正負號的值，傳回其中較小的值。|  
  
## 需求  
 **標頭：**amp.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)