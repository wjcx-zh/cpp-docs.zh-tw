---
title: "WeakReference::Resolve 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::WeakReference::Resolve"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Resolve 方法"
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakReference::Resolve 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### 參數  
 `riid`  
 介面 ID。  
  
 `ppvObject`  
 這個作業完成時，目前的強式參考的複本，如果強式參考計數不為零。  
  
## 傳回值  
  
-   S\_OK，則作業成功和強式參考計數為零。  將 `ppvObject` 屬性設為 `nullptr`。  
  
-   S\_OK，則作業成功和強式參考計數不為零。  `ppvObject` 參數被設定為強式參考。  
  
-   否則， HRESULT 表示這個的作業失敗的原因。  
  
## 備註  
 如果強式參考計數不為零，設定指定的指標指向目前的強式參考值。  
  
## 需求  
 **標頭：**implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [WeakReference 類別](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)