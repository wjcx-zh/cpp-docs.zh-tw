---
title: "ComPtrRef 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::Details::ComPtrRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtrRef 類別"
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ComPtrRef 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   typename T  
>  
class ComPtrRef : public ComPtrRefBase<T>;  
```  
  
#### 參數  
 `T`  
 [ComPtr\<T\>](../windows/comptr-class.md) 型別或衍生自其本身的型別，而不僅是 ComPtr 表示的介面。  
  
## 備註  
 表示型別 ComPtr\<T\> 物件的參考。  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[ComPtrRef::ComPtrRef 建構函式](../windows/comptrref-comptrref-constructor.md)|初始化 ComPtrRef 類別的新執行個體，從指定指標到另一 ComPtrRef 物件。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[ComPtrRef::GetAddressOf 方法](../windows/comptrref-getaddressof-method.md)|擷取 ComPtrRef 目前物件所表示的介面的指標位址。|  
|[ComPtrRef::ReleaseAndGetAddressOf 方法](../windows/comptrref-releaseandgetaddressof-method.md)|刪除目前 ComPtrRef 物件並傳回指標的指標到由 ComPtrRef 物件所代表的介面。|  
  
### 公用運算子  
  
|名稱|說明|  
|--------|--------|  
|[ComPtrRef::operator InterfaceType\*\* 運算子](../windows/comptrref-operator-interfacetype-star-star-operator.md)|刪除目前 ComPtrRef 物件並傳回指標的指標到由 ComPtrRef 物件所代表的介面。|  
|[ComPtrRef::operator T\* 運算子](../windows/comptrref-operator-t-star-operator.md)|傳回目前 ComPtrRef 物件的 [ptr\_](../windows/comptrrefbase-ptr-data-member.md) 資料成員的值。|  
|[ComPtrRef::operator void\*\* 運算子](../windows/comptrref-operator-void-star-star-operator.md)|刪除目前 ComPtrRef 物件，並將 ComPtrRef 物件代表的指標轉換成指向 `void`的指標的指標，然後傳回轉型指標。|  
|[ComPtrRef::operator\* 運算子](../windows/comptrref-operator-star-operator.md)|擷取指到目前 ComPtrRef 物件所表示的介面的指標。|  
|[ComPtrRef::operator\=\= 運算子](../windows/comptrref-operator-equality-operator.md)|表示兩個 ComPtrRef 物件是否不相等。|  
|[ComPtrRef::operator\!\= 運算子](../windows/comptrref-operator-inequality-operator.md)|表示兩個 ComPtrRef 物件是否不相等。|  
  
## 繼承階層  
 `ComPtrRefBase`  
  
 `ComPtrRef`  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)