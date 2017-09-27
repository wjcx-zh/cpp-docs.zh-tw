---
title: "執行階段類型資訊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ec36acfdba274a0eaf36c099da11f4462f2aad70
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="run-time-type-information"></a>執行階段類型資訊
執行階段類型資訊 (RTTI) 是一項機制，可在程式執行期間判斷物件的類型。 C++ 語言中加入 RTTI 的原因在於，有許多類別庫的廠商本身實作這項功能。 這樣會導致程式庫之間不相容。 因此，在語言層級支援執行階段類型資訊的需求變得很明確。  
  
 為避免混淆，這裡討論的 RTTI 幾乎完全限於指標。 不過，所討論的概念也適用於參考。  
  
 執行階段類型資訊有三個主要的 C++ 語言項目：  
  
-   [Dynamic_cast](../cpp/dynamic-cast-operator.md)運算子。  
  
     用於多型類型的轉換。  
  
-   [Typeid](../cpp/typeid-operator.md)運算子。  
  
     用於識別物件的實際類型。  
  
-   [Type_info](../cpp/type-info-class.md)類別。  
  
     用來保存 `typeid` 運算子傳回的類型資訊。  
  
## <a name="see-also"></a>另請參閱  
 [轉型](../cpp/casting.md)
