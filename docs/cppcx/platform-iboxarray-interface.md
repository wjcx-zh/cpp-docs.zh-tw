---
title: "Platform::IBoxArray 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IBoxArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::IBoxArray"
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::IBoxArray 介面
`IBoxArray` 是實值類型陣列的包裝函式，這些實值類型會在不同的應用程式二進位介面 \(ABI\) 之間傳遞或是儲存在 `Platform::Object^` 元素的集合中，例如在 XAML 控制項中。  
  
## 語法  
  
```cpp  
template <typename T>  
interface class IBoxArray  
```  
  
#### 參數  
 `T`  
 每個陣列元素中 Boxed 值的類型。  
  
## 備註  
 `IBoxArray` 是適用於 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] 的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] \(`Windows::Foundation::IReferenceArray`\) 名稱。  
  
## Members  
 `IBoxArray` 介面繼承自 `IValueType` 介面。`IBoxArray` 也有這些成員：  
  
|方法|描述|  
|--------|--------|  
|值|傳回之前儲存在這個 `IBoxArray` 執行個體中的 Unboxed 陣列。|  
  
## 請參閱  
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)