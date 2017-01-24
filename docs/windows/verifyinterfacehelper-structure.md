---
title: "VerifyInterfaceHelper 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::VerifyInterfaceHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VerifyInterfaceHelper 結構"
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# VerifyInterfaceHelper 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 基礎結構，而且不是針對直接從程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   bool isWinRTInterface,  
   typename I  
>  
struct VerifyInterfaceHelper;  
  
template <  
   typename I  
>  
struct VerifyInterfaceHelper<false, I>;  
```  
  
#### 參數  
 `I`  
 要驗證的介面  
  
 `isWinRTInterface`  
  
## 備註  
 驗證目前樣板參數定義的介面是否符合特定需求。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[VerifyInterfaceHelper::Verify 方法](../windows/verifyinterfacehelper-verify-method.md)||  
  
## 繼承階層架構  
 `VerifyInterfaceHelper`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)