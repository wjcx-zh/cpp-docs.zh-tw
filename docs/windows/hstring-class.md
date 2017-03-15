---
title: "HString 類別 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HString"
dev_langs: 
  - "C++"
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供對管理 HSTRING 控制代碼的支援。  
  
## 語法  
  
```cpp  
class HString;  
```  
  
## 備註  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 透過 HSTRING 控制代碼提供對字串的存取。  HString 類別提供方便函式和運算子以簡化 HSTRING 控制代碼的使用。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[HString::HString 建構函式](../windows/hstring-hstring-constructor.md)|初始化 HString 類別的新執行個體。|  
|[HString::~HString 解構函式](../windows/hstring-tilde-hstring-destructor.md)|終結 HString 類別目前的執行個體。|  
  
### Members  
  
|名稱|描述|  
|--------|--------|  
|[HString::Set 方法](../windows/hstring-set-method.md)|設定目前 HString 物件中的值為指定的寬字元字串或 HString 參數。|  
|[HString::Attach 方法](../windows/hstring-attach-method.md)|將指定的 HString 物件與目前的 HString 物件產生關聯。|  
|[HString::CopyTo 方法](../windows/hstring-copyto-method.md)|將目前的 HString 物件複製到 HSTRING 物件。|  
|[HString::Detach 方法](../windows/hstring-detach-method.md)|取消指定之 HString 物件與其基礎值的關聯。|  
|[HString::GetAddressOf 方法](../windows/hstring-getaddressof-method.md)|擷取基礎 HSTRING 控制代碼的指標。|  
|[HString::Get 方法](../windows/hstring-get-method.md)|擷取基礎 HSTRING 控制代碼的值。|  
|[HString::Release 方法](../windows/hstring-release-method.md)|刪除基礎字串值，並將目前 HString 物件初始化為空值。|  
|[HString::MakeReference 方法](../windows/hstring-makereference-method.md)|從指定的字串參數建立 HStringReference 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[HString::Operator\= 運算子](../windows/hstring-operator-assign-operator.md)|將另一個 HString 物件的值移至目前 HString 物件。|  
|[HString::Operator\=\= 運算子](../windows/hstring-operator-equality-operator.md)|表示兩個參數是否相等。|  
|[HString::Operator\!\= 運算子](../windows/hstring-operator-inequality-operator.md)|表示兩個參數是否不相等。|  
  
## 繼承階層架構  
 `HString`  
  
## 需求  
 **標題：**corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)