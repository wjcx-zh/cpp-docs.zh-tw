---
title: Managed 類型和 main 函式 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- main function, in managed applications
- managed code, main() function
ms.assetid: 9d0e9620-58c4-4dac-a0e1-ffeb95f80fa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6024f4b6e72fa997f816f7fee0b76778c5ebfc4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131302"
---
# <a name="managed-types-and-the-main-function-ccli"></a>Managed 類型和 main 函式 (C++/CLI)
在撰寫應用程式使用 **/clr**的引數**main （)** 函式不能是 managed 型別。  
  
 是正確的簽章的範例：  
  
```  
// managed_types_and_main.cpp  
// compile with: /clr  
int main(int, char*[], char*[]) {}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Managed 類型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)