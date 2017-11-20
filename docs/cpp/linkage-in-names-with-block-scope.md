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
ms.openlocfilehash: 0549538ba2af256d3a98b83dcb691327e387de9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="linkage-in-names-with-block-scope"></a>區塊範圍的名稱連結
下列連結規則適用於具有區塊範圍的名稱 (區域名稱)：  
  
-   名稱宣告為`extern`除非先前已宣告為具有外部連結**靜態**。  
  
-   具有區塊範圍的所有其他名稱都不具有連結。  
  
## <a name="see-also"></a>另請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)