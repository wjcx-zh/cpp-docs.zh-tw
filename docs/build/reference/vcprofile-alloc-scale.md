---
title: "VCPROFILE_ALLOC_SCALE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VCPROFILE_ALLOC_SCALE
dev_langs:
- C++
helpviewer_keywords:
- VCPROFILE_ALLOC_SCALE environment variable
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7b441f41106544633bd691c409fa04c989146f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE
修改保留設定檔的資料配置的記憶體的數量。  
  
## <a name="syntax"></a>語法  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### <a name="parameters"></a>參數  
 `scale_value`  
 您想要執行測試案例的記憶體容量的小數位數值。  預設為 1。  
  
## <a name="remarks"></a>備註  
 在罕見的情況下，則不會有記憶體不足，無法支援執行測試案例時，收集分析資料。  在這些情況下，您可以增加使用的記憶體數量`VCPROFILE_ALLOC_SCALE`。  
  
 如果您收到錯誤訊息表示您有記憶體不足，無法在測試回合期間，較大值指派給`VCPROFILE_ALLOC_SCALE`，直到執行完成，但沒有記憶體不足錯誤測試。  
  
## <a name="example"></a>範例  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## <a name="see-also"></a>請參閱  
 [特性指引最佳化的環境變數](../../build/reference/environment-variables-for-profile-guided-optimizations.md)