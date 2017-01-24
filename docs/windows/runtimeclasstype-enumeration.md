---
title: "RuntimeClassType 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClassType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClassType 列舉"
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassType 列舉
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 [RuntimeClass](../windows/runtimeclass-class.md) 執行個體支援的型別。  
  
## 語法  
  
```  
enum RuntimeClassType;  
```  
  
## Members  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`ClassicCom`|建立 COM 執行階段類別|  
|`Delegate`|相當於 **ClassicCom**。|  
|`InhibitFtmBase`|停用 `FtmBase` 支援，而 `__WRL_CONFIGURATION_LEGACY__` 未定義。|  
|`InhibitWeakReference`|停用弱式參考支援。|  
|`WinRt`|[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 類別。|  
|`WinRtClassicComMix`|`WinRt` 和 `ClassicCom` 的組合。|  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)