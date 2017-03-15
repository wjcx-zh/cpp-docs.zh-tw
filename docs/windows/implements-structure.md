---
title: "Implements 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Implements"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Implements 結構"
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Implements 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定介面的實作 QueryInterface 和 GetIid。  
  
## 語法  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;  
template <  
   int flags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;  
```  
  
#### 參數  
 `I0`  
 第零個介面 ID。\(強制\)  
  
 `I1`  
 第一個介面 ID。\(選擇性\)  
  
 `I2`  
 第二個介面 ID。\(選擇性\)  
  
 `I3`  
 第三個介面 ID。\(選擇性\)  
  
 `I4`  
 第四個介面 ID。\(選擇性\)  
  
 `I5`  
 第五個介面 ID。\(選擇性\)  
  
 `I6`  
 第六個介面 ID。\(選擇性\)  
  
 `I7`  
 第七個介面 ID。\(選擇性\)  
  
 `I8`  
 第八個介面 ID。\(選擇性\)  
  
 `I9`  
 第九個介面 ID。\(選擇性\)  
  
 `flags`  
 類別的設定旗標。  在 [RuntimeClassFlags](../windows/runtimeclassflags-structure.md) 結構指定的一或多個 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉型別。  
  
## 備註  
 衍生自指定的介面清單中並實作 QueryInterface 和 GetIid 的協助程式範本。  
  
 每個透過 `I9` 參數的 `I0` 參數必須衍生自 IUnknown、IInspectable 或 [ChainInterfaces](../windows/chaininterfaces-structure.md) 樣板。  `flags` 參數判斷是否支援以 IUnknown 或 IInspectable 產生。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`ClassFlags`|`RuntimeClassFlags<WinRt>`的一個同義資料表。|  
  
### 受保護的方法  
  
|名稱|說明|  
|--------|--------|  
|[Implements::CanCastTo 方法](../windows/implements-cancastto-method.md)|取得指定介面的指標。|  
|[Implements::CastToUnknown 方法](../windows/implements-casttounknown-method.md)|取得基礎 IUnknown 介面的指標。|  
|[Implements::FillArrayWithIid 方法](../windows/implements-fillarraywithiid-method.md)|插入目前第零個樣板參數指定的介面 ID 至指定的陣列元素。|  
  
### 受保護的常數。  
  
|名稱|說明|  
|--------|--------|  
|[Implements::IidCount 常數](../windows/implements-iidcount-constant.md)|保留已實作的介面 ID 數目。|  
  
## 繼承階層  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `ImplementsBase`  
  
 `ImplementsHelper`  
  
 `Implements`  
  
## 需求  
 **標頭：**implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)