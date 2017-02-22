---
title: "ComPtrRefBase 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::Details::ComPtrRefBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtrRefBase 類別"
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ComPtrRefBase 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### 參數  
 `T`  
 [ComPtr\<T\>](../windows/comptr-class.md) 型別或衍生自其本身的型別，而不僅是 ComPtr 表示的介面。  
  
## 備註  
 表示 [ComPtrRef](../windows/comptrref-class.md) 類別 \(Class\) 的基底類別 \(Base Class\)。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`InterfaceType`|範本參數 `T`類型之同義資料表。|  
  
### 公用運算子  
  
|名稱|說明|  
|--------|--------|  
|[ComPtrRefBase::operator IInspectable\*\* 運算子](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|將目前 [ptr\_](../windows/comptrrefbase-ptr-data-member.md) 資料成員轉型至 IInspectable 介面指標的指標。|  
|[ComPtrRefBase::operator IUnknown\*\* 運算子](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|將目前 [ptr\_](../windows/comptrrefbase-ptr-data-member.md) 資料成員轉型至 IUnknown 介面的指標的指標。|  
  
### 受保護的資料成員  
  
|名稱|說明|  
|--------|--------|  
|[ComPtrRefBase::ptr\_ 資料成員](../windows/comptrrefbase-ptr-data-member.md)|對目前樣板參數所指定型別的指標。|  
  
## 繼承階層  
 `ComPtrRefBase`  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)