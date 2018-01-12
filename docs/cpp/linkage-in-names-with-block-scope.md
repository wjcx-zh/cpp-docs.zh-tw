---
title: "區塊範圍的名稱連結 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- block scope [C++]
- external linkage, scope linkage rules
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fed200614ef6385aab24755e5eb202fd875494c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linkage-in-names-with-block-scope"></a>區塊範圍的名稱連結
下列連結規則適用於具有區塊範圍的名稱 (區域名稱)：  
  
-   名稱宣告為`extern`除非先前已宣告為具有外部連結**靜態**。  
  
-   具有區塊範圍的所有其他名稱都不具有連結。  
  
## <a name="see-also"></a>請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)