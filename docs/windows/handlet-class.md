---
title: "HandleT 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HandleT 類別"
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示物件的控制代碼。  
  
## 語法  
  
```  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
#### 參數  
 `HandleTraits`  
 定義控制項的一般特性 [HandleTraits](../windows/handletraits-structure.md) 結構的執行個體。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`Traits`|`HandleTraits`的一個同義資料表。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[HandleT::HandleT 建構函式](../windows/handlet-handlet-constructor.md)|初始化 HandleT 類別的新執行個體。|  
|[HandleT::~HandleT 解構函式](../windows/handlet-tilde-handlet-destructor.md)|取消初始化 HandleT 類別的執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[HandleT::Attach 方法](../windows/handlet-attach-method.md)|將指定的控制代碼與目前 HandleT 物件關聯。|  
|[HandleT::Close 方法](../windows/handlet-close-method.md)|關閉目前 HandleT 物件。|  
|[HandleT::Detach 方法](../windows/handlet-detach-method.md)|解除其基礎控制代碼的目前 HandleT 物件。|  
|[HandleT::Get 方法](../windows/handlet-get-method.md)|取得基礎控制代碼的值。|  
|[HandleT::IsValid 方法](../windows/handlet-isvalid-method.md)|表示目前 HandleT 物件是否表示控制代碼。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[HandleT::InternalClose 方法](../windows/handlet-internalclose-method.md)|關閉目前 HandleT 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[HandleT::operator\= 運算子](../windows/handlet-operator-assign-operator.md)|將指定的 HandleT 物件中的值移動至目前 HandleT 物件。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[HandleT::handle\_ 資料成員](../windows/handlet-handle-data-member.md)|包含 HandleT 由物件所表示的控制代碼。|  
  
## 繼承階層架構  
 `HandleT`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)