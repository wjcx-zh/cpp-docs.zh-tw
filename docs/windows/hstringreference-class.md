---
title: "HStringReference 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference"
dev_langs: 
  - "C++"
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HStringReference 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示從現有字串建立的 HSTRING。  
  
## 語法  
  
```cpp  
class HStringReference;  
```  
  
## 備註  
 新的 HSTRING 中支援緩衝區的存留期不受 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]管理。  呼叫端會在堆疊框架上配置來源字串，以避免堆積配置和排除記憶體遺漏的風險。  此外，呼叫端必須確保資料來源在附加的 HSTRING 的存留期內維持不變。  如需詳細資訊，請參閱[WindowsCreateStringReference function](http://msdn.microsoft.com/zh-tw/0361bb7e-da49-4289-a93e-de7aab8712ac)。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[HStringReference::HStringReference 建構函式](../windows/hstringreference-hstringreference-constructor.md)|初始化 HStringReference 類別的新執行個體。|  
  
### Members  
  
|成員|描述|  
|--------|--------|  
|[HStringReference::CopyTo 方法](../windows/hstringreference-copyto-method.md)|將目前的 HStringReference 物件複製到 HSTRING 物件。|  
|[HStringReference::Get 方法](../windows/hstringreference-get-method.md)|擷取基礎 HSTRING 控制代碼的值。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[HStringReference::Operator\= 運算子](../windows/hstringreference-operator-assign-operator.md)|將另一個 HStringReference 物件的值移至目前 HStringReference 物件。|  
|[HStringReference::Operator\=\= 運算子](../windows/hstringreference-operator-equality-operator.md)|表示兩個參數是否相等。|  
|[HStringReference::Operator\!\= 運算子](../windows/hstringreference-operator-inequality-operator.md)|表示兩個參數是否不相等。|  
  
## 繼承階層架構  
 `HStringReference`  
  
## 需求  
 **標題：**corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)