---
title: "ChainInterfaces 結構 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::ChainInterfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ChainInterfaces 結構"
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ChainInterfaces 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定可套用至一組介面 ID 的驗證和初始化函式。  
  
## 語法  
  
```  
template <  
   typename I0,  
   typename I1,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct ChainInterfaces : I0;  
template <  
   typename DerivedType,  
   typename BaseType,  
   bool hasImplements,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8,  
   typename I9  
>  
struct ChainInterfaces<MixIn<DerivedType, BaseType, hasImplements>, I1, I2, I3, I4, I5, I6, I7, I8, I9>;  
```  
  
#### 參數  
 `I0`  
 \(需要的\)介面 ID 0。  
  
 `I1`  
 \(需要的\)介面 ID 1。  
  
 `I2`  
 \(選擇性的\)介面 ID 2。  
  
 `I3`  
 \(選擇性的\)介面 ID 3。  
  
 `I4`  
 \(選擇性的\)介面 ID 4。  
  
 `I5`  
 \(選擇性的\)介面 ID 5。  
  
 `I6`  
 \(選擇性的\)介面 ID 6。  
  
 `I7`  
 \(選擇性的\)介面 ID 7。  
  
 `I8`  
 \(選擇性的\)介面 ID 8。  
  
 `I9`  
 \(選擇性的\)介面 ID 9。  
  
 `DerivedType`  
 衍生型別  
  
 `BaseType`  
 一個衍生型別的基底型別。  
  
 `hasImplements`  
 布林值，如果 `true`，表示您不能使用不是從 [實作](../windows/implements-structure.md) 結構衍生的類別和[MixIn](../windows/mixin-structure.md)結構一起。  
  
## Members  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[ChainInterfaces::CanCastTo 方法](../windows/chaininterfaces-cancastto-method.md)|指示指定的介面 ID 是否可以轉型為 ChainInterface 樣板參數所定義的每個特製化。|  
|[ChainInterfaces::CastToUnknown 方法](../windows/chaininterfaces-casttounknown-method.md)|轉換 `I0` 樣板參數所定義的型別之介面指標，其指標指向 IUnknown 。|  
|[ChainInterfaces::FillArrayWithIid 方法](../windows/chaininterfaces-fillarraywithiid-method.md)|將 `I0` 樣板參數定義的介面 ID 儲存在指定的介面 ID的陣列的指定位置裡。|  
|[ChainInterfaces::Verify 方法](../windows/chaininterfaces-verify-method.md)|確認範本參數`I0`到`I9`所定義的每個介面從 IUnknown 和 IInspectable 繼承，且`I0`從`I1`繼承到 `I9`。|  
  
### 受保護的常數。  
  
|名稱|描述|  
|--------|--------|  
|[ChainInterfaces::IidCount 常數](../windows/chaininterfaces-iidcount-constant.md)|介面 ID 總數包含在指定的樣板參數 `I0` 到 `I9`的介面中。|  
  
## 繼承階層架構  
 `I0`  
  
 `ChainInterfaces`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)