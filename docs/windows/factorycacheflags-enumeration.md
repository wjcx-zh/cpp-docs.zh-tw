---
title: FactoryCacheFlags 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
dev_langs:
- C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ba3d9b75ff72399e1b9a027c937c24bba4a6c37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874326"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags 列舉
決定是否要快取處理站物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>備註  
 根據預設，處理站快取原則指定為[ModuleType](../windows/moduletype-enumeration.md)樣板參數，當您建立[模組](../windows/module-class.md)物件。 若要覆寫這項原則，請指定`FactoryCacheFlags`時建立 factory 物件的值。  
  
|||  
|-|-|  
|`FactoryCacheDefault`|快取原則`Module`物件使用。|  
|`FactoryCacheEnabled`|可讓處理站快取不論`ModuleType`樣板參數，用來建立`Module`物件。|  
|`FactoryCacheDisabled`|停用處理站快取不論`ModuleType`樣板參數，用來建立`Module`物件。|  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)