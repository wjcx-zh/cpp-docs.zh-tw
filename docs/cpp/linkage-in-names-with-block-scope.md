---
title: "區塊範圍的名稱連結 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- block scope [C++]
- external linkage, scope linkage rules
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: 8
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
ms.openlocfilehash: de093c90e0da4a906d8aefebfb7048733c1a1f1d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="linkage-in-names-with-block-scope"></a>區塊範圍的名稱連結
下列連結規則適用於具有區塊範圍的名稱 (區域名稱)：  
  
-   名稱宣告為`extern`除非先前已宣告為具有外部連結**靜態**。  
  
-   具有區塊範圍的所有其他名稱都不具有連結。  
  
## <a name="see-also"></a>另請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)
