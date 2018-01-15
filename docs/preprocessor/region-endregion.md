---
title: "地區、 endregion |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs: C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad2eb3d094447ae3ae35b0dbe9dc0fef2fe06710
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 **#pragma endregion**的結束標記**#pragma 區域**區塊。  
  
 A`#region`區塊必須以結束**#pragma endregion**。  
  
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
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)