---
title: "RaiseException 函式 | Microsoft Docs"
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
  - "internal/Microsoft::WRL::Details::RaiseException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RaiseException 函式"
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RaiseException 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
inline void __declspec(noreturn)  
   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### 參數  
 `hr`  
 所引發之例外狀況的例外狀況程式碼;也就是作業失敗的 HRESULT。  
  
 `dwExceptionFlags`  
 表示可繼續之例外狀況的旗標 \(旗標值零\)，或非持續性的例外狀況 \(旗標值非零\)。  根據預設，非持續性的例外狀況。  
  
## 備註  
 引發在呼叫執行緒上的例外狀況。  
  
 如需詳細資訊，請參閱 Windows **RaiseException**函式。  
  
## 需求  
 **標題:** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)