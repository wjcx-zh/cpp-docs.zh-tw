---
title: "FactoryCacheFlags 列舉 | Microsoft Docs"
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
  - "module/Microsoft::WRL::FactoryCacheFlags"
dev_langs: 
  - "C++"
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FactoryCacheFlags 列舉
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

決定是否要快取 factory 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>備註  
 根據預設，處理站快取原則指定為 [ModuleType](../windows/moduletype-enumeration.md) 樣板參數，當您建立 [模組](../windows/module-class.md) 物件。 若要覆寫此原則，請指定 `FactoryCacheFlags` 時建立 factory 物件的值。  
  
|||  
|-|-|  
|`FactoryCacheDefault`|快取原則 `Module` 物件使用。|  
|`FactoryCacheEnabled`|可讓處理站快取不論 `ModuleType` 樣板參數，用來建立 `Module` 物件。|  
|`FactoryCacheDisabled`|停用處理站快取不論 `ModuleType` 樣板參數，用來建立 `Module` 物件。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft:: wrl 命名空間](../windows/microsoft-wrl-namespace.md)