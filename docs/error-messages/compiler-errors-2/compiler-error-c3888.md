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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 4b85385c97f5873c1b370cd72f0866439263f787
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3888"></a>編譯器錯誤 C3888
'name' : C++/CLI 不支援與這個常值資料成員關聯的常數運算式  
  
 *名稱*資料成員宣告與[常值](../../windows/literal-cpp-component-extensions.md)關鍵字初始化編譯器不支援的值。 編譯器僅支援常數整數、列舉或字串類型。 **C3888** 錯誤的可能原因是資料成員使用位元組陣列進行初始化。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查宣告的常值資料成員是支援的類型。  
  
## <a name="see-also"></a>另請參閱  
 [常值](../../windows/literal-cpp-component-extensions.md)
