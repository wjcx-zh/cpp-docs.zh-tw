---
title: "編譯器錯誤 C3888 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 26e55c8a675ada3fd2e88976bc9d9a51cfa8b751
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3888"></a>編譯器錯誤 C3888
'name' : C++/CLI 不支援與這個常值資料成員關聯的常數運算式  
  
 使用 *常值* 關鍵字所宣告的 [名稱](../../windows/literal-cpp-component-extensions.md) 資料成員，是以編譯器不支援的值進行初始化。 編譯器僅支援常數整數、列舉或字串類型。 **C3888** 錯誤的可能原因是資料成員使用位元組陣列進行初始化。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查宣告的常值資料成員是支援的類型。  
  
## <a name="see-also"></a>另請參閱  
 [名稱](../../windows/literal-cpp-component-extensions.md)
