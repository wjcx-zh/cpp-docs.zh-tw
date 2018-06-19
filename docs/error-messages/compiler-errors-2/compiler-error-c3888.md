---
title: 編譯器錯誤 C3888 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c11c897f35a6c395c4bc6ee6a64be51fa810911b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270660"
---
# <a name="compiler-error-c3888"></a>編譯器錯誤 C3888
'name' : C++/CLI 不支援與這個常值資料成員關聯的常數運算式  
  
 使用 *常值* 關鍵字所宣告的 [名稱](../../windows/literal-cpp-component-extensions.md) 資料成員，是以編譯器不支援的值進行初始化。 編譯器僅支援常數整數、列舉或字串類型。 **C3888** 錯誤的可能原因是資料成員使用位元組陣列進行初始化。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查宣告的常值資料成員是支援的類型。  
  
## <a name="see-also"></a>另請參閱  
 [名稱](../../windows/literal-cpp-component-extensions.md)