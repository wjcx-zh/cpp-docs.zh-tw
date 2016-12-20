---
title: "RuntimeClass 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClass 類別"
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示繼承指定之介面數目的具現化類別，並提供指定的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、傳統 COM 和弱式參考支援。  
  
 您通常會從 `RuntimeClass` 衍生您自己的 WRL 類型，因為這個類別會實作 `AddRef`、 `Release`和 `QueryInterface`，並協助管理模組的完整參考計數。  
  
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
class RuntimeClass : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT, RuntimeClassFlags<WinRt>>;  
  
template <  
   unsigned int classFlags,  
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
class RuntimeClass<RuntimeClassFlags<classFlags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT, RuntimeClassFlags<classFlags> >;  
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
  
 `classFlags`  
 一個或多個 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值的組合。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[RuntimeClass::RuntimeClass 建構函式](../windows/runtimeclass-runtimeclass-constructor.md)|初始化 RuntimeClass 類別目前的執行個體。|  
|[RuntimeClass::~RuntimeClass 解構函式](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|取消初始化 RuntimeClass 類別目前的執行個體。|  
  
## 繼承階層架構  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `RuntimeClass`  
  
## 需求  
 **標頭：**implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)