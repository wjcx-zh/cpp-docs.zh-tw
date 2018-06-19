---
title: 區塊範圍的名稱連結 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab7758e962c028c4746836e470ee43eaab510f9e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418883"
---
# <a name="linkage-in-names-with-block-scope"></a>區塊範圍的名稱連結
下列連結規則適用於具有區塊範圍的名稱 (區域名稱)：  
  
-   名稱宣告為`extern`除非先前已宣告為具有外部連結**靜態**。  
  
-   具有區塊範圍的所有其他名稱都不具有連結。  
  
## <a name="see-also"></a>另請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)