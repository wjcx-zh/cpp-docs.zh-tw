---
title: "InterfaceTraits 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::InterfaceTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InterfaceTraits 結構"
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InterfaceTraits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
  
template<  
   typename CloakedType  
>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
#### 參數  
 `I0`  
 介面的名稱。  
  
 `CloakedType`  
 對於 RuntimeClass、實作和 ChainInterfaces，介面不會在支援的介面 ID 清單中。  
  
## 備註  
 實作介面的一般特性。  
  
 第二個範本則是隱匿的介面的特製化。  第三個樣板是 Nil 參數的特製化。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`Base`|`I0`同義資料表的範本參數。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[InterfaceTraits::CanCastTo 方法](../windows/interfacetraits-cancastto-method.md)|指示指定的指標是否可轉換成 `Base`的指標。|  
|[InterfaceTraits::CastToBase 方法](../windows/interfacetraits-casttobase-method.md)|轉型指定指標為 `Base`的指標。|  
|[InterfaceTraits::CastToUnknown 方法](../windows/interfacetraits-casttounknown-method.md)|轉型指定指標為 IUnknow 的指標。|  
|[InterfaceTraits::FillArrayWithIid 方法](../windows/interfacetraits-fillarraywithiid-method.md)|指派 `Base` 的介面 ID 至索引引數所指定的陣列元素。|  
|[InterfaceTraits::Verify 方法](../windows/interfacetraits-verify-method.md)|驗證基底適當地衍生。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[InterfaceTraits::IidCount 常數](../windows/interfacetraits-iidcount-constant.md)|保留與目前 InterfaceTraits 物件有關聯的介面 ID 數目。|  
  
## 繼承階層架構  
 `InterfaceTraits`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)