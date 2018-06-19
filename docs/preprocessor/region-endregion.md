---
title: 地區、 endregion |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs:
- C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5590d2b251d86a9d20b62bfdb3d5bf929e3d92d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839443"
---
# <a name="region-endregion"></a>region、endregion
**#pragma 區域**可讓您指定一段程式碼，您可以展開或摺疊時使用[大綱功能](/visualstudio/ide/outlining)Visual Studio 程式碼編輯器。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
#### <a name="parameters"></a>參數  
 `comment` (選擇性)  
 會顯示在程式碼編輯器中的註解。  
  
 *名稱*（選擇性）  
 區域的名稱。  此名稱會顯示在程式碼編輯器中。  
  
## <a name="remarks"></a>備註  
 **#pragma endregion**的結束標記 **#pragma 區域**區塊。  
  
 A`#region`區塊必須以結束 **#pragma endregion**。  
  
## <a name="example"></a>範例  
  
```  
// pragma_directives_region.cpp  
#pragma region Region_1  
void Test() {}  
void Test2() {}  
void Test3() {}  
#pragma endregion Region_1  
  
int main() {}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)