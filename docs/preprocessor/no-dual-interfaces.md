---
title: no_dual_interfaces |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8923adb4cf2e92d72bf656064c6de8fc66e2a91
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850778"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**C + + 特定的**  
  
 變更編譯器產生雙重介面方法之包裝函式的方式。  
  
## <a name="syntax"></a>語法  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>備註  
 一般而言，包裝函式將會透過介面的虛擬函式表呼叫方法。 與`no_dual_interfaces`，包裝函式會改為呼叫**idispatch:: Invoke**叫用方法。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)