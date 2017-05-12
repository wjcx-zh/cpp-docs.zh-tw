---
title: "Platform::IntPtr 實值類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IntPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::IntPtr 結構"
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::IntPtr 實值類別
表示大小適用於平台、帶正負號的指標或控制代碼 \(32 位元或 64 位元\)。  
  
## 語法  
  
```cpp  
public value struct IntPtr  
```  
  
## Members  
 IntPtr 具有下列成員：  
  
|成員|描述|  
|--------|--------|  
|[IntPtr::IntPtr 建構函式](../cppcx/intptr-intptr-constructor.md)|初始化 IntPtr 的新執行個體。|  
|[IntPtr::op\_explicit 運算子](../cppcx/intptr-op-explicit-operator.md)|將指定的參數轉換為 IntPtr，或將指標轉換為 IntPtr 值。|  
|[IntPtr::ToInt32 方法](../cppcx/intptr-toint32-method.md)|將目前 IntPtr 轉換為 32 位元整數。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)