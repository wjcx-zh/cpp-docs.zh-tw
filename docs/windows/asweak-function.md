---
title: "AsWeak 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::AsWeak"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsWeak 函式"
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsWeak 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取對指定的執行個體的弱式參考。  
  
## 語法  
  
```  
template<  
   typename T  
>  
HRESULT AsWeak(  
   _In_ T* p,  
   _Out_ WeakRef* pWeak  
);  
```  
  
#### 參數  
 `T`  
 指向`p`參數型別的指標。  
  
 `p`  
 型別的執行個體。  
  
 `pWeak`  
 這個作業完成時，指向參數 `p`的弱式參考的指標。  
  
## 傳回值  
 S\_OK，如果這個作業成功，否則，指出失敗原因的錯誤 HRESULT。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)