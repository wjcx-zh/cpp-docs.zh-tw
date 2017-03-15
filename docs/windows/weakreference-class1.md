---
title: "WeakReference 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakReference 類別"
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# WeakReference 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
class WeakReference;  
```  
  
## 備註  
 表示可以搭配 Windows 執行階段或一般 COM 的*弱式參考*。  弱式參考表示可能有也可能沒有可存取的物件。  
  
 `WeakReference` 物件維護 *強式參考*，是指向物件和 *強式參考計數*，是以 Resolve\(\) 方法發出強式參考的複本數目。  當強式參考計數為非零值時，強式參考有效，且物件可存取。  當強式參考計數為零時，強式參考無效，而且物件是無法存取。  
  
 WeakReference 物件通常用來表示存在是由外部執行緒或應用程式控制項的物件。  例如，請從一個檔案物件參考建立 WeakReference 物件。  在檔案開啟時，強式參考有效。  不過，如果檔案已關閉，強式參考就會變成無效。  
  
 WeakReference 方法是執行緒安全。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[WeakReference::WeakReference 建構函式](../windows/weakreference-weakreference-constructor.md)|初始化 WeakReference 類別的新執行個體。|  
|[WeakReference::~WeakReference 解構函式](../windows/weakreference-tilde-weakreference-destructor.md)|取消初始化 \(終結\) WeakReference 類別目前的執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[WeakReference::DecrementStrongReference 方法](../windows/weakreference-decrementstrongreference-method.md)|遞減目前 WeakReference 物件的強式參考計數。|  
|[WeakReference::IncrementStrongReference 方法](../windows/weakreference-incrementstrongreference-method.md)|遞增目前 WeakReference 物件的強式參考計數。|  
|[WeakReference::Resolve 方法](../windows/weakreference-resolve-method.md)|如果強式參考計數不為零，設定指定的指標指向目前的強式參考值。|  
|[WeakReference::SetUnknown 方法](../windows/weakreference-setunknown-method.md)|設定目前物件的 WeakReference 強式參考至指定的介面指標。|  
  
## 繼承階層架構  
 `WeakReference`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)